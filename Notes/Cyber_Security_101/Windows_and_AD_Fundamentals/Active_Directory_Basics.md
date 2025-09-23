
---

````markdown
# Active Directory Basics

This module introduces the fundamental concepts and functionality provided by **Active Directory (AD)**.

---

## 📝 Room Objectives
By the end of this lesson, you should understand:

- What Active Directory is  
- What a Windows Domain is  
- What components make up an AD Domain  
- Forests and Domain Trusts  
- How users, computers, and policies are managed  

---

## Task 1: Introduction
Microsoft Active Directory is the backbone of many organizations. It simplifies management of devices and users within a corporate environment by centralizing identity and access control.

**Key points:**
- Centralized identity management
- Simplifies administration of accounts and policies
- Used across enterprises for authentication and authorization

---

## Task 2: Windows Domains
A **Windows Domain** is a group of users and computers managed under a single business or organization.

- **Domain Controller (DC):** The server responsible for running Active Directory services.
- **Centralized identity management:** Credentials are stored in a central repository, accessible across the network.
- **Security policies:** Policies can be enforced from AD and applied to all connected devices.

**Example:**  
Instead of configuring 300 computers individually, AD allows central management through a Domain Controller.

---

## Task 3: Active Directory Components
AD relies on the **Active Directory Domain Service (AD DS)** which stores information about objects in the network.

### Objects in AD
- **Users** – Represent people or service accounts.
- **Machines** – Every computer in the domain has an object account.
- **Groups** – Used to assign permissions and access rights.
- **Security Principals** – Users or groups that can be authenticated and authorized.

### Common Security Groups
- **Domain Admins** – Full control over the domain
- **Server Operators** – Manage Domain Controllers
- **Backup Operators** – Backup/restore files regardless of permissions
- **Account Operators** – Manage user accounts
- **Domain Users** – All standard users
- **Domain Computers** – All joined machines

---

## Task 4: Managing Users in AD
Users and groups are managed using the tool **Active Directory Users and Computers (ADUC)**.  

- **Organizational Units (OUs):** Containers that organize users, groups, and computers.
- **Delegation:** Specific permissions can be delegated, e.g., IT Support resetting user passwords.
- **Example:** A Sales OU can have its own accounts and policies separate from IT.

**PowerShell Example (resetting a password):**
```powershell
Set-ADAccountPassword -Identity sophie -Reset -NewPassword (Read-Host -AsSecureString "NewPassword")
Set-ADUser -Identity sophie -ChangePasswordAtLogon $true
````

---

## Task 5: Managing Computers in AD

All domain-joined computers are stored under the **Computers container** by default.
It’s best practice to separate machines into OUs:

* **Workstations**
* **Servers**
* **Domain Controllers**

This allows policies to be applied differently depending on machine type.

---

## Task 6: Group Policies

**Group Policy Objects (GPOs)** define configurations applied to users or computers.

* **Created in:** Group Policy Management Console (GPMC)
* **Linked to:** Organizational Units
* **Examples:**

  * Password length requirements
  * Restricting Control Panel access
  * Enforcing auto-lock after inactivity

**Force update GPOs manually:**

```powershell
gpupdate /force
```

---

## Task 7: Authentication Methods

AD supports multiple authentication protocols:

### Kerberos

* Default protocol in modern Windows domains
* Uses **tickets** for authentication (Ticket Granting Ticket, Service Ticket)
* More secure, prevents password transmission

### NTLM (NetNTLM)

* Legacy challenge/response protocol
* Less secure, only used for compatibility

---

## Task 8: Trees, Forests, and Trusts

* **Tree:** Multiple domains sharing the same namespace (e.g., `thm.local`, `uk.thm.local`, `us.thm.local`)
* **Forest:** A collection of domain trees in different namespaces (e.g., `thm.local` and `mht.local`)
* **Trust Relationships:**

  * **One-way trust:** Domain A trusts Domain B
  * **Two-way trust:** Both domains trust each other

---

## Task 9: Conclusion

You now understand the fundamentals of Active Directory, including:

* The purpose of Windows Domains
* Key AD components (users, machines, groups, OUs)
* Group Policies and authentication methods
* Domain trees, forests, and trust relationships

**Next steps:**

* Explore **Active Directory Hardening** to learn security best practices
* Study **Compromising Active Directory** modules to understand attacker techniques

---

```
