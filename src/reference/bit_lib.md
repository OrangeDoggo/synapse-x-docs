# Bit Library

## bdiv
```syn
<int> bit.bdiv(<uint> dividend, <uint> divisor)  
```
Divides `dividend` by `divisor`, remainder is not returned.
## badd
```syn
<int> bit.badd(<uint> a, <uint> b)  
```
Adds `a` with `b`, allows overflows.
## bsub
```syn
<int> bit.bsub(<uint> a, <uint> b)  
```
Subtracts `a` with `b`, allows overflows.
## bmul
```syn
<int> bit.bmul(<uint> val, <uint> by)  
```
Multiplies `val` using `by`, allows overflows.

**Note**: All bitwise functions within the `bit` lib return **signed** 32 bit integers. Take good note of that when implementing. If you want unsigned results, we suggest using `bit32`.
## band
```syn
<int> bit.band(<uint> val, <uint> by)  
```
Does a bitwise AND (&) on `val` using `by`.
## bor
```syn
<int> bit.bor(<uint> val, <uint> by)  
```
Does a bitwise OR (|) on `val` using `by`.
## bxor
```syn
<int> bit.bxor(<uint> val, <uint> by)  
```
Does a bitwise XOR (⊕) on `val` using `by`.
## bnot
```syn
<int> bit.bnot(<uint> val)  
```
Does a bitwise NOT on `val`.
## bswap
```syn
<int> bit.bswap(<uint> val)  
```
Does a bitwise swap on `val`.
## ror
```syn
<int> bit.rol(<int> value, <int> rotate_count)
```
Returns the `value` rotated right by `rotate_count`.
## rol
```syn
<int> bit.rol(<int> value, <int> rotate_count)
```
Returns the `value` rotated left by `rotate_count`.
## tohex
```syn
<string> bit.tohex(<uint> val)  
```
Converts `val` to a hex string.
## tobit
```syn
<int> bit.tobit(<uint> val)  
```
Converts `val` into proper form for bitwise operations.
## lshift
```syn
<int> bit.lshift(<uint> val, <uint> by)  
```
Does a left shift on `val` using `by`.
## rshift
```syn
<int> bit.rshift(<uint> val, <uint> by)  
```
Does a right shift on val using by.
## arshift
```syn
<int> bit.arshift(<int> value, <int> shift_count)
```
Returns the arithmetically shifted value.