# Windows Fundamentals 1

In part 1 of the Windows Fundamentals module, we learn about:
- The Windows desktop
- The NTFS file system
- UAC (User Account Control)
- Control Panel
- User accounts and permissions

---

## Task 1: Introduction to Windows
The Windows OS is a complex product with many system files, utilities, settings, and features. In this task, you deploy the Windows virtual machine.

**VM Credentials:**
```bash
User: administrator
Password: letmein123!
```

---

## Task 2: Windows Editions
Windows has been around since 1985 and is the dominant OS for home and corporate users. Over the years, Microsoft has released many versions:

- Windows XP → Popular and long-running, but reached end-of-life.
- Windows Vista → Major overhaul but poorly received.
- Windows 7 → Stable and widely adopted.
- Windows 8.x → Short-lived.
- Windows 10 → Popular modern release.
- Windows 11 → Current version (Home & Pro editions).

**Key Difference:**
- Pro edition allows enabling **BitLocker encryption** (not available on Home).

---

## Task 3: The Desktop (GUI)
The desktop is the graphical user interface (GUI) where you interact with Windows.

### Key Components
1. Desktop (shortcuts, icons)
2. Start Menu
3. Search Box
4. Task View
5. Taskbar
6. Toolbars
7. Notification Area

### Customization Commands
Right-click anywhere on the desktop to:
```bash
View → Change icon size
Sort by → Organize icons
New → Create new folders or shortcuts
```

### Display Settings
Open display settings:
```bash
Right-click desktop → Display settings
Right-click desktop → Personalize
```

### Start Menu Sections
- **Quick actions:** Lock, sign out, change account settings.
- **Recently added apps**
- **Tiles:** Pinned apps/programs (can right-click to unpin or resize).

### Taskbar
Right-click the taskbar to access:
```bash
Toolbars
Task View button
Taskbar settings
```

---

## Task 4: The File System
Windows uses **NTFS** (New Technology File System).

### NTFS Advantages
- Supports files >4GB
- File & folder permissions
- Compression
- **EFS (Encrypting File System)** support

### Permissions Types
| Permission       | Files Meaning                         | Folder Meaning |
|-----------------|--------------------------------------|---------------|
| Read            | View contents                        | View/list files & subfolders |
| Write           | Write data                           | Add files & subfolders |
| Read & Execute  | View + run files                     | View + run + traverse |
| Modify          | Read/write + delete                  | Read/write + delete |
| Full Control    | All actions                          | All actions |

### Viewing Permissions
```bash
Right-click file/folder → Properties → Security tab
```

### Alternate Data Streams (ADS)
NTFS allows files to have hidden streams of data. Useful but can hide malware.

---

## Task 5: The Windows\System32 Folder
System32 contains critical system files. Deleting anything here can render Windows unusable.

**System Variable for Windows folder:**
```bash
%windir%
```

---

## Task 6: User Accounts, Profiles, and Permissions
Two account types:
- **Administrator** → Full system control
- **Standard User** → Limited access

User profile folders are stored under:
```bash
C:\Users\<username>
```

### Viewing Users & Groups
Open Run dialog:
```bash
Win + R → lusrmgr.msc
```

Find:
- User accounts
- Groups (e.g., Remote Desktop Users, Users)
- Built-in Guest account (disabled by default)

---

## Task 7: User Account Control (UAC)
**UAC** helps prevent unauthorized changes by prompting for administrator credentials.

When running programs that require elevated privileges, you will see a prompt:
```bash
Do you want to allow this app to make changes to your device?
```

---

## Task 8: Settings and Control Panel
Windows has two main places for configuration:
- **Settings:** Modern interface (Windows 8+)
- **Control Panel:** Legacy interface (still widely used)

To change view in Control Panel:
```bash
Control Panel → View by: Small icons
```

---

## Task 9: Task Manager
Task Manager shows running processes, performance, and allows ending tasks.

Open Task Manager:
```bash
Ctrl + Shift + Esc
```
Or right-click Taskbar → Task Manager.

---

## Task 10: Conclusion
This was a basic overview of Windows. Topics covered:
- Desktop (GUI)
- NTFS file system & permissions
- System32 folder
- User accounts & permissions
- UAC
- Settings & Control Panel
- Task Manager

Terminate the Windows VM when finished.
