
# Active Directory Basics

Learn the fundamentals of Microsoft Active Directory (AD), how it organizes users, computers, and resources, and why it’s essential in enterprise networks.

---

## 🎯 Learning Objectives
This room will teach you to:

- Understand what Active Directory is
- Learn about domains, domain controllers, and objects
- Explore how computers and users are managed
- Configure and apply Group Policy Objects (GPOs)
- Understand authentication methods (Kerberos & NTLM)
- Learn about domains, trees, forests, and trusts

---

## 📝 Task 1 - Introduction to Active Directory
Active Directory (AD) centralizes **identity and access management** in Windows environments.  
It lets admins manage users, computers, groups, policies, and authentication all in one place.

- **Domain Controller (DC):** A server that runs AD DS and handles logins + directory services.  
- **Domain:** Logical boundary grouping computers/users under shared policies.  
- **Benefit:** Instead of configuring 200 PCs separately, manage them centrally from the DC.  

---

## 📝 Task 2 - Active Directory Objects
Everything in AD is stored as an **object**.

- **Users** – People with accounts and credentials.  
- **Computers** – Each device in the domain (e.g., `PC01`).  
- **Groups** – Bundle users/computers for shared permissions.  
- **OUs (Organizational Units)** – Containers that hold objects; help apply policies.  

**Key Terms:**  
- `Domain Admins` – Highest-privileged group in the domain.  
- `Server Operators`, `Backup Operators`, `Account Operators` – Specialized roles.  

---

## 📝 Task 3 - Managing Computers in AD
- New computers join the default **Computers** container.  
- Best practice: Move them into separate **OUs**:  
  - Workstations  
  - Servers  
  - Domain Controllers  

**Example PowerShell:** Resetting a password and forcing change at next login:
```powershell
Set-ADAccountPassword -Identity sophie -Reset -NewPassword (Read-Host -AsSecureString "New Password")
Set-ADUser -Identity sophie -ChangePasswordAtLogon $true
````

---

## 📝 Task 4 - Group Policy (GPO)

Policies that control **users** and/or **computers**.

* **Created in:** Group Policy Management
* **Linked to:** OUs (or domain)
* **Examples:** Password length, restrict Control Panel, auto-lock after inactivity
* **Replication:** Stored in `SYSVOL` share, replicated to DCs

**Force update on a machine:**

```powershell
gpupdate /force
```

---

## 📝 Task 5 - Authentication Methods

### Kerberos (default in modern domains)

Ticket-based system. Steps:

1. Client requests a **TGT** from the **KDC** (Domain Controller).
2. KDC sends back TGT + Session Key.
3. Client requests **TGS** for a service (uses Session Key + SPN).
4. KDC issues TGS (encrypted).
5. Client presents TGS → gains access.

✅ Secure: No passwords sent, relies on tickets.

### NTLM / NetNTLM (legacy)

Challenge-response system:

1. Client asks to authenticate.
2. Server sends a random **challenge**.
3. Client hashes (password + challenge).
4. Server/DC verifies.
5. Access allowed/denied.

⚠️ Less secure, kept for compatibility.

---

## 📝 Task 6 - Trees, Forests, and Trusts

* **Tree:** Domains that share a namespace (e.g., `thm.local`, `uk.thm.local`, `us.thm.local`).
* **Forest:** Multiple trees with different namespaces (e.g., `thm.local` + `mht.local`).
* **Trusts:** Allow cross-domain access.

  * One-way trust: A → B (A trusts B).
  * Two-way trust: Both domains trust each other.

---

## 📝 Key Terms

* **AD DS** – Active Directory Domain Services
* **DC** – Domain Controller
* **OU** – Organizational Unit
* **GPO** – Group Policy Object
* **SYSVOL** – DC share that replicates GPOs
* **SPN** – Service Principal Name
* **TGT/TGS** – Kerberos tickets

---

## 📝 Practice Examples

* In a Windows domain, credentials are stored in… → **Active Directory**
* The server that runs AD services is called… → **Domain Controller**
* Which group administers everything in a domain? → **Domain Admins**
* Default container new machines go into? → **Computers**
* Should you separate OUs for servers and workstations? → **Yes**
* Network share that distributes GPOs? → **SYSVOL**
* Default authentication protocol? → **Kerberos**
* Legacy protocol still supported? → **NTLM**
* Group of domains sharing a namespace? → **Tree**
* Needed for cross-domain access? → **Trust**

---

## ✅ Summary

* Active Directory centralizes accounts, computers, groups, and policies.
* Domains are managed by Domain Controllers.
* OUs + GPOs let you apply policies to the right users/computers.
* Kerberos = modern secure authentication, NTLM = legacy fallback.
* Trees, forests, and trusts let companies expand across multiple domains.
