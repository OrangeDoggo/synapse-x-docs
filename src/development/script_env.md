# Introduction to the Script Environment

We will first learn about certain changes from normal Lua that Synapse X has and how it can affect your scripts.

## Script Identity

Normal game scripts run at identity 2 - we can see this if we run `printidentity()` in a LocalScript.

On the other hand, Synapse X scripts run at identity 7, which allows vastly more access than a normal identity 2 script. Some examples of extended access include:

* Access to `game:GetService("CoreGui")`, a safe place to put user interfaces that is hard to detect by game scripts.
* Access to restricted functions (`game:HttpGet`, `game:GetObjects`, etc.) that allow for extended functionality that is not possible on normal game scripts.
* Access to supervise other scripts - this will be very important later on in the guide.

Synapse X also has a large set of API functions that allow you even more access & convenience. We will be extensively using them later on when we start to create scripts.

## The `script` global

Normally, LocalScripts are given a `script` global that allows access to children of the script/other properties. While Synapse X scripts are given a `script` global, its mostly fake - doing `script.Disabled = true` will not do anything for example on Synapse X.

Its **highly recommended** you never touch the `script` global on Synapse X as it can cause various security problems with your scripts.

## `shared`/`_G`

When Synapse X is attached, it will create a new `shared`/`_G` table instead of using the one already defined for other scripts. If you want to get the original `shared`/`_G`, use the `getrenv` function and index `shared`/`_G` from there. **Please be careful** doing this though, as a clever game script developer could set 'traps' with metatables to foil this. We will explain how to bypass these checks later on in this guide.

Lets now move onto [objects and metatables](./object_mts.md).