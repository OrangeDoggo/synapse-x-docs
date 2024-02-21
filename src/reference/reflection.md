# Reflection Functions

## Loadstring
```syn
<union<function, nil>, <string?>> loadstring(<string> chunk, <string?> chunk_name)  
```
Loads `chunk` as a Lua function with optional `chunk_name` and returns it if compilation is successful. Otherwise, if an error has occurred during compilation, `nil` followed by the error message will be returned.
## Check Caller
```syn
<bool> checkcaller(<void>)  
```
Returns `true` if the current thread is a Synapse thread. **Note**: Checkcaller does *NOT* check the call stack of the function, if you call a game function then it calls out to checkcaller, the result will be `true`! Be careful.
## Is Lua Closure
```syn
<bool> islclosure(<function> f)  
```
Returns true if `f` is an LClosure.
## Dump String
```syn
<string> dumpstring(<string> Script)  
```
Returns the Synapse formatted bytecode for source string `script`.
## Decompile
```syn
<string> decompile(union<LocalScript, ModuleScript, function, string, proto> Script, union?<string, bool> mode, <number?> timeout)  
```
Decompiles `Script` and returns the decompiled script with `timeout`. If the decompilation fails, then the return value will be an error message.

*Note*: The `mode` parameter is deprecated and is not used in newer versions of Synapse.