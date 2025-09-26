# Windows PowerShell

_Discover the "Power" in PowerShell and learn the basics._

---

## Task 1: Introduction
- PowerShell = command-line + scripting + automation.
- Objective: Learn basics, run commands, understand use in cyber security.
- Builds on **Windows Command Line** module.

---

## Task 2: What Is PowerShell?
- Cross-platform task automation & configuration framework.  
- Combines:
  - **Command-line interface**
  - **Scripting language**
  - **.NET Framework** integration
- **Object-oriented** → handles data as objects (with properties & methods).
- Expanded beyond Windows → macOS, Linux.  
- Origin: Early 2000s, Jeffrey Snover → solved Windows vs Unix handling (APIs vs text files).

**Key idea:**  
- Traditional CLI = text-based.  
- PowerShell = objects with rich properties + methods.

---

## Task 3: PowerShell Basics
### Launching PowerShell
- **Start Menu:** search `powershell`.  
- **Run dialog:** `Win + R` → `powershell`.  
- **File Explorer:** type `powershell` in address bar.  
- **Task Manager:** File → Run new task → `powershell`.  
- From **cmd.exe** → type `powershell`.

### Basic Syntax
- Commands = **cmdlets** (pronounced “command-lets”).
- **Verb-Noun** format:  
  - `Get-Content` → retrieve file content.  
  - `Set-Location` → change working directory.

### Discovering Cmdlets
- `Get-Command` → list all available cmdlets.
- `Get-Help <cmdlet>` → details, usage, examples.
- `Get-Alias` → shows shortcuts (e.g., `dir` = `Get-ChildItem`).

### Extending Functionality
- `Find-Module` → search online repositories.  
- `Install-Module` → install new cmdlets.  

**Examples:**
```powershell
Get-Command -Name Remove*
Write-Output "hello"
Get-Help New-LocalUser -examples
````

---

## Task 4: Navigating the File System and Working with Files

* `Get-ChildItem` → list files & dirs (`ls` equivalent).
* `Set-Location` → move to directory (`cd` equivalent).
* `New-Item` → create dir/file.
* `Remove-Item` → delete file/dir.
* `Copy-Item` / `Move-Item` → manage files.
* `Get-Content` → display file contents.

**Example:**

```powershell
Get-ChildItem C:\Users
```

---

## Task 5: Piping, Filtering, and Sorting Data

* Use `|` (pipe) to pass output between cmdlets.
* **Sorting**:
  `Get-ChildItem | Sort-Object Length`
* **Filtering**:
  `Get-ChildItem | Where-Object {$_.Extension -eq ".txt"}`
* **Selecting properties**:
  `Get-ChildItem | Select-Object Name, Length`
* **Pattern matching**:
  `Select-String -Path .\file.txt -Pattern "text"`

---

## Task 6: System and Network Information

* `Get-ComputerInfo` → system details (OS, hardware, BIOS).
* `Get-LocalUser` → list local users.
* `Get-NetIPConfiguration` → network configs.
* `Get-NetIPAddress` → IP address info.

**Example outputs include:** IP addresses, DNS servers, default gateway.

---

## Task 7: Real-Time System Analysis

* `Get-Process` → running processes.
* `Get-Service` → list services (running/stopped).
* `Get-NetTCPConnection` → active TCP connections.
* `Get-FileHash` → file integrity check (hashing).

---

## Task 8: Scripting

* Scripts = `.ps1` files.
* Automates repetitive/complex tasks.
* Useful for:

  * **Blue team:** log analysis, malware detection, IOC extraction.
  * **Red team:** enumeration, remote command execution, obfuscation.
  * **Admins:** enforce policies, automate management.

**Key Cmdlet:**

* `Invoke-Command` → run commands on local/remote systems.
* Example:

```powershell
Invoke-Command -ComputerName RoyalFortune -ScriptBlock { Get-Service }
```

---

## Task 9: Conclusion

* PowerShell = powerful tool for automation, scripting, and security.
* Supports IT pros, defenders, and attackers alike.
* Next step: **Linux Command Line**.
