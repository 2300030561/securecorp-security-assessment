# SecureCorp Security Assessment Engagement

**Role:** Junior Cybersecurity Consultant  
**Assessment Type:** Authorized Security Assessment  
**Organization:** SecureCorp  
**Prepared by:** Pulugutha Saketh  
**Date:** October 2026

---

## 1. Executive Summary

This report documents the security assessment performed for the SecureCorp lab environment as part of an authorized cybersecurity assessment engagement.

The assessment covered network and application security testing against the designated lab assets. Testing included web application security activities against DVWA, authentication-related testing against FTP and SSH services, and preparation for centralized security monitoring using Wazuh.

The assessment identified multiple security weaknesses in the intentionally vulnerable lab environment, including SQL Injection, Cross-Site Scripting (XSS), Brute Force exposure, Command Injection, and authentication-related weaknesses. Evidence was collected for the completed assessment activities and organized in the project repository.

The objective of the engagement was to demonstrate the identification of vulnerabilities, collection of security evidence, investigation of security events, and development of practical security recommendations.

Wazuh-based investigation and detection activities are documented separately as the monitoring component of the engagement and will be incorporated into the final investigation timeline and detection coverage sections when the required Wazuh evidence is available.

---


## 2. Scope & Rules of Engagement

### Scope

The assessment was conducted within the authorized SecureCorp cybersecurity lab environment. The assessment scope included:

- WSL2 Ubuntu attacker environment
- Metasploitable2 target system
- DVWA vulnerable web application
- FTP and SSH services exposed by the target
- Wazuh security monitoring environment

### Rules of Engagement

- Testing was performed only against authorized lab systems.
- The activities were conducted for cybersecurity assessment and learning purposes.
- Vulnerability testing was limited to the defined assessment environment.
- Evidence was collected from the assessment activities and stored in the project repository.
- No unauthorized external systems or production environments were targeted.

---


## 3. Asset Inventory & CIA Analysis

| Asset | Purpose | CIA Consideration |
|---|---|---|
| WSL2 Ubuntu | Attacker/testing environment | Integrity of testing tools and evidence |
| Metasploitable2 | Vulnerable target system | Confidentiality, Integrity, Availability |
| DVWA | Web application security testing | Confidentiality and Integrity |
| FTP Service | File transfer service under assessment | Confidentiality and Integrity |
| SSH Service | Remote administration service under assessment | Confidentiality and Integrity |
| Wazuh Server | Security monitoring and log analysis | Confidentiality, Integrity and Availability |

### CIA Analysis

**Confidentiality:**  
Unauthorized access to services or applications could expose sensitive information.

**Integrity:**  
Successful attacks such as SQL Injection or Command Injection could allow unauthorized modification or manipulation of application or system data.

**Availability:**  
Brute-force activity and exploitation of vulnerable services could affect service availability if performed at scale.

The assets above were assessed within the authorized laboratory environment.

---


## 4. Risk Assessment

The risk assessment considers the observed security weaknesses, their potential impact, and the affected services within the authorized lab environment.

| Finding | Affected Asset | Potential Impact | Risk Rating |
|---|---|---|---|
| SQL Injection | DVWA | Unauthorized database access or data manipulation | High |
| Cross-Site Scripting (XSS) | DVWA | Execution of malicious client-side script | Moderate |
| Brute Force | DVWA | Unauthorized account access | High |
| Command Injection | DVWA | Unauthorized operating-system command execution | Critical |
| FTP Authentication Weakness | Metasploitable2 FTP | Unauthorized access to FTP service | High |
| SSH Authentication Weakness | Metasploitable2 SSH | Unauthorized remote access | High |

### Risk Assessment Notes

The ratings reflect the potential security impact demonstrated by the authorized laboratory tests. They are intended to prioritize remediation activities within the assessment environment.

The assessment does not imply that these vulnerabilities exist in any production environment outside the defined lab scope.

