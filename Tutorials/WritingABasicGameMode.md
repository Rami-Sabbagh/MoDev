# How to write a basic gamemode for MoD
In this tutorial we will teach you how to write your own gamemode for MoD. This documentation is intended to be used by programmers who already knows how to program using Lua & LÖVE Framework.

## Gamemode files structure
###### Be sure to have a valied mod folder setup for your mod, If you don't know how, Follow [this](/Tutorials/CreatingASRCMod.md) tutorial first.
* /Mods/YourMod/Src/Modes/YourGamemode/ **Here most of your gamemode files go here**
* /Mods/YourMod/Src/Modes/YourGamemode/init.lua **This is the lua code file of your gamemode**
* /Mods/YourMod/Src/Modes/YourGamemode/Icon.png **This is icon image of your gamemode**
* /Mods/YourMod/Src/Modes/YourGamemode/Anim.webm **(Optional) This is the animation video of your gamemode that showcase how to play it**
* /Mods/YourMod/Src/Modes/YourGamemode/Thumb.webm **(Optional) This is a small version of the animation video of your gamemode that showcase how to play it but in lower quality**

## Starting with the init.lua file, The hardest one :P
Now create the ini.lua and past in the gamemode bones.
```lua
local base = require("Engine/effectBase") --Require the base template.

local effect = base:newEffect("BallEater") --Create a new effect, gamemodes are custom effects !
effect.meta = { --The meta, This contains info about the gamemode.
    name = "BallEater", --The name of the gamemode to display in the game.
    description = "A gamemode where you have to eat a blue ball before anyone else", --The description of the gamemode.
    wincondition = "The one who eats the ball first will win", --How to win this gamemode.
    losecondition = "Not eating the blue ball will kill you !", --How to loss this gamemode.
    playerwon = "Loves eating blue balls", --The status msg to show at the points screen.
    author = "MoveOrDevelop Team", --The author name.
    navMeshAI = true, --For AIs to use the navigation mesh 
    localOnly = true, --This gamemode is local (non twitch gamemode).

    time = 15 --The time in seconds for this gamemode.
}
```