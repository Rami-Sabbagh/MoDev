# Engine/GameObject.el
This is the file that's responsible about adding things to the game to draw & update.

There is three types of objects:

* **Static animated:** May or may not be animated, but are static, always remain in place. Ex: tiles.
* **Dynamic animated:** May or may not be animated, but are objects that can move, must be rechecked every frame to see if they are still in the same grid. Ex: Joe, boxes.
* **Static non-animated:** Are not animated, and do not move. Usually in large numbers. Are rendered manually with sprite batches. Ex: background tiles.
## Usage:
```lua
local GameObject = require("Engine/GameObject")
```
## Creating a new object:
###### There is 3 methods to create a new object, each for it's own object type:
### GameObject:newObject - **Function**
Creates a new static object.
```lua
local Obj = GameObject:newObject(x, y, imageName)
```
#### Arguments:
* x: **Number**: The x position of the object.
* y: **Number**: The y position of the object.
* imageName: **String**: The name of the image to use for the game object, without the extension.

#### Returns:
* Obj: **GameObject Instance**: The new static object.

### GameObject:newDynamicObject - **Function**
Creates a new dynamic object that can move.
```lua
local Obj = GameObject:newDynamicObject(x, y, imageName)
```
#### Arguments:
* x: **Number**: The x position of the object.
* y: **Number**: The y position of the object.
* imageName: **String**: The name of the image to use for the game object, without the extension.

#### Returns:
* Obj: **GameObject Instance**: The new dynamic object.

### GameObject:newUIObject - **Function**
Creates a new ui object that's always rendered.
```lua
local Obj = GameObject:newUIObject(x, y, imageName)
```
#### Arguments:
* x: **Number**: The x position of the object.
* y: **Number**: The y position of the object.
* imageName: **String**: The name of the image to use for the game object, without the extension.

#### Returns:
* Obj: **GameObject Instance**: The new ui object.

###### It's also possible to create a static child object:

### Obj:newChild - **Function**
Creates a new ui object that's always rendered.
```lua
local Child = Obj:newChild(x, y, imageName)
```
#### Arguments:
* x: **Number**: The x position of the object.
* y: **Number**: The y position of the object.
* imageName: **String**: The name of the image to use for the game object, without the extension.

#### Returns:
* Child: **GameObject Instance**: The new static child object