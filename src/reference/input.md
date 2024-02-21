# Input Functions

## Is Active
```syn
<bool> iswindowactive(<void>)  
```
Returns if the main window is in focus. This must return true for any other mouse/keyboard function to work.
## Keyboard
```syn
<void> keypress(<uint> keycode)  
```
Simulates a key press for the specified `keycode`. Keycodes are listed [here](https://docs.microsoft.com/en-us/windows/desktop/inputdev/virtual-key-codes).
```syn
<void> keyrelease(<uint> key)  
```
Releases `key` on the keyboard. You can access the key values from the link above.
## Left Click
```syn
<void> mouse1click(<void>)  
```
Simulates a full left mouse button press.
```syn
<void> mouse1press(<void>)  
```
Simulates a left mouse button press without releasing it.
```syn
<void> mouse1release(<void>)  
```
Simulates a left mouse button release.
## Right Click
```syn
<void> mouse2click(<void>)  
```
Simulates a full right mouse button press.
```syn
<void> mouse2press(<void>)  
```
Clicks down on the right mouse button.
```syn
<void> mouse2release(<void>)  
```
Simulates a right mouse button release.
## Mouse Movement
```syn
<void> mousescroll(<number> px)  
```
Scrolls the mouse wheel virtually by `px` pixels.
```syn
<void> mousemoverel(<number> x, <number> y)  
```
Moves the mouse cursor relatively to the current mouse position by coordinates `x` and `y`.
```syn
<void> mousemoveabs(<number> x, <number> y)  
```
Move's your mouse to the `x` and `y` coordinates in pixels from topleft of the main window.