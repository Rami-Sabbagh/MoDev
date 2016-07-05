# Engine/effectBase.el
Base class for creating special coded effects to be applied in the levels.
Also acts as a template for gamemodes.

## Usage:
```lua
local base = require("Engine/effectBase")
```

## base:newEffect: **Function**
Create a new effect / gamemode.
```lua
local effect = base:newEffect(name)
```
#### Arguments:
* name: **String**: The effect / gamemode name.

#### Returns:
* obj: **Object**: The effect / gamemode object.

#### Example:
```lua
local base = require("Engine/effectBase")

local effect = base:newEffect("testGamemode")
```
