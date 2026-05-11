# Phishing Investigation Playbook

## 1. Trigger

**Common triggers:**
- User reports a suspicious email
- SIEM alert for phishing indicators (URL, attachment, sender domain)
- Email security tool flags a message (e.g., Proofpoint, Defender, etc.)

---

## 2. Initial Triage

**Goals:** Quickly assess risk and decide whether to escalate.

**Steps:**
1. **Collect basic details:**
   - Reporter name and department
   - Time email was received
   - Email subject and sender
   - Whether any links were clicked or attachments opened

2. **Preserve evidence:**
   - Instruct user **not to delete** the email
   - Ask user to **forward as attachment** to security mailbox (if available)
   - Capture screenshots if needed

3. **Classify urgency:**
   - High: Credentials entered, malware executed, sensitive data exposed
   - Medium: Links clicked but no creds entered / unknown behavior
   - Low: Obvious spam, no interaction

---

## 3. Email Header & Content Analysis

**Header checks:**
- Compare **From** vs **Return-Path** vs **Reply-To**
- Check **SPF/DKIM/DMARC** results
- Look for mismatched domains or suspicious sending IPs
- Check sending IP/domain reputation (internal tools or public intel)

**Body/content checks:**
- Urgency, threats, or pressure (“immediate action required”)
- Requests for credentials, payments, gift cards, or sensitive data
- Poor grammar, odd phrasing, or unusual tone
- Display name spoofing (e.g., “CEO” but external address)

---

## 4. URL and Attachment Analysis

**URLs:**
- Hover over links and compare to displayed text
- Check for:
  - Typosquatting (e.g., `micr0soft.com`, `paypa1.com`)
  - URL shorteners
  - Non‑corporate login pages
- Use a safe analysis method:
  - Open in **isolated environment** or
  - Use URL analysis tools (sandbox, threat intel, etc.)

**Attachments:**
- Identify type: `.html`, `.pdf`, `.docx`, `.xlsm`, `.zip`, `.exe`, etc.
- For risky types (macros, executables, archives):
  - Analyze in sandbox if available
  - Do **not** open directly on production workstation

---

## 5. User Impact Assessment

**Questions to ask the user:**
- Did you click any links?
- Did you enter your username/password or other data?
- Did you open or download any attachments?
- Did anything unusual happen (pop‑ups, prompts, errors)?

**If credentials were entered:**
- Mark as **potential account compromise**
- Proceed to **containment** steps

---

## 6. Containment & Response

**If no interaction:**
- Block sender/domain in email security tool
- Search for and remove similar emails from other mailboxes (if tools allow)
- Mark case as **blocked / prevented**

**If user interacted (clicked or entered creds):**
1. **Account actions:**
   - Force password reset
   - Invalidate active sessions
   - Review recent login activity (locations, IPs, devices)
2. **Endpoint actions (if attachment executed):**
   - Run AV/EDR scan
   - Isolate endpoint if suspicious behavior is detected
3. **Email actions:**
   - Remove similar messages from other users’ inboxes
   - Block sender, domain, and URLs

---

## 7. Environment‑Wide Search

**Goals:** Identify spread and additional victims.

**Search for:**
- Same subject line or sender across mailboxes
- Same URLs or domains in email logs
- Same attachment hash in file/EDR logs
- Related alerts in SIEM (logins, MFA failures, unusual access)

---

## 8. Documentation

For each phishing incident, record:

- Date/time reported
- Reporter and department
- Email details (sender, subject, indicators)
- User interaction (clicked, entered creds, opened attachment)
- Analysis summary (headers, URLs, attachments)
- Containment steps taken
- Accounts/devices affected
- Final classification:
  - **Benign / False Positive**
  - **Spam**
  - **Phishing – Blocked**
  - **Phishing – User Compromised**
- Lessons learned / improvements

---

## 9. User Communication & Awareness

**If malicious:**
- Notify affected user(s) with:
  - What happened (high level)
  - What actions were taken
  - What they should watch for (suspicious logins, MFA prompts, etc.)

**Optional:**
- Use anonymized example in security awareness training
- Update internal guidance on reporting suspicious emails

---

## 10. Continuous Improvement

After closing the case:

- Add new indicators (domains, URLs, hashes) to blocklists
- Update this playbook if new patterns or gaps were identified
- Consider new detections in SIEM or email security tools
