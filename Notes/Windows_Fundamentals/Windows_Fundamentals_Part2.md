# Windows Fundamentals 2

## Introduction
In this module, we continue exploring the Windows operating system by covering:

- System Configuration (msconfig)
- UAC (User Account Control) settings
- Computer Management utilities
- System Information
- Resource Monitoring
- Command Prompt essentials
- Registry Editor basics

To start, launch the attached virtual machine (or browser-based machine) and follow along.

---

## Task 2 – System Configuration
The **System Configuration** utility (`msconfig`) is used for advanced troubleshooting and diagnosing startup issues.

### Launching System Configuration
You can launch it by typing the following in the Start Menu or Run dialog:

```bash
msconfig
```

### Tabs in System Configuration
The utility has five tabs:

- **General** – Select which devices/services Windows loads at boot (Normal, Diagnostic, or Selective startup)
- **Boot** – Configure boot options such as Safe Boot, No GUI Boot, Timeout, etc.
- **Services** – Lists all services (running/stopped) configured for the system
- **Startup** – (In Windows 10+) links to Task Manager to enable/disable startup items
- **Tools** – Provides quick access to other troubleshooting utilities

### Example Commands
Run individual tools from the **Tools** tab by launching their executable. Example:

```bash
control.exe
```

(Launches Control Panel)

---

## Task 3 – Change UAC Settings
**User Account Control (UAC)** helps prevent unauthorized changes to the system.

### Command to Open UAC Settings
```bash
UserAccountControlSettings.exe
```

You can move the slider to set notification level from “Always notify” to “Never notify.”

---

## Task 4 – Computer Management
The **Computer Management** utility (`compmgmt.msc`) is a collection of administrative tools grouped into:

- **System Tools** – Task Scheduler, Event Viewer, Shared Folders, Device Manager, etc.
- **Storage** – Disk Management
- **Services and Applications** – Manage Windows services and WMI control

### Common Components
- **Task Scheduler** – Create scheduled tasks to automate processes.
- **Event Viewer** – View logs for system/application events.
- **Shared Folders** – View all shared folders and sessions.
- **Device Manager** – View and manage hardware devices.
- **Disk Management** – Create, extend, shrink, or delete partitions.

### Launch Command
```bash
compmgmt.msc
```

---

## Task 5 – System Information
The **System Information** tool (`msinfo32.exe`) provides a full system overview.

### Sections:
- **System Summary** – Basic OS info (name, version, build)
- **Hardware Resources** – IRQs, DMA, memory usage
- **Components** – Hardware info (display, storage, network)
- **Software Environment** – Drivers, running tasks, environment variables

### Launch Command
```bash
msinfo32.exe
```

---

## Task 6 – Resource Monitor
The **Resource Monitor** utility (`resmon.exe`) shows CPU, memory, disk, and network usage in real time.

### Launch Command
```bash
resmon.exe
```

Sections include:
- **CPU** – Running processes and CPU usage
- **Memory** – Allocation and working set
- **Disk** – Read/write activity by process
- **Network** – Active TCP connections and network utilization

---

## Task 7 – Command Prompt
The **Command Prompt** (`cmd`) is a text-based interface for interacting with Windows.

### Basic Commands
```bash
hostname      # Displays the computer name
whoami        # Displays the logged-in user
cls           # Clears the screen
```

### Network Troubleshooting
```bash
ipconfig            # Show network configuration
ipconfig /all       # Detailed network configuration
ipconfig /?         # Show help manual for ipconfig
```

```bash
netstat            # Show active network connections
netstat -a         # Show all connections and listening ports
netstat -b         # Show process using each connection
```

### Net Command
```bash
net help
net help user
```
Lists syntax and subcommands (e.g., `net user`, `net share`, `net session`).

---

## Task 8 – Registry Editor
The **Registry Editor** allows you to view and modify Windows Registry keys.

### Launch Command
```bash
regedt32.exe
```

### Caution
Changes to the registry can affect OS stability. Make backups before making modifications.

---

## Task 9 – Conclusion
This module focused on system utilities available through **MSConfig** and direct commands.

You learned how to:
- Launch key tools (`msconfig`, `resmon.exe`, `msinfo32.exe`, `compmgmt.msc`, etc.)
- Adjust UAC settings
- View system information and logs
- Monitor performance in real time
- Use basic command-line tools for troubleshooting
- Access and understand the Windows Registry

---

**End of Windows Fundamentals 2**
