# Linux Fundamentals Part 1

---

## Introduction
- Linux is another operating system (like Windows, macOS).
- Powers: smart cars, Android devices, supercomputers, servers, home appliances, etc.
- In this room you will:
  - Run your first commands in an interactive Linux machine.
  - Learn essential commands to interact with the filesystem.
  - Search for files.
  - Get introduced to shell operators.

---

## Background on Linux
### Where is Linux Used?
- Websites  
- Car entertainment/control panels  
- Point of Sale (PoS) systems  
- Critical infrastructure (traffic lights, industrial sensors)

### Flavours of Linux
- "Linux" is an umbrella term for OS’s based on UNIX.  
- Open-source, comes in many distributions (Ubuntu, Debian, etc.).  
- Ubuntu Server can run on as little as **512 MB RAM**.  
- First Linux OS release: **1991**.  

---

## Interacting With Your First Linux Machine
- TryHackMe provides an Ubuntu machine you can interact with in-browser.  
- Once deployed, you can practice commands directly in the terminal.  

---

## Running Your First Few Commands
**Terminal** = purely text-based interface.  

Commands:
- `echo` → output text.  
  - Example: `echo Hello`  
- `whoami` → shows the username of the logged-in user.  

---

## Interacting With the Filesystem
Commands:
- `ls` → list files/directories.  
- `cd` → change directory.  
- `cat` → output contents of a file.  
- `pwd` → print working directory (full path).  

Examples:
- `ls`  
  - Lists current directory contents.  
- `cd Pictures`  
  - Change into the *Pictures* directory.  
- `cat todo.txt`  
  - Outputs contents of `todo.txt`.  
- `pwd`  
  - Shows full directory path (e.g., `/home/ubuntu/Documents`).  

---

## Searching for Files
### `find`
- Locate files/directories.  
- Example:  
  - `find -name passwords.txt` → search for file named `passwords.txt`.  
  - `find -name *.txt` → search for all `.txt` files.  

### `grep`
- Search file contents for specific values.  
- Example:  
  - `grep "81.143.211.90" access.log` → search log for matching IP.  

---

## Shell Operators
Symbols:
- `&` → run command in background.  
- `&&` → run multiple commands in sequence (only if first succeeds).  
- `>` → redirect output (overwrite).  
- `>>` → redirect output (append).  

Examples:
- `echo hey > welcome` → overwrite file with "hey".  
- `echo hello >> welcome` → append "hello" to file.  

---

## Conclusions & Summaries
You now know:
- Why Linux is commonplace.  
- How to interact with a Linux machine.  
- Core commands (`echo`, `whoami`, `ls`, `cd`, `cat`, `pwd`).  
- How to search with `find` and `grep`.  
- Basic shell operators (`&`, `&&`, `>`, `>>`).  

➡ Next: **Linux Fundamentals Part 2**.
