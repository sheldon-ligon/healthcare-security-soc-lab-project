
# Oracle Database 12c Hardening

## Overview

The Oracle Database 12c server stores sensitive patient information within the proposed physician's office environment. Database hardening provides an additional layer of protection beyond network segmentation and firewall security.

The following 20 proposed security measures are organized into five security categories based on DoD STIG guidance.

## 1. Access Control and Account Management

| Security Control | Proposed Configuration |
|---|---|
| Authorized Database Access | Restrict database access to authorized users and approved applications. |
| Unique User Identification | Assign individual accounts to database administrators to maintain accountability. |
| Administrative Account Separation | Separate privileged administrative accounts from standard user accounts. |
| PUBLIC Privileges | Review and revoke unnecessary privileges granted to PUBLIC. |

## 2. Authentication and Password Security

| Security Control | Proposed Configuration |
|---|---|
| Remote OS Authentication | Disable remote operating system authentication by setting REMOTE_OS_AUTHENT to FALSE. |
| Failed Login Attempts | Configure account lockout policies using FAILED_LOGIN_ATTEMPTS. |
| Inactive Database Accounts | Disable inactive accounts according to approved account management policies. |
| Password Security | Enforce password length and complexity through Oracle password verification functions. |

## 3. Auditing and Monitoring

| Security Control | Proposed Configuration |
|---|---|
| Audit Record Generation | Enable database security auditing. |
| Security Event Auditing | Record authentication attempts, account modifications, and administrative activities. |
| Audit Information Protection | Restrict unauthorized access, modification, and deletion of audit records. |
| Centralized Audit Logging | Forward relevant database audit records to SIEM-01. |

## 4. Network and Data Protection

| Security Control | Proposed Configuration |
|---|---|
| Restricted Network Access | Restrict database connections through firewall rules and network segmentation. |
| Communication Encryption | Protect database communications using approved encryption protocols. |
| Oracle Listener Security | Restrict listener administration to authorized personnel. |
| Data-at-Rest Encryption | Use Oracle Transparent Data Encryption (TDE) where supported and licensed. |

## 5. Patching, Maintenance, and Recovery

| Security Control | Proposed Configuration |
|---|---|
| Security Patching | Review Oracle security advisories and apply available supported security updates. |
| Unnecessary Database Objects | Review and remove unnecessary sample schemas and database components. |
| Database Backups | Establish scheduled and protected backups using Oracle Recovery Manager (RMAN). |
| Recovery Testing | Conduct periodic database restoration and recovery exercises. |

## Expected Security Benefits

- Reduced database attack surface.
- Improved access control and user accountability.
- Protection of sensitive patient information.
- Improved visibility into database security events.
- Reduced risk of unauthorized configuration changes.
- Improved database availability and recovery readiness.

## Implementation Considerations

These security measures represent proposed configurations and have not been implemented or validated against a live Oracle database server.

Because Oracle Database 12c is a legacy platform, migration to a supported database release should be included in the organization's long-term security strategy.

## References

- [DoD Security Technical Implementation Guides](https://public.cyber.mil/stigs/)
- [Oracle Database 12c Security Guide](https://docs.oracle.com/database/121/DBSEG/)

---

[Return to Week 4 Overview](README.md)

