
# NIST SP 800-53 Rev. 4 — Security Control Mapping

## Overview

This document maps the proposed physician's office network architecture to selected NIST SP 800-53 Revision 4 security controls.

The purpose is to demonstrate how network segmentation, access restrictions, encryption, monitoring, and backup capabilities support the protection of electronic protected health information (ePHI).

**Project Status:** Proposed architecture — controls have not been implemented or validated.

**Reference Framework:** NIST SP 800-53 Revision 4.

## 1. Security Control Mapping

| Control | Control Name | Proposed Implementation |
|---|---|---|
| SC-7 | Boundary Protection | Redundant next-generation firewalls, DMZ, network segmentation, and traffic filtering |
| AC-4 | Information Flow Enforcement | Default-deny inter-zone policies with explicitly authorized communication |
| AC-17 | Remote Access | Remote-access VPN, MFA, and restricted resource access |
| AC-18 | Wireless Access | Separate clinical and guest wireless networks with appropriate authentication |
| AC-3 | Access Enforcement | Role-based permissions and restricted access to healthcare applications |
| IA-2 | Identification and Authentication | Authentication of authorized users before access to protected systems |
| AU-6 | Audit Review, Analysis, and Reporting | Centralized log review and security event analysis |
| SI-4 | Information System Monitoring | IDS/IPS, SIEM monitoring, and suspicious activity alerts |
| SC-8 | Transmission Confidentiality and Integrity | TLS-protected application traffic and encrypted network communication |
| SC-13 | Cryptographic Protection | Approved cryptographic mechanisms for sensitive communications |
| CM-6 | Configuration Settings | Secure configuration baselines for network devices and servers |
| SI-2 | Flaw Remediation | Security patching and management of known vulnerabilities |
| RA-5 | Vulnerability Scanning | Planned vulnerability assessments of network devices and servers |
| CP-9 | Information System Backup | Local and encrypted off-site backups |
| CP-10 | Information System Recovery and Reconstitution | Documented restoration procedures and recovery testing |

## 2. Boundary Protection — SC-7

**Design Components:**
- FW-01 and FW-02 next-generation firewalls
- DMZ VLAN 70
- Internal VLAN segmentation
- Restricted external connectivity

**Security Objective:**

Protect internal healthcare systems by controlling traffic across network boundaries.

**Proposed Validation:**

Review firewall rules and verify that unauthorized traffic between security zones is blocked.

## 3. Information Flow Enforcement — AC-4

**Design Components:**
- Inter-VLAN access restrictions
- Default-deny network policies
- Restricted database communication
- Guest network isolation

**Security Objective:**

Permit only authorized communication between systems and network segments.

**Proposed Validation:**

Test permitted and denied connections between clinical, administrative, server, and guest VLANs.

## 4. Remote and Wireless Access — AC-17 / AC-18

**Design Components:**
- Site-to-site IPsec VPN
- Remote-access VPN with MFA
- WPA3-Enterprise clinical wireless
- Separate guest wireless network

**Security Objective:**

Protect remote and wireless access from unauthorized users and devices.

**Proposed Validation:**

Review VPN authentication settings, wireless security configurations, and access restrictions.

## 5. Monitoring and Auditing — AU-6 / SI-4

**Design Components:**
- Centralized SIEM server
- Firewall security logs
- Server authentication logs
- IDS/IPS alerts

**Security Objective:**

Identify suspicious activity and support security investigations.

**Proposed Validation:**

Generate controlled security events and verify that logs are collected, reviewed, and correlated appropriately.

## 6. Configuration and Vulnerability Management — CM-6 / SI-2 / RA-5

**Design Components:**
- Secure system configuration baselines
- Patch management procedures
- Vulnerability scanning
- Legacy system risk management

**Security Objective:**

Reduce vulnerabilities caused by insecure configurations and outdated software.

**Proposed Validation:**

Conduct configuration assessments and authenticated vulnerability scans using approved tools.

Windows 10 and Oracle Database 12 require particular attention because of their lifecycle and support limitations.

## 7. Backup and Recovery — CP-9 / CP-10

**Design Components:**
- Local backup server
- Encrypted cloud backup provider
- Restricted backup access
- Recovery procedures

**Security Objective:**

Maintain availability and recover critical healthcare information following disruptions.

**Proposed Validation:**

Perform controlled backup restoration tests and document recovery results.

## 8. Implementation Status

| Area | Current Status |
|---|---|
| Network architecture | Designed |
| Network segmentation | Proposed |
| Firewall and ACL policies | Documented conceptually |
| Remote and wireless access | Proposed |
| Security monitoring | Proposed |
| Backup and recovery | Proposed |
| Configuration hardening | Not implemented |
| Vulnerability assessment | Not performed |
| Security control validation | Not performed |

## Conclusion

The proposed physician's office network incorporates security design principles aligned with selected NIST SP 800-53 Revision 4 controls.

This mapping identifies the intended safeguards and their security objectives. It does not establish formal NIST compliance.

Actual implementation, testing, evidence collection, and ongoing assessment would be required to determine whether the controls are operating effectively.

## References

National Institute of Standards and Technology. (2013). *Security and privacy controls for federal information systems and organizations* (NIST Special Publication 800-53, Revision 4). https://doi.org/10.6028/NIST.SP.800-53r4
