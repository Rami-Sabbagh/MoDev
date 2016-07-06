# Engine/GameObject.el
This is the file that's responsible about adding things to the game to draw & update.

There is three types of objects:

* **Static animated:** May or may not be animated, but are static, always remain in place. Ex: tiles.
* **Dynamic animated:** May or may not be animated, but are objects that can move, must be rechecked every frame to see if they are still in the same grid. Ex: Joe, boxes.
* **Static non-animated:** Are not animated, and do not move. Usually in large numbers. Are rendered manually with sprite batches. Ex: background tiles.