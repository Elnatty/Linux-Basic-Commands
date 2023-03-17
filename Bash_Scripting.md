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

### Conditionals (if/else)

```bash
#!/bin/bash

:'
# syntax

name="Nathan"
if [ "$name" = "Nathan" ];
then
        echo "Welcome Nathan"
fi # end the if statement


example 1
name="Nathan"
if [ "$name" = "Nathan" ];
then
        echo "Welcome Nathan"
fi
'

# example 2
echo "kindly fill in the form below."
read -p "enter first name: " fname
read -p "enter last name: " lname

if [ "$fname" = "Nathan" ];
then
        echo "Welcome Nathan"
else
        echo "invalid user.."
fi
```

### Test scripts.

checking if a directory ```-d``` exists.
```bash
if [ -d /usr/share/wordlists ];
then
        echo "yes the wordlists folder exists"
else
        echo "no it dosen't exists."
fi
```

checking if a fiie ```-f``` exists.
```bash
if [ -d /usr/share/wordlists/rockyou.txt ];
then
        echo "yes the file exists"
else
        echo "no it dosen't exists."
fi
```
```bash
#!/bin/bash

if [ -e /etc/shadow ];
then
        echo "yes the file shadow exists"
else
        echo "no it dosen't exists."
fi
```

#
### For loops
syntax
```bash
#!/bin/bash

for i in $(); 
do
        command
done
```
example 1:
using for loop to loop through a list of names in a file called ```names.txt```
```bash
#!/bin/bash

for i in $( cat names.txt );
do
        echo "The names are: $i"
done

# ---------------------------------
# outputs
The names are: Alexis
The names are: Nathan
The names are: Hannah
The names are: Alabi
The names are: Lucas
The names are: Spiderman
```
__or__

names can be specified like "Nathan" or Nathan.
```bash
#!/bin/bash

for i in Nathan Hannah Alabi;
do
        echo "The names are: $i"
done

# --------------------------------
# outputs
The names are: Nathan
The names are: Hannah
The names are: Alabi
```

#
### Real world ping sweeper script.
This checks for ip addresses that are live in a network.

```bash
read -p "enter subnet:  " ipsubnet

for ip in $(seq 1 254);
do
        ping -c 1 $ipsubnet.$ip | grep "64 bytes" | cut -d " " -f 4 | tr -d ":" & 
done

```

#
### Password Generator
```bash
#!/bin/bash

# simple password generator
read -p "enter length of password:    " pass_length

for p in $(seq 1 5);
do
        # using openssl and base64 encoding method.
        echo "password $p: $(openssl rand -base64 48 | cut -c1-$pass_length)"
done

# outputs:
enter length of password:    40
password 1: w7pqSjJ3F8lQdRgYOeBSU1Bm15gDLC/H6qwURLvG
password 2: ECITFPNkMBDFAKCrvtWG+VIjdGNEVYQryN1AqDhG
password 3: VhO0m1mIYJBPRrQCA0jquCXcMrI6jtumQH88IjZh
password 4: fqbwzrDAkkBBTBE6uuJFjA5wjtnTd25klLs7URaI
password 5: ulGirHLhXR7U9NxFufnPlcqZXRqZ6M0s3UajbN88
```