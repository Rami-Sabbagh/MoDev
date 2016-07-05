## /Src/Modes/Stomp/init.el
This is a clone of stomp gamemode.

```lua
local base = require("Engine/effectBase");

local effect = base:newEffect("Stomp");
effect.meta = {
	name = "Stomp",
	description = "Jump on another player to eliminate them!",
	wincondition = "Last one standing wins",
	losecondition = "Getting jumped on kills you",
	playerwon = "LIKES TO BE ON TOP",	
	author = "Those Awesome Guys",
	navMeshAI = true,
	localOnly = true,

	time = 15
}

local utility = require("Src/MinigameUtility")
local networking = require("Src/Server/Networking")
local level;
local aliveNow;
local aijoes;
local joeArray;

function effect:init(Level,JoeArray)

	utility:init(Level,JoeArray)
	level = Level;
	joeArray = JoeArray;

	aliveNow = utility:GetAlive()
	aijoes = utility:GetAI()

	if not networking.isClient then
		level.AddAI = function(joe)
  			aijoes[#aijoes+1] = joe
		end
	end

	self:clearStompFlags()

end

function effect:clear()
	self:clearStompFlags()
	utility:Done()
end

function effect:clearStompFlags()
	for _,joe in pairs(joeArray) do
		joe.hasStompedThisRound = false
	end
end

function effect:update(dt)
	utility:DebugUpdate()

	if not networking.isClient then
		for i=1,#aijoes do 
			effect.AIBehavior(aijoes[i],dt)
		end
	end
end

function effect.JoeTileCollision(joeFixture, tileFixture, col)
	if joeFixture:getUserData()[1] == "JoeFeet" and not tileFixture:isSensor() then
		local joe = joeFixture:getUserData()[2]
		joe.noGroundAfterStomp = nil
	end
end

function effect.JoeJoeCollision(joe1Fixture,joe2Fixture,col)
	local joeName1 = joe1Fixture:getUserData()[1];
	local Joe1 = joe1Fixture:getUserData()[2];
	local joeName2 = joe2Fixture:getUserData()[1];
	local Joe2 = joe2Fixture:getUserData()[2];

	if Joe1.dead or Joe2.dead then return end

    local x, y   = Joe1.b2Object.body:getLinearVelocity()
    local x2, y2 = Joe2.b2Object.body:getLinearVelocity()
	
	if joeName1 == "JoeFeet" and joe2Fixture:isSensor() == false and y - y2 > 0 then
		if not networking.isClient then
			Joe2.dead = true;--kill that Joe!
			Joe2.health = 0;

			Joe1.b2Object.body:setLinearVelocity(x,-1000)

			Joe1.feetColArray = {};--to override what the JoeJoeCollision in TileAI does
			Joe1.jumping = true;
			Joe1.forcedJump = true;
			Joe1.touchedGround = false;
			Joe1.noGroundAfterStomp = true;
			Joe1.anim:gotoAndPlay("Jump","JumpLoop");
		end

		if Joe1:isFirstLocalHumanPlayer() then
			Joe1.hasStompedThisRound = true
		end
	end
end

function effect.AIBehavior(j,dt)
	local char = j;
	local AI = j.AI;

	--if it fails, do not reattempt, check for a new goal right away so as not to slow down
	--if(AI.onFail == nil)then AI.onFail = function(self) self.givenPath = nil end end

	--Callibrate aggressiveness 
	if AI.aggro == nil then 
		--This aggro factor controls how often it attacks versus how often it retreats
		AI.aggro = math.random() * .7 + .3
		AI.state = "attack"
		AI.stateCount = 0;
		AI.jumpCountDelay = math.random() * 1
		--print(char.skinName .. " is " .. tostring(AI.aggro * 100) .. "% aggressive")
		local rand = math.random()
		if(rand > AI.aggro)then 
			AI.state = "retreat"
		else 
			AI.state = "attack"
		end 

		AI.warmingUp = 2;--Time in seconds they spend warming up (running randomly around level)
	end

	--Get nearest Joe (since all difficulty behaviors need it in some way) 
	local chaseJoe = {dist=0,joe=nil} --get a random joe
	for i=1,#aliveNow do 
		local joe = aliveNow[i]
		if(joe ~= char)then 
			local dx = joe.x - char.x; 
			local dy = joe.y - char.y; 
			local dist = math.sqrt(dx * dx + dy * dy)
			if(chaseJoe.joe == nil)then chaseJoe = {dist=dist,joe=joe} end
			if(dist < chaseJoe.dist)then chaseJoe = {dist=dist,joe=joe} end
		end 
	end
	AI.chaseJoe = chaseJoe;

	local StompWithinRange = function(range)
		if AI.chaseJoe.joe == nil then return end
		if AI.chaseJoe.dist < 768 then 
			AI.overwritekeys = {}
			local dy = AI.chaseJoe.joe.y - (char.y+256);
			local dx = AI.chaseJoe.joe.x - char.x;
			if dy < 0 then 
				AI.overwritekeys.jump = true 
				if AI.overjumpcounter == nil then AI.overjumpcounter = 0 end 
				AI.overjumpcounter = AI.overjumpcounter + dt; 
				if AI.overjumpcounter > AI.jumpCountDelay then
					AI.overwritekeys.jump = nil
					AI.overjumpcounter = nil
					AI.jumpCountDelay = math.random() * 1
				end
			else 
				AI.overjumpcounter = nil
			end
			if dx > 0 then AI.overwritekeys.right = true else AI.overwritekeys.left = true end 
		end 
	end

	local ChaseClosest = function(dt)
		if AI.chaseJoe.joe == nil then return end

		--recheck every X time
		if AI.chaseTimer == nil then AI.chaseTimer = 0 else AI.chaseTimer = AI.chaseTimer - dt end

		if AI.chaseTimer <= 0 then
			AI.chaseTimer = AI.chaseTimer + 2
			AI:goTo(AI.chaseJoe.joe.x,AI.chaseJoe.joe.y)
		end
	end

	local Avoid = function()
		if AI.chaseJoe.joe == nil then return end
		local dx = AI.chaseJoe.joe.x - char.x;
		if math.abs(dx) < 768 and AI.chaseJoe.joe.y < char.y - 256 then 
			AI.overwritekeys = {}
			if(dx < 0)then AI.overwritekeys.right = true else AI.overwritekeys.left = true end 
		end
	end

	if AI.difficulty == 1 and AI.warmingUp <= 0 then 
		-- Move randomly around the level. 
		if not AI:isBusy() then
			AI:runRandomly()
		end

		--If another Joe within range, attempt to stomp (override running randomly)
		StompWithinRange(768)
	end 

	if AI.difficulty == 2 and AI.warmingUp <= 0 then 
		---Chase closest player
		ChaseClosest(dt)
		---If in range stomp
		StompWithinRange(768)
	end 

	if AI.difficulty == 3 and AI.warmingUp <= 0 then 
		--<<< Always tries to maintain high ground, always detecting if a player is above to avoid, and always trying to stomp
		
		AI.stateCount = AI.stateCount + dt; 
		if AI.stateCount > 2 then 
			AI.stateCount = 0; 
			local rand = math.random()
			if(rand > AI.aggro)then 
				AI.state = "retreat"
			else 
				AI.state = "attack"
			end 
		end

		if AI.state == "attack" then 
			---Chase closest player
			ChaseClosest(dt)
		end 
		if AI.state == "retreat" then 
			-- Move randomly around the level. 
			if not AI:isBusy() then 
				AI:runRandomly()
			end
		end
		---If in range stomp
		StompWithinRange(768)
		--Avoid if in range and above
		Avoid()
	end

	if level.started then 
		AI.warmingUp = AI.warmingUp - dt; 
	end
	if AI.warmingUp > 0 then 
		--Just go to a random tile
		if not AI:isBusy() then 
			AI:runRandomly()
		end
	end

	AI:step(dt);
end

return effect;
```
