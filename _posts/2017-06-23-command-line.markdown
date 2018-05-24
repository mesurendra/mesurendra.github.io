---
layout: post
title:  Command Line Tips and Tricks
date: 2016-06-23
description: this is what included images could look like
Tags: Linux
---

### Moving cursor in commandline
```shell
# Clears the entire line (press ctrl and u together)
$ctrl + u

# Delete word before the cursor
$ctrl + w

# I rarely use above keys since i joined vi camp:P
# Enjoy the power of vi in command line
# I really love it so its in may .bash_profile :)
$set -o vi
```
### Show working directory
```shell
$pwd
```

### Listing file
```shell
# List all file and folder in directory ~/Desktop with additional information
$ls -al ~/Deskop

# List all the file having 2 character extension
$ls *.??

# List file start with k or s
$ls [ks]*

# List all file whose first character is not k or s
$ls [!ks]*

# List file whose second character is u or i
$ls ?[ui]*
```

### Change Directory
```shell
# Take you to home directory
$cd

# Change directory to Documents
$cd Documents/

# Take you to previous directory
$cd ..

# Move last working directory
$cd -
```

### Make directory
```shell
# Make entire complex directory trees  inside current location ./work/a/b/c
$ mkdir -p work/a/b/c

# Make directory tree
$mkdir -p work/{d1,d2}/{src,bin,bak}
```

### Delete files and folder
```shell
# Remove unwoantedFile.txt
$rm  unwoantedFile.txt

# Remove all file having extension .pyc
$rm *.pyc

# Remove directory unwnatedFolder
$rm -r unwnatedFolder
```

### Rename file
```shell
# Change the name of the file from  file.txt text to file.xml
# Both commands do same work. Personally i prefer second one :)
$mv /home/abc/file.txt /home/abc/file.xml
$mv /home/abc/file.{txt,xml}
```

### Copy file
```shell
$cp  /source/folder/a.txt /destination/a.txt
```

### Searching files
```shell
# Find files/Folder haveing name workspace
$find . -name  workspace

# Find file  used in last 10 mins
$find / -mmin -10

# Find files modified between now and 1 day ago  (i.e., within the past 24 hours)
$find . -mtime 0

# Find files modified less than 1 day ago  (i.e., within the past 24 hours, as before)
$find . -mtime -1

# Find files modified between 24 and 48 hours ago
$find . -mtime 1

# Find files modified more than 48 hours ago
$find . -mtime +1

# Find files modified between  6 and 9 minutes ago
$find . -mmin +5 -mmin -10

# These options can be combined
$find . -type f -mtime 0 -iname *.mp

# Find file which has permission 644
$find . -perm 644

# Find all the txt files which contains word linux
$find . –name "*.txt" –print | xargs grep "linux"
```

### Work with compressed file
```shell
# Create file1_file2.tar by compressing /home/file1 and /home/file2
$tar -cvf file1_file2.tar /home/file1 /home/file2

# Uncompress file
$tar -xvf file1_file2.tar
```

### File count in a directory
```shell
$find . -type f | wc -l
$ls -laR | wc -l
```

### Alias long and frequent command
```shell
# map ls -al to la
$alias la="ls -al"

# i have this in my .bash_profile, i really love it
$alias  blog="cd /home/surendra/abc/cde/fgh/xyz; source activate blog"
$alias ipn="cd ~/Dropbox/notebooks/; source activate lab; ipython notebook "
$alias dush="du -sm *|sort -n|tail"
```

### Kill all target process
```shell
# Really handy to combine simple command to do complex task.
$ps -ef | grep php| awk  '{print $2}' | xargs kill
$ps aux | grep mypattern | awk '{ print $2}' | xargs kill

# Kill all the process associate with port 4000
$lsof -i :4000| awk '{ NR>1 print $2}' | xargs kill
```

### Executing multiple command at once
```shell
# Run two command in sequence as if they are typed in 2 different lines
$mkdir dir1; cd dir1

# Execute second command if first command fails
$mkdir dir1 || sudo mkdir dir1

# Execute second command if first common succeed
$mkdir dir1 && cd dir1

# Change to directory cd work/a/b/c but if the directory does not exist crate it
# then unzip ~/archive.tar in the location
$cd work/a/b/c || mkdir -p work/a/b/c && tar xvf -C work/a/b/c ~/archive.tar
```

