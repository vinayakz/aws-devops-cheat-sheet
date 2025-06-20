## 1.System Administration & Scripting
Linux commands

### 1. File Management
```sh
$ ls - List directory contents.
$ cd - Change directory.
$ pwd - Print working directory.
$ cp - Copy files or directories.
$ mv - Move or rename files or directories.
$ rm - Remove files or directories.
$ touch - Create a new empty file.
$ mkdir - Create a new directory.
$ rmdir - Remove an empty directory.
$ cat - Concatenate and display file contents.
$ head - Display the first few lines of a file.
$ tail - Display the last few lines of a file.
$ chmod - Change file permissions.
$ chown - Change file ownership.
$ find - Search for files in a directory hierarchy.
$ locate - Find files by name.
$ grep - Search text using patterns.
$ diff - Compare two files line by line.
$ tar - Archive files.
$ zip/unzip - Compress and extract files.
```

```sh
$ scp - Securely copy files over SSH

$ ls: List files and directories.
$ ls -l # Long listing with detail

$ cd: Change directory.
$ cd /home/swapna # Move to /home/swapna directory

$ pwd: Show current directory

$ cp: Copy file
$ cp file1.txt /tmp # Copy file1.txt to /tmp directory

$ mv: Move or rename files.
$ mv oldname.txt newname.txt # Rename file
$ mv file1.txt /tmp # Move to /tmp directory

$ rm: Remove files or directories
$ rm file1.txt # Remove a file
$ rm -rf /tmp/old_directory # Remove directory and contents


$ mkdir: Create directories
$ mkdir new_folder # Create a directory called new_folder

$ cat: Display file contents.
$ cat file.txt
```

### 2. System Information and Monitoring

```sh
$ top - Display running processes and system usage.
$ htop - Interactive process viewer.
$ ps - Display current processes.
v df - Show disk space usage.
$ du - Show directory space usage.
$ free - Show memory usage.
$ uptime - Show system uptime.
$ uname - Show system information.
$ whoami - Display the current logged-in user.
$ lsof - List open files and associated processes.
$ vmstat - Report virtual memory statistics.
$ iostat - Report I/O statistics.
$ netstat - Display network connections and routing tables.
$ ifconfig - Display or configure a network interface.
$ ping - Check network connectivity.
$ traceroute - Track the route packets take to a destination.
```

### 3. Package Management (Ubuntu/Debian)

```sh
$ apt-get update - Update package lists.
$ apt-get upgrade - Upgrade all packages
$ apt-get install - Install packages.
$ apt-get remove - Remove packages.
$ dpkg - Install, remove, and manage individual Debian packages.
$ apt-get: Install, remove, or update packages.
$ sudo apt-get update # Update package lists
$ sudo apt-get install nginx # Install NGINX
```

### 4. User and Permission Management

```sh
$ useradd - Add a new user.
$ userdel - Delete a user.
$ usermod - Modify a user.
$ passwd - Change user password.
$ groupadd - Create a new group.
$ groupdel - Delete a group.
$ groups - Show groups of a user.
$ su - Switch user.
$ sudo - Execute a command as another user, usually root.

----------------------------------
$ useradd: Add a new user.
  $sudo useradd -m newuser # Create a new user with a home directory
$ chmod: Change file permissions.
  $chmod 755 script.sh # Set permissions for owner and others
$ chown: Change file owner.
  $sudo chown newuser file.txt # Change ownership to newuser
```

### 5. Networking

```sh
$ curl - Transfer data from or to a server.
$ wget - Download files from the internet.
$ ssh - Secure shell to a remote server.
$ telnet - Connect to a remote machine.
$ nslookup - Query DNS records.
$ dig - DNS lookup utility.
$ iptables - Configure firewall rules.
$ firewalld - Firewall management (CentOS/RHEL).
$ hostname - Show or set the system hostname.
$ ping: Check connectivity to a host. 
```
### 6. Process Management

