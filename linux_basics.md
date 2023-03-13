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

```chmod ugo=rwx test.sh``` set read, write and execute permission for the test.sh file or, ```chmod ugo-x``` to remove execute permission for all users.

```chmod 777 test.sh``` set rwx for all users, ```chmod 764``` set rwx for owner, rw for group, and read permision for others.

```chmod 744 -R Test``` set permissions for parent folders and contents in folder (inheritance).

```groups dking``` shows all groups the user dking belongs to, ```groups root``` shows all group the root user belongs to.

```chown root test.sh``` change the test.sh file ownership to root, ```chgrp root test.sh``` change the group ownership to root.

```