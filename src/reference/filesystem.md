# Filesystem Functions

## Read File
```syn
<string> readfile(<string> path)  
```
Reads the contents of the file located at `path` and returns it. If the file does not exist, it errors.
## Write File
```syn
<void> writefile(<string> path, <string> contents)  
```
Writes contents to the supplied path.
Extensions that are not allowed: `.exe`, `.scr`, `.bat`, `.com`, `.csh`, `.msi`, `.vb`, `.vbs`, `.vbe`, `.ws`, `.wsf`, `.wsh`, `.ps1`, `.psy`. Attempting to call this function with those extensions will error.
## Append File
```syn
<void> appendfile(<string> path, <string> content)  
```
Appends `content` to the file contents at `path`. If the file does not exist, it errors.
## Load File
```syn
<union<function, nil>, <string?>> loadfile(<string> path)  
```
Loads in the contents of a file as a chunk and returns it if compilation is successful. Otherwise, if an error has occurred during compilation, `nil` followed by the error message will be returned.
## List Files
```syn
<table> listfiles(<string> folder)
```
Returns a table of files in `folder`.
## Is File
```syn
<bool> isfile(<string> path)
```
Returns if `path` is a file or not.
## Is Folder
```syn
<bool> isfolder(<string> path)
```
Returns if `path` is a folder or not.
## Make Folder
```syn
<void> makefolder(<string> path)
```
Creates a new folder at `path`.
## Delete Folder
```syn
<void> delfolder(<string> path)
```
Deletes the folder in the supplied `path`, if no folder exists, it errors.
## Delete File
```syn
<void> delfile(<string> path)
```
Deletes the file in the supplied `path`, if no file exists, it errors.