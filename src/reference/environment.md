# Environment Functions

## Get Global Environment
```syn
<table> getgenv(<void>)  
```
Returns the environment that will be applied to each script ran by Synapse.

## Get Environment
```syn
<table> getrenv(<void>)  
```
Returns the global environment for the LocalScript state.

## Get Registry
```syn
<table> getreg(<void>)  
```
Returns the Lua registry.

## Get Garbage Collection
```syn
<table> getgc(<bool?> include_tables)  
```
Returns all functions and userdata values within the GC. Passing `true` will also return tables.

## Get Instances
```syn
<table<Instance>> getinstances(<void>)  
```
Returns a list of all instances within the game.

## Get Nil Instances
```syn
<table<Instance>> getnilinstances(<void>)  
```
Returns a list of all instances parented to `nil` within the game.

## Get Scripts
```syn
<table<union<LocalScript, ModuleScript>>> getscripts(<void>)  
```
Returns a list of all scripts within the game.

## Get Loaded Modules
```syn
<table<ModuleScript>> getloadedmodules(<void>)  
```
Returns all ModuleScripts loaded in the game.

## Get Connections
```syn
<table<Connection>> getconnections(<ScriptSignal> obj)  
```
Gets a list of connections to the specified signal. You can do the following operations on a Connection:
| Example   | Description                               |
|-----------|-------------------------------------------|
|.Function   | The function connected to the connection |
|.State      | The state of the connection              |
|:Enable     | Enables the connection                   |
|:Disable    | Disables the connection                  |
|:Fire       | Fires the connection                     |

### Example
```lua
for i, connection in pairs(getconnections(workspace.ChildAdded)) do
    connection:Disable()
end
```
## Fire Signal
```syn
<void> firesignal(<ScriptSignal> Signal, <variant> Args...)
```
Fires all the connections connected to the signal `Signal` with `Args`.

## Fire Click Detector
```syn
<void> fireclickdetector(<ClickDetector> Detector, <number> Distance)
```
Fires the designated `ClickDetector` with provided `Distance`. If `Distance` isn't provided, it will default to 0.

## Fire Proximity Prompt
```syn
<void> fireproximityprompt(<ProximityPrompt> Prompt, <number> Distance)
```
Fires the designated `ProximityPrompt`.

## Fire Touch Interest
```syn
<void> firetouchinterest(<Instance> Part, <BasePart> ToTouch, <uint> Toggle)
```
Fakes a .Touched event to `ToTouch` with `Part`. The `Toggle` argument must be either 0 or 1 (for fire/un-fire).

**Note**: The `ToTouch` argument must have a child with class `TouchTransmitter` in order for this function to work.

## Is Network Owner
```syn
<bool> isnetworkowner(<BasePart> Part)
```
Returns `true` if the Part is owned by the player.

## Get Hidden Property
```syn
<variant> gethiddenproperty(<Instance> Object, <string> Property)  
```
Returns the hidden property `Property` from `Object`. Errors if the property does not exist.

## Set Hidden Property
```syn
<void> sethiddenproperty(<Instance> Object, <string> Property, <variant> Value)  
```
Sets the hidden property `Property` with `Value` from `Object`. Errors if the property does not exist.

## Set Simulation Radius
```syn
<void> setsimulationradius(<uint> SimulationRadius, <uint?> MaxSimulationRadius)  
```
Sets the player's SimulationRadius. If `MaxSimulationRadius` is specified, it will set that as well.