# Filesystem APIs

Synapse X contains functions that allow you to create, append, and remove files and folders within the Synapse X `workspace` directory. This allows you to save settings and any other information you may want later.

## Creating Files

You can create files with the `writefile` function.

```lua
writefile("test.txt", "Testing!")
```

This will write a file named `test.txt` with the contents `Testing!` in your Synapse X `workspace` folder.

## Appending Files

You can use `appendfile`, which has the same arguments as the `writefile` function, but does not overwrite the file.

```lua
appendfile("test.txt", "Testing!")
```

## Reading Files

You can use the `readfile` function, which reads a file if it exists, erroring if it does not.

```lua
local contents = readfile("test.txt")
```

There is also a variation if you want to load it as a script - use `loadfile` in that case.

## Checking if a file exists

You can use the `isfile` function, which returns true if you specified a valid file.

```lua
local valid = isfile("test.txt")
```

## Folders

The same interface exists for folders as well - `makefolder`, `delfolder`, `isfolder`.

Lets conclude this tutorial series with the [web APIs](./web_api.md).