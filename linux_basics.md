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

#
## Users and Groups Management/
```getent passwd``` lists all users in the system.

```getent group``` lists all groups in the system.

```passwd``` changing password for currently logged in user.

```sudo passwd dking``` changing password for the user dking.

```su dking``` switch to the user account.

```sudo useradd nathan``` add a new user nathan.

```sudo userdel -r nathan``` delete the user, specify ```-r``` to remove the user home directory.

```sudo useradd -m -c "new staff acct Nathan" -s /bin/bash nathan``` correct way to add a new user in linux.
```-m``` adds a directory in the /home directory for the user, ```-c``` is for comments on the user acct, ```-s``` is for specifying a custom shell for the new user. This account is without a password tho.

```sudo passwd nathan``` create a password for the new user acct. But this acct don't have sudo permissions.

```su nathan``` switch into the new user acct.

__visudo:__ this is where you manage permissions for users and groups.
```linux
sudo visudo
```
Under the ```# User privilege specification```, you can add a line defining permissions for a user, for example, this will allow the ```nathan``` user to be able to use the ```sudo apt-get``` cmds only.
```linux
nathan  ALL=(ALL) /usr/bin/apt-get
```

```pkexec visudo``` fix your corrupt visudo file.

```sudo groupadd marketing``` create a new group called marketing.

```cat /etc/groups``` views all the groups in the system.

```sudo usermod -aG marketers nathan``` adds a user into the new group.


#
## Networking in Linux
```ip addr``` view ip address of all interfaces.

```ip route``` view routing table.

```ip neigh``` view neighbours in the network.

```dhclient``` info about dhcp.

```netstat -t``` displays current tcp connections.

```netstat -l``` displays all listening ports.

```netstat -lt``` displays all listening tcp ports.

```netstat -lu``` displays all listening udp ports.

```netstat -p``` displays all running processes and their ids.

```sudo netdiscover -i enp2s0``` an active/passive recon tool, for scanning the network (using arp)

```sudo nano /etc/resolv.conf``` view and modify dns information.

```systemd-resolve --status``` view the dns info for all interfaces.

```sudo nano /etc/hosts``` you can block ads using the hosts file, by adding an entry under the ```127.0.1.1 dking``` example; ```0.0.0.0 google.com```, then restart network-manager ```sudo systecmtl restart network-manager.service```  now google.com cant be accessed again (you get redirected to the local host webpage).

#
## Tor and Proxychains.
using Tor to anonymize your traffic.
Tor uses port 9050 on your localhost to run.

```sudo apt-get install tor``` firstly install the tor service.

```sudo systemctl start tor``` start the tor service.

```sudo systemctl status tor``` check the status.

```sudo apt-get install proxychains``` secondly install proxychains.


```sudo nano /etc/proxychain.conf``` file to view and edit configs for proxychain.

> you can select between ```#dynamic_chain```, ```#strict_chain``` or ```#random_chain``` its all up to you.

> normally ```#random_chain``` is preferable for tor. To use this, uncomment it from the list ie; ```random_chain```.

> ```# Proxy DNS requests``` this ensures no memory/dns leaks. Make sure to uncomment it ie; ```Proxy DNS requests```.

> ```# ProxyList format``` gives you examples how to use other proxies (eg; socks5) apart from tor.

> Goto the [ProxyList] section, then add your proxies here. For tor, ```socks5  127.0.0.1  9050``` or your preffered proxies.

> __Finally,__ use the proxychains cmd with preffered browser to start using tor service, ie; ```proxychains firefox dnsleaktest.com``` to check.. Note; speed might be s,ow

### sites to check for dnsleaks:
+ https://whatleaks.site
+ https://dnsleaktest.com/results
+ https://whoer.net

> recommended extensions to disable WebRTC: 
+ WebRTC Leak Prevent.
+ uBlock Origin.

#
## Service and Process Management.
