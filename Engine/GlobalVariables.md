# Engine/GlobalVariables.el
This file containes all the global variables available in the game enviroment.

## GetImageQuality: **Function**
Returns the image quality.
```lua
local quality = GetImageQualtity(imgName)
```
#### Arguments:
* imgName: **String**: The name of the image, Example: "Joe"

#### Returns:
* quality: **String**: The quality of the image, can be "Hight", "Mid" or "Low".

## Round: **Function**
Rounds the number float value.
```lua
local roundedNum = Round(num)
```
#### Arguments:
* num: **Number**: The number to round.

#### Returns:
* roundedNum: **Number**: The rounding result.

## StringToArray: **Function**
Converts the string "1,2,3,4" to a table of numbers {1,2,3,4}
```lua
local array = StringToArray(str)
```
#### Arguments:
* str: **String**: The string to covert.

#### Returns:
* array: **Table**: The result array.

## isempty: **Function**
Returns if the string is empty or not.
```lua
local bool = isempty(str)
```
#### Arguments:
* str: **String / Nil**: The string to check.

#### Returns:
* bool: **Boolean**: Whether the string is empty or not.
* 
## CopyTable: **Function**
Copies/Clones a table and all its subtables.
```lua
local newTable = CopyTable(orig)
```
#### Arguments:
* orig: **Table**: The table to copy/clone

#### Returns:
* newTable: **Table**: The cloned table.

## RemoveGhosts: **Function**
It removes spaces from the given string.
```lua
local newStr = RemoveGhosts(str)
```
#### Arguments:
* str: **String**: The string to remove the spaces from.

#### Returns:
* newStr: **String**: The string without spaces.

## split: **Function**
Splits the string according the the given pattern.
```lua
local strTable = split(str,pattern)
```
#### Arguments:
* str: **String**: The string to split.
* pattern: **String**: The pattern to use when splitting.

#### Returns:
* strTable: **Table**: A table containing the splitting results.

#### Example:
```lua
local strTable = split("TADA,TODO,TEDE", ",")
for k, v in ipairs(strTable) do
  print(v)
end
```
**Console Output:**
```
TADA
TODO
TEDE
```

