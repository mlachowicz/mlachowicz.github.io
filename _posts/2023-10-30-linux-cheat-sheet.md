---
layout: post
title: "Linux Command Cheat Sheet"
excerpt: "A short list of useful commands in Linux systems."
image: images/kioptrix-12.jpg
tags:
  - linux
---

## Linux System Administration

1. Introduction
- Distributions
- Running commands from the command line

2. Working with files and directories
- File system structure
- Creating and deleting files and folders
- Copying, moving, and renaming files and folders
- Searching
- Viewing content
- Packing and unpacking files

3. File editing
- Text editor
- Command line editing with a stream editor

4. Working in the shell
- Command substitution
- Variables
- Init files
- Stream redirection

5. File system permissions
- Understanding permissions and ownership
- Displaying and verifying permissions
- Absolute and symbolic mode
- Changing permissions
- Access mode creation mask
- Changing ownership

6. Working with processes
- Displaying and searching for processes
- Process states
- Managing processes

7. System startup
- Boot program
- System state
- Init system configuration
- Managing services

8. Managing users
- User accounts
- Password security
- Groups
- Creating, changing, and deleting accounts
- User privileges

9. Working on the network
- Establishing secure remote connections
- File transfer
- Network configuration

10. Services
- Installing and configuring web application servers
- Firewall configuration
- High availability proxy server configuration

11. System maintenance
- Resource monitoring
- Task management
- System logs
- Package management

12. Shell scripts
- Basics of 'bash' shell programming
- Exit status
- Tests
- Functions

## 1. Introduction

### Distributions

Selected systems from the Debian family
- Debian
- Ubuntu
- Linux Mint
- Knoppix
- Kali Linux
- Parrot OS
- Armbian
- Tails

Selected systems from the Red Hat family
- Red Hat Enterprise Linux
- CentOS
- Oracle Linux
- Fedora
- Red Flag Linux

Selected systems from the Arch family
- Arch Linux
- Manjaro
- BlackArch
- Athena OS

### Running commands from the command line

Listing the contents of the current directory
```
ls
```

Full listing of directory contents
```
ls -l
```

Full listing of directory contents including hidden entries
```
ls -la
```

Listing the contents of a directory using the full path as an argument
```
ls /boot
```

Listing the contents of a directory using options and an argument
```
ls -lh /boot
```

Quick help for the ```ls``` command
```
ls --help
```

User manual for the ```ls``` command
```
man ls
```

## 2. Working with files and directories

### File system structure

/		    root directory of the entire file system hierarchy
/bin		essential binary command files
/boot		boot loader files
/dev		device files
/etc		system configuration files
/home		home directory for user files
/lib		shared libraries and kernel modules
/media		mount points for removable media
/mnt		temporary mount point for ordinary file systems
/opt		add-on application software packages
/proc		virtual file system providing process information
/root		home directory for the root user
/run		system information since the last boot
/sbin		essential system binaries
/srv		data for services provided by this system
/tmp		temporary files
/usr		secondary hierarchy for user data, containing binary and library files
/var		files that can change in size

### Creating and deleting files and folders

Creating an empty file
```
touch system.txt
```

Creating a directory
```
mkdir linux
```

Deleting a file
```
rm system.txt
```

Deleting a directory with its contents
```
rm -r linux
```

### Copying, moving, and renaming files and folders

Prepare files
```
mkdir linux files
touch system.txt
```

Copying a file to another existing directory
```
cp system.txt linux
```

Duplicating a file
```
cp system.txt system_copy.txt
```

Recursively copying a directory
```
cp -r linux linux_copy
```

Moving a file to another existing directory
```
mv system_copy.txt linux_copy
```

Moving a directory to another existing directory
```
mv linux_copy files
```

Renaming a file
```
mv system.txt os.txt
```

Listing the contents of directories in a tree format
```
sudo apt install tree
tree

--
.
├── files
│   └── linux_copy
│       ├── system_copy.txt
│       └── system.txt
├── linux
│   └── system.txt
└── os.txt

3 directories, 4 files
--
```

Renaming a directory
```
mv files/linux_copy files/copy
```

### Searching

Prepare files
```
echo Linux > os.txt
echo Windows, Linux, macOS > new.txt
```

Searching for files and directories with a given name in the current directory
```
find . -name "os.txt"
```

Searching for files and directories with a given name in a specific directory
```
find / -name "os.txt"
```

Searching for files containing specific text
```
grep "Linux" new.txt
```

### Viewing content

Displaying the content of a text file
```
cat os.txt
```

Displaying the content of a text file with line numbers
```
nl os.txt
```

Viewing the first few lines of a text file
```
head os.txt
```

Viewing the last few lines of a text file
```
tail os.txt
```

Displaying the content of a text file with a pager
```
less os.txt
```

### Packing and unpacking files

Creating a compressed archive with the ```tar``` command
```
tar -czvf archive.tar.gz os.txt
```

Extracting files from a compressed archive
```
tar -xzvf archive.tar.gz
```

Creating a compressed archive with the ```zip``` command
```
zip archive.zip os.txt
```

