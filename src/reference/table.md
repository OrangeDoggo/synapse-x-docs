# Table Functions

## Get Raw Metatable
```syn
<table> getrawmetatable(<table> value)  
```
Retrieve the metatable of value irregardless of value's metatable's `__metatable` field. Returns `nil` if it doesn't exist.
## Set Raw Metatable
```syn
<bool> setrawmetatable(<object> o, <table> mt)
```
Sets `o`'s metatable to `mt` even if the `__metatable` field exists in `o`'s metatable.
## Set Readonly
```syn
<void> setreadonly(<table> t, <bool> val)  
```
Sets `t`'s read-only value to `val`.
## Is Readonly
```syn
<bool> isreadonly(<table> t)  
```
Returns `t`'s read-only condition. 