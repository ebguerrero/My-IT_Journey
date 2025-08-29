# Defensive Security Intro (TryHackMe)

## What is Defensive Security?
- Focus: **prevent intrusions** and **detect/respond** to attacks.
- Blue Teams = defensive side of cyber security.
- Typical tasks include:
  - User training and awareness.
  - Documenting/managing assets.
  - Updating and patching systems.
  - Using preventative devices (firewalls, IPS).
  - Logging and monitoring devices.

## Key Areas of Defensive Security
- **Security Operations Center (SOC)**  
  - Team of professionals monitoring networks/systems for malicious events.  
  - Handles vulnerabilities, policy violations, unauthorized access attempts, and intrusions.  
  - Ensures detection + prevention to reduce damage.  

- **Threat Intelligence**  
  - Information gathering about adversaries and threats.  
  - Goal: achieve **threat-informed defense**.  
  - Examples: ransomware groups, nation-state cyber actors, corporate espionage.  

- **Digital Forensics & Incident Response (DFIR)**  
  - **Digital Forensics**: analyze digital evidence from logs, files, memory, storage.  
  - **Incident Response**: steps to respond to attacks:  
    1. Preparation  
    2. Detection & Analysis  
    3. Containment, Eradication, and Recovery  
    4. Post-Incident Activity (lessons learned).  

- **Malware Analysis**  
  - Study malware behavior to understand impact and defenses.  
  - Types of malware:  
    - Virus → attaches to a program.  
    - Trojan Horse → hides malicious code.  
    - Ransomware → encrypts data and demands payment.  
  - Methods:  
    - **Static Analysis**: inspect code without running.  
    - **Dynamic Analysis**: run in sandbox and observe behavior.  

## Practical Example: SIEM (Security Information & Event Management)
- SOC analysts use SIEM dashboards to aggregate logs and alerts.  
- Analysts investigate alerts to separate real threats from noise.  
- Example scenario:  
  - Multiple failed login attempts from one user.  
  - Suspicious login from new location at odd hours.  
  - Malicious IP flagged in SIEM.  
- Simulation flag result: THM{THREAT-BLOCKED}

- ## Key Takeaways
- Defensive security = monitoring, prevention, and response.  
- Blue Teams protect systems using SOC, DFIR, Threat Intel, Malware Analysis, and SIEM.  
- Complements Offensive Security by fixing and guarding against weaknesses.
