## Part 1: Linux File System Hierarchy

- `/` (root)
  - Starting point of the filesystem. All directories branch from here.
  - Command: `ls -l /`
  - Contains: bin, etc, home

- `/home`
  - Personal directories for users
  - Command: `ls -l /home`
  - Contains: user1, ubuntu

- `/root`
  - Home directory of the root/admin user
  - Command: `ls -l /root`
  - Contains: Admin scripts, configs

- `/etc`
  - System-wide configuration files
  - Command: `ls -l /etc`
  - Contains: hostname, passwd

- `/var/log`
  - System and application log files
  - Command: `ls -l /var/log`
  - Contains: syslog, auth.log
  - Use when troubleshooting issues

- `/tmp`
  - Temporary files created by system and users
  - Command: `ls -l /tmp`
  - Contains: temp files, cache
  - Use when checking temporary storage usage

- `/bin`
  - Essential command binaries
  - Command: `ls -l /bin`
  - Contains: ls, cp, mv
  - Use when finding basic system commands

- `/usr/bin`
  - User-level command binaries and installed programs
  - Command: `ls -l /usr/bin`
  - Contains: python, git
  - Use when locating installed tools

- `/opt`
  - Optional or third-party software
  - Command: `ls -l /opt`
  - Contains: custom applications
  - Use when checking manually installed software

## Find the largest log file in /var/log
```bash
du -sh /var/log/* 2>/dev/null | sort -h | tail -5
```
- du -sh /var/log/*
    - du = check disk usage
    - -s = summary per item
    - -h = human-readable (KB, MB, GB)
    - * = all files/folders in /var/log and  Shows size of each log file/folder

- 2>/dev/null
    - 2 = error output (stderr)
    - /dev/null = discard output and Hides permission errors

- | (pipe)
    -  Sends output to next command

- sort -h
    - Sorts by size
    - Understands KB/MB/GB Smallest → largest

- tail -5
    - Shows last 5 lines, Displays 5 largest items
    - Final Meaning (one line): Shows top 5 largest log files/folders in /var/log while hiding errors

## Scenario 1: Service Not Starting
```
Step 1: systemctl status myapp  
Why: Check if service is running or failed

Step 2: journalctl -u myapp -n 50  
Why: View recent error logs

Step 3: systemctl is-enabled myapp  
Why: Check if it starts on boot

Step 4: systemctl list-units --type=service | grep myapp  
Why: Confirm service exists

```
## Scenario 2: High CPU Usage
```
Step 1: top  
Why: See live CPU usage

Step 2: ps aux --sort=-%cpu | head -10  
Why: Identify top CPU-consuming processes

Step 3: Note PID  
Why: Track problematic process

```
## Scenario 3: Finding Docker Logs
```
Step 1: systemctl status docker  
Why: Check service health

Step 2: journalctl -u docker -n 50  
Why: View recent logs

Step 3: journalctl -u docker -f  
Why: Follow logs in real time

```

## Scenario 4: Permission Denied Script
```
Step 1: ls -l backup.sh  
Why: Check permissions

Step 2: chmod +x backup.sh  
Why: Give execute permission

Step 3: ./backup.sh  
Why: Run the script

```
