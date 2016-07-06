# Engine/JoeClass.el
Allows you to create Joe's, with are seperate self contained objects.

Controlling something about all Joe's should be done through this JoeClass.
#### Usage:
```lua
local JoeClass = require("Engine/JoeClass")
```
## JoeClass:newJoe - **Function**
Creates a new joe and adds it to the game.
```lua
local Joe = JoeClass:newJoe(x,y,controltype,scale,ui)
```
#### Arguments:
* x: **Number / Nil**: The x position of the new joe.
* y: **Number / Nil**: The y position of the new joe.
* controltype: **Unknown / Nil**: The controltype of joe, Unknown usage..
* scale: **Number / Nil**: How much to scale the new joe, nil gives 1 scale.
* ui: **Boolean / Nil**: Whether this is a UI joe that doesn't move (Like the scores screen), or A dynamic joe that moves in a b2world.

#### Returns:
* Joe: **JoeClass Instance**: The new joe.

## Joe:applyKnockback - **Function**
Knocks back joe, like the blow back gamemode.
```lua
Joe:applyKnockback(x, y)
```
#### Arguments:
* x: **Number**: The amount of x to knock the player back with.
* y: **Number**: The amount of y to knock the player back with.

## Joe.OnLand - **Callback Function**
Called when joe lands on ground.
Original callback creates the dust poofs affect.
```lua
function Joe.OnLand(joe)
	--Do something here.
	JoeClass.OnLand(joe) --Call the original onland callback so dust poofs happen.
end
```
#### Arguments:
* joe: **JoeClass Instance**: The joe that landed on the ground.