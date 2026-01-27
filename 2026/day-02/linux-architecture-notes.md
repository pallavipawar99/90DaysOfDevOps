# Day 02 – Linux Architecture, Processes, and systemd

## - The core components of Linux (kernel, user space, init/systemd)
#### **Application -> shell -> kernel -> hardware**
#### 1 . Application: 
It represents what the user wants the system to do.
ex. ls,cd ,mkdir
#### 2 . Shell : 
The shell is a command-line interface where the user types commands.
It interprets the command and passes the request to the kernel.
#### 3 . kernel : 
The kernel is the core of Linux.
It receives requests from the shell, manages system resources, and communicates with the hardware.
#### 4 . hardware : 
The kernel interacts with hardware and returns the result back to the user.
