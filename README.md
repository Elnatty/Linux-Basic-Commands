# Linux Cheat Sheet:
```
Basic:
pwd                ==> print the name of current directory   || Ex: pwd
whoami             ==> print the current user                || Ex: whoami
cd [directoryName] ==> enter a directory               		 || Ex: cd Music
cd ..              ==> go back to the parent directory       || Ex: cd ..
cp [file]          ==> copy file                             || Ex: cp music.mp3
ls                 ==> list all items in the current folder  || Ex: ls
clear              ==> clears the terminal                   || Ex: clear
mkdir [foldername] ==> makes folder with the specified name  || Ex: mkdir Songs
rmdir [foldername] ==> removes the specified folder          || Ex: rmdir Songs
echo [param]       ==> outputs the value of the variable	 || Ex: echo "Hi"
					   or string to stdout		             
tree 			   ==> lists the files in the current		 || Ex: tree 
					   directory in tree like format 
```
For sorting files:
mv [file] [newname]==> rename a file or folder  			 || Ex: mv exe txt
cat [filename]     ==> reads the specified file              || Ex: cat cmds.txt
tac [filename]     ==> reads the specified file in reverse   || Ex: tac cmds.txt
tail [file, file]  ==> reads first 10 lines of the files     || Ex: tail cmds.txt
zip [file, file]   ==> compresses the specified files        || Ex: zip files
vi [file]          ==> edit file in the terminal             || Ex: vi cmds.txt
gedit [file]       ==> edits the file in text editor         || Ex: gedit cm.txt
nano [file]        ==> edit file in nano editor              || Ex: nano cmds.txt
tar                ==> same as bzip2 						 || Ex: tar file
bzip2 -z / -d      ==> compress and decompress files with    || Ex: bzip2 -z cmds
                       the extension "bz2" respectively  
gzip               ==> same as bzip2 but compresses files    || Ex: gzip file
						with a gz extension.

Getting help:
man [command]      ==> show the manual of the command        || Ex: ls man
[command] --help   ==> similar to man but ouputs in terminal || Ex: pwd --help
apropos [word]     ==> search for the word in description    || Ex: aprpos list
					   of all commands

More advanced: 
reboot             ==> reboot the system                     || Ex: reboot
which [command]    ==> ouputs the location of the command    || Ex: which ls
su [username]      ==> impersonate as the specified user     || Ex: su root
id				   ==> print user and group information 	 || Ex: id
hostname		   ==>  display or seta computer`s hostname  || Ex: hostname
uname -a          ==> show  all the information of the OS    || Ex: uname -a
exit               ==> exit the current user or the terminal || Ex: exit
shutdown -P +min   ==> shutdowns the system        			 || Ex: shutdown -P

Networking: 
ifconfig           ==> lists all the network interfaces on   || Ex: ifconfig
					   your machine 
netstat            ==> displays network connections for TCP, || Ex: netstat
					   routing tables, and a number of 
                       network interface and network 
                       protocol statistic

For listing hardware:
lscpu             ==> list CPU architecture information      || Ex: lscpu
lsusb             ==> list information about usbs            || Ex: lsusb
lsblk 			  ==> list block devices					 || Ex: lsblk
lsof			  ==> list opened files						 || Ex: lsof
lspci       	  ==> list PCI devices  	 				 || Ex: lscpi

System Administration: 
  User Management:
  who 			     ==> prints the current logged in users  || Ex: who
  users              ==> shows names of users logged in      || Ex: users
  adduser [username] ==> adds another user                   || Ex: adduser david
  useradd [username] ==> same as adduser but is not preferrd || Ex: useradd david
  deluser            ==> deletes a user                      || Ex: deluser david
  usermod [user]	 ==> modify user settings & prefrences   || Ex: usermod david --shell /bin/bash
  passwd [user]      ==> change the password of the user	 || Ex: passwd  
  uptime             ==> shows how long the system has been  || Ex: uptime
                         running, number logged on users and 
                         the system load averages		
  visudo 			 ==> recommended way to edit   			 || Ex: sudo visudo
  						 /etc/sudoers file
  vipw 			     ==> recommended way to edit /etc/passwd || Ex: sudo vipw
  						 file
  systemctl 		 ==> mangae all the background running   || Ex: sudo systemctl disable ssh
  						 services (daemons)
  journalctl 		 ==> see all the logs for systemctl		 || journalctl -xe
  
  Important Files:
  /etc/passwd     ==> stores information of all the users	 || cat /etc/passwd
  /etc/shadow     ==> stores the hashed version of every 	 || cat /etc/passwd
					user`s password
   
ps(Process Status)==> displays currently-running processes   || Ex: ps
ss(Socket Status) ==> used to dump socket statistics and	 || Ex: ss
					  displays information 

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
```top``` view all users and their running processes.

```free``` view ram usage infomation.

```ps aux``` view a snapshot of running processes.

```systemctl``` shows all running services.

```sudo systemctl start tor.service``` starts the tor service.

```sudo system status tor``` checks status of tor service.

```sudo systemctl enable ssh.service``` enables specified (ssh) service to be loaded automatically on boot.

```service tor status``` another way to start services, although ```systemctl``` is better.


#
## SSH and SSH Security (using openssh).
```ssh -i sshkey.private bandit14@localhost``` logging in to a ssh session by specifying a private key with ```-i```. Set permission for the key file, its usually ```400```.

