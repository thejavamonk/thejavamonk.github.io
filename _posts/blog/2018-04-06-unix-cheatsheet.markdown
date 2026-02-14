---
layout: post
title:  "Unix Commands Cheatsheet for Developers"
date:   2018-04-06
categories: blog
tags: unix linux bash shell
---

A comprehensive cheatsheet of commonly used Unix/Linux commands for developers. This guide covers essential commands for daily development tasks.

## File and Directory Operations

**List files and directories**
{% highlight bash %}
ls -la                    # List all files with details
ls -lh                    # List with human-readable file sizes
ls -lt                    # Sort by modification time
ls -lS                    # Sort by file size
{% endhighlight %}

**Navigate directories**
{% highlight bash %}
cd /path/to/dir          # Change to directory
cd ..                    # Go up one level
cd ~                     # Go to home directory
cd -                     # Go to previous directory
pwd                      # Print working directory
{% endhighlight %}

**Create, copy, move, delete**
{% highlight bash %}
mkdir dirname            # Create directory
mkdir -p dir/sub/sub2    # Create nested directories
touch filename           # Create empty file or update timestamp
cp file1 file2           # Copy file
cp -r dir1 dir2          # Copy directory recursively
mv oldname newname       # Rename or move file/directory
rm filename              # Remove file
rm -r dirname            # Remove directory recursively
rm -rf dirname           # Force remove directory (use with caution!)
{% endhighlight %}

## File Content and Search

**View file contents**
{% highlight bash %}
cat file.txt             # Display entire file
head file.txt            # Show first 10 lines
head -n 20 file.txt      # Show first 20 lines
tail file.txt            # Show last 10 lines
tail -n 20 file.txt      # Show last 20 lines
tail -f file.txt         # Follow file updates in real-time
less file.txt            # View file with pagination
more file.txt            # View file page by page
{% endhighlight %}

**Search for text in files**
{% highlight bash %}
grep "pattern" file.txt                    # Search for pattern in file
grep -i "pattern" file.txt                 # Case-insensitive search
grep -r "pattern" /path/to/dir             # Recursive search in directory
grep -rnw '/path/to/somewhere/' -e 'pattern'  # Recursive with line numbers
grep -l "pattern" *.txt                    # List files containing pattern
grep -v "pattern" file.txt                 # Invert match (exclude pattern)
grep -c "pattern" file.txt                 # Count matching lines
grep -A 3 -B 3 "pattern" file.txt          # Show 3 lines after and before match
{% endhighlight %}

**Find files**
{% highlight bash %}
find . -name "*.txt"                       # Find files by name
find . -type f -name "*.java"              # Find files of specific type
find . -type d -name "test*"               # Find directories
find . -mtime -7                           # Find files modified in last 7 days
find . -size +10M                          # Find files larger than 10MB
find . -name "*.log" -delete               # Find and delete files
find . -name "*.txt" -exec grep "text" {} \;  # Execute command on found files
{% endhighlight %}

## Process Management

**View processes**
{% highlight bash %}
ps aux                   # List all running processes
ps aux | grep java       # Find specific processes
top                      # Interactive process viewer
htop                     # Enhanced interactive process viewer (if installed)
pgrep process_name       # Get process ID by name
{% endhighlight %}

**Manage processes**
{% highlight bash %}
kill PID                 # Terminate process by ID
kill -9 PID              # Force kill process
killall process_name     # Kill all processes by name
pkill process_name       # Kill processes by name pattern
bg                       # Send process to background
fg                       # Bring process to foreground
jobs                     # List background jobs
nohup command &          # Run command immune to hangups
{% endhighlight %}

## System Information

**System details**
{% highlight bash %}
uname -a                 # System information
hostname                 # Show hostname
uptime                   # System uptime
date                     # Current date and time
cal                      # Calendar
whoami                   # Current username
id                       # User ID and group info
{% endhighlight %}

**Resource usage**
{% highlight bash %}
free -h                  # Memory usage (human-readable)
df -h                    # Disk space usage
du -h directory          # Directory size
du -sh *                 # Size of each item in current directory
top                      # CPU and memory usage
vmstat                   # Virtual memory statistics
iostat                   # CPU and I/O statistics
{% endhighlight %}

## Networking

**Network information**
{% highlight bash %}
ifconfig                 # Network interface configuration (deprecated)
ip addr                  # Show IP addresses (modern)
ip route                 # Show routing table
netstat -tuln            # List listening ports
ss -tuln                 # Socket statistics (modern alternative to netstat)
lsof -i :8080            # Show what's using port 8080
{% endhighlight %}

**Network connectivity**
{% highlight bash %}
ping hostname            # Test connectivity
curl https://api.example.com         # Make HTTP request
wget https://example.com/file.zip    # Download file
ssh user@hostname        # Connect via SSH
scp file.txt user@host:/path         # Copy file over SSH
telnet hostname port     # Test port connectivity
{% endhighlight %}

## File Permissions

**View and modify permissions**
{% highlight bash %}
ls -l                    # View file permissions
chmod 755 file.sh        # Set permissions (rwxr-xr-x)
chmod +x script.sh       # Make file executable
chmod -R 755 directory   # Recursively set permissions
chown user:group file    # Change owner and group
chown -R user directory  # Recursively change owner
{% endhighlight %}

**Permission numbers**
```
4 = read (r)
2 = write (w)
1 = execute (x)
7 = rwx (4+2+1)
6 = rw- (4+2)
5 = r-x (4+1)
```

