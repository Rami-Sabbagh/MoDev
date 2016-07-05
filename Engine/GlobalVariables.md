# Engine/GlobalVariables.el
This file containes all the global variables available in the game enviroment.

## _Version: **String**
The current game version.

## _GlobalMessageQueue: **Table**
Unknown yet.

## _AdminSteamIds: **Table**
Unknown yet.

## _Fonts: **Table**
Loaded fonts holder.
```lua
love.graphics.setFont(_Fonts["BebasNeue"])
love.graphics.setColor(0,0,0,255)
love.graphics.print("Test",50,50)
```

## _Images: **Table**
Loaded images holder.
```lua
love.graphics.setColor(255,255,255,255)
love.graphics.draw(_Images["Joe"],0,0)
```

## _ImageDatas: **Table**
The image datas of the loaded images.

## _Sounds: **Table**
Loaded sounds holder.

## _SoundsData: **Table**
Unknown yet.

## _SoundsDuration: **Table**
Unknown yet.

## _rawJData: **Table**
**Unparsed** jsons holder.
```lua
local JSON = require("Engine/JSON") --Require the json parser.
local JData = JSON:decode(_rawJData["HugeTextSheetEng"]) --Parse the json data of the Lib/UI/HUD/HugeTextSheetEng.json file
for k,v in pairs(JData) do
  print("["..type(v)//"] "..tostring(k)..": "..tostring(v)) --Print the content of the json data.
end
```

## _rawINIData: **Table**
**Unparsed** inis holder.

## _DrawCalls: **Number**
Counts the number of draw calls per frame (doesn't count stuff rendered in miscRenders) used in Console.lua

## _emptyfn: **Function**
Useless empty function
```lua
_emptyfn = function()end
```