```sh
$ kill - Send a signal to a process
$ killall - Kill processes by name.
$ pkill - Kill processes by pattern matching.
$ bg - Move a job to the background.
$ fg - Bring a job to the foreground.
$ jobs - List background jobs.
--------------------------------------------------
$ ps: Show running processes.
  $ ps aux | grep nginx # List processes related to nginx

$ kill: Terminate a process by PID.
  $ kill 1234 # Kill process with PID 1234

$ pkill: Kill processes by name.
  $ pkill nginx # Kill all nginx processes
```

### 7. Disk Management

```sh
$ fdisk - Partition a disk
$ mkfs - Make a filesystem.
$ mount - Mount a filesystem.
$ umount - Unmount a filesystem
$ lsblk - List block devices.
$ blkid - Print block device attributes.
$ fdisk: Manage disk partitions.
$ sudo fdisk -l # List disk partitions
------------------------------------------
$ mount: Mount a filesystem.
  $ sudo mount /dev/sdb1 /mnt # Mount device sdb1 to /mnt
```

### 8. Text Processing

```sh
$ awk - Pattern scanning and processing
$ sed - Stream editor for modifying text.
$ sort - Sort lines of text files.
$ uniq - Report or omit repeated lines.
$ cut - Remove sections from each line of files.
$ wc - Word, line, character count.
$ tr - Translate or delete characters.
$ nl - Number lines of files.
--------------------------------

$ grep: Search text.
  $ grep -a '^2025-06-06' error.log > ~/error_2025-06-06.log

$ awk: Process text with patterns.
  $ awk '{print $1}' file.txt # Print the first column of each line.

$ sed: Edit text in streams.
  $ sed 's/old/new/g' file.txt # Replace "old" with "new"
```

### 9. Logging and Auditing

```sh
$ dmesg - Print or control kernel ring buffer.
$ journalctl - Query the systemd journal.
$ logger - Add entries to the system log.
$ last - Show listing of last logged-in users.
$ history - Show command history.
$ tail -f - Monitor logs in real time.

$ tail: View end of file in real time.
  $ tail -f /var/log/nginx/access.log # Follow NGINX access log

$ journalctl: View system logs.
  $ sudo journalctl -u nginx # Logs for NGINX service

```

### 10. Archiving and Backup

```sh
$ tar - Archive files.
$ rsync - Synchronize files and directories.
$ tar: Archive files.
---------------------------

$ tar -cvf archive.tar /path/to/files # Create an archive
$ tar -xvf archive.tar # Extract an archive
```

### 11. System Configuration and Management

```sh
$ crontab - Schedule periodic tasks.
$ systemctl - Control the systemd system and service manager.
$ service - Start, stop, or restart services.
$ timedatectl - Query and change the system clock.
$ reboot - Restart the system.
$ shutdown - Power off the system.
```

### 12. Containerization & Virtualization

```sh
$ docker - Manage Docker containers
$ kubectl - Manage Kubernetes clusters
$ docker: Manage Docker containers.
$ docker ps # List running containers
$ docker run -d -p 8080:80 nginx # Run NGINX container
$ kubectl: Manage Kubernetes clusters.
  $ kubectl get pods # List all pods
  $ kubectl apply -f deployment.yaml # Deploy configuration
```

### 13. Git Version Control

```sh
$ git status - Show the status of changes.
$ git add - Add files to staging.
$ git commit - Commit changes.
$ git push - Push changes to a remote repository.
$ git pull - Pull changes from a remote repository.
$ git clone - Clone a repository.
$ git remote -v - Show URLs of remote repositories.
$ git remote add <name> <url> - Add a new remote repository.
$ git remote remove <name> - Remove a remote repository by name.
$ git remote rename <old-name> <new-name> - Rename a remote repository.
```

### 14. Network Troubleshooting and Analysis

```sh
$ traceroute: Track packet route
$ traceroute google.com # Show hops to google.com
$ netstat: View network connections, routing tables, and more. 
$ netstat -tuln # Show active listening ports with protocol info
$ ss: Display socket statistics (modern alternative to netstat). 
$ ss -tuln # Show active listening ports
$ iptables: Manage firewall rules.
$ sudo iptables -L # List current iptables rules
```

