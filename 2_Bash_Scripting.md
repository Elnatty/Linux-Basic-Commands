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

#
### if statements.
```bash
#!/bin/bash

name=2004  

if [ $name -eq 200 ];
then
        echo "condition is true."
else
        echo "condition is false"
fi
```
We are going to check if a file/application exist, if not, then it installs it automatically.
> you can check for the existence of a file ie, ```which htop``` outputs ```/usr/bin/htop``` meaning its available in the system.

```bash
#!/bin/bash

name=/usr/bin/htop              

if [ -f $name ];
then
        echo "htop exists.. launching it now ! !"
else
        echo "not found, installing it now ! !"
        sudo apt update && sudo apt intall -y htop
fi

$name
```