# Security Advisory: PHPGurukul Hospital Management System v4.0
**Vendor:** PHPGurukul | **Product:** Hospital Management System | **Version:** 4.0
**Status:** Unpatched (0-Day) | **Total Vulnerabilities:** 6

##  Executive Summary
Syntropy Security discovered **six (6)** high/critical vulnerabilities in the PHPGurukul Hospital Management System v4.0. These flaws allow unauthenticated attackers to compromise the database, bypass authentication, and access sensitive patient records (PHI).

The evidence for these findings is divided between the comprehensive **PDF Report**, specific **Proof of Concept Scripts**, and **Video Demonstrations**.

##  Vulnerability Index & Proof Artifacts

| ID | Vulnerability Name | Severity | Proof Source |
| :--- | :--- | :--- | :--- |
| **CVE-2026-XXXX** | **Unauthenticated SQL Injection** <br> *(get_doctor.php)* | **Critical** | 📄 [**PDF Report (Page 2)**](Syntropy_Security_HMS_Report_Final.pdf) |
| **CVE-2026-XXXX** | **Admin Auth Bypass SQL Injection** <br> *(Admin Login)* | **Critical** | 📄 [**PDF Report (Page 7)**](Syntropy_Security_HMS_Report_Final.pdf) |
| **CVE-2026-XXXX** | **Broken Access Control (RBAC)** <br> *(Patient to Admin Escalation)* | **Critical** | 📜 [**RBAC_Privilege_Escalation.txt**](RBAC_Privilege_Escalation.txt) |
| **CVE-2026-XXXX** | **Cross-Site Request Forgery (CSRF)** <br> *(Add Doctor Account)* | **High** | 📜 [**CSRF_Add_Doctor.txt**](CSRF_Add_Doctor.txt) <br> 📺 [**Watch Video PoC**](https://youtu.be/jP3iIFMMA_0) |
| **CVE-2026-XXXX** | **Insecure Direct Object Reference (IDOR)** <br> *(Access Patient Records)* | **High** | 📄 [**PDF Report (Page 2)**](Syntropy_Security_HMS_Report_Final.pdf) <br> 📺 [**Watch Video PoC**](https://youtu.be/Zmdcmx_cXH0) |
| **CVE-2026-XXXX** | **Stored Cross-Site Scripting (XSS)** <br> *(Account Takeover)* | **High** | 📄 [**PDF Report (Page 6)**](Syntropy_Security_HMS_Report_Final.pdf) <br> 📺 [**Watch Video PoC**](https://youtu.be/1Jg05Dsp1NA) |

##  Credits
**Discovered by:** Sankalp Devidas Hanwate
**Organization:** Syntropy Security
