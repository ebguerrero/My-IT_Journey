# 07 — Cryptographic Solutions

## 🎯 Learning Objectives
- Define the difference between **symmetric** and **asymmetric** cryptography.  
- Explain hashing, digital signatures, and certificates.  
- Recognize common cryptographic protocols.  

---

## Task 1 – Symmetric Cryptography
- Uses a **single shared key** for both encryption and decryption.  
- Fast and efficient.  
- Challenge: securely sharing the key.  

**Examples:** AES (Advanced Encryption Standard), 3DES (Triple Data Encryption Standard).  

---

## Task 2 – Asymmetric Cryptography
- Uses **key pairs** (public + private).  
- Public key encrypts, private key decrypts (or vice versa for signatures).  
- Solves the **key distribution problem**.  

**Examples:** RSA, ECC (Elliptic Curve Cryptography).  

---

## Task 3 – Hashing & Digital Signatures
- **Hashing** → One-way transformation, ensures integrity (e.g., SHA-256).  
- **Digital Signature** → Combines hashing + asymmetric encryption to prove authenticity and integrity.  

---

## Task 4 – Certificates & PKI
- **PKI (Public Key Infrastructure)** manages issuance/revocation of certificates.  
- Certificates bind a public key to an identity.  
- Certificate Authorities (CAs) issue trusted certificates.  

---

## Task 5 – Cryptographic Protocols
- **TLS (Transport Layer Security)** → encrypts data in transit.  
- **IPSec (Internet Protocol Security)** → secures network traffic.  
- **PGP/GPG (Pretty Good Privacy/GNU Privacy Guard)** → email encryption.  

---

## 📝 Key Terms
- **Symmetric / Asymmetric Encryption**  
- **Hash Function**  
- **Digital Signature**  
- **PKI (Public Key Infrastructure)**  
- **TLS / IPSec / PGP**  

---

## 💡 Practice Prompts
- Explain the difference between **symmetric** and **asymmetric encryption**.  
- What does a **digital signature** provide?  
- Why is PKI important for trust online?  

