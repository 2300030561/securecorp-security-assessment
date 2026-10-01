# SecureCorp Security Assessment Engagement

**Junior Cybersecurity Consultant**

**Prepared by:** Pulugutha Saketh  
**Assessment:** Authorized Security Assessment  
**Date:** October 2026

---

## Slide 2 — Engagement Overview

### Objective

Assess the security posture of the authorized SecureCorp laboratory environment and demonstrate:

- Network and service assessment
- Web application security testing
- Authentication security testing
- Security evidence collection
- Security monitoring and investigation
- Risk identification and remediation planning

### Assessment Phases

1. Environment Setup
2. Red Team Assessment
3. Wazuh Investigation & Detection
4. Recommendations & Final Debrief

---

## Slide 3 — Lab Environment

### Assessment Architecture

**Attacker**
- WSL2 Ubuntu
- Security testing tools

**Target**
- Metasploitable2
- FTP and SSH services
- DVWA web application

**Monitoring**
- Wazuh Server
- Manager
- Indexer
- Dashboard

### Assessment Flow

`WSL2 Attacker → Metasploitable2 / DVWA → Logs → Wazuh`

---

## Slide 4 — Scope & Rules of Engagement

### In Scope

- Metasploitable2 target system
- DVWA web application
- FTP service
- SSH service
- Wazuh monitoring environment

### Rules

- Testing was performed only against authorized laboratory systems.
- Activities were conducted for cybersecurity assessment and learning purposes.
- Evidence was collected from controlled assessment activities.
- No external production systems were targeted.

---


---

## Slide 5 — Asset Inventory & Risk

| Asset | Role | Security Importance |
|---|---|---|
| Metasploitable2 | Vulnerable target | High |
| DVWA | Web application target | High |
| FTP | File transfer service | High |
| SSH | Remote administration | High |
| Wazuh | Security monitoring | Critical |

### CIA Considerations

- **Confidentiality:** Protect credentials and sensitive data
- **Integrity:** Prevent unauthorized modification
- **Availability:** Maintain service availability

---

## Slide 6 — Red Team Assessment

### Assessment Activities

- Network/service discovery
- DVWA brute-force testing
- SQL Injection
- Cross-Site Scripting (XSS)
- Command Injection
- FTP authentication testing
- SSH authentication testing

### Evidence Collected

Assessment evidence was stored in the project repository under:

`evidence/week2/`

---

## Slide 7 — Key Security Findings

### SQL Injection
- Database query manipulation demonstrated
- Potential unauthorized data access
- **Risk:** High

### Cross-Site Scripting
- Malicious script input demonstrated
- Potential client-side impact
- **Risk:** Moderate

### DVWA Brute Force
- Repeated authentication attempts demonstrated
- Indicates weak authentication protection
- **Risk:** High

### Command Injection
- OS command execution through application input demonstrated
- Potential system compromise
- **Risk:** Critical

---

## Slide 8 — Authentication & Network Findings

### FTP Authentication Testing

- Repeated authentication attempts were performed
- Demonstrates need for stronger authentication controls
- **Risk:** High

### SSH Authentication Testing

- Authentication failures were generated and investigated
- Strong passwords and additional access controls are recommended
- **Risk:** High

### Network Assessment

- Network/service discovery was part of the assessment methodology
- Nmap evidence should be retained when available
- No unsupported scan results are reported

---


---

## Slide 9 — Wazuh Detection & Investigation

### Detection Objective

Wazuh was planned as the centralized security monitoring platform for:

- Authentication events
- Web application activity
- Suspicious requests
- Repeated login failures
- Security alerts

### Investigation Questions

For each activity:

- What happened?
- When did it happen?
- Which system was affected?
- What was the source IP?
- Was it automatically detected or manually investigated?
- What evidence supports the finding?

**Wazuh investigation evidence: Pending completion of the monitoring environment.**

---

## Slide 10 — Incident Timeline

### Assessment Timeline

**Discovery**
→ Identify target services and attack surface

**Web Testing**
→ SQL Injection, XSS, Brute Force, Command Injection

**Authentication Testing**
→ FTP and SSH authentication testing

**Investigation**
→ Review available logs and Wazuh alerts

**Risk Assessment**
→ Evaluate impact and likelihood

**Remediation**
→ Recommend security controls

> Timeline timestamps and Wazuh alert evidence will be added after final investigation.

---

## Slide 11 — Security Recommendations

### Authentication
- Enforce strong password policies
- Implement MFA
- Apply account lockout/rate limiting
- Disable unnecessary accounts

### Web Application Security
- Use parameterized SQL queries
- Validate and sanitize input
- Implement output encoding
- Apply secure coding practices

### Network Security
- Restrict unnecessary services
- Apply firewall rules
- Limit administrative access
- Segment critical systems

### Monitoring
- Centralize security logs
- Monitor authentication failures
- Configure Wazuh detection rules
- Maintain incident timelines

---

## Slide 12 — Conclusion

### Key Takeaways

- Multiple security weaknesses were demonstrated in the authorized lab.
- Web application and authentication controls require strengthening.
- Security monitoring is essential for detecting repeated attack activity.
- Findings were documented with supporting evidence.
- Recommendations focus on reducing attack surface and improving detection.

### Final Deliverables

- Security Assessment Report
- Attack Evidence
- Detection & Investigation Evidence
- Security Recommendations
- Final Presentation

**Thank You**

