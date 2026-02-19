# Day 28 Notes – Teach Back Exercise

---

## 🧩 1. Git Branching (Explained Simply)

Git branching is a way to work on changes without affecting the main project.  
Think of it like creating a copy of a document to try new ideas safely.  

The `main` branch contains the stable, working version of the project.  
When you create a new branch, you can add features or fix bugs there.  

Other developers can keep working on `main` at the same time.  
Once your work is tested and ready, you merge it back into `main`.  

This helps teams work in parallel without breaking the project.

---

## 🔐 2. File Permissions in Linux

File permissions in Linux control who can read, write, or execute a file.  

There are three types of users:
- Owner
- Group
- Others  

There are three types of permissions:
- Read (`r`)
- Write (`w`)
- Execute (`x`)  

For example:
rwxr-xr--

- Owner → can read, write, and execute  
- Group → can read and execute  
- Others → can only read  

Permissions help keep the system secure and prevent unauthorized changes.  
Admins use commands like `chmod` and `chown` to manage them.

---

## ⏰ 3. What is Crontab?

A crontab is a Linux tool used to schedule tasks automatically.  
It allows the system to run commands at specific times or intervals.  

For example, you can schedule a backup every night at 2 AM.  

Each line in a crontab file defines:
- When to run
- What command to run  

The format looks like this:
```
* * * * * command_to_run
| | | | |
| | | | └── Day of Week (0 - 7)  (Sunday = 0 or 7)
| | | └──── Month (1 - 12)
| | └────── Day of Month (1 - 31)
| └──────── Hour (0 - 23)
└────────── Minute (0 - 59)
```

System administrators use crontab to automate backups, clean logs, restart services, and more.  
It saves time and ensures important tasks run consistently.

---
