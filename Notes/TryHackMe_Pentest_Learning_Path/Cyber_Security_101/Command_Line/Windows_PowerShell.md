
# Windows PowerShell

Discover the *Power* in PowerShell and learn the basics.

---

## 📘 Learning Objectives

This room will teach you how to:

- Learn what PowerShell is and its capabilities.  
- Understand the basic structure of PowerShell's language.  
- Learn and run some basic PowerShell commands.  
- Understand PowerShell’s many applications in the cybersecurity industry.  

---

## 🏴 Task 1 – Introduction

PowerShell is the second major command-line utility built for the Windows operating system (after Windows Command Line).  
It is powerful for automation, system management, and cybersecurity tasks.

### Objectives
- Learn what PowerShell is and its capabilities.  
- Understand the basics of its command syntax.  
- Learn how to run PowerShell commands.  
- See how it applies to security.  

---

## ⚙️ Task 2 – What is PowerShell?

**From Microsoft:**

> “PowerShell is a cross-platform task automation solution made up of a command-line shell, a scripting language, and a configuration management framework.”

### A Brief History
- Early 2000s: Windows admins struggled with cmd.exe & batch files.  
- Jeffrey Snover (Microsoft engineer) → proposed object-oriented approach.  
- Released in 2006 → integrated with .NET Framework.  
- 2016 → Microsoft released PowerShell Core (cross-platform, open-source).  

### Why It’s Powerful
- **Object-oriented**: handles data as objects (with properties & methods), instead of just plain text.  
- Makes managing complex systems easier (e.g., copying files, stopping processes).  
- Expanded beyond Windows → now works on macOS, Linux.  

**Key difference vs. Command Prompt (cmd.exe):**
- cmd.exe = text-based → parses input/output as strings.  
- PowerShell = works with objects → richer data handling.  

---

## 💻 Task 3 – PowerShell Basics

### Launching PowerShell
Ways to start it:
- **Start Menu**: search `powershell`.  
- **Run dialog**: `Win + R` → `powershell`.  
- **File Explorer**: type `powershell` in address bar.  
- **Task Manager**: File → Run new task → `powershell`.  
- **From cmd.exe**: type `powershell`.  

---

### Basic Syntax
- Commands are called **cmdlets** (pronounced *command-lets*).  
- Format: **Verb-Noun**  

Examples:  
```powershell
Get-Content     # retrieves file content  
Set-Location    # changes current directory  
````

---

### Discovering Cmdlets

* `Get-Command` → list all available cmdlets.
* `Get-Help <cmdlet>` → details, usage, examples.
* `Get-Alias` → shows shortcuts (e.g., `dir` → `Get-ChildItem`).

Example:

```powershell
Get-Command -Name Remove*  
Write-Output "Hello"  
Get-Help New-LocalUser -examples  
```

---

### Extending Functionality

Search modules:

```powershell
Find-Module -Name "PowerShellGet"
```

Install a module:

```powershell
Install-Module -Name "PowerShellGet"
```

---

## 📂 Task 4 – Navigating the File System and Working with Files

PowerShell has cmdlets for handling directories & files.

### Directories

List contents (like `dir`):

```powershell
Get-ChildItem
```

Change directory (like `cd`):

```powershell
Set-Location -Path ".\Documents"
```

Create directory:

```powershell
New-Item -Path ".\captain-cabin\captain-wardrobe" -ItemType "Directory"
```

Remove directory:

```powershell
Remove-Item -Path ".\captain-cabin"
```

---

### Files

Create file:

```powershell
New-Item -Path ".\captain-cabin\captain-boots.txt" -ItemType "File"
```

Delete file:

```powershell
Remove-Item -Path ".\captain-cabin\captain-boots.txt"
```

Copy file:

```powershell
Copy-Item ".\file1.txt" ".\file2.txt"
```

Move file:

```powershell
Move-Item ".\file1.txt" ".\file2.txt"
```

Read file contents (like `type`/`cat`):

```powershell
Get-Content -Path ".\captain-hat.txt"
```

---

## 🔗 Task 5 – Piping, Filtering, and Sorting Data

Piping (`|`) passes output from one cmdlet into another.

Example (sort files by size):

```powershell
Get-ChildItem | Sort-Object Length
```

Filtering:

```powershell
Get-ChildItem | Where-Object {$_.Extension -eq ".txt"}
```

Selecting properties:

```powershell
Get-ChildItem | Select-Object Name, Length
```

Pattern matching:

```powershell
Select-String -Path ".\file.txt" -Pattern "text"
```

Comparison operators:

* `-eq` → equal to
* `-ne` → not equal
* `-gt` → greater than
* `-ge` → greater or equal
* `-lt` → less than
* `-le` → less or equal

Example (filter by size):

```powershell
Get-ChildItem | Where-Object {$_.Length -gt 100}
```

---

## 🖥️ Task 6 – System and Network Information

* `Get-ComputerInfo` → system details (OS, hardware, BIOS).
* `Get-LocalUser` → list local users.
* `Get-NetIPConfiguration` → network configs.
* `Get-NetIPAddress` → IP address info.

Example outputs include:

* IP addresses
* DNS servers
* Default gateway

---

## 📊 Task 7 – Real-Time System Analysis

* `Get-Process` → view running processes.
* `Get-Service` → list services (running/stopped).
* `Get-NetTCPConnection` → view active TCP connections.
* `Get-FileHash` → file integrity check (hashing).

---

## 📝 Task 8 – Scripting

Scripts = `.ps1` files.
They automate repetitive/complex tasks.

### Why It’s Useful

* **Blue team**: log analysis, malware detection, IOC extraction.
* **Red team**: enumeration, remote command execution, obfuscation.
* **Admins**: enforce policies, automate management.

### Key Cmdlet

`Invoke-Command` → run commands on local/remote systems.

Example:

```powershell
Invoke-Command -ComputerName RoyalFortune -ScriptBlock { Get-Service }
```

---

## 🏁 Task 9 – Conclusion

* PowerShell = powerful tool for automation, scripting, and security.
* Supports IT pros, defenders, and attackers alike.
* Next step: **Linux Command Line**.

