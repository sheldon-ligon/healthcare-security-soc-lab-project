
# Data Flow and Network Access Security

## Overview

This document describes the proposed data flows and access restrictions within the physician's office network.

The objective is to protect electronic protected health information (ePHI) through controlled communication between security zones.

**Status:** Proposed security policies — not implemented or tested.

## 1. Authorized Data Flows

| Source | Destination | Purpose | Security Control |
|---|---|---|---|
| Clinical VLAN 20 | Approved applications in VLAN 30 | Patient records and scheduling | Authentication, TLS, restricted application access |
| Administrative VLAN 10 | Approved applications in VLAN 30 | Scheduling and billing | Role-based access control (RBAC), TLS |
| Application Servers | Oracle Database Server | Retrieve and update patient records | Restricted database connections |
| Internal Exchange Server | DMZ Email Security Gateway | Approved email delivery | Restricted mail protocols |
| Physician's Office | Parent Company | Authorized business communication | Site-to-site IPsec VPN |
| Remote Staff | Approved Internal Resources | Remote healthcare operations | VPN, MFA, least privilege |
| Backup Server | Cloud Backup Provider | Off-site backup and recovery | Encrypted transfer and storage |
| Network Devices and Servers | SIEM VLAN 50 | Security logging and monitoring | Protected log transmission |

## 2. Proposed Network Access Policy

| Source | Destination | Action | Justification |
|---|---|---|---|
| Guest VLAN 40 | Internet | Allow (filtered) | Visitor Internet access |
| Guest VLAN 40 | Internal VLANs | Deny | Prevent unauthorized access |
| Clinical VLAN 20 | Approved Server Applications | Allow (restricted) | Support patient care |
| Administrative VLAN 10 | Approved Server Applications | Allow (restricted) | Support office operations |
| Clinical/Admin Workstations | Direct Oracle Administration | Deny | Restrict privileged database access |
| DMZ VLAN 70 | Internal Networks | Deny by default | Limit exposure from external services |
| Remote VPN Users | Approved Resources | Allow (restricted) | Secure authorized remote access |
| All Other Unapproved Traffic | Protected Networks | Deny | Enforce least privilege |

**Default Policy:** Deny inter-zone traffic unless an explicit authorization permits the required communication.

## 3. Patient Information Flow

A typical patient record request follows this logical sequence:

1. An authorized healthcare employee authenticates to a clinical workstation.
2. The workstation connects to an approved healthcare application over an encrypted connection.
3. Network access policies permit only the required application traffic.
4. The application server requests authorized patient information from the Oracle database.
5. The database returns the requested information to the application.
6. The application presents the information to the authorized employee.
7. Relevant authentication, application, and security events are recorded for auditing.

Clinical workstations should not require unrestricted direct access to the patient database.

## 4. Encryption and Data Protection

**Data in Transit**
- Use TLS 1.2 or later for supported application connections.
- Use IPsec for site-to-site communication.
- Require encrypted remote-access VPN connections.
- Protect security log transmission where supported.

**Data at Rest**
- Encrypt sensitive patient information and backups.
- Restrict access to encryption keys.
- Protect database and backup storage from unauthorized access.

## 5. Security Monitoring

The centralized security monitoring system collects relevant events from firewalls, servers, and other network infrastructure.

Priority monitoring activities include:

- Failed authentication attempts.
- Unauthorized access attempts between VLANs.
- Suspicious remote VPN activity.
- Database access anomalies.
- Unexpected changes to privileged accounts.
- Backup failures and unusual data transfers.

Alerts require investigation and documented response procedures.

## 6. NIST Security Control Alignment

| NIST Control | Application |
|---|---|
| SC-7 — Boundary Protection | Security zones, firewalls, and DMZ |
| AC-4 — Information Flow Enforcement | Authorized communication between VLANs |
| AC-17 — Remote Access | VPN security and remote access restrictions |
| SC-8 — Transmission Confidentiality and Integrity | Protected network communication |
| AU-6 — Audit Review, Analysis, and Reporting | Security log review |
| SI-4 — Information System Monitoring | Suspicious activity detection |

## Conclusion

The proposed data flow architecture follows least-privilege and defense-in-depth principles.

Separating network segments, restricting access to patient information, and monitoring communication between security zones help reduce unauthorized access and potential lateral movement.

These controls require implementation and validation before their effectiveness can be confirmed.
