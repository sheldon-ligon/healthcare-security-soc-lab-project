
# Architecture Decisions and Security Justifications

## Project Scope

This document explains the security design decisions for the proposed physician's office network.

The architecture supports two physicians, ten clinical workstations, administrative operations, healthcare application servers, and secure connectivity to external services.

**Status:** Proposed architecture — not implemented or tested.

## 1. Network Segmentation

**Decision:** Separate the network into six VLANs.

| VLAN | Purpose | Security Justification |
|---|---|---|
| 10 | Administration | Restrict access to office operations |
| 20 | Clinical | Separate clinical workstations from other users |
| 30 | Servers | Protect critical applications and patient data |
| 40 | Guest Wi-Fi | Isolate untrusted personal devices |
| 50 | Security Monitoring | Restrict access to monitoring infrastructure |
| 70 | DMZ | Separate externally exposed email services |

**Justification:**

Network segmentation reduces unnecessary communication between systems and limits potential lateral movement following a compromise.

**Implementation Consideration:**

VLAN separation alone does not enforce complete security isolation. Inter-VLAN communication must be controlled through firewall policies or properly configured access control lists (ACLs).

**NIST Mapping:** SC-7, AC-4

## 2. Redundant Next-Generation Firewalls

**Decision:** Use two next-generation firewalls in a high-availability configuration.

**Justification:**

Firewalls inspect and filter traffic entering and leaving the physician's office. Redundancy helps reduce downtime if the primary firewall fails.

Integrated IDS/IPS capabilities provide additional protection against suspicious network activity.

**Implementation Consideration:**

Configure state synchronization, failover monitoring, restricted management access, and default-deny security policies.

A redundant firewall pair does not eliminate other single points of failure, such as the ISP connection or core switch.

**NIST Mapping:** SC-7, SI-4, CP-8

## 3. Demilitarized Zone (DMZ)

**Decision:** Place the email security gateway in VLAN 70 while keeping Microsoft Exchange in the internal server network.

**Justification:**

The email security gateway filters incoming messages before they reach the internal email server.

This reduces direct exposure of Exchange to Internet-originated threats, including malicious attachments and phishing attempts.

**Implementation Consideration:**

Permit only necessary email communication between the gateway and Exchange. Block unauthorized DMZ-to-internal connections.

**NIST Mapping:** SC-7, AC-4

## 4. Clinical and Guest Wireless Security

**Decision:** Use separate clinical and guest wireless networks.

**Justification:**

Clinical wireless access requires stronger authentication because authorized devices may access sensitive healthcare applications.

Guest devices are untrusted and require Internet-only access.

**Implementation Consideration:**

- Clinical wireless: WPA3-Enterprise and IEEE 802.1X where supported.
- Guest wireless: Isolated VLAN with Internet-only access.
- Apply client isolation and restrict access to internal networks.

**NIST Mapping:** AC-18, SC-7

## 5. Network Access Control (NAC)

**Decision:** Include NAC and RADIUS authentication services.

**Justification:**

Network access control helps verify users and devices before allowing access to protected network resources.

This reduces the risk of unauthorized devices connecting to clinical and administrative networks.

**Implementation Consideration:**

Configure appropriate authentication policies, device authorization, and restricted access for noncompliant devices.

**NIST Mapping:** AC-3, IA-2

## 6. Centralized Security Monitoring

**Decision:** Establish a dedicated security monitoring network in VLAN 50.

**Justification:**

Centralized logging improves visibility into firewall activity, authentication failures, and suspicious events across the environment.

This supports incident investigation and security auditing.

**Implementation Consideration:**

Collect relevant security logs, synchronize system time, protect log integrity, and configure actionable alerts.

**NIST Mapping:** AU-6, SI-4

## 7. Secure External Connectivity

**Decision:** Use encrypted VPN connections for parent-company communication and authorized remote access.

**Justification:**

VPN connections protect sensitive information transmitted across untrusted networks.

Multifactor authentication adds protection against compromised remote-access credentials.

**Implementation Consideration:**

- Site-to-site IPsec VPN for parent-company connectivity.
- Remote-access VPN with MFA.
- Restrict access to approved internal resources.
- Log remote authentication and connection activity.

**NIST Mapping:** AC-17, SC-8, SC-13

## 8. Backup and Recovery

**Decision:** Use local backup infrastructure and encrypted off-site cloud backups.

**Justification:**

Healthcare operations require reliable access to patient records. Backups support recovery from equipment failures, accidental deletion, and ransomware incidents.

**Implementation Consideration:**

Protect backup credentials, restrict modification permissions, maintain protected backup copies, and test restoration procedures.

**NIST Mapping:** CP-9, CP-10

## 9. Legacy System Risk

**Decision:** Retain Windows 10 and Oracle Database 12 in the proposed architecture to satisfy the project requirements.

**Justification:**

These platforms are explicitly required by the assignment but introduce lifecycle and security concerns.

**Implementation Consideration:**

- Identify available security updates and support options.
- Restrict administrative access.
- Apply appropriate system hardening.
- Monitor for suspicious activity.
- Develop migration plans to supported platforms.

**NIST Mapping:** SI-2, RA-5, CM-6

## Conclusion

The proposed architecture uses defense-in-depth principles to protect healthcare operations and sensitive patient information.

Network segmentation, access controls, firewalls, encryption, monitoring, and backup capabilities address different security risks.

These decisions represent a logical security design. Actual effectiveness must be validated through configuration reviews, testing, vulnerability assessments, and operational monitoring.
