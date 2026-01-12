# PHPGurukul-HMS-CVE
A security assessment of the Hospital Management System (v4.0) identified four critical vulnerabilities. These flaws allow unauthenticated attackers to exfiltrate database contents, bypass authentication to access administrative consoles, and hijack high-privileged sessions via Cross-Site Scripting.

# Security Advisory: PHPGurukul Hospital Management System v4.0
**Vendor:** PHPGurukul | **Product:** Hospital Management System | **Version:** 4.0
**Status:** Unpatched (0-Day)

## Executive Summary
Syntropy Security discovered multiple critical vulnerabilities in the PHPGurukul Hospital Management System v4.0. These flaws allow unauthenticated attackers to compromise the database, bypass authentication, and access sensitive patient records (PHI).

## Vulnerability List

| ID | Vulnerability Type | Severity | Status |
| :--- | :--- | :--- | :--- |
| **CVE-2026-XXXX** | Unauthenticated SQL Injection (get_doctor.php) | **Critical** | Reported to MITRE |
| **CVE-2026-XXXX** | Authentication Bypass (Admin Login) | **Critical** | Reported to MITRE |
| **CVE-2026-XXXX** | Insecure Direct Object Reference (IDOR) | **High** | Reported to MITRE |
| **CVE-2026-XXXX** | Stored Cross-Site Scripting (XSS) | **High** | Reported to MITRE |

## Technical Analysis
For full technical details, reproduction steps, and Proof of Concept (PoC) code, please refer to the attached report:
📄 [**Read Full Vulnerability Report (PDF)**](Syntropy_Security_HMS_Report_Final.pdf)

## Credits
**Discovered by:** Sankalp Devidas Hanwate
**Organization:** Syntropy Security
