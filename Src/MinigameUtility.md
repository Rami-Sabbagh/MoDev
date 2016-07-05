# MinigameUtility.el
This class contains helpful functions that can be used by the minigames.
### Usage:
```lua
local MinigameUtility = require("Src/MinigameUtility")
```

## Utility:givePermakill: **Function**
Sets joe to die forever instead of respawn
```lua
Utility:givePermakill(joe)
```

## Utility:init: **Function**
Setup things like the currently alive joe's and the dead joe's arrays.
And sets up the Drop in/out functions to allow the creation/deletion of a Joe without breaking the other systems.
```lua
Utility:init(Level,JoeArray)
```

## Utility:GetAlive: **Function**
Returns the array of joe's alive right now.
```lua
local AliveJoes = Utility:GetAlive()
```

## Utility:GetDead: **Function**
Returns an array of the joe's that died in ORDER that they died in.
```lua
local deathOrder = Utility:GetDead()
```

## Utility:rankArrayToScoreArray: **Function**
Unknown yet.
```lua
local ScoreArray = Utility:rankArrayToScoreArray(rankArray,scoresToAssign)
```

## Utility:GetAI: **Function**
Unknown yet.
> Developer Comment: do I really have to keep explaining?
```lua
local aiArray = Utility:GetAI()
```

## Utility:Done: **Function**
Returns the original Joe's respawn functions (turns off permakill)
```lua
Utility:Done()
```

## Utility:DebugUpdate: **Function**
Unknown yet.
> Developer Comment: temporary debug thing to allow Xelu to place splats by clicking for screenshot purposes.
```lua
Utility:DebugUpdate(dt)
```