---


## 5. Methodology

The security assessment followed a structured methodology covering environment validation, reconnaissance, vulnerability testing, evidence collection, security monitoring, and reporting.

### 5.1 Environment Validation

The authorized laboratory environment was prepared using WSL2 Ubuntu, Metasploitable2, DVWA, and the Wazuh monitoring platform.

### 5.2 Discovery

Network and service discovery activities were planned to identify reachable hosts, exposed services, and potential attack surfaces.

### 5.3 Web Application Testing

DVWA was used to perform controlled security testing against common web application vulnerabilities, including:

- SQL Injection
- Cross-Site Scripting (XSS)
- Brute Force
- Command Injection

### 5.4 Authentication Testing

Controlled authentication testing was performed against the FTP and SSH services available on the target system.

### 5.5 Evidence Collection

Command output and assessment results were captured as evidence files. The evidence was organized in the project repository according to the assessment phase.

### 5.6 Security Monitoring

Wazuh was designated as the centralized security monitoring platform for log collection, alert investigation, and detection analysis. Wazuh investigation results will be documented separately based on the available monitoring evidence.

### 5.7 Reporting

The final assessment report consolidates the scope, assets, risks, attack findings, detection coverage, recommendations, and supporting evidence.

---


## 6. Attack Simulation Findings

### 6.1 SQL Injection

**Attack ID:** T2.4  
**Target:** DVWA  
**Affected Service:** DVWA Web Application  
**Evidence:** `evidence/week2/week2-dvwa-sqli.txt`  
**Attack Demonstrated:** SQL Injection testing was successfully performed against the intentionally vulnerable DVWA application.  
**Impact:** A vulnerable SQL query may allow an attacker to manipulate database queries and potentially access or modify unauthorized information.  
**Risk Rating:** High  
**Detection:** Wazuh detection status is pending documented Week 3 evidence.  
**Recommendation:** Use parameterized queries/prepared statements, validate and sanitize input, apply least-privilege database accounts, and monitor application logs for suspicious SQL payloads.

---


### 6.2 Cross-Site Scripting (XSS)

**Attack ID:** T2.5  
**Target:** DVWA  
**Affected Service:** DVWA Web Application  
**Evidence:** `evidence/week2/week2-dvwa-xss.txt`  
**Attack Demonstrated:** Cross-Site Scripting testing was successfully performed against the intentionally vulnerable DVWA application.  
**Impact:** A successful XSS attack can allow malicious client-side scripts to execute in a victim's browser and may affect session security or application trust.  
**Risk Rating:** Moderate  
**Detection:** Wazuh detection status is pending documented Week 3 evidence.  
**Recommendation:** Apply context-aware output encoding, validate user input, use appropriate Content Security Policy controls, and monitor web application logs for suspicious script payloads.

---


### 6.3 DVWA Brute Force

**Attack ID:** T2.3  
**Target:** DVWA  
**Affected Service:** DVWA Authentication  
**Evidence:** `evidence/week2/week2-dvwa-bruteforce.txt`  
**Attack Demonstrated:** Controlled repeated authentication attempts were performed against the DVWA login functionality.  
**Impact:** Weak authentication controls can allow repeated password guessing and increase the possibility of unauthorized account access.  
**Risk Rating:** High  
**Detection:** Wazuh detection status is pending documented Week 3 evidence.  
**Recommendation:** Implement account lockout or rate limiting, enforce strong password policies, use MFA where appropriate, and monitor repeated authentication failures.

---


### 6.4 Command Injection

**Attack ID:** T2.6  
**Target:** DVWA  
**Affected Service:** DVWA Web Application  
**Evidence:** `evidence/week2/week2-dvwa-command-injection.txt`  
**Attack Demonstrated:** Controlled command-injection testing was performed against the intentionally vulnerable DVWA application.  
**Impact:** Successful command injection can allow unauthorized operating-system commands to be executed with the privileges of the vulnerable application.  
**Risk Rating:** Critical  
**Detection:** Wazuh detection status is pending documented Week 3 evidence.  
**Recommendation:** Avoid direct execution of user-controlled input, use strict allowlists and input validation, apply least privilege, and monitor application and system logs for suspicious command activity.

