# linux Cmds

```ctl + alt + t``` open terminal.

```ctl + shift + w``` close terminal.

```sudo apt-get update && apt-get upgrade && apt-get dist-upgrade && apt-get clean``` refresh your linux dist.

```ls -lR Documents``` list Recursively all directories and sub directories within a folder.

```cd ~``` go back to user home directory.

```echo 'Hello World' > test.txt``` redirect the echo content into the txt file.

```cat /etc/passwd > password.txt``` redirect contents into other files.

```cp password.txt Test``` copying files into folders.

```rm -R Test``` remove/delete a directory.

```vim password.txt``` to use the vim editor, ```i``` to insert text, hit ```esc```, type ```:q!```, then hit ```enter``` to exit vim and discard changes.

#
## chmod and chgrp.

```chmod ugo=rwx test.sh``` set read, write and execute permission for the test.sh file or, ```chmod ugo-x``` to remove execute permission for all users.

```chmod 777 test.sh``` set rwx for all users, ```chmod 764``` set rwx for owner, rw for group, and read permision for others.

```chmod 744 -R Test``` set permissions for parent folders and contents in folder (inheritance).

```groups dking``` shows all groups the user dking belongs to, ```groups root``` shows all group the root user belongs to.

```chown root test.sh``` change the test.sh file ownership to root, ```chgrp root test.sh``` change the group ownership to root.

#
## indepth search with grep, locate and find.
```grep "word" /etc/passwd``` search for cAsE-sEnTitIvE term "word", or ```grep -i "word" /etc/passwd``` for non cAsE-sEnTitIvE keywords.

```cat /etc/passwd | grep "dking"``` piping outputs into grep to find keywords. eg; ```ifconfig | grep "inet"``` displays results for keyword "inet"

> __Note:__ ```>``` pipes output into a specified location without displaying content on the screen, while ```|``` also pipes output into a specified location while displaying content on the screen. eg; ```cat /etc/passwd > /home/dking/Desktop/test.txt``` and ```cat /etc/passwd | /home/dking/Desktop/test.txt```

```locate "passwd" | grep "/etc/passwd"``` using locate and grep efficiently.

```locate --all "*.conf" | grep resolv``` using locate to find all occurences of the '.conf' extensions, then piping the output to grep to find.

```locate --all -c passwd``` viewing total number of search results using the '-c' argument or ```locate -i -c /etc/passwd``` to get count results for directories.

> __easy way to find occurrences of files__

```find /etc/ -print | grep hosts``` find "hosts" from the ```/etc``` directory or ```find /etc/ -print | grep python```


```sudo find / -type f -name "proxychains.conf"``` ```'/'``` denotes the root dir, ```-type f``` denotes type of file; either ```type d``` for directory or ```type f``` for file, ```-name``` is to specify file name.

```sudo find / -type d -name "dking"``` to find the ```d``` directory name "dking". or ```sudo find / -type d -iname "dking"``` to denote for non case sensitive results.

```find /etc -name "proxychains.conf" -size +1M``` finding stuffs by indicating filesize.

```find /home/ -type f -perm 744``` use find to search for ```f``` file types with specific permissions.

```find . -type f -size 1033c ! -executable``` the ```.``` means current dir, ```! -executable``` means not executable, ```-size 1033c``` means files with size of 1033 bytes.

```find / -user bandit7 -group bandit6 -size 33c -type f``` search for results in entire file system with specified user, group, size and file type.

```find $HOME -name "*.mp4" -group vivek -ls``` To list file in ls command format pass the -ls option to the find.


```find . -type f | xargs file``` finding content in the current dir with ```.```, and using the ```xargs``` to get human readable content ```file``` (readable items from a file).

```man find | grep "byte"``` easily use the mannual guide and grep to find keywords instead of going through the entire mannual.



#
## Enumerating User and PC info.

```whoami``` prints currently logged in user.

```who``` prints all logged in users.

```hostname``` prints workstation name.

```sudo nano /etc/hostname``` to edit workstation name. 

```id``` displays ids, group ids of currently logged in user (basic user enumeration).


```lsb_release -a``` basic info about your installed debian linux distribution, or ```cat /etc/issue```

```lscpu``` enumerating cpu information.

```uname -a``` enumerating kernel info.

```du -sh *``` view current disk usage, ```du -sh * | grep "10M"``` searching for folders with specified sizes, or ```sudo du -sh * | grep "G"```

```du -shc *``` view the total size of all folders in the current dir.

```df -h``` view entire disk usage details.



#
## Strings manipulations using sort and uniq

```sort data.txt``` sort data in accending order.

```uniq -u``` works after data has been sorted. A good usecase for 'uniq' is ```sort data.txt | uniq -u``` sort data, then print out the unique value on the screen.


#
## Shells configurations
```cat /etc/shells``` view all shells in ur linux dist.

```cat /etc/passwd | grep dking``` displays the current shell for specified users.

```chsh``` change shell to desired shell, then enter the particular shell path ie; ```/usr/bin/fish``` then logout and login.

#
## Archiving and Decompressing with tar.
```tar -cf test.tar Test/``` compressing ```Test``` folder to a tar file ```test.tar```.

```tar -xvf test.tar``` extracting/decompressing the tar file, ```-xvf``` means extract, file and verbose output.

#
## Archiving and Decompressing with tar.gz.
```tar -czf test.tar.gz Test/``` compress using the tar.gz format.

```tar -xzf test.tar.gz``` decompress using the tar.gz format.