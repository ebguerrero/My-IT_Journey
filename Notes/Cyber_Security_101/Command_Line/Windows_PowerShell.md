# Windows PowerShell

Discover the "Power" in PowerShell and learn the basics.

---

## 📘 Learning Objectives
This room will teach you how to:
- Learn what PowerShell is and its capabilities.
- Understand the basic structure of PowerShell's language.
- Learn and run some basic PowerShell commands.
- Understand PowerShell's many applications in the cybersecurity industry.

---

## 📜 Task 1 – Introduction

PowerShell is the second major command-line utility built for the Windows operating system (after Windows Command Line).  
It is powerful for automation, system management, and cybersecurity tasks.

**Objectives:**
- Learn what PowerShell is and its capabilities.  
- Understand the basics of its command syntax.  
- Learn to run basic PowerShell commands.  
- See how it applies to security.  

---

## 📜 Task 2 – What Is PowerShell?

From Microsoft:  
> “PowerShell is a cross-platform task automation solution made up of a command-line shell, a scripting language, and a configuration management framework.”

### A Brief History
- Early 2000s: Windows admins struggled with cmd.exe & batch files.  
- Jeffrey Snover (Microsoft engineer) → proposed object-oriented approach.  
- Released in 2006 → integrated .NET Framework.  
- 2016 → Microsoft released **PowerShell Core** (cross-platform, open-source).

### Why It’s Powerful
- **Object-oriented**: handles data as **objects** (with **properties** & **methods**) instead of just plain text.  
- Makes managing complex systems easier (e.g., copying files, stopping processes).  
- Expanded to **Windows, macOS, Linux**.  

**Key difference vs. cmd.exe:**  
- **cmd.exe**: text-based → parses input/output as strings.  
- **PowerShell**: works with objects → richer data handling.

---

## 📜 Task 3 – PowerShell Basics

### Launching PowerShell
Ways to start it:
- **Start Menu**: search `powershell`.  
- **Run dialog**: `Win + R`, type `powershell`.  
- **File Explorer**: type `powershell` in address bar.  
- **Task Manager**: File → Run new task → `powershell`.  
- **From cmd.exe**: type `powershell`.  

---

### Basic Syntax
- **Commands** are called **cmdlets** (pronounced *command-lets*).  
- **Format**: `Verb-Noun`  
  - Example:  
    ```powershell
    Get-Content    # retrieves file content
    Set-Location   # changes current directory
    ```

---

### Discovering Cmdlets
- List all cmdlets:  
  ```powershell
  Get-Command
````

* Filter by type (e.g., only functions):

  ```powershell
  Get-Command -CommandType "Function"
  ```
* Get help/documentation:

  ```powershell
  Get-Help Get-Date
  ```
* Aliases (shortcuts for commands):

  ```powershell
  Get-Alias
  ```

Examples:

```powershell
Get-Command -Name Remove*
Write-Output "Hello"
Get-Help New-LocalUser -examples
```

---

### Extending Functionality

* Search modules:

  ```powershell
  Find-Module -Name "PowerShellGet"
  ```
* Install a module:

  ```powershell
  Install-Module -Name "PowerShellGet"
  ```

---

## 📜 Task 4 – Navigating the File System and Working with Files

PowerShell has cmdlets for handling directories & files.

### Directories

* List contents (like `dir`):

  ```powershell
  Get-ChildItem
  ```
* Change directory (like `cd`):

  ```powershell
  Set-Location -Path ".\Documents"
  ```
* Create directory:

  ```powershell
  New-Item -Path ".\captain-cabin" -ItemType "Directory"
  ```
* Remove directory:

  ```powershell
  Remove-Item -Path ".\captain-cabin"
  ```

---

### Files

* Create file:

  ```powershell
  New-Item -Path ".\captain-cabin\captain-boots.txt" -ItemType "File"
  ```
* Delete file:

  ```powershell
  Remove-Item -Path ".\captain-cabin\captain-boots.txt"
  ```
* Copy file:

  ```powershell
  Copy-Item -Path ".\captain-hat.txt" -Destination ".\captain-cabin\captain-hat2.txt"
  ```
* Move file:

  ```powershell
  Move-Item -Path ".\file1.txt" -Destination ".\file2.txt"
  ```
* Read file contents (like `type`/`cat`):

  ```powershell
  Get-Content -Path ".\captain-hat.txt"
  ```

Example:

```powershell
Get-ChildItem C:\Users
```

---

## 📜 Task 5 – Piping, Filtering, and Sorting Data

Piping (`|`) sends output from one cmdlet into another.

Examples:

```powershell
Get-ChildItem | Sort-Object Length
Get-ChildItem | Where-Object -Property Extension -eq ".txt"
Get-ChildItem | Select-Object Name,Length
Select-String -Path ".\captain-hat.txt" -Pattern "hat"
```

Operators:

* `-ne`: not equal
* `-gt`: greater than
* `-lt`: less than
* `-ge`: greater or equal
* `-le`: less or equal

Example (objects >1000 bytes):

```powershell
Get-ChildItem | Where-Object Property Length -gt 1000
```

---

## 📜 Task 6 – System and Network Information

* Computer/system info:

  ```powershell
  Get-ComputerInfo
  ```
* Local user accounts:

  ```powershell
  Get-LocalUser
  ```
* Network config (like `ipconfig`):

  ```powershell
  Get-NetIPConfiguration
  ```
* IP address info:

  ```powershell
  Get-NetIPAddress
  ```

Outputs include IP addresses, DNS servers, gateway info, system specs, etc.

---

## 📜 Task 7 – Real-Time System Analysis

Monitor live system activity.

* Processes:

  ```powershell
  Get-Process
  ```
* Services:

  ```powershell
  Get-Service
  ```
* Network connections (like `netstat`):

  ```powershell
  Get-NetTCPConnection
  ```
* File integrity checks (hashing):

  ```powershell
  Get-FileHash -Path .\ship-flag.txt
  ```

---

## 📜 Task 8 – Scripting

Scripts = `.ps1` files. Automates repetitive/complex tasks.

**Uses:**

* **Blue team** → log analysis, malware detection, IOC extraction.
* **Red team** → enumeration, remote execution, obfuscation.
* **Admins** → enforce policies, automate mgmt.

### Key Cmdlet: `Invoke-Command`

Runs commands on local/remote systems.

Examples:

```powershell
# Run a script on a server
Invoke-Command -FilePath C:\scripts\test.ps1 -ComputerName Server01

# Run command on a remote server
Invoke-Command -ComputerName Server01 -Credential Domain\User -ScriptBlock { Get-Culture }
```

Lab example:

```powershell
Invoke-Command -ComputerName RoyalFortune -ScriptBlock { Get-Service }
```

---

## 📜 Task 9 – Conclusion

PowerShell is a powerful tool for:

* Automation
* Scripting
* Security

Supports IT pros, defenders, and attackers alike.
