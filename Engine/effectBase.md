# Engine/effectBase.el
Base class for creating special coded effects to be applied in the levels.
Also acts as a template.

## Usage:
```lua
local base = require("Engine/effectBase")
```

## base:newEffect: **Function**
Create a new effect.
```lua
local effect = base:newEffect(name)
```
#### Arguments:
* name: **String**: The effect name.

#### Returns:
* obj: **Object**: The effect  object.

#### Example:
```lua
local base = require("Engine/effectBase")

local effect = base:newEffect("testEffect")
```

## base:init: **Callback Function**
Initialized once the effect is run.
This is used to initialize all your stuff or create objects!
```lua
function effect:init(level, JoeArray)
  
end
```
#### Arguments:
* level: **Engine Level Class**: The loaded level.
* JoeArray: **Table**: An array containing the joes for the game, usually 4 for MoD.

## base:clear: **Callback Function**
Cleans up anything that was done by this effect when it gets stopped.
Make sure to remove anything you added in the init function!
```lua
function effect:clear()
  
end
```

## base:update: **Callback Function**
The main update function, runs every frame.
```lua
function effect:update(dt)
  
end
```
#### Arguments:
* dt: **Number**: The delta time in seconds (the time between every update call).
