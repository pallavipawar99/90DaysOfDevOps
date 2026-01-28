# Day 03 – Linux Commands Practice
## 1. Process management
```
1. ps
   → Shows processes running in the current shell

2. ps -ef
   → Lists all running processes in full format

3. ps aux
   → Displays all processes with CPU and memory usage

4. top
   → Shows real-time running processes and system usage

5. htop
   → Interactive and user-friendly process viewer (if installed)

6. pgrep ssh
   → Finds process ID (PID) of ssh process

7. pidof nginx
   → Displays PID of a running program

8. kill PID
   → Sends SIGTERM to stop a process gracefully

9. kill -9 PID
   → Force kills a process immediately

10. pkill firefox
    → Kills process by name

11. bg
    → Resumes a stopped job in background

12. fg
    → Brings a background job to foreground

13. jobs
    → Lists background and stopped jobs

14. nice -n 10 command
    → Starts a process with lower priority

15. renice -n -5 PID
    → Changes priority of an existing process

16. uptime
    → Shows system running time and load average

17. watch -n 2 ps -ef
    → Re-runs command every 2 seconds for monitoring

18. vmstat
    → Displays memory, CPU, and process statistics

19. free -h
    → Shows memory usage related to running processes

20. strace -p PID
    → Traces system calls of a running process

```

## 2. File system
```
1. pwd
   → Displays the current working directory path

2. ls
   → Lists files and directories

3. ls -lh
   → Lists files with size in human-readable format

4. cd /path
   → Changes the current directory

5. tree
   → Displays directory structure in tree format

6. mkdir test
   → Creates a new directory

7. mkdir -p a/b/c
   → Creates nested directories

8. rmdir empty_dir
   → Deletes an empty directory

9. rm file.txt
   → Deletes a file

10. rm -rf folder
    → Force deletes a directory and its contents

11. cp file1 file2
    → Copies a file

12. cp -r dir1 dir2
    → Copies a directory recursively

13. mv old new
    → Renames or moves a file or directory

14. touch file.txt
    → Creates an empty file

15. cat file.txt
    → Displays file content

16. less file.txt
    → Views file content page by page

17. head -n 10 file.txt
    → Displays first 10 lines of a file

18. tail -n 10 file.txt
    → Displays last 10 lines of a file

19. df -h
    → Shows disk space usage

20. du -sh folder
    → Shows total size of a directory

```

## 3. Networking troubleshooting
```
1. ip addr
   → Displays IP address and network interfaces

2. ip link
   → Shows network interfaces and their status (UP/DOWN)

3. ip route
   → Displays routing table

4. ping google.com
   → Checks connectivity to a remote host

5. traceroute google.com
   → Traces the network path to a destination

6. tracepath google.com
   → Traces route without root privileges

7. ss -tulnp
   → Shows listening TCP/UDP ports with process info

8. netstat -tulnp
   → Displays open ports and active connections

9. curl https://example.com
   → Tests HTTP/HTTPS connectivity

10. curl -I https://example.com
    → Fetches only HTTP response headers

11. wget https://example.com
    → Downloads a file from the internet

12. dig google.com
    → Performs DNS lookup

13. nslookup google.com
    → Queries DNS records

14. hostname
    → Displays system hostname

15. hostname -I
    → Shows system IP addresses

16. ifconfig
    → Displays network interface info (legacy)

17. tcpdump -i eth0
    → Captures network packets on an interface

18. nc -zv host port
    → Tests connectivity to a specific port

19. whois example.com
    → Displays domain registration info

20. arp -a
    → Shows ARP table entries

```