## string.trim: **Function**
Remove trailing and leading whitespace from string, Read more [here](http://en.wikipedia.org/wiki/Trim_(8programming))
```lua
local trimmedStr = string.trim(str)
```
#### Arguments:
* str: **String**: The string to trim.

#### Returns:
* trimmedStr: **String**: The result of trimming.

## table.val_to_str: **String**
Convert any value to string, Supports: Strings,Tables,Numbers,Booleans,Nils
```lua
local str = table.val_to_str(val)
```
#### Arguments:
* val: **Tables / Strings / Numbers / Booleans / Nils**: The value to convert into a string.

#### Returns:
* str: **String**: The result string.

## table.key_to_str: **Function**
Converts a table key to a string.
```lua
local str = table.key_to_str(k)
```
#### Arguments:
* k: **Strings/Numbers/Booleans/Tables/Nils**: The table key.

#### Returns:
* str: **String**: The result string.

## table.tostring: **Function**
Converts a table to string.
```lua
local str = table.tostring(tbl)
```
#### Arguments:
* tbl: **Table**: The table to convert into a string.

#### Returns:
* str: **String**: The result string.

## table.reverse: **Function**
Reverse the table key order.
```lua
local newTable = table.reverse(tbl)
```
#### Arguments:
* tbl: **Table**: The table to reverse its order.

#### Returns:
* newTable: **Table**: The reversed table.

## GetFont: **Function**
Return a font.
```lua
local font = GetFont(FontName, FontSize)
```
#### Arguments:
* FontName: **String**: The name of the font.
* FontSize: **Number**: The size of the font.

#### Returns:
* Font: **LÖVE Font Class**: The font requested.

#### Example:
```lua
love.graphics.setFont(GetFont("BebasNeue",24))
love.graphics.setColor(0,0,0,255)
love.graphics.print("Test",50,50)
```

## replacePrintFunctions: **Function**
A function used internaly by the code to replace love graphics print function with a one that offests some fonts.

## GetDistanceLineToPoint: **Function**
Given a point, a gradient and y intercept, it calculates distance between the point and the line.
```lua
local dist = GetDistanceLineToPoint(x,y,m,c)
```
#### Arguments:
* x: **Number**: The x position of the point.
* y: **Number**: The y position of the point.
* m: **Number**: Y Intercept.
* c: **Number**: Gradient.

#### Returns:
* dist: **Number**: The distance from the line to the point.

## SetCursor: **Function**
Sets the curson image.
```lua
SetCursor(imagename,hotx,hoty)
```
#### Arguments:
* imagename: **String**: The cursor image name.
* hotx: **Number**: The x position of the cursor clicking point.
* hoty: **Number**: The y position of the cursor clicking point.

## GetCursor: **Function**
Returns the current cursor name.
```lua
local cursorName = GetCursor()
```
#### Returns:
* cursorName: **String**: The current cursor name.

#### require2: **Function**:
An advanced version of the require function that returns the latest modified version of the requested file.
```lua
local lib = require2(filepath)
```
#### Arguments:
* filepath: **String**: The path to the file.

#### Returns:
* lib: **Table / String / Number / Boolean / Nil**: The returning var from the library, it will be a table mostly.

#### Example:
```lua
local MinigameUtility = require2("Src.MinigameUtility")
```

## b64enc: **Function**
Encrypts a string using base64.
```lua
local encStr = b64enc(str)
```
#### Arguments:
* str: **String**: The string to encrypt.

#### Returns:
* encStr: **String**: The encrypted string.

## b64dec: **Function**
Decrypts a string ecrypted using base64.
```lua
local decStr = b64dec(encStr)
```
#### Arguments:
* encStr: **String**: The encrypted string to decrypt.

#### Returns:
* decStr: **String**: The decrypted string.

## OpenSaveFolder: **Function**
Opens the game save folder.
```lua
OpenSaveFolder(subfolder)
```
#### Arguments:
* subfolder: **String / Nil**: To open a sub folder in the game save folder.

## table.find: **Function**
Searches for the give value in the table, and return the key if found.
```
local key = table.find(t, value)
```
#### Arguments:
* t: **Table**: The table to search in.
* value: **Table / String / Number / Boolean / Nil**: The value to search for.

#### Returns:
* key: **String / Number / Boolean**: The key of the value if found, false if not found.

## Warning: **Function**
Throws a warning (print) in the console without crashing.
```lua
Warning(msg)
```
#### Arguments:
* msg: **Table / String / Number / Boolean / Nil**: The warning msg to show in the console.

## Shockwave: **Function**
Takes x and y relative to screen
Unknown args :P
```lua
Shockwave(x,y,power,speed,width)
```
#### Arguments:
* x: **Number**: The x position of something..
* y: **Number**: The y position of something..
* power: **Number**: Something..
* speed: **Number**: Something..
* width: **Number**: The width of something..

## ChromaticPulse: **Function**
Creates a chromatic pulse ?
Unknown args :P
```lua
ChromaticPulse(time,power)
```
#### Arguments:
* time: **Number**: Something..
* power: **Number**: Something..

## ScreenShake: **Function**
Creates a screenshake ?
Unknown args :P
```lua
ScreenShake(power, decay)
```
#### Arguments:
* power: **Number**: Something..
* decay: **Number**: Something..

## FreezeFrame: **Function**
Freezes the current frame for a specific time ?
```lua
FreezeFrame(time)
```
#### Arguments:
* time: **Number**: The amount of seconds to freeze the current frame for ?

## math.wrap: **Function**
Wraps the value around the low and high arguments.
```lua
local wrappedNumber = math.wrap(low,value,high)
```
#### Arguments:
* low: **Number**: The smallest range inorder to warp the number.
* value: **Number**: The number to warp.
* high: **Number**: The largest range inorder to warp the number.

#### Returns:
* wrappedNumber: **Number**: The wrapping result.

## GetPrivateIP: **Function**
Get's the private (network) ip of the client, and then calls the given callback with the ip.
```lua
GetPrivateIP(callback)
```
#### Arguments:
* callback: **Function**: The function to call after getting the ip, the ip is passed as an argument.

#### Example:
```lua
GetPrivateIP(function(ip) print("Got Private IP: ",ip) end
```

## GetPublicIP: **Function**
Get's the public ip of the client, and then calls the given callback with the ip.
```lua
GetPublicIP(callback)
```
#### Arguments:
* callback: **Function**: The function to call after getting the ip, the ip is passed as an argument.

#### Example:
```lua
GetPublicIP(function(ip) print("Got Public IP: ",ip) end
```

## HSVtoRGB: **Function**
Converts a color from HSV to RGB.
```lua
local r,g,b = HSVtoRGB(h, s, v)
```
#### Arguments:
* h: **Number**: The h value of the color.
* s: **Number**: The s value of the color.
* v: **Number**: The v value of the color.

#### Returns:
* r: **Number**: The r value of the color.
* g: **Number**: The g value of the color.
* b: **Number**: The b value of the color.

## open_url_in_steam_or_browser: **Function**
Open a page in the steam web browse if steam is running, or opens it in the os default browser.
```lua
open_url_in_steam_or_browser(url)
```
#### Arguments:
* url: **String**: The url to open.

## truncate_by_width: **Function**
Cuts the part of the text that's longer than the given width. Supports UTF8
```lua
local truncatedStr = truncate_by_width(text, width, font)
```
#### Arguments:
* text: **UTF8 String**: The string to truncate.
* width: **Number**: The limit width.
* font: **LÖVE Font Class**: The font to use.

#### Returns:
* truncatedStr: **UTF8 String**: The truncated string.

## _Version: **String**
The current game version.

## _Fonts: **Table**
Loaded fonts holder.

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

## _DEFAULT_MIPMAP: **Number**
Unknown yet, but it's value is -5;

## Unknown Variables:
**Booleans:** _INTERNET, _ERROR_REPORTING, _AntialiasSupported, _EditorGrid, _GamepadOutput, _OutOfFocusSound, _POSTPROCESS_UI, _PAUSE, _BLUR, _Mipmap, _SPLASH, _SPLATTER, _BoundKeys, _LiveAIMatch

**Numbers:** _TimePlayed, _currentFrameTime, _FPScap, _debugModeCycler

**Strings:** _currentModeName, _LastGameType

**Tables:** _GlobalMessageQueue, _AdminSteamIds, _SoundsData, _SoundsDuration, _TweenTimeTo, _EmailThread, _cam2, _ShaderArray, _mouseUp, _KeyInput, _GamepadTap, _GamepadPress, _JoySticks, _DefaultCursor, _UnlockedHiddenCharacters, _miscUIRenders, _memoryTest _filesToUpdate
