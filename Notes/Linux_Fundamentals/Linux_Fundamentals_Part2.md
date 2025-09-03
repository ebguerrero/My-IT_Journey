# Linux Fundamentals Part 2

## Introduction
In Part 2 of Linux Fundamentals, we move beyond the in-browser terminal and begin logging into and controlling remote machines using SSH.  
This part focuses on:

- Unlocking more potential with flags and arguments  
- Advancing filesystem interaction (copying, moving, deleting files)  
- Discovering file and folder access management (permissions & users)  
- Running first scripts and executables  

---

## Accessing Your Linux Machine Using SSH

### What is SSH?
- **SSH (Secure Shell):** Protocol that allows secure remote command execution.  
- Encrypts data during transmission over a network.  

### Why It’s Important
- Remote control of servers/machines.  
- Encrypted, secure communication.  

### Basic SSH Command
```bash
ssh username@<IP>
Replace <IP> with the machine's IP address.

Example:

bash
Copy code
ssh tryhackme@10.10.224.147
Password: tryhackme (for TryHackMe labs).

Introduction to Flags and Switches
Most commands support arguments/flags, usually identified with:

- (short form)

-- (long form)

Examples with ls:

bash
Copy code
ls        # List visible files
ls -a     # List all files (including hidden .file)
ls --help # Show available options for the command
The Man (Manual) Page
Purpose: The man command provides detailed documentation for system commands.

Example:

bash
Copy code
man ls
Navigation:

Use arrow keys (↓) to scroll down

Press q to quit

Common Option:

bash
Copy code
ls -lh
-h → Displays output in a “human-readable” format (KB/MB/GB).

Filesystem Interaction (Continued)
Commands
bash
Copy code
touch note        # Create a new file
mkdir mydirectory # Create a new directory
cp note note2     # Copy a file
mv note2 note3    # Move or rename a file
rm note           # Remove a file
rm -R mydirectory # Remove a directory recursively
file note         # Determine the type of a file
Permissions 101
Permission Types:

Read (r): View file contents

Write (w): Modify or delete file

Execute (x): Run file as a program/script

Viewing permissions:

bash
Copy code
ls -lh
Users & Groups
Linux permissions can be granular. Each file/folder has an owner and a group.

Switching Users:

bash
Copy code
su <username>    # Switch to another user
su -l <username> # Switch with full login environment
Common Directories
/etc → System configuration files (passwd, shadow, sudoers).

/var → Variable data (e.g., logs under /var/log).

/root → Home directory of the root user.

/tmp → Temporary files (cleared on reboot, accessible by all users).

Summary
By completing Linux Fundamentals Part 2, you learned:

How to connect to a Linux machine remotely using SSH

How to use flags and switches effectively

Where to find documentation with the man pages

Extended filesystem interactions (create, move, copy, delete)

File permissions and switching users

Important system directories (/etc, /var, /root, /tmp)
