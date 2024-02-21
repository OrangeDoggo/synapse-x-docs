# Hooking Functions

## Hook Function
```syn
<function> hookfunction(<function> old, <function> hook)  
```
Hooks function `old`, replacing it with the function `hook`. The old function is returned, you must use this function in order to call the original function.

## Hook Metamethod
```syn
<function> hookmetamethod(<Object> object, <string> metamethod, <function> hook)  
```
Hooks the `metamethod` passed in the `object`'s metatable with `hook`. A function to call the original metamethod is returned, you must use this function in order to call the original metamethod.

This function will error if an object without a metatable is passed or a invalid metamethod is passed.
## New C Closure
```syn
<function> newcclosure(<function> f)  
```
Pushes a new CClosure that invokes function `f` upon call.