# 🐧 Linux Shells

Learn about scripting and the different types of Linux shells.

---

## 🎯 Learning Objectives
This room will teach you how to:
- Learn interaction with **Linux shells**
- Use **basic shell commands**
- Explore the **types of Linux shells** available
- Write some **shell scripts**

---

## Task 1 – Introduction to Linux Shells

Most of us use the **GUI (Graphical User Interface)** daily, but Linux also provides the **CLI (Command Line Interface)** via a shell for efficiency and control.  
Think of it like this:

- **GUI** = ordering food from a menu → waiter brings it.  
- **CLI** = going into the kitchen yourself → you directly choose & cook.  
- **Shell** = the helpful chef who interprets your requests.

Advantages:
- CLI is faster and more resource-friendly.  
- Provides more **power** and **control** over the OS.  
- Common in hacking/IT operations.

💡 **Facilitator between user & OS = Shell**

---

## Task 2 – How To Interact With a Shell?

Most Linux distributions use **Bash (Bourne Again SHell)** by default.

### Common Commands
```bash
pwd             # Print current working directory
cd Desktop      # Change directory
ls              # List directory contents
cat filename.txt # Display file contents
grep THM dictionary.txt # Search for a word in a file
````

✅ **Answers:**

* Default shell = **Bash**
* Directory listing command = **ls**
* Search inside files = **grep**

---

## Task 3 – Types of Linux Shells

Check your current shell:

```bash
echo $SHELL
```

List available shells:

```bash
cat /etc/shells
```

Switch shell:

```bash
zsh
```

### Common Shells

**Bash (Bourne Again SHell)**

* Default in most Linux distros.
* Tab completion, command history, strong scripting capabilities.

**Fish (Friendly Interactive Shell)**

* Beginner-friendly, syntax highlighting, customizable.
* No auto spell correction for commands.

**Zsh (Z Shell)**

* Advanced customization, plugins, scripting.
* Syntax highlighting available with plugins.

| Feature           | Bash               | Fish                       | Zsh                 |
| ----------------- | ------------------ | -------------------------- | ------------------- |
| Full Name         | Bourne Again Shell | Friendly Interactive Shell | Z Shell             |
| Scripting         | Extensive support  | Limited scripting          | Excellent w/ extras |
| Tab completion    | Basic              | Advanced                   | Plugin-based        |
| Customization     | Basic              | Some (themes)              | Advanced            |
| User-friendliness | Familiar to most   | Very friendly              | Depends on setup    |
| Syntax highlight  | ❌ Not available    | ✅ Built-in                 | ✅ With plugins      |

✅ **Answers:**

* Shell with syntax highlighting by default = **Fish**
* Shell without auto spell correction = **Bash**
* Command to see history = **history**

---

## Task 4 – Shell Scripting and Components

Shell scripting = combining commands into `.sh` files for automation.

### Create a Script

```bash
nano first_script.sh
```

Example script:

```bash
#!/bin/bash
echo "Hey, what's your name?"
read name
echo "Welcome, $name"
```

Make executable:

```bash
chmod +x first_script.sh
./first_script.sh
```

### Loops

```bash
#!/bin/bash
for i in {1..10}
do
  echo $i
done
```

### Conditional Statements

```bash
#!/bin/bash
echo "Please enter your name:"
read name
if [ "$name" = "Stewart" ]; then
  echo "Welcome Stewart! Here is the secret: THM_Script"
else
  echo "Sorry! You are not authorized."
fi
```

### Comments

```bash
# This is a comment
# Comments improve readability, don’t affect execution
```

✅ **Answers:**

* Shebang in Bash script = `#!/bin/bash`
* Command to give executable permissions = `chmod +x`
* Iterative tasks = **loops**

---

## Task 5 – The Locker Script

**Scenario**: Secure a locker with a script that verifies Username, Company, and PIN.

Example:

```bash
#!/bin/bash
# Define variables
username=""
companyname=""
pin=""

for i in {1..3}; do
  if [ "$i" -eq 1 ]; then
    echo "Enter Username:"; read username
  elif [ "$i" -eq 2 ]; then
    echo "Enter Company Name:"; read companyname
  else
    echo "Enter PIN:"; read pin
  fi
done

# Check values
if [ "$username" = "John" ] && [ "$companyname" = "Tryhackme" ] && [ "$pin" = "7385" ]; then
  echo "Authentication Successful. Access granted."
else
  echo "Authentication Denied!!"
fi
```

✅ **Answer:** Correct PIN = **7385**

---

## Task 6 – Practical Exercise

Run script as **root**:

```bash
sudo su
```

Script searches `/var/log/*.log` files for a keyword.
Example flags:

* **Flag**: `thm-flag01-script`
* **Directory**: `/var/log`

✅ **Answers:**

* File with keyword = `authentication.log`
* Cat sleeping = `under the table`

---

## Task 7 – Conclusion

* Linux shells are powerful tools for automation, scripting, and control.
* Learned about **Bash, Fish, and Zsh**.
* Practiced scripting with **variables, loops, conditionals, comments**.
* Built scripts for authentication and log search.

