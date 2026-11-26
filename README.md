Penetration Testing Report — Portfolio Sample (Redacted)

Black-Box Web Application Pentest

This is a redacted portfolio sample of a supervised cybersecurity training exercise conducted in a controlled lab environment with written authorisation. Client identity, personal data, real filenames, and exact figures have been removed or replaced with placeholders. The methodology, findings structure, and risk-rating approach are preserved to demonstrate process and reporting ability.

Prepared by: Uchechukwu Favour Chinenye

Engagement: Cybersecurity Internship Training Exercise

Target: [Redacted — training lab environment]

Engagement Type: Black-Box Penetration Test

Duration: 5 Days

Executive Summary
   
This report documents a black-box penetration test carried out against a healthcare provider's web infrastructure (client name redacted), conducted under written client authorisation as part of a structured cybersecurity training exercise. The objective was to identify vulnerabilities, demonstrate real-world impact through controlled exploitation, and report findings with actionable remediation guidance.
During the engagement, three confidential patient pathology lab reports were retrieved from the target application. 

Two of these PDF files were protected with weak, dictionary-crackable passwords, which were recovered using a basic dictionary attack against the extracted PDF password hashes. Further analysis of the retrieved material led to the discovery of an additional, more severe exposure: an unprotected database backup file containing the client's complete shareholder register and full staff salary records for 30 employees.

Taken together, these findings represent a serious breach of confidentiality, affecting patient health information (regulated personal data), financial remuneration data, and corporate ownership information. The overall risk to the client is rated Critical. Immediate remediation is recommended before this system is exposed to production traffic or real patient data.

 Scope and Methodology
 
2.1 Scope

Target: [Redacted] — client healthcare provider web application

Type: Full black-box penetration test

Scope restriction: testing limited strictly to the target domain

Out of scope: social engineering, denial-of-service testing, testing outside the agreed target

Authorisation: written authorisation provided by the client to conduct security testing on their web infrastructure

2.2 Methodology

Testing followed a staged approach consistent with standard black-box methodology:

Reconnaissance — passive and active information gathering against the target to identify exposed entry points and application behaviour.

Initial Access — analysis of authentication mechanisms and input handling to identify and exploit a weakness granting unauthorised access to a restricted area of the site, resulting in retrieval of three confidential patient PDF lab reports.

Data Extraction — analysis of the protection mechanism on each retrieved file and selection of appropriate cracking tools and wordlists to recover file contents.

Further Exposure Discovery — inspection of file properties and content of all retrieved material, which revealed a path to an additional, undisclosed data exposure on the server.

Reporting — documentation of all findings with evidence, risk ratings, and remediation recommendations.

2.3 Tools Used

Kali Linux (VirtualBox VM) as the testing environment
Firefox for target reconnaissance and file retrieval
networkwalks.com/hash-calculator/ ($pdf$...) extraction tooling
networkwalks.com/password-cracker
Dictionary-based password cracking (built-in and custom wordlists)
Manual inspection of PDF metadata and document properties

2.4 Limitations

Testing was conducted independently within a 5-day window against a designated target only. No denial-of-service or social-engineering techniques were used. Findings reflect the state of the application and exposed files at the time of testing.

 Findings and Proof of Exploitation
   
3.1 Unauthorised Access to Confidential Patient Records

Risk Rating: 🔴 Critical

A weakness in the application's access control and/or authentication handling allowed unauthorised retrieval of three confidential patient pathology laboratory reports (filenames redacted), each containing full patient names, dates of birth, patient IDs, referring physicians, and detailed clinical test results.

Evidence
Report 1 — Patient: [Redacted], lab panel included multiple results flagged LOW.
Report 2 — Patient: [Redacted], lab panel included multiple results flagged HIGH.
Report 3 — Patient: [Redacted], lab panel included results flagged HIGH.

All three reports are marked "CONFIDENTIAL" by the client itself, confirming the sensitivity of the exposed data.
Impact
Direct breach of patient confidentiality and healthcare data protection obligations.
Exposure of special-category personal health information for three identifiable individuals.
Potential regulatory and reputational consequences for the client under applicable data protection law.

3.2 Weak Password Protection on Confidential PDFs

Risk Rating: 🔴 Critical
The retrieved PDF files were protected using PDF standard encryption (R3 / 128-bit RC4) with weak, easily guessable passwords. PDF password hashes were extracted in $pdf$ hash format and successfully cracked using a basic 100-entry dictionary wordlist in under a few seconds of compute time.

Evidence
Report 3 — password recovered as a short symbol-based pattern via a custom wordlist (value redacted).
Report 2 — password recovered as a common dictionary word using the built-in 100-entry wordlist, matched on attempt 2 of 100 (value redacted).

Cracking speed and attempt count (1–2 guesses out of 100) demonstrate the passwords offered negligible real-world protection.
Impact
Encryption provides a false sense of security when paired with weak, common passwords.
Any attacker with basic tooling (no specialised skill required) can recover the plaintext contents.
Compounds the impact of Finding 3.1 by defeating the one control that was in place.

