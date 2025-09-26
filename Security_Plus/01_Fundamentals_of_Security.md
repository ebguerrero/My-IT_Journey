# 01 — Fundamentals of Security

## 🎯 Learning Objectives
- Explain the **CIA Triad** (Confidentiality, Integrity, Availability).  
- Define and apply **AAA** (Authentication, Authorization, Accounting).  
- Compare security **control categories** (technical, managerial, operational, physical).  
- Distinguish security **control types** (preventive, detective, corrective, etc.).  
- Describe **non-repudiation**, **Zero Trust**, and the relationship between **threats, vulnerabilities, and risks**.

---

## Task 1 – Core Concepts
- **Information Security** → protecting data from unauthorized access, modification, destruction, or disclosure.  
- **CIA Triad**:  
  - **Confidentiality** → Ensures data is only seen by those authorized. Example: encryption.  
  - **Integrity** → Ensures information is accurate and unchanged. Example: hashing or digital signatures.  
  - **Availability** → Ensures systems and data are accessible when needed. Example: redundancy or failover.  

- **AAA Framework**:  
  - **Authentication** → Verifying identity (passwords, biometrics, tokens).  
  - **Authorization** → Determining what resources a user can access.  
  - **Accounting** → Tracking and logging user activity.  

- **Non-repudiation** → A user cannot deny actions they performed, supported by mechanisms like **digital signatures** or transaction logs.  

---

## Task 2 – Security Controls
- **Categories** (based on where they apply):  
  - **Technical controls** → software/hardware (firewalls, antivirus, access controls).  
  - **Managerial controls** → policy, standards, risk assessments.  
  - **Operational controls** → training, awareness, incident response processes.  
  - **Physical controls** → locks, fences, cameras, guards.  

- **Types** (based on their purpose):  
  - **Preventive** → stop incidents (firewalls, access restrictions).  
  - **Deterrent** → discourage attackers (warning signs, visible guards).  
  - **Detective** → identify events (intrusion detection systems, logs).  
  - **Corrective** → fix issues (patches, backup restoration).  
  - **Compensating** → backup safeguards when primary controls aren’t possible.  
  - **Directive** → enforce behavior (policies, posted procedures).  

---

## Task 3 – Risk Model
- **Threat** → something that could cause harm (actor, event, hazard).  
- **Vulnerability** → weakness in a system or process.  
- **Risk** → the probability of a threat exploiting a vulnerability.  
  - Example: Weak password (vulnerability) + phishing email (threat) = risk of account compromise.  
  - If either threat or vulnerability is missing, risk is nearly zero.  

---

## Task 4 – Zero Trust
- **Principle**: “Never trust, always verify.” Every user, device, and transaction is continuously validated.  
- **Control Plane** → defines and enforces policies (identity verification, access rules).  
- **Data Plane** → systems/users where data is processed and accessed.  

---

## 📝 Key Terms
- **CIA Triad**  
- **AAA (Authentication, Authorization, Accounting)**  
- **Non-repudiation**  
- **Zero Trust**  
- **Threat vs Vulnerability vs Risk**  

---

## 💡 Practice Prompts
- Give an example of a **technical control** and a **managerial control**.  
- Define **integrity** and explain two ways to ensure it.  
- Explain why a risk cannot exist without both a **threat** and a **vulnerability**.  

