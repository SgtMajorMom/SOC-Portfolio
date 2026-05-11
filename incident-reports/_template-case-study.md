# Incident Case Study – [Title of Incident]

## 1. Summary
**Date:**  
**Analyst:**  
**Incident Type:** (Phishing, Malware, Suspicious Login, Account Compromise, etc.)  
**Severity:** Low / Medium / High  
**Status:** Closed / In Progress  

**Short Summary:**  
1–2 sentences describing what happened, how it was detected, and the outcome.

---

## 2. Detection & Trigger
**Source of Alert:**  
- SIEM alert name  
- Email security tool  
- User report  
- EDR detection  
- Cloud identity alert  

**Initial Indicators:**  
- Suspicious sender  
- Unusual login location  
- Malware hash  
- URL/domain  
- Endpoint behavior  

---

## 3. Timeline of Events
| Time (EST) | Event |
|------------|--------|
| 09:14 | Alert triggered in SIEM |
| 09:16 | Analyst began triage |
| 09:20 | User contacted for verification |
| 09:32 | Containment actions initiated |
| 10:05 | Incident resolved |

*(Adjust as needed — this table is recruiter gold.)*

---

## 4. Investigation Details

### 4.1 Evidence Collected
- Email headers  
- URLs  
- Attachment hash  
- Login logs  
- Endpoint alerts  
- User statements  

### 4.2 Analysis Performed
- Header analysis  
- URL sandboxing  
- Hash lookup (VirusTotal, internal intel)  
- Log correlation  
- MFA/identity review  
- EDR scan results  

### 4.3 Findings
- What was confirmed malicious  
- What was benign  
- What was suspicious but inconclusive  

---

## 5. Containment & Remediation

### 5.1 Actions Taken
- Blocked sender/domain  
- Forced password reset  
- Removed emails from mailboxes  
- Isolated endpoint  
- Ran AV/EDR scan  
- Disabled sessions/tokens  
- Updated blocklists  

### 5.2 Impact Assessment
- Users affected  
- Devices affected  
- Data exposure (if any)  
- Lateral movement (yes/no)  

---

## 6. Root Cause Analysis (RCA)
**What caused the incident?**  
- User clicked link  
- Credentials entered  
- Vulnerable endpoint  
- Misconfiguration  
- External threat actor  

**Why it succeeded or failed:**  
- Missing detection  
- User error  
- Lack of MFA  
- Outdated signatures  
- Successful security controls  

---

## 7. Lessons Learned
- What worked well  
- What needs improvement  
- What should be added to playbooks  
- What detections should be created or tuned  

---

## 8. Preventive Recommendations
- Add new SIEM detection  
- Improve email filtering  
- Update endpoint policies  
- Provide user training  
- Strengthen MFA enforcement  
- Patch/update systems  

---

## 9. Final Classification
**Final Verdict:**  
- False Positive  
- Spam  
- Phishing – Blocked  
- Phishing – User Compromised  
- Malware – Contained  
- Account Compromise  
- Policy Violation  
- Other  

**Incident Closed:** Yes / No  
