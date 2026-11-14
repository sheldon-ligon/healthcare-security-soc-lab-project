
# Security Control Mapping – HIPAA Compliance

## Objective
Map the physician's office security and privacy requirements to the safeguards proposed in the Week 1 network architecture.

## Proposed Security Control Mapping

| Security Requirement | Proposed Security Control | Network Component | Purpose |
|---|---|---|---|
| Network boundary protection | High-availability firewalls with IDS/IPS | FW-01 / FW-02 | Filter traffic and detect suspicious network activity |
| Patient data segregation | VLAN segmentation and access control lists (ACLs) | VLAN 10, 20, 30, 40 | Restrict unnecessary communication between network segments |
| Patient record protection | Role-based access control (RBAC) | Oracle Patient Database / EHR Application | Limit access to authorized healthcare personnel |
| Secure remote access | VPN with multifactor authentication | Remote Access VPN | Protect remote connections and verify user identities |
| Parent organization connectivity | Site-to-site IPsec VPN | FW-01 / FW-02 | Encrypt communication between organizational networks |
| Audit logging | Centralized log collection | SIEM-01 / VLAN 50 | Collect and review security events |
| Wireless security | WPA3-Enterprise and 802.1X | Clinical Wireless Network / VLAN 20 | Authenticate devices and users connecting to clinical Wi-Fi |
| Guest network isolation | Internet-only access with firewall restrictions | VLAN 40 | Prevent guest devices from accessing internal systems |
| Data recovery | Local and encrypted cloud backups | Backup Server / Cloud Backup | Support recovery after incidents or system failures |
| Incident response | Documented investigation and containment procedures | SIEM-01 / Firewalls / Servers | Support investigation and containment of security incidents |

## Security Architecture Decisions

### 1. Network Segmentation
The network separates administrative, clinical, server, guest, and security monitoring systems into different VLANs. Inter-VLAN access is restricted to necessary communication paths.

### 2. Access Control
Healthcare personnel should receive access based on their job responsibilities. Individual accounts, RBAC, and MFA help prevent unauthorized access to patient information.

### 3. Monitoring and Detection
Security logs from firewalls, authentication services, and critical servers are forwarded to SIEM-01. Security personnel can review suspicious events and investigate potential incidents.

### 4. Data Protection and Recovery
Patient information should be protected through encryption, restricted access, and secure backups. Local and cloud backup resources support disaster recovery planning.

## Implementation Status
**Proposed / Not Deployed**

This mapping documents planned security safeguards for an academic physician's office architecture. It does not represent verified HIPAA compliance or production implementation.

## Related Documentation
- [Week 2 Overview](README.md)
- [HIPAA Requirements](hipaa-requirements.md)
- [Week 1 Network Architecture](../01-network-boundary-design/)

