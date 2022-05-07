---
layout: default
title: modules
nav_order: 1
# has_children: true
parent: Python
grand_parent: Programming
---
# Modules
Manage the self-written functions.
[Official docs](https://docs.python.org/3/tutorial/modules.html#packages)

---
## The Module Search Path
Say we import ```spam```:<br>
Step 1: search for a built-in module with that name. <br>
Step 2: search in  in a list of directories given by the variable *sys.path* which is initialized from these locations: <br>
- The directory containing the input script
- PYTHONPATH (a list of directory names, with the same syntax as the shell variable PATH).
- The installation-dependent default.


## Packages
Structure Python’s module namespace by using “dotted module names”.