### Crontab for scheduling
```shell
# Edit the crontab
$crontab -e

# List currnet crontab
$crontab -l

# Run python file at desktop. */5 => every 5 minutes
# MIN   HOUR   MDAY  MON  DOW   COMMAND
  */5     *      *     *    *    python ~/Desktop/db_track.py

# Run command at 5:00am,10:00am and 3:00pm every day
00 5,10,15,20 * * *  python ~/Desktop/db_track.py

#To remove crontag
$corntab -r
```

### Environment variable
```shell
# List all environment variables
$env

# Executable path
$echo $PATH
```

### Change mode of file
```shell
# Set file permission write, read and execute to user, group and other (777)
$chmod 777 file1

# Makes the permissions of file2 the same as file1
$chmod --reference file1 file2
```

### Command History
```shell
# Show last used commands
$(up arrow)

# Latest 20 history command
$history  20

# List command history containing word mysql
$history 500 | grep mysql

# Reverse search in command history (press ctrl and r together)
$Ctrl + r

Repeat Ctrl + r to loop through results

# Cancel the search and restore original line
Ctrl + g
```

### To see the usage and free space in hard drive
```shell
# Show free disk space in human readable way
$df - h

# Utilized system space
$df -lP| awk 'NR>1 {sum +=$3 } END  {print "%d GiB", sum/2^20}'

# Total system space
$df -lP| awk 'NR>1 {sum +=$2 } END  {print "%d GiB", sum/2^20}'

# How much disk storage directory "somedir" is using Much much more intuitive and readable.
$du -sh somedir

# Get the 10 biggest files/folders for the current direcotry
$du -s * | sort -n | tail
```

### Copy over remote computer
```shell
# Copy files from a local computer to a remote computer
$scp somefile username@server:/home/username/

# Copy files from remote computer to local computer
$scp username@server:/home/username/file_name /home/local-username/file-name

# This is really interesting and very useful, as the files copied from one server
# to the other,are not going to pass through your computer. The traffic is going
# to pass from one server to the other directly.
$scp user_name1@server1:/home/user_name1/file_name user_name2@server2:/home/user_name2/
```

### SSH connection
```shell
ssh -p port number username@ip_address
```

### Miscellaneous
```shell
# Run last command as root
$sudo !!

# Clear terminal screen
$ctrl + l

# Increase the font size (press control and plus together)
$ctrl+

# Decrease font size (press control and minus together)
$ctrl-

# Command completion (tab key)
#instead of typing ifconfig you can do following
$ifc(press tabkey)

# Generate a random ordered list of 20 numbers. For example to determine order of presentation
$seq 20 | shuf

# Download file using commandline
$wget http://aaa.come/abc.pdf

# Find location of specific **ls** command
$where is ls

# Displays a single line description of a command
$whatis chmod
$whatis mkdir

# Get detailed information of system
$uname -a

# View configuration of network interface
$ifconfig -a

# Display the process in the system sorted by cup usage
$top

# See memory information
$cat  /proc/memingo

# See current date time in command line
$date

# Display the top ten running processes - sorted by memory usage
# ps returns all running processes which are then sorted by the 4th field in numerical order and the top 10 are sent to STDOUT
$ps aux | sort -nk +4 | tail

# Delete all files in a folder that don't match a certain file extension
$rm !(*.py|*.java|*.sh)
```

### Using hashtag in  commands
```shell
# Run php command to kill the process
$ps -ef | grep php| awk  '{print $2}' | xargs kill

# To run the same command we can do reverse search.
#However, if the command content is not unique appending hashtag may slove the issue.
$ps -ef | grep php| awk  '{print $2}' | xargs kill #kill_php
```


###  Working with external drives
```shell
# View All Mounts
$mount

# See the disk logical name
$sudo fdisk -l

# The general mount command syntax to mount a device
$mount -t type device destination_dir

# Mount drive sdd1
$mount /dev/sdd1 /mnt

# Unmount drive /dev/sdd1
$umount /dev/sdd1

```
