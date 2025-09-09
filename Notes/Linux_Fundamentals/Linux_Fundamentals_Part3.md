
````markdown
# Linux Fundamentals Part 3

## Introduction
Welcome to part three (and the finale) of the Linux Fundamentals module.  
So far, throughout the series, you have got hands-on with some fundamental concepts and used some important commands.  

This room is going to showcase some useful utilities and applications that you are likely to use day-to-day.  
You're also going to advance your Linux-fu skills by learning about automation, package management, and service/application logging.

---

## Deploy Your Linux Machine
- Deploy the target Linux machine (IP will be provided in TryHackMe lab).  
- Use credentials:  
  - **Username:** `tryhackme`  
  - **Password:** `tryhackme`  

---

## Terminal Text Editors

### Introducing Terminal Text Editors
Until now, we’ve only used `echo` and pipes (`>` / `>>`) to create files.  
For real editing, we use terminal text editors like **Nano** or **Vim**.

### Nano
To create or edit a file:  
```bash
nano filename
````

#### Example

```bash
nano myfile
```

Nano allows:

* Searching text
* Copy & Paste
* Jumping to a line number
* Finding line numbers

Exit: `Ctrl + X`
Save: `Ctrl + O`

### Vim

More advanced text editor. Benefits:

* Highly customizable (shortcuts, configs).
* Syntax highlighting (great for coding).
* Works on most Linux systems by default.
* Many community tutorials/cheatsheets exist.

---

## General/Useful Utilities

### Downloading Files (wget)

`wget` lets you download files directly from the web.

Example:

```bash
wget https://assets.tryhackme.com/additional/linux-fundamentals/part3/myfile.txt
```

### Transferring Files with SCP (SSH Copy)

`scp` copies files between machines securely over SSH.

#### Example: copy local → remote

```bash
scp important.txt ubuntu@192.168.1.30:/home/ubuntu/transferred.txt
```

#### Example: copy remote → local

```bash
scp ubuntu@192.168.1.30:/home/ubuntu/documents.txt notes.txt
```

### Serving Files with Python Web Server

Quickly serve files using Python:

```bash
python3 -m http.server
```

By default runs on **port 8000**.

Access from another machine:

```bash
wget http://MACHINE_IP:8000/myfile
```

Stop the server with:
`Ctrl + C`

---

## Processes 101

### Viewing Processes

List running processes:

```bash
ps
```

View all processes:

```bash
ps aux
```

Real-time process monitoring:

```bash
top
```

### Managing Processes

Kill a process by PID:

```bash
kill 1337
```

Signals:

* `SIGTERM` – Gracefully terminate
* `SIGKILL` – Force kill
* `SIGSTOP` – Suspend

### System Startup Services

Control processes with `systemctl`:

```bash
systemctl [option] [service]
```

Examples:

```bash
systemctl start apache2
systemctl stop apache2
systemctl enable apache2
systemctl disable apache2
```

### Background & Foreground

Run process in background:

```bash
./script.sh &
```

Bring process to foreground:

```bash
fg
```

Suspend process:
`Ctrl + Z`

---

## Maintaining Your System: Automation

### Cron & Crontab

Schedule jobs with cron. Edit jobs with:

```bash
crontab -e
```

Crontab format:

```
MIN HOUR DOM MON DOW CMD
```

Example: run backup every 12 hours:

```bash
0 */12 * * * cp -R /home/cmnatic/Documents /var/backups/
```

Run on reboot:

```bash
@reboot
```

---

## Maintaining Your System: Package Management

### Software Repositories

Linux packages are installed via **APT** (Advanced Package Tool).

Config files live under:

```bash
/etc/apt/sources.list
/etc/apt/sources.list.d/
```

### Adding a Repository

1. Add GPG key:

   ```bash
   wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -
   ```
2. Create repo file:

   ```bash
   touch /etc/apt/sources.list.d/sublime-text.list
   ```
3. Add entry:

   ```
   deb https://download.sublimetext.com/ apt/stable/
   ```
4. Update & install:

   ```bash
   apt update
   apt install sublime-text
   ```

Remove repo:

```bash
add-apt-repository --remove ppa:PPA_Name/ppa
apt remove [software-name]
```

---

## Maintaining Your System: Logs

Logs are stored in `/var/log/`.

### Examples

* Apache2 logs: `/var/log/apache2/`
* Fail2Ban logs: `/var/log/fail2ban.log`
* UFW (firewall) logs: `/var/log/ufw.log`

These logs are crucial for:

* Monitoring system health
* Detecting intrusions
* Debugging software

---

## Conclusion & Summary

Welcome to the end of the Linux Fundamentals module! 🎉

This part taught you:

* Using terminal text editors (Nano, Vim)
* General utilities like `wget`, `scp`, and serving content with Python webserver
* Managing and monitoring processes
* Automating tasks with cron
* Package management with APT
* System log monitoring in `/var/log`

**Next steps:**

* [Bash Scripting](https://tryhackme.com/room/bashscripting)
* [Regular Expressions](https://tryhackme.com/room/catregex)




