# Linux Environment Setup & Exploration

This repository documents my hands-on practice with Linux environment setup, navigation, file management, permissions, and system monitoring as part of a DevOps learning journey.

## 📁 Repository Structure
linux-task-1/
├── README.md               # This documentation
├── command_history.txt     # Complete command log
├── screenshots/           # All terminal screenshots
│   ├── navigation.png
│   ├── permissions.png
│   ├── system_monitor.png
│   └── file_editing.png
├── linux_practice/        # Practice files and directories
│   ├── greeting.txt
│   ├── config.txt
│   ├── notes.txt
│   └── projects/
└── learning_summary.md    # Personal learning notes


## 🚀 What I Learned

### 1. **Ubuntu Installation**
- Successfully installed Ubuntu 22.04 LTS on VirtualBox
- Configured virtual machine settings (4GB RAM, 25GB storage)
- Learned to use terminal for all operations

### 2. **Directory Navigation**
- Mastered essential commands: `pwd`, `ls`, `cd`
- Understood Linux filesystem hierarchy
- Differentiated between root (`/`) and home (`~`) directories

### 3. **File & Directory Management**
- Created files and directories using `mkdir`, `touch`
- Removed items safely with `rm`, `rmdir`
- Practiced recursive operations with `-r` flag

### 4. **File Operations**
- Viewed files using `cat`, `less`, `head`, `tail`
- Edited files with `nano` text editor
- Learned basic `vim` navigation

### 5. **Permissions & Ownership**
- Understood file permission notation (rwx)
- Modified permissions using `chmod` (numeric and symbolic)
- Changed ownership with `chown` and `chgrp`
- Learned about `sudo` privileges

### 6. **System Monitoring**
- Monitored processes with `top` and `htop`
- Checked disk usage with `df -h`
- Monitored memory with `free -m`
- Learned to check system uptime and load average

## 📋 Essential Commands Quick Reference