## Compression and Archives

**Tar archives**
{% highlight bash %}
tar -czf archive.tar.gz directory/       # Create compressed archive
tar -xzf archive.tar.gz                  # Extract compressed archive
tar -tf archive.tar.gz                   # List contents without extracting
tar -xzf archive.tar.gz -C /path         # Extract to specific directory
{% endhighlight %}

**Zip files**
{% highlight bash %}
zip -r archive.zip directory/            # Create zip archive
unzip archive.zip                        # Extract zip archive
unzip -l archive.zip                     # List contents
unzip archive.zip -d /path               # Extract to specific directory
{% endhighlight %}

**Other compression**
{% highlight bash %}
gzip file.txt            # Compress file (creates file.txt.gz)
gunzip file.txt.gz       # Decompress file
bzip2 file.txt           # Compress with bzip2
bunzip2 file.txt.bz2     # Decompress bzip2
{% endhighlight %}

## Text Processing

**Manipulate text**
{% highlight bash %}
wc file.txt              # Count lines, words, characters
wc -l file.txt           # Count lines only
sort file.txt            # Sort lines alphabetically
sort -n file.txt         # Sort numerically
sort -r file.txt         # Reverse sort
uniq file.txt            # Remove duplicate lines
cut -d',' -f1 file.csv   # Extract first column from CSV
awk '{print $1}' file    # Print first column
sed 's/old/new/g' file   # Replace text
tr 'a-z' 'A-Z' < file    # Convert lowercase to uppercase
{% endhighlight %}

**Combine commands**
{% highlight bash %}
cat file.txt | grep "error" | wc -l      # Count error lines
ps aux | grep java | awk '{print $2}'    # Get Java process IDs
tail -f app.log | grep ERROR             # Monitor log for errors
find . -name "*.txt" | xargs grep "text" # Search text in found files
{% endhighlight %}

## User and Group Management

**User operations**
{% highlight bash %}
sudo command             # Execute as superuser
su - username            # Switch user
useradd username         # Create user
usermod -aG group user   # Add user to group
passwd username          # Change user password
groups username          # Show user's groups
{% endhighlight %}

## Environment and Variables

**Environment variables**
{% highlight bash %}
env                      # Show all environment variables
echo $PATH               # Show PATH variable
export VAR=value         # Set environment variable
export PATH=$PATH:/new/path  # Add to PATH
alias ll='ls -la'        # Create alias
unalias ll               # Remove alias
history                  # Show command history
!123                     # Execute command #123 from history
!!                       # Execute last command
{% endhighlight %}

## Disk and File System

**Disk operations**
{% highlight bash %}
df -h                    # Show disk usage
df -i                    # Show inode usage
du -sh directory         # Show directory size
du -h --max-depth=1      # Show size of subdirectories
mount                    # Show mounted filesystems
lsblk                    # List block devices
fdisk -l                 # List disk partitions (requires sudo)
{% endhighlight %}

## Useful Shortcuts and Tips

**Command line shortcuts**
```
Ctrl + C                 # Terminate current command
Ctrl + Z                 # Suspend current command
Ctrl + D                 # Exit shell or end input
Ctrl + L                 # Clear screen
Ctrl + A                 # Move to beginning of line
Ctrl + E                 # Move to end of line
Ctrl + R                 # Search command history
Tab                      # Auto-complete
```

**Redirects and pipes**
{% highlight bash %}
command > file.txt       # Redirect output to file (overwrite)
command >> file.txt      # Append output to file
command 2> error.txt     # Redirect errors to file
command &> all.txt       # Redirect output and errors
command1 | command2      # Pipe output to another command
command < input.txt      # Read input from file
{% endhighlight %}

## Performance and Monitoring

**Monitor system**
{% highlight bash %}
dmesg                    # System messages
journalctl -f            # Follow systemd logs
last                     # Show last logged in users
w                        # Who is logged in and what they're doing
uptime                   # How long system has been running
sar                      # System activity report
strace command           # Trace system calls
ldd binary               # Show shared library dependencies
{% endhighlight %}

## Developer-Specific Commands

**For Java developers**
{% highlight bash %}
jps                      # List Java processes
jstat -gc PID            # Java GC statistics
jstack PID               # Thread dump
jmap -heap PID           # Heap dump
{% endhighlight %}

**For Docker users**
{% highlight bash %}
docker ps                # List running containers
docker ps -a             # List all containers
docker images            # List images
docker logs container_id # View container logs
docker exec -it container_id bash  # Enter container shell
{% endhighlight %}

**Version control (Git)**
{% highlight bash %}
git status               # Check repository status
git log --oneline        # Compact commit history
git diff                 # Show changes
git branch -a            # List all branches
{% endhighlight %}

---

**Pro Tips:**
- Use `man command` to read the manual for any command
- Use `command --help` for quick usage information
- Combine multiple commands with `&&` (run if previous succeeds) or `;` (run regardless)
- Use `*` for wildcards: `*.txt` matches all text files
- Use `Ctrl+R` to search through command history interactively

**Additional Resources:**
- [GNU Core Utilities Manual](https://www.gnu.org/software/coreutils/manual/)
- [Linux Command Line Basics](https://www.gnu.org/software/bash/manual/)
- [Stack Overflow - Unix/Linux Questions](https://stackoverflow.com/questions/tagged/unix)