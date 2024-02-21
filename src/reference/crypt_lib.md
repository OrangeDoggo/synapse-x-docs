# Crypt Library

## Encrypt
```syn
<string> syn.crypt.encrypt(<string> data, <string> key)  
```
Encrypts `data` with `key` (algorithm used is AES-GCM, random nonce generated per call).
## Decrypt
```syn
<string> syn.crypt.decrypt(<string> data, <string> key)  
```
Decrypts `data` with `key`.
## Base64 Encode
```syn
<string> syn.crypt.base64.encode(<string> data)  
```
Encodes `data` with `base64`.
## Base64 Decode
```syn
<string> syn.crypt.base64.decode(<string> data)  
```
Decodes `data` with `base64`.
## Hash
```syn
<string> syn.crypt.hash(<string> data)
```
Hashes `data` with SHA-384.
## Derive
```syn
<string> syn.crypt.derive(<string> value, <uint> len)
```
Derives a secret key from `value` with the length of `len`.
## Random
```syn
<string> syn.crypt.random(<uint> size)
```
Generates a random string with `size` (cannot be negative or exceed 1024).

## Custom
### Encrypt
```syn
<string> syn.crypt.custom.encrypt(<string> cipher, <string> data, <string> key, <string> iv/nonce)
```
Encrypts `data` with `key` using selected `cipher` and `iv/nonce`.
### Decrypt
```syn
<string> syn.crypt.custom.decrypt(<string> cipher, <string> data, <string> key, <string> iv/nonce)
```
Decrypts `data` with `key` using selected `cypher` and `iv/nonce`.
### Hash
```syn
<string> syn.crypt.custom.hash(<string> algorithm, <string> data)
```
Hashes `data` with `algorithm`.
### Encryption/Decryption ciphers

You can use both `-` and `_`. With Blowfish `bf` or `blowfish`.
|AES    |Blowfish   |
|-------|-----------|
|aes-cbc|bf-cbc     |
|aes-cfb|bf-cfb     |
|aes-ctr|bf-ofb     |
|aes-ofb|           |
|aes-gcm|           |
|aes-eax|           |
### Hashing algorithms

Same goes here, you can use `-` or `_`.
|MD5|SHA1   |SHA2       |SHA3       |
|---|-------|-----------|-----------|
|md5|sha1   |sha224     |sha3-256   |
|	|sha256 |sha3-384   |           |
|	|sha384 |sha3-512   |           |
|	|sha512 |           |           |
## Example
```lua
local enc = syn.crypt.custom.encrypt(
    "aes-gcm",
    "hi gamers!", 
    "$nLliCMdi7gcynsFCK9u0aVNdtkNIiZG",
    "Agd13KuKIL2$") -- in production, generate a nonce via syn.crypt.random

print(enc)

print(syn.crypt.custom.decrypt(
    "aes-gcm",
    enc,
    "$nLliCMdi7gcynsFCK9u0aVNdtkNIiZG",
    "Agd13KuKIL2$")) --"hi gamers"
```