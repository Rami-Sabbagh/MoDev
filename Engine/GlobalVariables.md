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

## _SheetScales: **Table**
Holds scaled down sheet info

## _INTERNET: **Boolean**
Unknown yet.

## _TimePlayed: **Number**
Unknown yet.

## _Padding: **Table**
Holds the p2 padding info for images.

## _IsUI: **Table**
Tells which images were loaded from the UI folder so the engine don't apply mipmapping on them.

## _Dir: **String**
initalized in conf.lua, for accessing files using Lua's i/o library.

## _DEFAULT_LANGUAGE: **String**
The default language for the game to use for first time boot, value: "Eng".

## _LANGUAGE: **String**
The current game language.

## _ERROR_REPORTING: **Boolean**
Unknown yet.

## _INVITE_NOTIFICATION: **Number**
0:None 1:Friends 2:All
Defaults to 2.

## _CONVENTION: **Boolean**
Xelu uses this when he is showing off in a convention ??

## _SPECTATOR_KEYS: **Boolean**
Special screen after successful Speed Run, I guess it's for Xelu in conventions ;)

## _FIRST_TIME_PLAYING: **Boolean**
The name says it, Its used to show the language selection & tutorial level in the first time boot.

## _RELIABLE_UPDATES: **Boolean**
Whether the game update traffic should be sent reliable (true) vs unreliable (false). Defaults to unreliable (false).

## _Screen: **Table**
Initialized in conf.lua, stores the screen/window properties.

## _NetworkConfig: **Table**
Initialized in conf.lua, stores the networking properties.

## _AntialiasSupported: **Boolean**
Unknown yet.

## _StartupCommands: **Table**
To save the initial commands from startup.ini

## _DEFAULT_MIPMAP: **Number**
Unknown yet, but it's value is -5;

## _Mouse: **Table**
Used for getting mouse position.
Content: x (number), y (number), worldX (number), worldY (number)

## _TweenTimeTo: **Table**
Unknown yet.

## _recoveryLevelData: **Nil / LevelData**
Keeps track of level being edited in the editor to save in case of crash.

## _EmailThread: **Table**
> Wow, why would MoveOrDie have an EmailThread ??
Unknown yet.

## _cam: **Table**
Global camera object.

## _cam2: **Table**
Unknown yet.

## _Grid: **Table**
Used to keep track of objects on screen, using in Engine/SpatialHash.el

## _SHADER: **Table**
Global shader constant, to know whether to turn off shaders or keep them.

## _CANVAS: **Table**
Global canvas constant, to know whether canvases are supported or not.

## _DXT: **Table**
Global dxt constant, to know whether dxt is supported or not.

## _ShaderArray: **Table**
Unknown yet.

## _prevShaderData: **Table**
> I guess it's to avoid resending shader data.
Unknown yet.

## _ShaderErrors: **String**
Defaults to empty string, changes to the error message incase of a shader errors (That's what I guess).

## _EditorGrid: **Boolean**
Unknown yet.