```ssh -t username@ipaddress /bin/sh``` the ```t``` helps changes the default ```/bin/bash``` to ```sh``` in event where it logs you out while signing in to your account.

```ncat --ssl localhost 31000``` login using ssl with ncat.

> the openssh service is a client-server service.

> ```sudo apt-get install openssh-client``` to install client on your client linux machine.

> ```sudo apt-get install openssh-server``` install openssh server client.

> ```cat /etc/ssh/sshd_config``` this is the file that contains the client configs.

> ```ssh-keygen -t rsa``` creating a rsa public-private key-pair for securing your ssh server/session.

> ```ssh-copy-id dking@192.168.0.145``` after generating the keys, you have to copy the id by specifying your ssh-client inorder to add the public key to your ssh-client. Then after that, disable password authentication on your ssh-server for ssh login, so you don't have to use password authentication anymore.

> ```sudo nano /etc/ssh/sshd_config``` scroll to the ```#PasswordAuthentication yes``` and change to ```no```

> make sure you copy your private key to a secured folder and remove rwx permissions for groups and others.

> ```scp test.txt dking@192.168.0.145:/home/dking/``` copying files in ssh environment.

#
## curl
Curl is a utility that allows you to transfer data to from a network server using one of the supportes protocols, http, https, ftp, ftps, sftp, tftp, telnet etc.

```curl --help``` or ```man curl``` help manual.

```curl -o /home/dking/Desktop/hsploit.html https://hsploit.com ``` output the content of the site to a directory ```-o``` and specifying the protocol and site.

```curl -o kaliLinux.iso https://link-to-download-kali.iso``` download contents from the internet with curl using a customized name.

```curl -O https://link-to-download-kali.iso``` specifying ```-O``` downloads the file with its original name ditectly.

```curl -I https://techfashy.com``` specifying the ```-I``` returns the response header sent back the webserver.

```curl -v https://hackersploit.org/``` you can also view the request headers, tls/ssl handshake of a site.


#
## UFW (uncomplicated firewall).
```sudo nano /etc/default/ufw``` default ufw config file.

```sudo ufw status verbose``` checking ufw full status.

```sudo ufw status numbered``` numbers and views all rules, making deleting a rul very easy, for eg; ```sudo ufw delete 1``` deletes rule number 1.

```sudo ufw enable``` enable ufw.

```sudo ufw disable``` disable ufw.

```sudo ufw reset``` reset settings to default config.

```sudo ufw default allow incoming``` to allow incoming connections for systems.

```sudo ufw allow ssh``` or ```sudo ufw allow 22``` for allowing incoming ssh connections.

```sudo ufw allow http``` or ```sudo ufw deny 80 to allow and deny incoming http services.

```sudo ufw allow proto tcp from any to any port 80,443``` self explanatory.

```ufw deny 21/ftp``` deny ftp service.

```ufw deny 3306``` deny sql service.

```sudo ufw deny proto tcp from any to any port 3306``` deny all connections to the sql db.

```ufw allow 192.168.0.1``` allow incoming connection from your gateway(isp) to get internet access.

```sudo ufw allow from 192.168.0.140 to any port 22``` this allows the ip to access the ssh service.

```sudo ufw allow  from 192.168.0.0/24``` allow for a particular subnet.

### Tips to securing ubuntu server with UFW
1. ```sudo ufw reset``` Its better to reset all existing rules and start adding rules manually by yourself. In case you are connected via ssh to the server, make sure the ufw servise is disabled 1st, so as not to get thrown out of your ssh connection ie; ```sudo ufw disable``` before running the ```sudo ufw reset``` cmd.

2. Default policies for incoming connections should be denied, and allowed for outgoing connections. ```sudo ufw default deny incoming``` and ```sudo ufw default allow outgoing```

3. In this case we want to keep port 80, 443 and 22 open. ```sudo ufw allow ssh```, ```sudo ufw allow http```, ```sudo ufw allow https```. And also allow connection from a particular ip address ```sudo ufw allow from 10.0.0.1```.

4. ```sudo ufw allow from 10.0.0.10 to any port 22``` this blocks ssh connections from all ips except ```10.0.0.10``` or for subnets ```10.0.0.1/24```.

5. We are done. You can start/enable ufw service now. 
```sudo systemctl start ufw```, then  ```sudo ufw enable```.

6. ```sudo ufw status verbose``` to check if all is right.

7. ```sudo ufw reset``` reset your rules if you made some mistakes.

#
## Clear your Tracks (Logs) on Linux
This involves wiping all the activity of an attacker so as to avoid any form of detection by incidence response teams or forensic teams such as: clear logs, modify/clear any created registries and remove any files or accts they used.

### on Linux;
The log files are located in the ```cd var/log```

> __shred__ allows you to delete data/files permanently and do so without possibility of recovery.

```sudo shred -vfzu auth.log``` use the ```man shred``` to view the ```-vfzu``` arguments. Auth log contains authentication activities, kernel.log file and other files you used that generated a log file.

### Bash History.
```sudo nano /home/username/.bash_history``` displays history of all used cmds. Instead of clearing/shredding the file, you can use the null redirect to clear the file ```>.bash_history```.


#
## OTW Strings Manipulation.
```file data.txt``` displays file type.

```strings data.txt | grep "="``` this cmd iterates through the data in the data.txt file and searches for the "=".

```strings data.txt | base64 -d``` decoding and encoded base64 text in a data.txt file.
