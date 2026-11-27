
# Week 4 – Oracle Database 12c STIG Hardening

## Project Overview

This phase of the Healthcare Security Portfolio focuses on hardening the Oracle Database 12c server within the proposed physician's office environment using Department of Defense (DoD) Security Technical Implementation Guide (STIG) requirements.

This project builds upon the network boundary design, HIPAA security compliance, and NIST SP 800-53 security controls established in Weeks 1–3.

## Objective

- Reduce database security vulnerabilities.
- Enforce least privilege and access control.
- Strengthen database authentication.
- Establish database auditing and centralized monitoring.
- Protect electronic protected health information (ePHI).
- Maintain database availability and recovery capabilities.

## Database Environment

| Component | Configuration |
|---|---|
| Database | Oracle Database 12c |
| IP Address | 10.10.30.30 |
| Network Segment | VLAN 30 – Server Network |
| Data Classification | Sensitive / ePHI |
| Security Monitoring | SIEM-01 |
| SIEM IP Address | 10.10.50.10 |
| SIEM Network | VLAN 50 – Security Monitoring |
| Security Framework | DoD STIG |

## Proposed Database Hardening Controls

The following 20 security measures represent the proposed database hardening plan developed during Week 4.

### Access Control and Account Management

| Security Control | Proposed Configuration |
|---|---|
| Authorized Database Access | Restrict database connections to authorized users and applications. |
| Unique User Identification | Assign individual accounts to database administrators. |
| Administrative Account Separation | Separate privileged accounts from standard user accounts. |
| PUBLIC Privileges | Review and revoke unnecessary PUBLIC privileges. |

### Authentication and Password Security

| Security Control | Proposed Configuration |
|---|---|
| Remote OS Authentication | Disable remote operating system authentication. |
| Failed Login Attempts | Configure account lockout policies to restrict repeated failed authentication attempts. |
| Inactive Accounts | Disable inactive and unauthorized database accounts according to approved policy. |
| Password Security | Enforce password length and complexity requirements. |

### Auditing and Monitoring

| Security Control | Proposed Configuration |
|---|---|
| Audit Record Generation | Enable database security auditing. |
| Security Event Auditing | Record authentication, account modifications, and administrative activities. |
| Audit Information Protection | Restrict unauthorized access and modification of audit records. |
| Centralized Audit Logging | Forward relevant database audit records to SIEM-01. |

### Network and Data Protection

| Security Control | Proposed Configuration |
|---|---|
| Restricted Network Access | Limit database connections through firewall rules and network segmentation. |
| Communication Encryption | Protect database communications using approved encryption protocols. |
| Oracle Listener Security | Restrict listener administration to authorized personnel. |
| Data-at-Rest Encryption | Implement approved encryption, such as Oracle Transparent Data Encryption (TDE), where supported. |

### Patching, Maintenance, and Recovery

| Security Control | Proposed Configuration |
|---|---|
| Security Patching | Review Oracle security advisories and apply supported updates. |
| Unnecessary Database Objects | Remove unnecessary sample schemas and database components. |
| Database Backups | Establish scheduled and protected backups using Oracle Recovery Manager (RMAN). |
| Recovery Testing | Conduct periodic database restoration and recovery exercises. |

## Security Monitoring and SOC Integration

Database audit records would be forwarded to SIEM-01 for centralized monitoring and security analysis.

Monitoring activities would include:

- Repeated failed authentication attempts.
- Unauthorized database access.
- Privileged account modifications.
- Changes to database permissions.
- Suspicious administrative activities.
- Unauthorized configuration changes.

These activities would support security event correlation, incident investigation, and threat detection.

## Expected Security Outcomes

- Reduced database attack surface.
- Improved protection of sensitive patient information.
- Enhanced user accountability.
- Improved visibility into database security events.
- Reduced risk of unauthorized access.
- Improved database resilience and recovery readiness.
- Support for HIPAA security compliance.

## Implementation Limitations

This project represents a proposed healthcare security architecture and database hardening plan.

The configurations have not been deployed or tested against a live Oracle database server. The proposed measures do not constitute a completed STIG compliance assessment.

Oracle Database 12c is also a legacy platform. Migration to a supported database release should be considered as part of the organization's long-term security strategy.

## Skills Demonstrated

- Database security and hardening
- STIG-based security planning
- Security configuration management
- Access control and least privilege
- Database auditing
- SIEM integration planning
- Vulnerability management
- Healthcare information security
- Security compliance documentation

## References

- [DoD Security Technical Implementation Guides](https://public.cyber.mil/stigs/)
- [Oracle Database 12c Security Guide](https://docs.oracle.com/database/121/DBSEG/)
- [NIST SP 800-53 Rev. 4 – Security and Privacy Controls](https://doi.org/10.6028/NIST.SP.800-53r4)
- [NIST SP 800-66 Rev. 2 – HIPAA Security Rule](https://doi.org/10.6028/NIST.SP.800-66r2)

---

Part of the Healthcare Security Portfolio – Information Systems Security and Assurance.
