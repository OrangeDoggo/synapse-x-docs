# Using the Debug API

We still haven't covered one of the most important APIs within Synapse - the `debug` API. The `debug` API allows full control over the execution state of any running script, which we will now explain how to use.

## `debug.*upvalue(s)`

We will first be explaining the most simple (but arguably the most used) function within the `debug` API - the upvalue functions.

You might be asking, *what is a upvalue*? An upvalue is a local variable that is used in more than 1 function. See an example below of an upvalue:

```lua
local TestVariable = "Hello, world!"

local function Test()
    print(TestVariable)
    TestVariable = "Still - Hello, world!"
    print(TestVariable)
end

Test()
```

The `TestVariable` is an upvalue within the `Test` function. We can grab and modify that variable with the `debug.setupvalue` function.

An example of this is shown below:

```lua
local TestVariable = "Hello, world!"

local function Test()
    print(TestVariable)
    TestVariable = "Still - Hello, world!"
    print(TestVariable)
end

debug.setupvalue(Test, 1, "Hello, modified world!")
Test()
```

Instead of printing `"Hello, world!"` followed by `"Still - Hello, world!"` as it normally would, it instead prints `Hello, modified world!` first!

## Call-stack Levels

You can also call the full set of `debug` functions with a function level instead of the function itself, just like `getfenv`/`setfenv`.

```lua
local TestVariable = "Hello, world!"

local function Test()
    local function InnerFunction()
        --2 refers to the Test function
        debug.setupvalue(2, 1, "Hello, modified world!")
    end

    InnerFunction()

    print(TestVariable)
    TestVariable = "Still - Hello, world!"
    print(TestVariable)
end

Test()
```

This will produce the same results as the above script.

## `debug.*constants`

We will next be explaining the constant functions, which can be used to get/modify the constant values within a script.

An example is provided below:

```lua
local TestVariable = "Hello, world!"

local function Test()
    print(TestVariable)
    TestVariable = "Still - Hello, world!"
    print(TestVariable)
end

debug.setconstant(Test, 2, "Modified - Hello, world!")
Test()
```

This will print out `"Hello, world!"` proceeded by `"Modified - Hello world!"` instead of `"Still - Hello, world!"`.

**Note**: Certain low number values (`0`-`65535`) may not show up in the constant functions. We plan to add support for them later.
## `debug.*stack`

The `debug` API also has one other set of functions - the stack functions.

The stack functions allow you to modify any value on the stack of any function currently running that has called you. This is mostly used to modify local variables that are not upvalues. Please note this only supports call-stack levels unlike the rest of the functions.

An example is shown below:

```lua
local function Test()
    local TestVariable = "Hello, world!"
    local function InnerFunction()
        --2 refers to the Test function
        debug.setstack(2, 1, "Hello, modified world!")
    end

    InnerFunction()

    print(TestVariable)
    TestVariable = "Still - Hello, world!"
    print(TestVariable)
end

Test()
```

This will also produce the same results as the upvalue testing script.

## Miscellaneous debug functions

The `debug` API also contains some other useful functions:

`debug.validlevel` - This will allow you to check if a call-stack level actually exists or not. Makes you not need to do `pcall` for debug functions with stack levels.

`debug.getregistry` - This allows you to get the Lua registry, which can be used to get connections in memory and other information.

Lets now move on to [calling external functions](./calling_extern_references.md).