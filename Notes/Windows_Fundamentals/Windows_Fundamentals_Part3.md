# Windows Fundamentals 3

In **Windows Fundamentals 3**, we explore security-focused tools and settings that ship with Windows OS, including Windows Update, Windows Security, Firewall & Network Protection, and other built-in features.

---

## Task 1: Introduction
We continue our journey exploring the Windows operating system, this time focusing on security-related features.

**Machine Details:**
```text
Machine IP: 10.201.103.166
User: administrator
Password: letmein123!
```

The machine was started via the browser.

---

## Task 2: Windows Updates
Windows Update is a Microsoft service that provides security updates, patches, and feature enhancements.

- **Patch Tuesday** – Updates are typically released on the 2nd Tuesday of each month.
- Urgent updates may be pushed outside Patch Tuesday.

To open Windows Update:
```bash
control /name Microsoft.WindowsUpdate
```

Key highlights in the VM:
- Updates are managed by the organization.
- No updates available (VM does not have internet access).
- Restart may be required after updates.

**Answer:**
- Date of definition updates installed: **5/3/2021**

---

## Task 3: Windows Security
Windows Security is your hub for managing device protection.

Focus on **Protection Areas:**
- **Virus & Threat Protection**
- **Firewall & Network Protection**
- **App & Browser Control**
- **Device Security**

Status icons:
- ✅ Green = Protected
- ⚠️ Yellow = Review recommended
- ❌ Red = Immediate attention required

**Answer:**
- Area needing immediate attention: **Virus & Threat Protection**

---

## Task 4: Virus & Threat Protection
This section includes:
- **Current threats** – shows active threats and scan history.
- **Virus & Threat Protection Settings** – where you manage real-time protection, exclusions, and updates.
- **Ransomware Protection** – optional feature to protect against ransomware.

**Key Setting:**
- **Real-time protection** was turned **off** in the VM.

**Answer:**
- Setting Windows asks you to turn on: **Real-time protection**

---

## Task 5: Firewall & Network Protection
Windows Firewall controls traffic flow in and out of the device.

**Firewall Profiles:**
- **Domain** – Used when connected to a domain controller.
- **Private** – Used for home or private networks.
- **Public** – Used for public networks (e.g., airport Wi-Fi).

To open advanced firewall settings:
```bash
wf.msc
```

**Answer:**
- If connected to airport Wi-Fi, active firewall profile: **Public network**

---

## Task 6: App & Browser Control
This section manages **Microsoft Defender SmartScreen** settings.

- **SmartScreen** helps protect against phishing and malicious downloads.
- **Exploit protection** is built into Windows 10/Server 2019 by default.

Recommendation: Keep default settings unless you know what you're doing.

---

## Task 7: Device Security
Provides information about security features available on the device.

- **Core isolation / Memory integrity** – Virtualization-based security feature.
- **TPM (Trusted Platform Module)** – Hardware chip that securely stores cryptographic information.

**Answer:**
- TPM stands for **Trusted Platform Module**

---

## Task 8: BitLocker
BitLocker is a drive encryption feature that protects data from theft or exposure.

- Works best with **TPM version 1.2+**.
- On systems without TPM, you must use a removable drive containing a **startup key**.

**Answer:**
- Removable drive must contain: **Startup key**

---

## Task 9: Volume Shadow Copy Service (VSS)
VSS allows creating **restore points** and **shadow copies** of files for backup and recovery.

You can:
- Create restore points
- Perform system restore
- Configure or delete restore points

Right-click a drive → **Configure Shadow Copies** to access settings.

**Answer:**
- VSS stands for **Volume Shadow Copy Service**

---

## Task 10: Conclusion
Windows Fundamentals 3 covered:
- Windows Update
- Windows Security (Virus & Threat Protection, Firewall, etc.)
- BitLocker
- Volume Shadow Copy Service

Further reading:
- Antimalware Scan Interface
- Credential Guard
- Windows Hello
- New Windows 10 security features

> Attackers often abuse built-in Windows tools in a technique called **Living Off the Land**. Understanding these tools helps defenders recognize and prevent such attacks.
