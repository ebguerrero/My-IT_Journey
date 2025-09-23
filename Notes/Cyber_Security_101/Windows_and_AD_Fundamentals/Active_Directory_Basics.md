Got it — thanks for calling that out. I rewrote **Active\_Directory\_Basics.md** to match the exact “Pre-Security lesson” style you used for DNS/HTTP (clear H1, “Overview,” task-like sections with short bullets, examples, code blocks, “Key Terms,” “Practice,” and a closing “Summary”).
Just copy-paste this into:

`Notes/Cyber_Security_101/Windows_and_AD_Fundamentals/Active_Directory_Basics.md`

---

````markdown
# Active Directory Basics

---

## Overview
Active Directory (AD) centralizes identity and access management in Windows environments.  
It lets admins manage **users, computers, groups, policies,** and **authentication** from one place.

---

## Windows Domains
- **Domain:** Logical boundary that groups users/computers for shared authentication & policy.
- **Domain Controller (DC):** Server that runs **AD DS** and handles logons & directory queries.
- **Central store:** Credentials and objects are kept in the directory instead of on each PC.

**Real-world:** Rather than configuring 300 machines one by one, you manage them from the DC.

---

## Active Directory Objects
- **Users** – People or services that sign in (security principals).
- **Computers** – Each domain-joined machine has an account (e.g., `PC1$`).
- **Groups** – Collect users/computers to grant permissions at once.
- **Organizational Units (OUs)** – Containers to organize objects and **scope policies**.
- **Common built-in groups:**
  - **Domain Admins** – Admin over the domain.
  - **Server Operators, Backup Operators, Account Operators**
  - **Domain Users, Domain Computers, Domain Controllers**

---

## Managing Users in AD
Tool: **Active Directory Users and Computers (ADUC)**  
- Create/disable users, reset passwords, move objects between OUs.
- **Delegation:** Grant limited rights (e.g., Helpdesk resets passwords for Sales OU).

**PowerShell examples:**
```powershell
# Reset a user password and force change at next logon
Set-ADAccountPassword -Identity sophie -Reset -NewPassword (Read-Host -AsSecureString "New Password")
Set-ADUser -Identity sophie -ChangePasswordAtLogon $true
````

---

## Managing Computers in AD

* New domain members land in **Computers** container by default.
* Best practice: move into purpose OUs:

  * **Workstations**
  * **Servers**
  * **Domain Controllers**
* Separate OUs ⇒ different security baselines per device type.

---

## Group Policy (GPO)

* **What:** Settings that apply to **users** and/or **computers**.
* **Where:** Create in **Group Policy Management**; **link** to OUs (or domain).
* **Examples:** Password policy, restrict Control Panel, auto-lock after inactivity.
* **Replication:** Policies live under the **SYSVOL** share and replicate to DCs.

**Force refresh on a machine:**

```powershell
gpupdate /force
```

---

## Authentication Methods

### Kerberos (default in modern domains)

Ticket-based flow:

1. Client requests **TGT** from the **KDC** (on the DC).
2. KDC returns **TGT** + **Session Key**.
3. Client requests a **TGS** for a specific service (uses Session Key + SPN).
4. KDC returns **TGS** (encrypted to the service).
5. Client presents **TGS** to the service and authenticates.

**Notes:** No password transmitted; relies on shared secrets and tickets.

### NTLM / NetNTLM (legacy)

Challenge–response flow:

1. Client asks to authenticate.
2. Server sends a **challenge**.
3. Client computes a **response** from the challenge + password hash.
4. Server verifies via the DC.
5. Access allowed/denied.

**Notes:** Kept for compatibility; less secure than Kerberos.

---

## Trees, Forests, and Trusts

* **Tree:** Domains sharing a namespace (e.g., `thm.local`, `uk.thm.local`, `us.thm.local`).
* **Forest:** Multiple trees with different namespaces (e.g., `thm.local` + `mht.local`).
* **Trusts:** Let users in one domain access resources in another.

  * **One-way trust:** A → B (A trusts B).
  * **Two-way trust:** Mutual.

---

## Key Terms

* **AD DS** – Active Directory Domain Services (directory service on DCs).
* **DC** – Domain Controller.
* **OU** – Organizational Unit (policy/application boundary).
* **GPO** – Group Policy Object (settings for users/computers).
* **SYSVOL** – DC share that stores/logically replicates GPOs.
* **SPN** – Service Principal Name (Kerberos target).
* **TGT/TGS** – Kerberos tickets (granting / service).

---

## Practice Examples

* **In a Windows domain, credentials are stored in…** → *Active Directory*
* **The server that runs AD services is called…** → *Domain Controller*
* **Which group typically administers everything in a domain?** → *Domain Admins*
* **Machine account name for `TOM-PC`** → *`TOM-PC$`*
* **Create separate OUs for Servers and Workstations?** → *Yes*
* **Network share that distributes GPOs** → *`SYSVOL`*
* **Can a single GPO target users and computers?** → *Yes (with respective sections)*
* **Is NTLM the default auth in modern domains?** → *No (Kerberos is)*
* **Kerberos ticket that lets you request other tickets** → *TGT*
* **Is a user’s password sent over the network with NTLM?** → *No*
* **Group of domains sharing a namespace** → *Tree*
* **Needed for cross-domain access A ↔ B** → *Trust relationship*

---

## Summary

* AD centralizes **accounts, machines, groups, and policies** on **Domain Controllers**.
* Use **OUs** to organize and scope **GPOs** to the right users/computers.
* **Kerberos** is the default (tickets), **NTLM** is legacy (challenge/response).
* Multi-domain environments form **trees/forests** and rely on **trusts** for access.

---

```

If you want me to reformat **Search_Skills.md** in the exact same style too (same section order & headings), I can do that next.
```
