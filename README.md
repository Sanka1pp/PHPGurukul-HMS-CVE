# Security Advisory: Multiple Critical Vulnerabilities in PHPGurukul Hospital Management System

| **Advisory Property** | **Details** |
| :--- | :--- |
| **Vendor** | PHPGurukul |
| **Product** | Hospital Management System (HMS) |
| **Version** | 4.0 |
| **Vulnerability Count** | 6 |
| **Status** | Unpatched (0-Day) |
| **Date** | January 2026 |

## 1. Executive Summary
Syntropy Security has identified six (3 Critical + 3 High) security vulnerabilities in the PHPGurukul Hospital Management System v4.0. These vulnerabilities fundamentally compromise the confidentiality, integrity, and availability of the application. The flaws allow unauthenticated remote attackers to extract the complete database, bypass administrative authentication mechanisms, and access Protected Health Information (PHI) of patients.

Due to the severity of these findings (including Remote Account Takeover and Full Database Disclosure), immediate remediation is recommended.

## 2. Vulnerability Index and Proof of Concept
The technical evidence for these findings is distributed across a comprehensive PDF report, specific exploit scripts, and video demonstrations.

| Vulnerability Type | Severity | CVE ID | Proof Artifacts & Documentation |
| :--- | :--- | :--- | :--- |
| **Unauthenticated SQL Injection**<br>*(Endpoint: get_doctor.php)* | **Critical** | *Pending* | • [**PDF Report (Page 2)**](Syntropy_Security_HMS_Report_Final.pdf) |
| **Admin Authentication Bypass (SQLi)**<br>*(Endpoint: Admin Login)* | **Critical** | *Pending* | • [**PDF Report (Page 7)**](Syntropy_Security_HMS_Report_Final.pdf) |
| **Broken Access Control (RBAC)**<br>*(Patient to Admin Escalation)* | **Critical** | *Pending* | • [**Exploit Code (RBAC_Privilege_Escalation.txt)**](RBAC_Privilege_Escalation.txt) |
| **Cross-Site Request Forgery (CSRF)**<br>*(Privileged Account Creation)* | **High** | *Pending* | • [**Exploit Code (CSRF_Add_Doctor.txt)**](CSRF_Add_Doctor.txt)<br>• [**Video Demonstration**](https://youtu.be/jP3iIFMMA_0) |
| **Insecure Direct Object Reference (IDOR)**<br>*(Access to Patient Records)* | **High** | *Pending* | • [**PDF Report (Page 2)**](Syntropy_Security_HMS_Report_Final.pdf)<br>• [**Video Demonstration**](https://youtu.be/Zmdcmx_cXH0) |
| **Stored Cross-Site Scripting (XSS)**<br>*(Account Takeover)* | **High** | *Pending* | • [**PDF Report (Page 6)**](Syntropy_Security_HMS_Report_Final.pdf)<br>• [**Video Demonstration**](https://youtu.be/1Jg05Dsp1NA) |

## 3. Technical Analysis
### 3.1 SQL Injection (CWE-89)
The application fails to parameterize user input in critical authentication and data retrieval endpoints. Specifically, the `get_doctor.php` endpoint allows unauthenticated XPATH injection, and the administrative login portal allows tautology-based authentication bypass (`' OR '1'='1`).

### 3.2 Broken Access Control (CWE-284 & CWE-639)
The application relies on obscure URLs rather than session-based Role-Based Access Control (RBAC). Low-privileged users can access administrative views by forcibly browsing to the `/admin/` directory. Furthermore, the application fails to validate object ownership, allowing authenticated patients to iterate through the `viewid` parameter to access the medical history of other users (IDOR).

### 3.3 Client-Side Enforcement Failures (CWE-352 & CWE-79)
The application lacks Anti-CSRF tokens on state-changing requests, allowing attackers to forge requests that create privileged accounts. Additionally, user input is stored and rendered without encoding, leading to Stored XSS that facilitates session hijacking.

## 4. Remediation Recommendations
The vendor has not released a patch at the time of this disclosure. Administrators are advised to:
1.  **Network Isolation:** Restrict access to the administrative panel to trusted IP addresses only.
2.  **Web Application Firewall (WAF):** Deploy rules to block common SQL injection patterns (e.g., `UNION SELECT`, `OR 1=1`) and XSS payloads (`<script>`, `javascript:`).
3.  **Code Revision:**
    * Implement Prepared Statements (PDO) for all database queries.
    * Enforce `session_start()` and role verification checks at the top of every PHP file in the `/admin/` directory.
    * Implement anti-CSRF tokens on all POST forms.

## 5. Credits
**Research & Discovery:** Sankalp Devidas Hanwate
**Organization:** Syntropy Security
