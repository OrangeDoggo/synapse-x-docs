# Importance of `Newcclosure`

`Newcclosure` is a very important function in Synapse X, which we will be explaining to make sure you use it correctly.

You may be asking, "why is `newcclosure` so important?", and there is a simple answer - **not using `newcclosure` opens you up to a multitude of detection vectors**.

## Detecting metatable hooks

Smart game script developers back at the time when metamethod hooks were first starting to be popular had a good idea of how to detect them - check the call-stack for suspicious environments that indicate metamethod hooks are present.

The general way to do this was via the `xpcall` function and forcing an error within the original function that was called by the hook. An example of this technique is described below:

```lua
local Env = getfenv()

xpcall(function()
    return game:_____()
end, function()
    for i = 0, 10 do
        if getfenv(i) ~= Env then
            warn("Detected metamethod tampering!")
        end
    end
end)
```

`newcclosure` will make sure that Synapse X functions are not on the `xpcall` call-stack, protecting you from this attack.

There was also the method of checking error messages for changes - this was also popularly used back at the start of popularity for metatable hooks.

```lua
local OldErr, OldMsg = pcall(function() return game:____() end)

while wait(1) do
    local Err, Msg = pcall(function() return game:____() end)

    if OldErr ~= Err or OldMsg ~= Msg then
        warn("Detected metamethod tampering!")
    end
end
```

`newcclosure` will make sure this attack does not happen either.

In short, **always** use newcclosure for both metamethod hooks and function hooks, which we will now to go back to.

For now, lets go back to [metamethod hook examples](./metamethod_hook_examples.md).