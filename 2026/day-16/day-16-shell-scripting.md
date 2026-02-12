# Day 16 – Shell Scripting Basics

### Task 1: Your First Script
1. Create a file `hello.sh`
2. Add the shebang line `#!/bin/bash` at the top
3. Print `Hello, DevOps!` using `echo`
4. Make it executable and run it

```bash
chmod +x hello.sh
./hello.sh
```

**Document:** What happens if you remove the shebang line?

    - Without shebang, the script may still run if executed with bash hello.sh
    - But ./hello.sh may fail or use a different shell
    - Shebang tells the system which interpreter to use

---

### Task 2: Variables
1. Create `variables.sh` with:
   - A variable for your `NAME`
   - A variable for your `ROLE` (e.g., "DevOps Engineer")
   - Print: `Hello, I am <NAME> and I am a <ROLE>`

   ![alt text](image-2.png)

   ![alt text](image-3.png)

2. Try using single quotes vs double quotes — what's the difference?
    - Double quotes ("") : Hello, I am PALLAVI and I am a DevOps Engineer
    - Single quotes ('') : Hello, I am $NAME and I am a $ROLE

---

### Task 3: User Input with read
1. Create `greet.sh` that:
   - Asks the user for their name using `read`
   - Asks for their favourite tool
   - Prints: `Hello <name>, your favourite tool is <tool>`

    ![alt text](image.png)

    ![alt text](image-1.png)

---

### Task 4: If-Else Conditions
1. Create `check_number.sh` that:
   - Takes a number using `read`
   - Prints whether it is **positive**, **negative**, or **zero**

    ![alt text](image-4.png)

    ![alt text](image-5.png)

2. Create `file_check.sh` that:
   - Asks for a filename
   - Checks if the file **exists** using `-f`
   - Prints appropriate message

   ![alt text](image-6.png)

   ![alt text](image-7.png)

---

### Task 5: Combine It All
Create `server_check.sh` that:
1. Stores a service name in a variable (e.g., `nginx`, `sshd`)
2. Asks the user: "Do you want to check the status? (y/n)"
3. If `y` — runs `systemctl status <service>` and prints whether it's **active** or **not**
4. If `n` — prints "Skipped."

    ![alt text](image-8.png)

    ![alt text](image-9.png)