---


### 6.5 FTP Authentication Testing

**Attack ID:** T2.7
**Target:** Metasploitable2
**Affected Service:** FTP
**Evidence:** `evidence/week2/week2-ftp-hydra.txt`
**Attack Demonstrated:** Controlled authentication testing was performed against the FTP service in the authorized lab environment.
**Impact:** Weak FTP authentication controls may allow unauthorized access to the file-transfer service and potentially expose or modify accessible files.
**Risk Rating:** High
**Detection:** Wazuh detection status is pending documented Week 3 evidence.
**Recommendation:** Disable unnecessary FTP services, prefer secure file-transfer protocols, enforce strong passwords and rate limiting, and monitor repeated authentication failures.

---

### 6.6 SSH Authentication Testing

**Attack ID:** T2.8
**Target:** Metasploitable2
**Affected Service:** SSH
**Evidence:** `evidence/week2/week2-ssh-auth-evidence.txt`
**Attack Demonstrated:** Controlled authentication testing was performed against the SSH service in the authorized lab environment.
**Impact:** Weak SSH authentication controls may allow unauthorized remote access to the target system.
**Risk Rating:** High
**Detection:** Wazuh detection status is pending documented Week 3 evidence.
**Recommendation:** Enforce strong authentication, disable unnecessary accounts, use key-based authentication where appropriate, apply rate limiting, and monitor repeated SSH authentication failures.

---

## 7. Detection Coverage, Investigation Notes & Incident Timeline

### 7.1 Detection Coverage

| Assessment Activity | Expected Log Source | Detection Status |
|---|---|---|
| DVWA Brute Force | Apache/DVWA authentication logs | Pending Wazuh evidence |
| SQL Injection | Apache/DVWA web logs | Pending Wazuh evidence |
| XSS | Apache/DVWA web logs | Pending Wazuh evidence |
| Command Injection | Apache/DVWA web logs and system logs | Pending Wazuh evidence |
| FTP Brute Force | FTP/vsftpd logs | Pending Wazuh evidence |
| SSH Brute Force | SSH authentication logs | Pending Wazuh evidence |
| Network Scanning | Network/security logs | Pending Wazuh evidence |

### 7.2 Investigation Notes

The Week 2 attack activities provide the baseline events that should be correlated with Wazuh monitoring data during the investigation phase.

For each activity, the investigation should identify:

- What happened
- When the activity occurred
- Affected system and service
- Source IP address
- Targeted account or application
- Relevant log source
- Wazuh rule or alert, when available
- Whether the activity was automatically detected or manually identified
- Potential impact
- Recommended response

At the time of report preparation, Wazuh-specific evidence for these activities had not been fully documented. Therefore, no Wazuh alert IDs, rule levels, timestamps, or detection results are claimed without supporting evidence.

### 7.3 Incident Timeline

A complete incident timeline will be added after the Wazuh investigation evidence is collected and correlated with the Week 2 assessment activity timestamps.

---


## 8. Security Recommendations

The following recommendations are based on the vulnerabilities demonstrated during the authorized assessment.

### 8.1 Web Application Security

- Use parameterized queries and prepared statements to prevent SQL Injection.
- Validate and sanitize all user-controlled input.
- Apply context-aware output encoding to prevent XSS.
- Avoid passing untrusted input directly to operating-system commands.
- Implement secure error handling without exposing sensitive system information.

### 8.2 Authentication Security

- Enforce strong and unique passwords.
- Implement account lockout or rate limiting for repeated authentication failures.
- Enable Multi-Factor Authentication (MFA) where supported.
- Monitor authentication failures and suspicious login patterns.
- Disable unused accounts and unnecessary authentication services.

