---
layout: default
title: modules
nav_order: 1
# has_children: true
parent: Python
grand_parent: Programming
---

# Modules
Manage the self-written functions. (details see
[official docs](https://docs.python.org/3/tutorial/modules.html#packages) &
[real Python](https://realpython.com/python-import/#import-internals))

---
## About os.path
Determine the current directory using os.path.dirname:
```
current_directory = os.path.dirname(__file__)
```
Determine the parent directory using os.path.split:
```
parent_directory = os.path.split(current_directory)[0] # Repeat as needed
```
Join parent_directory with any sub-directories:
```
file_path = os.path.join(parent_directory, 'path-to-file')
```



## The Module Search Path
Say we import ```spam```:<br>
Step 1: search for a built-in module with that name. <br>
Step 2: search in  in a list of directories given by the variable *sys.path* which is initialized from these locations: <br>
- The directory containing the input script
- PYTHONPATH (a list of directory names, with the same syntax as the shell variable PATH).
- The installation-dependent default.

## Packages
Structure Python’s module namespace by using “dotted module names”. <br>
Template structure to maintain a growing collection of modules. 
```python
sound/                          Top-level package
      __init__.py               Initialize the sound package
      formats/                  Subpackage for file format conversions
              __init__.py
              wavread.py
              wavwrite.py
              aiffread.py
              aiffwrite.py
              auread.py
              auwrite.py
              ...
      effects/                  Subpackage for sound effects
              __init__.py
              echo.py
              surround.py
              reverse.py
              ...
      filters/                  Subpackage for filters
              __init__.py
              equalizer.py
              vocoder.py
              karaoke.py
              ...
```



## Reloading Modules
``` importlib.reload(module-name)```