# Miscellaneous Functions

## Set Clipboard
```syn
<void> setclipboard(<string> value)  
```
Sets `value` to the clipboard.
## Set Fast Flag
```syn
<void> setfflag(<string> FFlag, <string> Value)
```
Sets `FFlag` with `Value`. Must be run before the game loads, auto execute + auto launch recommended.
## Get Namecall Method
```syn
<string> getnamecallmethod(<void>)
```
Returns the namecall method if the function is called in an `__namecall` metatable hook.
## Set Namecall Method
```syn
<void> setnamecallmethod(<string> method)
```
Sets the current namecall method to the new namecall `method`. Must be called in a `__namecall` metatable hook.
## Get Synapse Asset
```syn
<Content> getsynasset(<string> path)
```
Returns a `Content` string that can be used as a fake Asset ID for GUI elements. Please note this will only affect your client.

Note: Certain instances only work with specific file types. For example, `VideoFrame`'s only work with `.webm` encoded videos.
## Get Special Info
```syn
<table> getspecialinfo(<Instance> obj)  
```
Gets a list of special properties for `MeshParts`, `UnionOperations`, and `Terrain` instances.
|MeshParts  |UnionOperations    |Terrain        |
|-----------|-------------------|---------------|
|PhysicsData|AssetId            |SmoothGrid     |
|InitialSize|ChildData          |MaterialColors |
|           |FormFactor         |               |
|	        |InitialSize        |               |	
|	        |MeshData	        |               |
|	        |PhysicsData        |               |

## Save Instance
```syn
<void> saveinstance(<table> t)  
```
Saves the current game into your workspace folder. You can use table `t` to customize options for this.
|Option|Value                           |
|-----------|---------------------------|
|mode       |optimized / full / scripts |
|noscripts  |true / false               |
|scriptcache|true / false               |
|timeout    |any number                 |
## Message Box
```syn
<uint> messagebox(<string> text, <string> caption, <uint> flags)
```
Creates a message box with parameters text, caption and style.
|Style                          |Number |
|-------------------------------|-------|
|OK                             |0      |
|OK / Cancel                    |1      |
|Abort / Retry / Ignore         |2      |
|Yes / No / Cancel              |3      |
|Yes / No                       |4      |
|Retry / Cancel                 |5      |
|Cancel / Try Again / Continue  |6      |

|Code   |Description                        |
|-------|-----------------------------------|
|1      |The OK button was selected         |
|2      |The Cancel button was selected.    |
|3      |The Abort button was selected.     |
|4      |The Retry button was selected.     |
|5      |The Ignore button was selected.    |
|6      |The Yes button was selected.       |
|7      |The No button was selected.        |
|10     |The Try Again button was selected. |
|11     |The Continue button was selected.  |