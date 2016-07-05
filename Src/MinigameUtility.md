# MinigameUtility.el
This class contains helpful functions that can be used by the minigames.
### Usage:
```lua
local MinigameUtility = require("Src/MinigameUtility")
```

## MinigameUtility:givePermakill: **Function**
Sets joe to die forever instead of respawn
```lua
MinigameUtility:givePermakill(joe)
```

## MinigameUtility:init: **Function**
Setup things like the currently alive joe's and the dead joe's arrays.
And sets up the Drop in/out functions to allow the creation/deletion of a Joe without breaking the other systems.
```lua
MinigameUtility:init(Level,JoeArray)
```

## MinigameUtility:GetAlive: **Function**
Returns the array of joe's alive right now.
```lua
local AliveJoes = MinigameUtility:GetAlive()
```

## MinigameUtility:GetDead: **Function**
Returns an array of the joe's that died in ORDER that they died in.
```lua
local deathOrder = MinigameUtility:GetDead()
```

## MinigameUtility:rankArrayToScoreArray: **Function**
Unknown yet.
```lua
local ScoreArray = MinigameUtility:rankArrayToScoreArray(rankArray,scoresToAssign)
```

## MinigameUtility:GetAI: **Function**
Unknown yet.
> Developer Comment: do I really have to keep explaining?
```lua
local aiArray = MinigameUtility:GetAI()
```

## MinigameUtility:Done: **Function**
Returns the original Joe's respawn functions (turns off permakill)
```lua
MinigameUtility:Done()
```

## MinigameUtility:DebugUpdate: **Function**
Unknown yet.
> Developer Comment: temporary debug thing to allow Xelu to place splats by clicking for screenshot purposes.
```lua
MinigameUtility:DebugUpdate(dt)
```
