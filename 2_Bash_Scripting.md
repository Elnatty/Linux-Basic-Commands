# Bash Scripting 

### variables
this is like a subshell that executes the cmd ```ls``` in the background, in this case it executes it and stores the output into the variable ```files```
```bash
#!/bin/bash

files=$(ls)
echo $files

# output:
Downloads     Public     Templates
Desktop       Music      py_test  Videos
Documents     Pictures   snap     vmware
```
#
### Math Functions
```expr``` the evaluate expressions is used for maths operations.
```bash
expr 50 + 40
expr 50 - 40
expr 40 / 5
expr 30 \* 4  # we escape the multiplication symbol in bash.

# outputs:
90
10
200
120
```