Penetration Testing Report – Healthcare Web Application

Black-Box Web Application Penetration Testing | Portfolio Project

Details 

Full Name:Uchechukwu Favour Chinenye 

Internship Academy:Networkwalks.com Academy(https://networkwalks.com/) 

Instructor:Mr Waqas Karim CCIE 

Batch:BO84D 

Project Type:Cybersecurity Internship Training

Engagement Duration:5 Days 

Testing Approach:Black-Box Penetration Testing

1. Project Overview

This project documents a supervised black-box penetration testing exercise conducted in a controlled laboratory environment with written authorization.

The assessment focused on identifying security vulnerabilities within a healthcare web application, demonstrating their potential impact through controlled testing, and providing appropriate remediation recommendations.

The exercise uncovered several security weaknesses involving:

- Broken access control.
- Weak password protection on confidential PDF documents.
- Exposure of sensitive patient records.
- Exposure of staff salary and shareholder database records.
- Inadequate protection of sensitive database backups.

The report demonstrates practical penetration testing methodology, vulnerability identification, evidence documentation, risk assessment, and security remediation.

2. Project Objectives

The main objectives were to:

1. Identify security weaknesses in a web application.
2. Examine authentication and access control mechanisms.
3. Retrieve and analyse exposed documents within the authorized scope.
4. Assess PDF password protection mechanisms.
5. Identify sensitive information exposed through database backups.
6. Evaluate the potential impact of discovered vulnerabilities.
7. Recommend appropriate security improvements.

3. Methodology

The assessment followed a structured black-box penetration testing approach.

| Phase | Description 
| Reconnaissance | Passive and active information gathering to identify exposed entry points. |
| Initial Access | Examination of authentication and input-handling weaknesses. |
| Data Extraction | Retrieval and analysis of confidential PDF documents. |
| Password Analysis | Extraction and dictionary-based testing of PDF password hashes. |
| Further Exposure Discovery | Inspection of retrieved materials and discovery of an exposed database backup. |
| Reporting | Documentation of findings, risk ratings, evidence and remediation recommendations. |

4. Tools and Technologies Used

| Tool | Purpose |

| Kali Linux | Penetration testing environment |
| VirtualBox | Virtual laboratory environment |
| Firefox | Web application reconnaissance and file retrieval |
| PDF Hash Extraction Tools | Extraction of PDF password hashes |
| Dictionary Wordlists | Password strength assessment |
| Manual File Inspection | Examination of document metadata and properties |

5. Key Findings

The assessment identified the following security issues:

 Finding 1: Broken Access Control

Risk Rating: CRITICAL

A weakness in the application's access control and/or authentication handling allowed unauthorized retrieval of three confidential patient pathology laboratory reports.

Potential Impact:
- Exposure of confidential patient information.
- Violation of patient privacy.
- Potential regulatory and reputational consequences.

 Finding 2: Weak PDF Password Protection

Risk Rating: CRITICAL

Two PDF documents were protected with weak passwords that were successfully recovered through dictionary-based password testing.

Potential Impact:
- Unauthorized access to confidential documents.
- Exposure of sensitive patient information.
- Reduced effectiveness of document encryption.

 Finding 3: Staff Salary Database Exposure

Risk Rating: HIGH

An exposed database backup contained staff records covering 30 employees, including names, job titles, departments and monthly salary information.

Potential Impact:
- Employee privacy violations.
- Exposure of confidential financial information.
- Increased risk of targeted social engineering.

 Finding 4: Shareholder Information Exposure

Risk Rating: HIGH

The exposed database backup also contained a shareholder register covering 10 shareholders, including ownership percentages and share classes.

Potential Impact:
- Exposure of commercially sensitive corporate information.
- Potential misuse of shareholder information.
- Corporate governance and privacy concerns.

Finding 5: Inadequate Database Backup Protection

Risk Rating: CRITICAL

An unprotected database backup was accessible through the identified exposure path.

Potential Impact:
- Unauthorized access to sensitive organizational records.
- Exposure of employee and corporate information.
- Increased risk of further data compromise.

 6. Risk Assessment Summary

| No. | Vulnerability | Risk Rating |

| 1 | Broken access control | 🔴 Critical |
| 2 | Weak PDF password protection | 🔴 Critical |
| 3 | Staff salary database exposure | 🟠 High |
| 4 | Shareholder register exposure | 🟠 High |
| 5 | Inadequate backup protection | 🔴 Critical |

Overall Engagement Risk: CRITICAL

 7. Recommendations and Remediation

The following security improvements were recommended:

Access Control
- Enforce proper authentication and authorization checks.
- Apply the principle of least privilege.
- Restrict access to sensitive application endpoints.

Document Security
- Use strong, randomly generated passwords.
- Avoid weak or dictionary-based passwords.
- Implement appropriate encryption and access-controlled document delivery.

Database Backup Security
- Remove exposed database backups from web-accessible directories.
- Store backups in encrypted and access-controlled locations.
- Implement monitoring and logging for backup access.

Organizational Security
- Conduct a data protection impact assessment.
- Rotate potentially exposed credentials and secrets.
- Provide staff security awareness training.
- Conduct follow-up security testing after remediation.

8. Skills Demonstrated

This project provided practical exposure to:

- Black-box penetration testing.
- Web application security assessment.
- Authentication and access control analysis.
- PDF password hash extraction.
- Dictionary-based password testing.
- Sensitive data exposure identification.
- Database backup security assessment.
- Vulnerability documentation.
- Risk assessment and remediation reporting.

9. Conclusion

This project demonstrates the importance of identifying and addressing security weaknesses in web applications, particularly systems handling sensitive healthcare and organizational information.

Through this supervised training exercise, I gained practical exposure to penetration testing methodology, vulnerability assessment, password security analysis, sensitive data exposure, and professional security reporting.

The experience further strengthened my interest in cybersecurity and my commitment to developing practical security analysis skills.

10. Ethical Disclaimer

This repository contains a redacted portfolio sample of a supervised cybersecurity training exercise conducted in a controlled laboratory environment with written authorization.

Client identity, personal information, actual filenames and exact figures have been removed or replaced with placeholders.

The project is intended strictly for educational and portfolio purposes. All security testing must be conducted only on systems for which explicit authorization has been granted.

Client identity, personal information, actual filenames and exact figures have been removed or replaced with placeholders.
The project is intended strictly for educational and portfolio purposes. All security testing must be conducted only on systems for which explicit authorization has been granted.