### Navigation
```bash
pwd                     # Print working directory
ls -la                  # List all files with details
cd /path/to/directory   # Change directory
cd ~                    # Go to home directory
cd ..                   # Go up one level
File Operations:-
touch filename.txt      # Create empty file
mkdir dirname           # Create directory
cp source dest          # Copy file/directory
mv source dest          # Move/rename
rm filename             # Remove file
rm -r dirname           # Remove directory recursively

File Viewing:-
cat filename            # Display entire file
less filename           # View file page by page
head -n 10 filename     # Show first 10 lines
tail -n 10 filename     # Show last 10 lines
tail -f logfile         # Follow file in real-time

Permissions:-
chmod 755 filename      # Set rwxr-xr-x permissions
chmod +x script.sh      # Add execute permission
chown user:group file   # Change ownership
ls -l                   # View permissions

System Info:-
df -h                   # Disk space in human format
free -m                 # Memory usage in MB
top                     # Process monitoring
htop                    # Enhanced process viewer
uptime                  # System uptime and load
uname -a                # System information

Searching:-
find . -name "*.txt"    # Find files by name
grep "pattern" file     # Search text in file
grep -r "text" .        # Recursive search

🔧 Tools Used
VirtualBox - Virtualization platform

Ubuntu 22.04 LTS - Linux distribution

Terminal - Bash shell

Git - Version control

Markdown - Documentation

Session 2: Creating Files & Directories:-
# Create practice directory
$ mkdir linux_practice
$ cd linux_practice

# Create multiple directories
$ mkdir dir1 dir2 dir3
$ ls
dir1  dir2  dir3

# Create files
$ touch file1.txt file2.txt file3.md
$ ls -la
total 16
drwxr-xr-x 5 ubuntu ubuntu 4096 [date] .
drwxr-xr-x 3 ubuntu ubuntu 4096 [date] ..
drwxr-xr-x 2 ubuntu ubuntu 4096 [date] dir1
drwxr-xr-x 2 ubuntu ubuntu 4096 [date] dir2
drwxr-xr-x 2 ubuntu ubuntu 4096 [date] dir3
-rw-r--r-- 1 ubuntu ubuntu    0 [date] file1.txt
-rw-r--r-- 1 ubuntu ubuntu    0 [date] file2.txt
-rw-r--r-- 1 ubuntu ubuntu    0 [date] file3.md

# Nested directory structure
$ mkdir -p projects/{web,data,scripts}/backup
$ tree projects/
projects/
├── data
│   └── backup
├── scripts
│   └── backup
└── web
    └── backup

# Remove operations
$ rmdir dir3
$ rm file1.txt

Session 3: File Viewing & Editing:-
# Create and view file
$ echo "Hello Linux World!" > greeting.txt
$ cat greeting.txt
Hello Linux World!

# Append content
$ echo "Learning Linux commands" >> greeting.txt
$ cat greeting.txt
Hello Linux World!
Learning Linux commands

# Multi-line file creation
$ cat > config.txt << EOF
# Server Configuration
Host: localhost
Port: 8080
User: admin
EOF

$ cat config.txt
# Server Configuration
Host: localhost
Port: 8080
User: admin

# Word count
$ wc greeting.txt
2  5 40 greeting.txt

# Using nano editor
$ nano notes.txt
# [Opened nano, added text, saved with Ctrl+X]

Session 4: Permissions & Ownership:-
# Check permissions
$ ls -la
drwxr-xr-x 4 ubuntu ubuntu 4096 [date] .
drwxr-xr-x 3 ubuntu ubuntu 4096 [date] ..
-rw-r--r-- 1 ubuntu ubuntu   40 [date] greeting.txt
-rwxr-xr-x 1 ubuntu ubuntu    0 [date] script.sh

# Change permissions
$ chmod 644 greeting.txt
$ ls -l greeting.txt
-rw-r--r-- 1 ubuntu ubuntu 40 [date] greeting.txt

$ chmod +x script.sh
$ ls -l script.sh
-rwxr-xr-x 1 ubuntu ubuntu 0 [date] script.sh

# Ownership changes (with sudo)
$ sudo touch system_file.txt
$ ls -l system_file.txt
-rw-r--r-- 1 root root 0 [date] system_file.txt

$ sudo chown ubuntu:ubuntu system_file.txt
$ ls -l system_file.txt
-rw-r--r-- 1 ubuntu ubuntu 0 [date] system_file.txt

Session 5: System Monitoring:-
# Disk usage
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        25G  4.2G   20G  18% /

# Memory usage
$ free -m
               total        used        free      shared  buff/cache   available
Mem:            3934         876        1643          21        1414        2801
Swap:           2048           0        2048

# System uptime
$ uptime
10:30:45 up 1:30, 1 user, load average: 0.08, 0.03, 0.01

# Process monitoring
$ top
# [Shows system processes, CPU, memory usage]

# Install htop
$ sudo apt update
$ sudo apt install htop
$ htop
# [Enhanced process viewer interface]

Session 6: Additional Commands Practice:-
# Search for files
$ find . -name "*.txt"
./greeting.txt
./config.txt
./notes.txt

# Search within files
$ grep "Linux" *.txt
greeting.txt:Hello Linux World!
greeting.txt:Learning Linux commands

# Process management
$ ps aux | grep bash
ubuntu    1234  0.0  0.1  10000  5000 pts/0    Ss   10:00   0:00 -bash

# Network check
$ ping -c 4 google.com
PING google.com (142.250.74.46) 56(84) bytes of data.
64 bytes from del03s08-in-f14.1e100.net (142.250.74.46): icmp_seq=1 ttl=117 time=15.4 ms
64 bytes from del03s08-in-f14.1e100.net (142.250.74.46): icmp_seq=2 ttl=117 time=15.6 ms
64 bytes from del03s08-in-f14.1e100.net (142.250.74

