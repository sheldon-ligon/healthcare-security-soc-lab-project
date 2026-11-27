
# Week 4 – Oracle Database 12c STIG Hardening

## Overview

This phase focuses on developing a database hardening plan for the Oracle Database 12c server within the proposed physician's office environment using DoD Security Technical Implementation Guide (STIG) requirements.

The project builds upon the network boundary design, HIPAA security requirements, and NIST SP 800-53 controls established in Weeks 1–3.

## Objectives

- Strengthen database security and access control.
- Document 20 proposed database security measures.
- Protect electronic protected health information (ePHI).
- Establish database auditing and centralized security monitoring.
- Support database availability and recovery.

## Database Environment

| Component | Configuration |
|---|---|
| Database | Oracle Database 12c |
| IP Address | 10.10.30.30 |
| Network Segment | VLAN 30 – Server Network |
| Security Monitoring | SIEM-01 |
| Security Framework | DoD STIG |

## Project Documentation

| Document | Description |
|---|---|
| [Database Hardening](database-hardening.md) | 20 proposed database security measures |
| [Audit and Monitoring](audit-monitoring.md) | Database auditing, centralized logging, and SIEM integration |
| [Control Mapping](control-mapping.md) | Mapping database security measures to applicable security requirements |

## Implementation Status

This project represents a proposed database hardening design. The security configurations have not been implemented or tested on a live Oracle database server.

## References

- [DoD Security Technical Implementation Guides](https://public.cyber.mil/stigs/)
- [Oracle Database 12c Security Guide](https://docs.oracle.com/database/121/DBSEG/)
- [NIST SP 800-53 Rev. 4](https://doi.org/10.6028/NIST.SP.800-53r4)

---

[Return to Main Project](../README.md)
