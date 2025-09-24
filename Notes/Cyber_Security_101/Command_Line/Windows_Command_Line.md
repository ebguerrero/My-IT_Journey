
# 💻 Windows Command Line  

Learn the essential Windows commands.  

---

## 🎯 Learning Objectives  

This room will teach you how to:  

- Display basic system information  
- Check and troubleshoot network configuration  
- Manage files and directories  
- Check and manage running processes  

---

## 📝 Task 1 – Introduction  

Everyone prefers a GUI until they master a command-line interface (CLI).  
Advantages of CLI:  

- **Lower resource usage** – Uses fewer system resources than GUIs.  
- **Automation** – Batch files and scripts simplify repeated tasks.  
- **Remote management** – Convenient for SSH access to servers, routers, IoT devices.  

**Default Windows CLI:** `cmd.exe`  

---

## 📝 Task 2 – Basic System Information  

### Commands  

```cmd
set
````

* Shows environment variables (system path, etc).

```cmd
ver
```

* Displays OS version.

```cmd
systeminfo
```

* OS name, build, manufacturer, processor, memory, etc.

### Useful Tricks

* `more` → View output page by page.
* `driverquery | more` → List drivers one page at a time.
* `help` → Help for a command.
* `cls` → Clear the screen.

---

## 📝 Task 3 – Network Troubleshooting

### 🌐 Network Configuration

```cmd
ipconfig
```

* Shows IP, subnet, default gateway.

```cmd
ipconfig /all
```

* Full network details: MAC, DHCP, DNS.

### 🔌 Connectivity

```cmd
ping example.com
```

* Test connectivity with ICMP packets.

```cmd
tracert example.com
```

* Trace route to target host.

```cmd
nslookup example.com
```

* DNS lookup for a hostname.

```cmd
netstat
```

* Displays active connections and listening ports.

```cmd
netstat -abom
```

* Shows connections with process info.

---

## 📝 Task 4 – File and Disk Management

### 📂 Working With Directories

```cmd
cd
```

* Change directory / show current location.

```cmd
dir
```

* List contents of current directory.
* Options: `/a` (hidden/system files), `/s` (all subdirectories).

```cmd
tree
```

* Display subdirectory structure visually.

```cmd
mkdir folder_name
```

* Create a directory.

```cmd
rmdir folder_name
```

* Remove a directory.

### 📄 Working With Files

```cmd
type file.txt
```

* Show contents of a text file.

```cmd
more file.txt
```

* View long text files page by page.

```cmd
copy file1.txt file2.txt
```

* Copy file.

```cmd
move file1.txt file2.txt
```

* Move file.

```cmd
del file.txt
```

* Delete file.

```cmd
erase file.txt
```

* Delete file (same as `del`).

**Tip:** Use `*` as a wildcard (e.g., `copy *.md C:\Markdown`).

---

## 📝 Task 5 – Task and Process Management

### Commands

```cmd
tasklist
```

* List running processes.

```cmd
tasklist /FI "imagename eq notepad.exe"
```

* Filter tasks by name.

```cmd
taskkill /PID 1234
```

* Kill process by PID.

```cmd
taskkill /FI "imagename eq sshd.exe"
```

* Kill processes by name filter.

---

## 📝 Task 6 – Conclusion

Additional useful commands:

* `chkdsk` – Check file system and disk volumes.
* `driverquery` – List installed device drivers.
* `sfc /scannow` – Scan and repair system files.

**Reminder:**

* Use `more file.txt` to display text files.
* Pipe long output: `some_command | more`
* Use `/ ?` with most commands to view help.

### 🔑 Shutdown Commands

```cmd
shutdown /s
```

* Shutdown system.

```cmd
shutdown /r
```

* Restart system.

```cmd
shutdown /a
```

* Abort scheduled shutdown.
