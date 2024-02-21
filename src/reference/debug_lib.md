# Debug Library

## Get Constants
```syn
<table> debug.getconstants(union<function, number> fi)  
```
Retrieve the constants in function `fi` or at level `fi`.
## Get Constant
```syn
<variant> debug.getconstant(union<function, number> fi, <number> idx)  
```
Returns the constant at index `idx` in function `fi` or level `fi`.
## Set Constant
```syn
<void> debug.setconstant(union<function, number> fi, union<string, int> idx, union<number, bool, nil, string> value)  
```
Set constant `idx` to tuple `value` at level or function `fi`.

## Get Upvalues
```syn
<table> debug.getupvalues(union<function, number> fi)  
```
Retrieve the upvalues in function `fi` or at level `fi`.
## Get Upvalue
```syn
<variant> debug.getupvalue(union<function, number> fi, <number> idx)
```
Returns the upvalue with name `idx` in function or level `fi`.
## Set Upvalue
```syn
<void> debug.setupvalue(<function, number> fi, <number> idx, <table> value)  
```
Set upvalue `idx` to value value at `level` or function `fi`.

## Get Protos
```syn
<table> debug.getprotos(<function> f)
```
Returns a table containing the inner functions of function `f`. Note these functions will not have upvalues, use `debug.getproto` with activated `true` to get a list of instances.
## Get Proto
```syn
union<function, table<function>> debug.getproto(<function, number> f, <int> index, <bool?> activated)
```
Gets the inner function of `f` at `index`.

Note if `activated` is true, instead it will return a table of functions. These are the instances of that function that exist within the GC.
## Set Proto
```syn
<void> debug.setproto(<function> fi, <number> index, <function> replacement)
```
Replaces `fi` at `index` with function `replacement` at level or function `fi`.

## Get Stack
```syn
<table> debug.getstack(<number> indice)
```
Gets the method stack at level `indice`.
## Set Stack
```syn
<void> debug.setstack(<number> indice, <number> indice, <table> value)
```
Set the stack indice at level `indice` to value `value` at level or function `fi`.

## Set Metatable
```syn
<table> debug.setmetatable(<table> o, <table> mt)  
```
Set the metatable of `o` to `mt`.
## Get Registry
```syn
<table> debug.getregistry(<void>)  
```
Returns the Lua registry.
## Get Info
```syn
<table> debug.getinfo(union<function, number> fi, <string> w = "flnSu")  
```
Returns a table of info pertaining to the lua function `fi`.