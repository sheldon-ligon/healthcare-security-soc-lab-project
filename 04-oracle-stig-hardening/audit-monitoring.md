
# Oracle Database Auditing and Security Monitoring

## Overview

Database auditing and security monitoring provide visibility into activities occurring within the Oracle Database 12c server. Centralized monitoring supports threat detection, incident investigation, user accountability, and the protection of electronic protected health information (ePHI).

## Monitoring Environment

| Component | Configuration |
|---|---|
| Data Source | Oracle Database 12c |
| Database IP Address | 10.10.30.30 |
| Database Network | VLAN 30 – Server Network |
| Monitoring System | SIEM-01 |
| SIEM IP Address | 10.10.50.10 |
| Monitoring Network | VLAN 50 – Security Monitoring |

## Database Audit Requirements

| Auditable Event | Security Purpose |
|---|---|
| Successful Authentication | Track authorized database access. |
| Failed Authentication | Identify potential brute-force attacks. |
| Account Creation and Deletion | Detect unauthorized account modifications. |
| Privilege Changes | Identify unauthorized privilege escalation. |
| Administrative Activities | Maintain accountability for privileged users. |
| Configuration Changes | Detect unauthorized configuration modifications. |
| Sensitive Data Access | Identify potentially unauthorized access to patient information. |
| Audit Policy Changes | Detect attempts to disable or modify security auditing. |

## Centralized Logging Architecture

Database audit records would be collected and forwarded to SIEM-01 for centralized security monitoring.

Proposed log flow:

    Oracle Database 12c
    10.10.30.30 (VLAN 30)
            |
            v
    Audit Log Collection
            |
            v
    Firewall / Access Control
            |
            v
    SIEM-01
    10.10.50.10 (VLAN 50)
            |
            v
    Alert Generation
            |
            v
    SOC Analyst Investigation

## Proposed SIEM Detection Use Cases

| Detection Use Case | Potential Security Threat |
|---|---|
| Multiple failed database logins | Brute-force attack |
| Failed logins followed by successful authentication | Potential account compromise |
| Unexpected privileged account creation | Unauthorized access or persistence |
| Unauthorized privilege changes | Privilege escalation |
| Unusual access to patient records | Potential data exposure or insider threat |
| Unauthorized audit policy modification | Defense evasion |
| Database access from unauthorized systems | Potential network intrusion |

## SOC Analyst Workflow

1. Receive and acknowledge the security alert.
2. Review database audit records.
3. Identify the affected account, source system, and event timestamps.
4. Correlate related authentication and network events.
5. Determine alert disposition, severity, and priority.
6. Document investigation findings.
7. Escalate confirmed incidents according to established procedures.

## Audit Log Protection

- Restrict access to authorized security personnel.
- Protect audit records against unauthorized modification and deletion.
- Maintain synchronized system timestamps.
- Encrypt audit records during transmission.
- Retain audit records according to organizational and regulatory requirements.
- Monitor changes to database auditing configurations.

## Expected Security Benefits

- Centralized visibility into database security events.
- Improved detection of suspicious activities.
- Enhanced incident investigation capabilities.
- Improved accountability for privileged database users.
- Support for HIPAA audit control requirements.
- Support for NIST Audit and Accountability (AU) controls.

## Implementation Status

This document represents a proposed database auditing and SIEM integration design. Audit collection, log forwarding, and detection use cases have not been implemented or tested against a live Oracle database.

## References

- [Oracle Database 12c Security Guide](https://docs.oracle.com/database/121/DBSEG/)
- [DoD Security Technical Implementation Guides](https://public.cyber.mil/stigs/)
- [NIST SP 800-53 Rev. 4](https://doi.org/10.6028/NIST.SP.800-53r4)
- [NIST SP 800-66 Rev. 2](https://doi.org/10.6028/NIST.SP.800-66r2)

---

[Return to Week 4 Overview](README.md)
