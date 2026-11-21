
# NIST SP 800-53 Rev. 4 — Healthcare Security Controls

## Project Overview

This project examines how security controls from NIST Special Publication 800-53 Revision 4 can be applied to a proposed physician's office network to strengthen the protection of electronic protected health information (ePHI).

The project builds on the network architecture developed in Week 1 and the HIPAA security requirements identified in Week 2. It focuses on two NIST control families:

- **Access Control (AC):** Restricting unauthorized access to healthcare systems and sensitive patient information.
- **Audit and Accountability (AU):** Recording, monitoring, and reviewing system activities to support security investigations.

Eight security controls were selected to demonstrate how access restrictions and security monitoring can support the proposed healthcare environment.

## Project Objectives

- Identify relevant NIST SP 800-53 Revision 4 security controls.
- Apply access management principles to clinical, administrative, and server systems.
- Explain how network segmentation and secure remote access protect sensitive information.
- Establish proposed audit logging and security monitoring requirements.
- Map selected NIST controls to the physician's office network architecture.
- Identify methods for verifying security controls during future implementation.

## Selected NIST Controls

| Access Control (AC) | Audit and Accountability (AU) |
|---|---|
| AC-2: Account Management | AU-2: Audit Events |
| AC-3: Access Enforcement | AU-6: Audit Review, Analysis, and Reporting |
| AC-4: Information Flow Enforcement | AU-8: Time Stamps |
| AC-17: Remote Access | AU-9: Protection of Audit Information |

## Network Environment

The proposed healthcare network includes:

- **VLAN 10:** Administrative workstations
- **VLAN 20:** Clinical workstations
- **VLAN 30:** Healthcare application and database servers
- **VLAN 40:** Isolated guest wireless network
- **VLAN 50:** Security monitoring network containing SIEM-01
- **VLAN 70:** Demilitarized zone (DMZ) for externally facing services

Security controls are designed to restrict unnecessary communication between network segments, protect access to patient information, and support centralized security monitoring.

## Project Documentation

- [Access Control](access-control.md) — Account management, access enforcement, information flow, and remote access.
- [Audit and Accountability](audit-accountability.md) — Audit events, log analysis, timestamps, and audit protection.
- [Security Control Mapping](control-mapping.md) — Relationships between NIST controls, network components, and verification methods.

## Project Status

**Status:** Proposed security architecture and control assessment.

The controls documented in this project represent recommended security measures. They have not been implemented or independently verified in a production healthcare environment.

## References

Joint Task Force Transformation Initiative. (2013). *Security and privacy controls for federal information systems and organizations* (NIST SP 800-53 Rev. 4). National Institute of Standards and Technology. https://doi.org/10.6028/NIST.SP.800-53r4

Marron, J. (2024). *Implementing the Health Insurance Portability and Accountability Act (HIPAA) Security Rule: A cybersecurity resource guide* (NIST SP 800-66 Rev. 2). National Institute of Standards and Technology. https://doi.org/10.6028/NIST.SP.800-66r2

