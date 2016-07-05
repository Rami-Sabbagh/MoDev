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

## base:init: **Function**
Initialized once the effect is run.
This is used to initialize all your stuff or create objects!
```lua
function effect:init(level, JoeArray)
  
end
```
