# 06 — Data Protection

## 🎯 Learning Objectives
- Explain methods of protecting sensitive data (encryption, masking, tokenization).  
- Compare data classifications and handling requirements.  
- Describe data retention and destruction practices.  
- Recognize privacy regulations and best practices.  

---

## Task 1 – Data Classification
- **Public** → No risk if disclosed (e.g., press releases).  
- **Internal/Private** → Limited distribution, may harm business if leaked.  
- **Confidential** → Requires strong protections, includes trade secrets.  
- **Restricted/Highly Sensitive** → Maximum protection; disclosure could cause severe harm (e.g., patient records).  

**Tip:** Organizations often define **labeling systems** (confidential stamps, access restrictions).  

---

## Task 2 – Data Protection Techniques
- **Encryption** → Protects confidentiality; data unreadable without key.  
- **Hashing** → Ensures integrity; outputs a unique fixed value.  
- **Masking** → Hides sensitive portions (e.g., showing only last 4 digits of a credit card).  
- **Tokenization** → Replaces sensitive data with random “tokens” that map to originals in a secure database.  

---

## Task 3 – Data Handling
- **Data in transit** → Protect with TLS (Transport Layer Security).  
- **Data at rest** → Encrypt on disks/servers.  
- **Data in use** → Protect memory/processes against side-channel attacks.  

---

## Task 4 – Data Retention & Disposal
- **Retention policies** → Define how long to keep records.  
- **Secure destruction**:  
  - **Wiping/Overwriting** → Rewriting data to prevent recovery.  
  - **Degaussing** → Removing magnetic fields from drives.  
  - **Physical destruction** → Shredding, pulverizing media.  

---

## Task 5 – Privacy & Regulations
- **GDPR (General Data Protection Regulation)** → European law protecting personal data.  
- **CCPA (California Consumer Privacy Act)** → Grants California residents rights over their data.  
- **HIPAA (Health Insurance Portability and Accountability Act)** → U.S. regulation for healthcare data.  

---

## 📝 Key Terms
- **Data Masking**  
- **Tokenization**  
- **Data Retention Policy**  
- **GDPR / CCPA / HIPAA**  

---

## 💡 Practice Prompts
- Compare **masking** and **tokenization**.  
- What are three methods to securely destroy sensitive data?  
- Explain the purpose of a **data retention policy**.  

