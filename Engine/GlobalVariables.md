# Engine/GlobalVariables.el
This file containes all the global variables available in the game enviroment.

## GetImageQuality: **Function**
Returns the image quality.
```lua
local quality = GetImageQualtity(imgName)
```
#### Args:
* imgName: **String**: The name of the image, Example: "Joe"

#### Returns:
* quality: **String**: The quality of the image, can be "Hight", "Mid" or "Low".

## Round: **Function**
Rounds the number float value.
```lua
local roundedNum = Round(num)
```
#### Args:
* num: **Number**: The number to round.

#### Returns:
* roundedNum: **Number**: The rounding result.

## StringToArray: **Function**
Converts the string "1,2,3,4" to a table of numbers {1,2,3,4}
```lua
local array = StringToArray(str)
```
#### Args:
* str: **String**: The string to covert.

#### Returns:
* array: **Table**: The result array.

## isempty: **Function**
Returns if the string is empty or not.
```lua
local bool = isempty(str)
```
#### Args:
* str: **String / Nil**: The string to check.

#### Returns:
* bool: **Boolean**: Whether the string is empty or not.

## _Version: **String**
The current game version.

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

## _StartupCommands: **Table**
To save the initial commands from startup.ini

## _DEFAULT_MIPMAP: **Number**
Unknown yet, but it's value is -5;

## _Mouse: **Table**
Used for getting mouse position.
Content: x (number), y (number), worldX (number), worldY (number)

## _recoveryLevelData: **Nil / LevelData**
Keeps track of level being edited in the editor to save in case of crash.

## _cam: **Table**
Global camera object.

## _Grid: **Table**
Used to keep track of objects on screen, using in Engine/SpatialHash.el

## _SHADER: **Table**
Global shader constant, to know whether to turn off shaders or keep them.

## _CANVAS: **Table**
Global canvas constant, to know whether canvases are supported or not.

## _DXT: **Table**
Global dxt constant, to know whether dxt is supported or not.

## _prevShaderData: **Table**
Used to avoid resending shader data.

## _ShaderErrors: **String**
Defaults to empty string, changes to the error message incase of a shader errors (That's what I guess).

## _POSTPROCESS: **Boolean**
Whether post process is enabled in the advanced video settings page or not.

## _CHROMATICENABLED: **Boolean**
Whether chromatic aberration is enabled in the advanced video settings page or not.

## _OCCLUSION: **Boolean**
Whether ambient occlusion is enabled in the advanced video settings page or not.

## _FSAA: **Number**
Antialiasing level, 0 Means disabled.

## _DUST_POOFS: **Boolean**
Whether dust poofs are enabled in the advanced video settings page or not.

## _DEBUGInfo: **Boolean**
Whether developer console is enabled in the general settings page or not, To enable extra debugging prints.

## _PROPS: **Boolean**
Whether props are enabled in the advanced video settings page or not.

## _VIBRATION: **Boolean**
Whether controller rumble is enabled in the general settings page or not.

## _SHAKE: **Boolean**
Whether screenshake is enabled in the advanced video settings page or not.

## _PULSE: **Boolean**
Whether rhythm pulse is enabled in the advanced video settings page or not.


## _mouseButtons: **Table**
Used in Events.el, for detecting when mouse buttons are held.

## _mouseTap: **Table**
Used in Events.el, for detecting when a mouse button is tapped.

## _KeyTap: **Table** 
Used in Events.el for detecting key taps. It reset at the end of the update function in main.lua

## _KeyPress: **Table**
Used in Events.el for detecting key presses. Remains true until the key is released.

## _cKeyTap: **Table**
Stands for "Console Key Tap", must seperate these to seperate focus. Use this for text and console typing. Key Tap is used for in-game key presses only.

## _cKeyInput: **Table**
Stands for "Console Key Input", must seperate these to seperate focus. Use this for text and console typing. Key Tap is used for in-game key presses only.

## _cKeyPress: **Table**
Stands for "Console Key Press", must seperate these to seperate focus. Use this for text and console typing. Key Tap is used for in-game key presses only.

## _JoyTap: **Table**
Used in Events.el for detecting joystick taps. Doesn't work if game isn't focused.

## _JoyPress: **Table**
Used in Events.el for detecting key presses. Doesn't work if game isn't focused.

## _world: **Nil / LÖVE Physics world object**
Initalized in GameSetup.el, the box2d game world.

## _Gravity: **Number**
The y gravity of the b2world.

## _b2Factor: **Number**
Box2d time factor.

## _RenderArray: **Table**
Holds sub arrays of special things that need to be rendered, like UI objects.
Contains: UI (table), GUI (table), Dynamic (table)

## _numOfObjectsOnScreen: **Number**
To log the number of objects being rendered in the current frame.

## _SoundArray: **Table**
Holds sounds that are currently updating/playing.

## _Batches: **Table**
Holds the sprite batches to be rendered. They are added as normal objects.

## _BatchNames: **Table**
Associative array to hold them by name.

## _globalTimers: **Table**
Used in GlobalTimer.lua to sync certain animations.

## _b2Scale: **Number**
Used to scale up the graphics from the box2d bodies.
It is used in all b2Object.lua functions to divide game coordinates into box2d coordinates before use.
It is used in GameObject.lua to scale the box2d functions up to game coordinates for making objects follow their box2d bodies and for debug drawing.

## _miscRenders: **Table**
This is for rendering things at a specific depth without having to do it manually.

## _StartMode: **String**
The game starting state file name, Defaults to "Splash".

## _debugThing, _debugThing2, _debugThing3, _debugTriangles ,_debugShapes: **Tables**
Debugging tables.

## _debugModes: **Table**
The debug modes for the editor I guess.
Contains: "none", "classic", "ai", "netcode", "navmesh", "navmesh-edit", "performance".

## _debugMode: **String**
The current debug mode for the editor I guess.

## _TEXTUREQUALITY: **String**
The current quality of the textures, Defaults to "High".

## _TEXTURESCALES: **Table**
The texture scales according to the current texture quality.
Contains: High = 1, Medium = 0.75, Low = 0.5

## _SERVER: **Nil**
The game server thread.

## _JOYFRAMEDELAY: **Number**
Delays a check in Events.lua

## _ImageQualities: **Table**
Stores each image's current quality

## _GHOST_UNLOCK_LEVEL: **Number**
The player level required to unlock the ghost, Defaults to 6.

## _ROUNDS_PER_MINUTE: **Number**
The amount of router per minute, Defaults to 1.

## Unknown Variables:
* **Booleans:**
  * _INTERNET
  * _ERROR_REPORTING
  * _AntialiasSupported
  * _EditorGrid
  * _GamepadOutput
  * _OutOfFocusSound
  * _POSTPROCESS_UI
  * _PAUSE
  * _BLUR
  * _Mipmap
  * _SPLASH
  * _SPLATTER
  * _BoundKeys
  * _LiveAIMatch

* **Numbers:*
  * _TimePlayed
  * _currentFrameTime
  * _FPScap
  * _debugModeCycler

* **Strings:**
  * _currentModeName
  * _LastGameType

* **Tables:**
  * _GlobalMessageQueue
  * _AdminSteamIds
  * _SoundsData
  * _SoundsDuration
  * _TweenTimeTo
  * _EmailThread
  * _cam2
  * _ShaderArray
  * _mouseUp
  * _KeyInput
  * _GamepadTap
  * _GamepadPress
  * _JoySticks
  * _DefaultCursor
  * _UnlockedHiddenCharacters
  * _miscUIRenders
  *  _memoryTest