Extracting files from a compressed archive
```
unzip archive.zip
```

4. File editing

### Text editor

Opening a text file in the 'nano' text editor:
```
nano os.txt
```

### Command line editing with a stream editor

Replacing text in a file using 'sed'
```
echo "Hello, World!" > greeting.txt
sed -i 's/Hello/Hi/' greeting.txt
```

5. Working in the shell

### Command substitution

Running a command and using its output as an argument for another command
```
ls -l /bin/$(which nano)
```

### Variables

Defining and displaying a variable
```
MY_VAR="Hello, Shell!"
echo $MY_VAR
```

### Init files

Displaying the contents of the ```.bashrc``` file
```
cat ~/.bashrc
```

Editing the ```.bashrc``` file
```
nano ~/.bashrc
```

### Stream redirection

Redirecting the output of a command to a file
```
ls -l > list.txt
```

Redirecting the output of a command and appending it to a file
```
ls -l >> list.txt
```

Redirecting the input of a command from a file
```
cat < os.txt
```

6. File system permissions

### Understanding permissions and ownership

Listing file permissions
```
ls -l os.txt
```

Displaying the owner of a file
```
ls -l os.txt
```

### Absolute and symbolic mode

Changing file permissions using absolute mode
```
chmod 644 os.txt
```

Changing file permissions using symbolic mode
```
chmod u+x os.txt
```

* Changing permissions

Changing the owner of a file
```
chown user1 os.txt
```

Changing the group of a file
```
chown :group1 os.txt
```

### Access mode creation mask

Viewing the current umask value
```
umask
```

Changing the umask value
```
umask 022
```

### Changing ownership

Changing the owner and group of a file
```
chown user1:group1 os.txt
```

7. Working with processes

### Displaying and searching for processes

Listing running processes
```
ps
```

Listing all processes
```
ps aux
```

Displaying information about a specific process
```
ps -p 1
```

Searching for processes by name
```
pgrep systemd
```

### Process states

Viewing process states
```
man ps
```

### Managing processes

Sending signals to processes
```
kill -9 1234
```

Stopping a process
```
killall process_name
```

8. System startup

### Boot program

Viewing the boot program configuration
```
cat /etc/default/grub
```

Updating the boot program configuration
```
update-grub
```

### System state

Viewing the current runlevel
```
runlevel
```

Changing the current runlevel
```
init 3
```

### Init system configuration

Viewing the system initialization configuration
```
ls /etc/rc*.d/
```

### Managing services

Displaying the status of a service
```
systemctl status ssh
```

Starting a service
```
systemctl start ssh
```

Stopping a service
```
systemctl stop ssh
```

Restarting a service
```
systemctl restart ssh
```

9. Managing users

### User accounts

Adding a user account
```
adduser user1
```

Changing the password of a user
```
passwd user1
```

Deleting a user account
```
deluser user1
```

### Password security

Enforcing password policies
```
cat /etc/security/pwquality.conf
cat /etc/security/pwquality.conf.d/common-password
```

### Groups

Creating a group
```
groupadd group1
```

Adding a user to a group
```
usermod -aG group1 user1
```

### Creating, changing, and deleting accounts

Changing user account properties
```
usermod -s /bin/bash user1
```

### User privileges

Displaying user privileges
```
sudo -l
```

10. Working on the network

### Establishing secure remote connections

Connecting to a remote server using SSH
```
ssh user1@remote_server
```

Transferring files securely using SCP
```
scp file.txt user1@remote_server:/path/to/destination
```

### File transfer

Transferring files using ```rsync```
```
rsync -avz source_directory/ user1@remote_server:/path/to/destination/
```

### Network configuration

Viewing network interfaces
```
ifconfig
```

Viewing routing tables
```
route
```

11. Services

### Installing and configuring web application servers

Installing Apache web server
```
apt install apache2
```

Configuring the Apache web server
```
nano /etc/apache2/sites-available/000-default.conf
```

### Firewall configuration

Displaying the firewall status
```
ufw status
```

Allowing traffic on a specific port
```
ufw allow 80/tcp
```

### High availability proxy server configuration

Displaying the HAProxy configuration
```
cat /etc/haproxy/haproxy.cfg
```

12. System maintenance

### Resource monitoring

Displaying system information
```
top
```

Viewing memory usage
```
free -m
```

### Task management

Listing running tasks
```
ps aux
```

Killing a task
```
kill -9 process_id
```

### System logs

Viewing system logs
```
cat /var/log/syslog
```

### Package management

Updating the package database
```
apt update
```

Upgrading installed packages
```
apt upgrade
```

13. Shell scripts

### Basics of ```bash``` shell programming

Creating a shell script
```
nano my_script.sh
```

Running a shell script
```
./my_script.sh
```

### Exit status

Checking the exit status of a command
```
echo $?
```

### Tests

Using conditional statements in shell scripts
```
if [ condition ]; then
  # Code to run if the condition is true
else
  # Code to run if the condition is false
fi
```

### Functions

Defining and calling a function in a shell script
```
my_function() {
  # Function code here
}

my_function  # Calling the function
```