### 8.3 Network & Service Security

- Disable unnecessary services and exposed ports.
- Restrict administrative services using firewall rules and network segmentation.
- Prefer secure protocols over legacy or unencrypted services.
- Regularly patch operating systems and network-facing applications.

### 8.4 Logging & Monitoring

- Centralize security-relevant logs using a security monitoring platform such as Wazuh.
- Configure alerts for repeated authentication failures and suspicious web activity.
- Maintain accurate timestamps to support incident investigation.
- Regularly review alerts and investigate anomalous activity.

### 8.5 Backup & Recovery

- Maintain regular backups of critical data.
- Store backups separately from production systems.
- Periodically test backup restoration procedures.
- Protect backups using appropriate access controls.

### 8.6 Security Awareness

- Provide security awareness training to users and administrators.
- Educate users about password security and phishing risks.
- Establish procedures for reporting suspected security incidents.

---


## 9. Incident Report & Conclusion

### 9.1 Incident Summary

The assessment demonstrated multiple security weaknesses within the authorized SecureCorp laboratory environment. The observed activities included web application attacks against DVWA and authentication testing against FTP and SSH services on the target system.

The findings demonstrate how weak input validation, insecure authentication controls, and exposed services can increase the risk of unauthorized access or command execution.

### 9.2 Evidence Status

Evidence for the completed Week 2 activities has been preserved in the project repository under `evidence/week2/`.

The Wazuh investigation component remains dependent on obtaining and documenting the corresponding Wazuh agent, alert, log-search, and timeline evidence. No unsupported Wazuh detection claims are included in this report.

### 9.3 Conclusion

The assessment successfully demonstrated controlled security testing against the authorized laboratory environment. The identified weaknesses provide clear remediation opportunities involving secure coding, authentication hardening, service reduction, network controls, centralized logging, monitoring, and regular security maintenance.

The final assessment package should include the supporting evidence, Wazuh investigation screenshots, incident timeline, final recommendations, and presentation materials.

---


## 10. Appendices

### Appendix A – Week 2 Evidence

The following evidence files document the completed Week 2 assessment activities:

- `evidence/week2/week2-dvwa-bruteforce.txt`
- `evidence/week2/week2-dvwa-command-injection.txt`
- `evidence/week2/week2-dvwa-sqli.txt`
- `evidence/week2/week2-dvwa-xss.txt`
- `evidence/week2/week2-ftp-hydra.txt`
- `evidence/week2/week2-ssh-auth-evidence.txt`

### Appendix B – Wazuh Evidence

The following Week 3 evidence is required for the final submission:

- DVWA brute-force Wazuh evidence
- SQL Injection Wazuh evidence
- XSS Wazuh evidence
- Command Injection Wazuh evidence
- FTP authentication Wazuh evidence
- SSH authentication Wazuh evidence
- Incident timeline
- Wazuh dashboard showing the enrolled agent as Active

These items should be added after the Wazuh investigation is completed.

### Appendix C – Missing or Pending Evidence

The following items were not available at the time of report preparation:

- Original Nmap scan evidence
- Wazuh detection screenshots
- Wazuh incident timeline
- Wazuh agent Active screenshot

These items are explicitly marked as pending rather than being fabricated.

---

## 11. Evidence and Submission Checklist

- [x] Cover Page
- [x] Executive Summary
- [x] Scope & Rules of Engagement
- [x] Asset Inventory & CIA Analysis
- [x] Risk Assessment
- [x] Methodology
- [x] Week 2 Attack Simulation Findings
- [ ] Wazuh Detection Coverage
- [ ] Investigation Notes with Wazuh Evidence
- [ ] Incident Timeline
- [x] Security Recommendations
- [x] Conclusion
- [x] Evidence Index
- [ ] Final Presentation
- [ ] Final PDF export