3.3 Exposure of Shareholder and Staff Salary Database

Risk Rating: 🔴 Critical
Further inspection of the retrieved material and file properties revealed a path to an additional file on the server (filename redacted): an unprotected database backup export containing two highly sensitive data tables — the client's full shareholder register and complete staff salary records.

Evidence
Shareholders' Information table: 10 named shareholders (including individuals and a corporate/trust entity), with shareholding percentages and share class — see Table 1 (sample, anonymised).

Staff Information table: 30 employees with name, job title, department, and monthly salary — sample in Table 2 (anonymised, figures illustrative).

The source file itself carries a confidentiality note stating it should be "handled and shared only with authorised recipients" — confirming it was not intended for public or unauthenticated access.

Impact

Exposure of individual compensation data breaches employee privacy and could enable targeted social engineering or pay-equity disputes.
Exposure of shareholder identities and holdings is commercially sensitive and could affect corporate governance, M&A positioning, or personal safety of named individuals.
Indicates a systemic issue: sensitive backups are reachable through the same access path as the original vulnerability, suggesting inadequate segmentation between application data and administrative/backup data.

Table 1 — Shareholders' Information (structure preserved, names anonymised)

Shareholder
Share %
Share Class
Shareholder A
18%
Ordinary
Shareholder B (corporate entity)
15%
Ordinary
Shareholder C
12%
Ordinary
Shareholder D (family trust)
11%
Ordinary
Shareholder E
10%
Ordinary
Shareholder F
9%
Ordinary
Shareholder G
8%
Preferential
Shareholder H
7%
Ordinary
Shareholder I
6%
Ordinary
Shareholder J
4%

Preferential
Table 2 — Staff Salary Information (sample structure, names and figures redacted)

Role (anonymised)
Job Title
Department
Monthly Salary
Employee 1
Medical Director
Management
[Redacted]
Employee 2
Chief Financial Officer
Finance
[Redacted]
Employee 3
Chief Pathologist
Diagnostics Lab
[Redacted]
Employee 4
Anaesthetist
Theatre
[Redacted]
Employee 5
Consultant Cardiologist
Cardiology
[Redacted]
Employee 6
Consultant Radiologist
Radiology
[Redacted]
Employee 7
Consultant Physician
Internal Medicine
[Redacted]

(27 further employees)

Employee 30
Receptionist
Front Office
[Redacted]


 Risk Rating Summary

Finding:Risk Rating
1 Broken access control exposing confidential patient pathology reports (3 PDFs retrieved without authorisation)
🔴 Critical
2 Weak / dictionary-crackable password protection on confidential PDF attachments
🔴 Critical
3 Full staff salary register exposed (30 employees, names, roles, departments, pay)
🟠 High
4 Shareholder register exposed (10 shareholders, names, shareholding %, share class)
🟠 High
5 Sensitive data stored in an unencrypted, improperly access-controlled backup file (filename redacted) reachable from the same exposure path
🔴 Critical
Overall engagement risk to the client: CRITICAL

 Recommendations and Remediation

5.1 Access Control

Implement and enforce proper authentication and authorisation checks on all endpoints that serve patient records; ensure restricted areas cannot be reached without valid, verified credentials.
Apply the principle of least privilege — no single access path should expose both patient records and unrelated administrative/financial backups.

5.2 Document and File Security

Discontinue password-protecting sensitive files with weak, dictionary-guessable passwords; where PDF encryption is used, enforce strong, randomly generated, per-document passwords (minimum 12+ characters, no dictionary words).
Prefer transport- and storage-level encryption plus access-controlled delivery over relying on PDF password protection alone.

5.3 Backup and Data Handling

Remove publicly or improperly accessible database backup exports from any web-reachable location immediately.
Store backups in access-controlled, encrypted storage separate from the web application, with logging and alerting on access.
Classify and label sensitive exports (PII, salary, shareholder data) and apply handling controls consistent with that classification before any export is generated.

5.4 Organisational Controls

Conduct a data protection impact assessment given the exposure of patient health data.
Rotate any credentials or secrets that may have been exposed alongside this data.
Provide staff awareness training on secure handling and sharing of confidential exports.
Schedule a follow-up retest once remediations are implemented to confirm the issues are resolved.

Conclusion

This engagement identified critical, chained vulnerabilities in the client's web application and data handling practices: broken access control enabling retrieval of confidential patient records, weak password protection that was trivially defeated, and a serious collateral exposure of corporate shareholder and staff salary data. These findings should be treated as high priority. Addressing the access control weakness and removing the exposed backup file are the most urgent remediation steps.
This is a redacted portfolio sample of a project conducted in a controlled training environment for educational purposes only, under explicit written authorisation from the target owner. Client identity, personal data, and exact figures have been removed. These techniques must never be applied to any system without explicit written permission from its owner.
