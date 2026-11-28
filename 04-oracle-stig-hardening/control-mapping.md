
# Database Security Control Mapping

## Overview

This document maps the proposed Oracle Database 12c hardening measures to applicable NIST SP 800-53 Revision 4 security controls and HIPAA Security Rule requirements.

The purpose is to demonstrate how database hardening supports the overall security and compliance architecture of the proposed physician's office.

## 1. Access Control and Account Management

| Database Security Measure | NIST Control | Control Name |
|---|---|---|
| Authorized Database Access | AC-3 | Access Enforcement |
| Unique User Identification | IA-2 | Identification and Authentication |
| Administrative Account Separation | AC-6 | Least Privilege |
| Restriction of PUBLIC Privileges | AC-6 | Least Privilege |

## 2. Authentication and Password Security

| Database Security Measure | NIST Control | Control Name |
|---|---|---|
| Remote OS Authentication Restrictions | IA-2 | Identification and Authentication |
| Failed Login Attempts | AC-7 | Unsuccessful Logon Attempts |
| Inactive Database Accounts | AC-2 | Account Management |
| Password Security | IA-5 | Authenticator Management |

## 3. Auditing and Monitoring

| Database Security Measure | NIST Control | Control Name |
|---|---|---|
| Audit Record Generation | AU-12 | Audit Generation |
| Security Event Auditing | AU-2 | Audit Events |
| Audit Information Protection | AU-9 | Protection of Audit Information |
| Centralized Audit Logging | AU-6 | Audit Review, Analysis, and Reporting |

## 4. Network and Data Protection

| Database Security Measure | NIST Control | Control Name |
|---|---|---|
| Restricted Network Access | SC-7 | Boundary Protection |
| Communication Encryption | SC-8 | Transmission Confidentiality and Integrity |
| Oracle Listener Security | AC-3 | Access Enforcement |
| Data-at-Rest Encryption | SC-28 | Protection of Information at Rest |

## 5. Patching, Maintenance, and Recovery

| Database Security Measure | NIST Control | Control Name |
|---|---|---|
| Security Patching | SI-2 | Flaw Remediation |
| Removal of Unnecessary Database Objects | CM-7 | Least Functionality |
| Database Backups | CP-9 | Information System Backup |
| Recovery Testing | CP-4 | Contingency Plan Testing |

## 6. HIPAA Security Rule Alignment

| HIPAA Requirement | Regulatory Reference | Proposed Security Measure |
|---|---|---|
| Access Control | 45 CFR 164.312(a)(1) | Database access restrictions and least privilege |
| Unique User Identification | 45 CFR 164.312(a)(2)(i) | Individual database user accounts |
| Audit Controls | 45 CFR 164.312(b) | Database auditing and centralized monitoring |
| Integrity | 45 CFR 164.312(c)(1) | Protection against unauthorized data modification |
| Person or Entity Authentication | 45 CFR 164.312(d) | Database authentication and account security |
| Transmission Security | 45 CFR 164.312(e)(1) | Encrypted database communications |
| Data Backup Plan | 45 CFR 164.308(a)(7)(ii)(A) | Scheduled database backups |
| Disaster Recovery Plan | 45 CFR 164.308(a)(7)(ii)(B) | Database recovery procedures |

## Security Framework Integration

The proposed security architecture integrates three complementary security frameworks:

- HIPAA establishes healthcare information security requirements.
- NIST SP 800-53 provides security and privacy controls.
- DoD STIGs provide technology-specific security configuration guidance.

Together, these frameworks support a defense-in-depth approach to protecting sensitive patient information.

## Assessment Status

The mappings represent proposed relationships between database security measures and applicable security requirements.

They do not constitute an official DISA crosswalk, completed compliance assessment, or certification of HIPAA compliance.

Implementation and technical validation would be required before determining actual compliance.

## References

- [DoD Security Technical Implementation Guides](https://public.cyber.mil/stigs/)
- [NIST SP 800-53 Rev. 4](https://doi.org/10.6028/NIST.SP.800-53r4)
- [NIST SP 800-66 Rev. 2](https://doi.org/10.6028/NIST.SP.800-66r2)
- [HIPAA Security Rule – 45 CFR Part 164](https://www.ecfr.gov/current/title-45/subtitle-A/subchapter-C/part-164)
- [Oracle Database 12c Security Guide](https://docs.oracle.com/database/121/DBSEG/)

---

[Return to Week 4 Overview](README.md)
