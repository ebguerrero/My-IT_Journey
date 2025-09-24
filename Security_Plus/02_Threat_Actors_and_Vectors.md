# 02 — Threat Actors & Vectors

Who attacks, why they attack, and how they get in.

---

## 🎯 Learning Objectives
- Identify types of **threat actors** and their motivations.  
- Describe common **attack vectors** and what makes up an **attack surface**.  
- Understand deception defenses (honeypots, honeytokens).

---

## Task 1 — Threat Actor Types
- **Script kiddies** — low skill, reuse tools.  
- **Hacktivists** — ideology-driven.  
- **Organized crime** — financially motivated (ransomware, fraud).  
- **Nation-state / APT** — long-term espionage, high sophistication.  
- **Insiders** — negligent or malicious employees/contractors.

**Motivations**: money, espionage, disruption, ideology, personal grievance.

---

## Task 2 — Attack Vectors
- Email (phishing), web apps (XSS, SQLi), removable media, cloud misconfig, weak credentials, RDP/SMB, open ports, insecure Wi-Fi/Bluetooth, supply chain.
- **Fileless attacks** use legit processes (PowerShell, WMI).

---

## Task 3 — Attack Surface & Reduction
- **Attack surface** = all entry/interaction points (ports, services, accounts).  
- Reduce surface: disable unused services, patch, network segmentation, least privilege, inventory.

---

## Task 4 — Deception Techniques
- **Honeypots/honeynets**, **honeytokens** (fake credentials/files), decoy services.  
- Use for early detection & to study attacker TTPs.

---

## Key Terms
- TTP (Tactics, Techniques, Procedures), APT, phishing, watering hole, supply-chain attack, fileless

---

## Practice Prompts
- List 5 common attack vectors and one control to reduce each.  
- Explain the difference between an attack vector and the attack surface.  
- Name two deception tools and what they detect.

---

> Notes: condensed from Dion’s Security+ guide.
