# Intro to Bash Scripting.
```#!/bin/bash``` the shabang.
> Note; anything after the ```#!``` is used as the interpreter ie; ```/bin/bash```

> Specifying permissions for your scripts, because by default you won't be able to execute ```.sh``` shell scripts. 
+ To grant execution permission: 
  ```bash
  chmod +x script.sh
  ```
+ To revert to previous permission:
  ```bash
  chmod -x script.sh
  ```

#
## Variables.
```bash
#!/bin/bash

# defining variables
FNAME="Nathan"
LNAME="Alabi"

# callin the variables
echo "My name is $FNAME $LNAME"

# concatinating variables with other text.
SPORT="Foot"
echo "Most popular sport is ${SPORT}ball"
```

### user inputs.
```bash
#!/bin/bash

# example 1
# user input
# read -p "enter your name: " name
# echo "welcome, $name"

# example 2
echo enter your name below,
read -p "firstname: " fname
read -p "lastname: " lname
read -p "age: " age

echo "Your name is $fname $lname and you are $age years old."
```