# Script Functions

## Get Script Environment
```syn
<table> getsenv(union<LocalScript, ModuleScript> Script)  
```
Returns the environment of `Script`. Errors if the script is not loaded in memory.
## Get Calling Script
```syn
<union<LocalScript, ModuleScript, nil>> getcallingscript(<void>)  
```
Gets the script that is calling this function.
## Get Script Closure
```syn
<function> getscriptclosure(union<LocalScript, ModuleScript> Script)  
```
Gets a bare function from the script passed. Please note this is not the original function of the script and will not have upvalues/enviornment correctly defined.
## Get Script Hash
```syn
<string> getscripthash(union<LocalScript, ModuleScript> Script)  
```
Returns a SHA384 hash of the scripts bytecode. You can use this to detect changes of a script.