### 15. Advanced File Management
```sh
$ find: Search files by various criteria.
$ find /var -name "*.log" # Find all .log files under /var
$ find /home -type d -name "test" # Find directories named "test"
$ locate: Quickly find files by nam
$ locate apache2.conf # Locate apache2 configuration file
```

### 16. File Content and Manipulation

```sh
$ split: Split files into parts.
$ split -l 500 largefile.txt smallfile # Split file into 500-line chunks
$ sort: Sort lines in files.sort file.txt # Sort lines alphabetically
$ sort -n numbers.txt # Sort numerically
$ uniq: Remove duplicates from sorted files.
$ sort file.txt | uniq # Remove duplicate lines
```

### 17. Advanced Shell Operations

```sh
$ xargs: Build and execute commands from standard input.
  $ find . -name "*.txt" | xargs rm # Delete all .txt files
$ tee: Read from standard input and write to standard output and files.
  $ echo "new data" | tee file.txt # Write output to file and terminal
```

### 18. Performance Analysis

```sh
$ iostat: Display CPU and I/O statistics.
  $ iostat -d 2 # Show disk I/O stats every 2 seconds
$ vmstat: Report virtual memory stats.
  $ vmstat 1 5 # Display 5 samples at 1-second intervals.
$ sar: Collect and report system activity information.
  $ sar -u 5 5 # Report CPU usage every 5 seconds
```

### 19. Disk and File System Analysis

```sh
$ lsblk: List block devices.
  $ lsblk -f # Show filesystems and partitions
$ blkid: Display block device attributes.
  $ sudo blkid # Show UUIDs for devices
$ ncdu: Disk usage analyzer with a TUI.
  ncdu / # Analyze root directory space usage
```

### 20 File Compression and Decompression

```sh
$ gzip: Compress files.
  $ gzip largefile.txt # Compress file with .gz extension
$ gunzip: Decompress .gz files.
  $ gunzip largefile.txt.gz # Decompress file
$ bzip2: Compress files with higher compression than gzip.
  $ bzip2 largefile.txt # Compress file with .bz2 extension
```

### 21. Environment Variables and Shell Management

```sh
$ env: Display all environment variables.
$ set: Set or display shell options and variables.
  $ set | grep PATH # Show the PATH variable
$ unset: Remove an environment variable.
  $ unset VAR_NAME # Remove a specific environment variable
```

### 22. System Security and Permissions

```sh
$ umask: Set default permissions for new files.
  $ umask 022 # Set default permissions to 755 for new files
$ chmod: Change file or directory permissions.
  $ chmod 700 file.txt # Owner only read, write, execute
$ chattr: Change file attributes.
  $ sudo chattr +i file.txt # Make file immutable
$ lsattr: List file attributes.
  $ lsattr file.txt # Show attributes for a file
```

### 23. Troubleshooting and Debugging

```sh
$ strace: Trace system calls and signals.
  $ strace -p 1234 # Trace process with PID 1234
$ lsof: List open files by processes.
  $ lsof -i :8080 # List processes using port 8080
$ dmesg: Print kernel ring buffer messages.
  $ dmesg | tail -10 # View last 10 kernel messages
```
### 24. File Transfer

```sh
$ rsync: Sync files between local and remote systems.
 $ rsync -avz /local/dir user@remote:/remote/dir
$ scp: Securely copy files between hosts.
  $ scp file.txt user@remote:/path/to/destination # Copy to remote
$ ftp: Transfer files using FTP protocol.
  $ ftp example.com # Connect to FTP server example.com
```

### Job Management and Scheduling

```sh
$ bg: Send a job to the background.
  $ ./script.sh & # Run a script in the background
$ fg: Bring a background job to the foreground.
  $ fg %1 # Bring job 1 to the foreground
$ at: Schedule a command to run once at a specified time.
  $ echo "echo Hello, DevOps" | at now + 2 minutes # Run in 2 minutes
```
