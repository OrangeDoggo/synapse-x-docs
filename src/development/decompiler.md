# Using the Decompiler

Synapse X includes another powerful tool to help you develop scripts - the **decompiler**. The decompiler allows you to see the full Lua source code of any game LocalScript or ModuleScript, allowing you to easily understand how a game works.

To start, you can execute the **Script Dumper** from the Synapse X Script Hub. After that, it may take 5-10 minutes for all scripts on the game to decompiled, which will then be placed in your Synapse X `workspace` folder. You can then open up the file and take a look at all game scripts.

An example of a decompiled script is shown below:

```lua
-- Decompiled with the Synapse X Luau decompiler.

function CreateGui()
    local v1 = Instance.new("ScreenGui");
    local v2 = Instance.new("Frame");
    local v3 = Instance.new("Frame");
    local v4 = Instance.new("TextLabel");
    local v5 = Instance.new("TextBox");
    local v6 = Instance.new("Frame");
    local v7 = Instance.new("Frame");
    local v8 = Instance.new("TextButton");
    local v9 = Instance.new("TextLabel");
    local v10 = Instance.new("TextLabel");
    local v11 = Instance.new("ImageLabel");
    local v12 = Instance.new("Frame");
    local v13 = Instance.new("Frame");
```

You may notice that decompiled output looks a lot different from the original source of that script - this is because of debugging information being irrevocably lost during the compilation process. Synapse does its best to make the decompiled source look as good as possible, but unfortunately decompilation is mostly a guessing game, which will inevitably lead to differences in the decompiled output.

If you find specific issues within the decompiler, we would recommend you report them via our Bug Report category on [our support site](https://synapsesupport.io).

Nonetheless, the decompiler is a powerful tool in your arsenal, which we will put to use in our next section, [using the debug API](./debug_api.md).