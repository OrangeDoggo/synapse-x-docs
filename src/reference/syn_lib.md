# Syn Library

## Cache Replace
```syn
<void> syn.cache_replace(<Instance> obj, <Instance> t_obj)  
```
Replace `obj` in the instance cache with `t_obj`.
## Cache Invalidate
```syn
<void> syn.cache_invalidate(<Instance> obj)  
```
Invalidate `obj`'s cache entry, forcing a re-cache upon the next lookup.
## Set Thread Identity
```syn
<void> syn.set_thread_identity(<uint> n)  
```
Sets the current thread identity.
## Get Thread Identity
```syn
<uint> syn.get_thread_identity(<void>)  
```
Returns the current thread identity.
## Is Cached
```syn
<bool> syn.is_cached(<Instance> obj)  
```
Returns true if `obj` is currently cached within the registry.
## Write Clipboard
```syn
<void> syn.write_clipboard(<string> content)  
```
Writes `content` to the current Windows clipboard.
## Queue On Teleport
```syn
<void> syn.queue_on_teleport(<string> code)
```
Executes `code` after player is teleported.
### Example
```lua
game:GetService("Players").LocalPlayer.OnTeleport:Connect(function(State)
    if State == Enum.TeleportState.Started then
        syn.queue_on_teleport("<script to execute after TP>")
    end
end)
```
## Protect Gui
```syn
<void> syn.protect_gui(<obj> GUI)
```
Protects your `GUI` from recursive FindFirstChild-style attacks. After you call the function, recursive FFA calls from non-Synapse contexts will skip over your protected instances & all children of such instances.
### Example
```lua
local GUI = game:GetObjects("whatever")[1]
syn.protect_gui(GUI) -- You should call protect_gui before your GUI is parented.
GUI.Parent = game:GetService("CoreGui")
```
## Unprotect Gui
```syn
<void> syn.unprotect_gui(<Instance> GUI)
```
Removes protection from the `GUI`. Errors if `gui` isn't already protected.
## Is Beta
```syn
<bool> syn.is_beta(<void>)
```
Returns a bool indicating whether the user is using Synapse Beta or not.
## Crypto
```syn
<...> syn.crypto.*
```
Alias for `syn.crypt.*`. You can view the functions in the [cryptography library](./crypt_lib.md) section.
## Request
```syn
<table> syn.request(<table> options)
```
Sends a http request with parameters in `options`.
### Request Dictionary Fields
|Name	    |Type       |Required   |Description                                                                                                |
|-----------|-----------|-----------|-----------------------------------------------------------------------------------------------------------|
|Url	    |String     |Yes        |The target URL for this request. Must use `http` or `https` protocols.                                     |
|Method	    |String     |No         |The HTTP method being used by this request, most often GET or POST.                                        |
|Headers	|Dictionary |No         |A dictionary of headers to be used with this request. Most HTTP headers are accepted here, but not all.    |
|Cookies	|Dictionary |No         |A dictionary of cookies to be used with this request.                                                      |
|Body	    |String     |No         |The request body. Can be any string, including binary data. Must be excluded when using the GET or HEAD HTTP methods. It might be necessary to specify the `Content-Type` header when sending JSON or other formats.                                                                           |
### Response Dictionary Fields
|Name           |Type       |Description                                                                                                    |
|---------------|-----------|---------------------------------------------------------------------------------------------------------------|
|Success        |Boolean	|The success status of the request. This is true if and only if the StatusCode lies within the range [200, 299].|
|StatusCode     |Integer	|The HTTP response code identifying the status of the response.                                                 |
|StatusMessage  |String	    |The status message that was sent back.                                                                         |
|Headers        |Dictionary	|A dictionary of headers that were set in this response.                                                        |
|Cookies        |Dictionary	|A dictionary of cookies that were set in this response.                                                        |
|Body           |String	    |The request body (content) received in the response.                                                           |
### Synapse Headers
|Name	            |Description                                                                                                                                    |
|-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
|Syn-Fingerprint    |Users HWID, changes between PCs.                                                                                                               |
|Syn-User-Identifier|Similar to `Syn-Fingerprint` , but does not change between PCs. Pretty useful as a way to identify Synapse accounts for cross-PC save data/etc.  |
|User-Agent         |The version of synapse the request was made from. Example: `synx/v2.1.3b`.                                                                       |
### Example
```lua
local response = syn.request(
    {
        Url = "http://httpbin.org/post",  -- This website helps debug HTTP requests
        Method = "POST",
        Headers = {
            ["Content-Type"] = "application/json"  -- When sending JSON, set this!
        },
        Body = game:GetService("HttpService"):JSONEncode({hello = "world"})
    }
)
    
for i,v in pairs(response) do
    print(i,v)
    
    if type(v) == "table" then
        for i2,v2 in pairs(v) do
            warn(i2,v2)
        end
    end
end
```
## Secure Call
### **Notice: This function is deprecated and will be removed in Synapse V3.**
```syn
<variant...> syn.secure_call(<function> func, union<LocalScript, ModuleScript, table> script, <variant> args...)
```
Spoofs caller environment and context when calling `func` with `script`'s environment. You can pass as many arguments `args` as is required. `secure_call` returns whatever the called function returns.

You can also pass a table to `script` if you wish to customize how the call will occur:
|Name	        |Type	            |Required   |Description                                                                        |
|---------------|-------------------|-----------|-----------------------------------------------------------------------------------|
|Script	        |Local/ModuleScript	|Yes        |The script that the call will be spoofed as.                                       |
|Environment	|Table	            |No         |The enviornment that the call will be spoofed as. By default it is getsenv(Script) |
|LineNumber	    |Number	            |No         |The line number that the call will be spoofed as. By default is random.            |
### Example
```lua
local KeyHandler = require(game:GetService("ReplicatedStorage").Assets.Modules.KeyHandler)
local PlayerName = game:GetService("Players").LocalPlayer.Name
local FakeEnv = game:GetService("Workspace").Live[PlayerName].CharacterHandler.Input

local Result = syn.secure_call(KeyHandler, FakeEnv)
local Event = syn.secure_call(Result.getKey, FakeEnv, "ApplyFallDamage", "plum")

--Do whatever
```
## Create Secure Function
```syn
<string> syn.create_secure_function(<string> code)
```
Protects your `code` with secure function, making it much more difficult for others to alter or view your code. This function can only be used by users who have been given access.
## Run Secure Function
```syn
<void> syn.run_secure_function(<string> code)
```
Runs `code` protected by secure function.