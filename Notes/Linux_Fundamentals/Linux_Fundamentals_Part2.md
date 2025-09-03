# Linux Fundamentals Part 2

---

## Introduction
In Part 2 of Linux Fundamentals, we move beyond the in-browser terminal and begin logging into and controlling remote machines using SSH. This part focuses on:
- Unlocking more potential with flags and arguments
- Advancing filesystem interaction (copying, moving, deleting files)
- Discovering file and folder access management (permissions & users)
- Running first scripts and executables

---

## Accessing Your Linux Machine Using SSH
**What is SSH?**
- **SSH (Secure Shell):** Protocol that allows secure remote command execution.
- Encrypts data during transmission over a network.

**Why it’s important:**
- Remote control of servers/machines.
- Encrypted, secure communication.

**Basic SSH Command:**
```bash
ssh username@<IP>

Replace <IP> with the machine’s IP address.
Example: ssh tryhackme@10.10.224.147
Password: tryhackme (for TryHackMe labs)

Introduction to Flags and Switches
Most commands support arguments/flags, usually identified with - (short form) or -- (long form).
Examples with ls:
ls → List visible files
ls -a → List all files (including hidden .file)
ls --help → Show available options for the command

The Man (Manual) Page
Use man <command> to view detailed documentation.
Example: man ls
Navigation:
Use arrow keys (⬇ to scroll down).
Press q to quit.

Common option:
-h → Displays output in a “human-readable” format (e.g., KB/MB/GB).

Filesystem Interaction (Continued)
Commands:
touch → Create a new file
Example: touch note
mkdir → Create a new directory
Example: mkdir mydirectory
rm → Remove a file
Example: rm note
rm -R → Remove a directory recursively
Example: rm -R mydirectory
cp → Copy a file
Example: cp note note2
mv → Move/rename a file
Example: mv note2 note3
file → Determine the type of a file
Example: file note

Permissions 101
Permission Types:
Read (r): View file contents.
Write (w): Modify or delete file.
Execute (x): Run file as a program/script.

Viewing Permissions: ls -lh

Users & Groups:
Linux permissions can be granular.
Files/folders have an owner and a group.

Switching Users:
su <username> → Switch to another user.
su -l <username> → Switch user with full login environment.

Common Directories
/etc → System configuration files (e.g., passwd, shadow, sudoers).
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
