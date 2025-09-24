
# Windows Command Line

Learn the essential Windows commands.

---

## 📝 Learning Objectives
This room will teach you how to:

- Display basic system information  
- Check and troubleshoot network configuration  
- Manage files and directories  
- Check and manage running processes  

---

## Task 1 - Introduction
Everyone prefers a GUI until they master a command-line interface (CLI).  

Advantages of CLI:
- **Lower resource usage** – Uses fewer system resources than GUIs.  
- **Automation** – Batch files and scripts simplify repeated tasks.  
- **Remote management** – Convenient for SSH into servers, routers, IoT devices.  

**Default Windows CLI:** `cmd.exe`

---

## Task 2 - Basic System Information

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

## Task 3 - Network Troubleshooting

### Network Configuration

```cmd
ipconfig
```

* Shows IP, subnet, default gateway.

```cmd
ipconfig /all
```

* Full network details: MAC, DHCP, DNS.

### Connectivity

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

* Show connections + process names + PIDs.

---

## Task 4 - File and Disk Management

### Directory Navigation

```cmd
cd
```

* Change directory.

```cmd
dir
```

* List contents.

```cmd
tree
```

* Display directory structure visually.

### Create / Delete Directories

```cmd
mkdir foldername
```

* Create a directory.

```cmd
rmdir foldername
```

* Remove a directory.

### File Operations

```cmd
type file.txt
```

* Show file contents.

```cmd
copy file1.txt file2.txt
```

* Copy file.

```cmd
move file1.txt newfolder\
```

* Move file.

```cmd
del file.txt
```

* Delete file.

Supports wildcards:

```cmd
copy *.md C:\Markdown
```

---

## Task 5 - Task and Process Management

### View Processes

```cmd
tasklist
```

* Lists all processes.

```cmd
tasklist /FI "imagename eq notepad.exe"
```

* Filter for a specific process.

### Kill Process

```cmd
taskkill /PID 1516
```

* Kill by PID.

```cmd
taskkill /IM notepad.exe
```

* Kill by process name.

---

## Task 6 - Conclusion

Other useful commands:

* `chkdsk` – Checks file system and disks for errors/bad sectors.
* `driverquery` – Lists installed drivers.
* `sfc /scannow` – Scans and repairs system files.

### Shutdown / Restart

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

---

## ✅ Key Takeaways

* CLI is lightweight, automatable, and remote-friendly.
* Commands exist for system info, networking, files, and processes.
* `/?` shows help for most commands.
* Use `shutdown`, `tasklist`, `taskkill`, `ipconfig`, `netstat` for practical system control.
