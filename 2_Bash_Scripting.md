# Bash Scripting 

## output data on the screen.
1. using printf
```bash
name="DKing"
printf "My name is %s\n" $name

#outputs: My name is Nathan
```
2. using echo
```bash
name="Dking"
echo "My name is $name"

#outputs: My name is Nathan
```


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
# using variables now
i=5
j=10
k=$(($i + $j))
echo $k      # outputs 15.


# outputs:
90
10
200
120
```

> Important Note: to make use of or concatenate inbuilt commands in scripts we use the syntax:
```bash
# for example; pwd
cur_dir=$(pwd)
echo $cur_dir   #outputs the pwd value.
```
but if we want to evaluate or carryout operations on integers we use a similar syntax:
```bash
a=10
b=20
c=$(($a + $b))
echo $c         #outputs 30
```
another example:
```bash
fname="Nathan"
lname="Alabi"

echo "My name is $fname $lname with username $(whoami)"    #outputs My name is Nathan Alabi with username dking

p="My name is $fname $lname with username $(whoami)"

q="$p, 1 + 1 = $((1 + 1))"

echo $q    #outputs My name is Nathan Alabi with username dking, 1 + 1 = 2

```
#
### if statements.
Using conditionals with Numbers
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
Using conditionals with Strings.
```bash
#!/bin/bash

read -p "Enter a username: " username

if [ $username = "DKin" ];then
        echo "Welcome to the Lair $username";
else
        echo "error...";
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
or

```bash
#!/bin/bash

program=htop

if command -v $program;
then
        echo "htop exists.. launching it now ! !"
else
        echo "not found, installing it now ! !"
        sudo apt update && sudo apt intall -y $program
fi

$program
```

#
### exit codes
We can use exit codes determine whether a code execution was successful or not.

```bash
#!/bin/bash

program=htop

sudo apt install htop
echo "The exit code for the $program installation is $?"

# outputs
# The exit code for the $program installation is 0
```

a more finetuned script on error codes:
```bash
#!/bin/bash

prog=htop

sudo apt install $prog
if [ $? -eq 0 ]
then
        echo "Installation of $prog was successful"
        echo "$prog is located at: $(which $prog)"
else
        echo "$prog installation failed."
fi

# outputs:
:'
Installation of htop was successful
htop is located at: /usr/bin/htop
'
```

a more finetuned script on error codes:
we will be redirecting outputs to a log file instead of printing on screen.
```bash
#!/bin/bash

prog=htop

sudo apt install $prog >> success_logs.log
if [ $? -eq 0 ]
then
        echo "Installation of $prog was successful" >> success_logs.log
        echo "$prog is located at: $(which $prog)" >> success_logs.log
else
        echo "$prog installation failed." >> failure_logs.log
fi

# outputs
:'
Reading package lists...
Building dependency tree...
Reading state information...
htop is already the newest version (2.2.0-2build1).
The following packages were automatically installed and are no longer required:
  libwireshark15 libwiretap12 libwsutil13
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
Installation of htop was successful
htop is located at: /usr/bin/htop
'
```

#
### while loops
we will be counting from 1-10 here.
```bash
#!/bin/bash

num=1 

while [ $num -le 5 ]
do
        echo $num
        num=$(($num + 1))
        sleep 0.5
done

#outputs:
:'
1
2
3
4
5
'
```
#
### Universal update script
```bash
#!/bin/bash

release_file=/etc/os-release

# the -q ensures quiet mode.
if grep -q "debian" $release_file
then
        # this check if the linux system is debian dist  
        sudo apt update && sudo apt upgrade && sudo apt dist-upgrade -y
else
        # this checks if the host is Arch based system
        sudo paacman -Syu
fi
```

```bash
#!/bin/bash

release_file=/etc/os-release

if grep -q "Debian" $release_file || grep -q "Ubuntu" $release_file
then
        # this checks for "Debian" or "Ubuntu" based systems
        sudo apt update && sudo apt upgrade && sudo apt dist-upgrade -y
else
        # this checks if the host is Arch based system
        sudo paacman -Syu
fi
```

#
### for loops
```bash
#!/bin/bash

for i in {1..10}
do
        echo $i
        sleep 0.5
done

# outputs 1...to....10
```
```bash
Traversing the content of a file using for loop.

x=$(cat /etc/passwd)

IFS=$'\n'
for i in $x; do
        echo $i
done
```

```bash
#!/bin/bash

# going through all files with the .log extension in the log files folder
for i in ~logfiles/*.log
do
        # then converting them to a .tar.gz file.
        tar -czvf $i.tar.gz $i
done
```
using for loop to iterate contents of a .txt file
```bash
#!/bin/bash

f=aa.txt

for i in `cat $f`
do
        echo $i
        sleep 1
done

#outputs
:'
Monday
Tuesday
Wednesday
Thursday
Friday
Saturday
Sunday
'
```

#
### Where to store scripts in the linux system.
location: /usr/local/bin/

moving it to the directory. `sudo mv simple.sh /usr/local/bin/update`

you might want to change ownership for the script, so that for anyone to run the script they need sudo password.
```bash
sudo chown root:root /usr/local/bin/update

# outputs
we can now type `update` from any location now, and this executes the script.
```
### Adding variables to local path:
`export PATH=/usr/local/bin:$PATH` this adds the `/usr/local/bin` to env local path.

#
### Data Streams;
1. __Standary Output:__ output that is printed to the screen that does not constitute an error. eg; 

2. Standard Errorr: 
