# 06 — Data Protection

## 🎯 Learning Objectives
- Explain methods for protecting data at rest, in transit, and in use.  
- Recognize different data classifications and handling policies.  
- Understand concepts like DLP, tokenization, and obfuscation.

---

## Task 1 – Data States
- **At rest** → stored on device/disk/database. Protect with full-disk or file-level encryption (BitLocker, AES).  
- **In transit** → moving across a network. Protect with TLS, VPN, IPSec.  
- **In use** → being processed in memory. Defenses: secure enclaves, OS controls.

---

## Task 2 – Data Classification
- Levels: **Public**, **Internal**, **Confidential**, **Restricted/Top Secret**.  
- Each level defines labeling, storage, transfer, destruction.  
- Policies driven by org rules and regulations (HIPAA, PCI-DSS).

---

## Task 3 – Data Loss Prevention (DLP)
- Monitors and restricts sensitive info leaving the org.  
- Types: **network-based**, **endpoint-based**, **cloud DLP**.  
- Prevents leaks via email, USB, uploads, screenshots.

---

## Task 4 – Data Obfuscation
- **Masking** → replace with lookalike values.  
- **Tokenization** → replace with tokens tied to secure vault.  
- **Anonymization** → permanently strip identifiers.  
- **Pseudonymization** → replace identifiers but allow re-ID with key.

---

## Key Terms
- Data at rest / transit / use  
- DLP  
- Masking, Tokenization, Anonymization  

---

## Practice Prompts
- What are the 3 states of data? Give one protection for each.  
- Compare tokenization vs anonymization.  
- Give 2 examples of DLP in action.
