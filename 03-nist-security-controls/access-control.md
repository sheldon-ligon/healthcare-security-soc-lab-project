
# Access Control (AC) — NIST SP 800-53 Rev. 4

## Overview

The Access Control (AC) family focuses on ensuring that users and systems can access only the resources they are authorized to use.

In the proposed physician's office network, access controls help protect electronic protected health information (ePHI) by restricting access to clinical applications, administrative systems, and patient databases.

This document examines four selected controls:

- AC-2: Account Management
- AC-3: Access Enforcement
- AC-4: Information Flow Enforcement
- AC-17: Remote Access

These controls are proposed security requirements and have not been implemented or verified in a production environment.

---

## AC-2: Account Management

### Control Objective

Manage user accounts throughout their lifecycle, including account creation, modification, review, disabling, and removal.

### Proposed Implementation

- Assign individual accounts to physicians, clinical personnel, and administrative employees.
- Avoid shared user credentials.
- Assign permissions based on employee responsibilities.
- Review user accounts periodically.
- Disable accounts when employees leave the organization.
- Remove unnecessary or inactive accounts.

### Healthcare Application

A physician may require access to patient medical records, while a receptionist may only need access to scheduling and approved administrative information.

If an employee leaves the organization, their account should be disabled promptly to prevent unauthorized access.

### Verification Methods

- Review the organization's user account inventory.
- Examine account creation and termination procedures.
- Verify that inactive and terminated employee accounts are disabled.
- Compare assigned permissions against employee responsibilities.

**Status:** Proposed — Not Implemented

---

## AC-3: Access Enforcement

### Control Objective

Enforce approved access permissions to prevent unauthorized users from accessing protected systems and information.

### Proposed Implementation

- Implement role-based access control (RBAC).
- Assign permissions based on job responsibilities.
- Restrict access to sensitive healthcare applications.
- Limit database access to authorized application services and administrators.
- Review permissions when employee responsibilities change.

### Healthcare Application

Clinical personnel may require access to patient medical records, while administrative employees may only need access to appointment scheduling or billing functions.

Application-level permissions should prevent users from accessing information outside their approved responsibilities.

### Verification Methods

- Review application access permissions.
- Test access using authorized test accounts with different roles.
- Confirm that unauthorized roles cannot access restricted information.
- Review database permissions and privileged accounts.

**Status:** Proposed — Not Implemented

---

## AC-4: Information Flow Enforcement

### Control Objective

Control how information moves between systems and network segments according to approved security policies.

### Proposed Implementation

The physician's office network uses separate VLANs to organize and protect different systems.

| VLAN | Network | Purpose |
|---|---|---|
| 10 | 10.10.10.0/24 | Administrative workstations |
| 20 | 10.10.20.0/24 | Clinical workstations |
| 30 | 10.10.30.0/24 | Application and database servers |
| 40 | 10.10.40.0/24 | Guest wireless network |
| 50 | 10.10.50.0/24 | Security monitoring |
| 70 | 10.10.70.0/24 | DMZ |

Proposed security measures include:

- Apply default-deny rules between network segments.
- Allow only approved communication between VLANs.
- Restrict direct access to the Oracle patient database.
- Isolate guest wireless devices from internal healthcare systems.
- Use firewall policies and access control lists (ACLs) to enforce approved traffic flows.

### Healthcare Application

The Oracle patient database is located in VLAN 30 at 10.10.30.30.

Clinical workstations in VLAN 20 should access patient information through authorized healthcare applications rather than connecting directly to the database.

Guest devices in VLAN 40 should have internet access only and should not communicate with internal healthcare systems.

### Verification Methods

- Review firewall rules and inter-VLAN ACLs.
- Test approved and unauthorized network connections.
- Verify guest network isolation.
- Examine firewall logs for blocked connection attempts.
- Confirm that only approved application services can connect to the patient database.

**Status:** Proposed — Not Implemented

---

## AC-17: Remote Access

### Control Objective

Establish and enforce security requirements for remote connections to organizational systems.

### Proposed Implementation

- Require approved remote-access VPN connections.
- Enforce multifactor authentication (MFA).
- Restrict remote access based on employee responsibilities.
- Monitor remote authentication and connection activity.
- Limit site-to-site VPN communication to approved services.
- Disable remote access when no longer required.

### Healthcare Application

Physicians who need to access patient information outside the office should connect through the organization's approved VPN.

The proposed site-to-site IPsec VPN connecting the physician's office to its parent organization should permit only authorized network traffic.

Remote access should not automatically provide unrestricted access to all internal systems.

### Verification Methods

- Review VPN configuration and authentication policies.
- Verify MFA enforcement using authorized test accounts.
- Confirm remote users can access only approved systems.
- Examine VPN connection and authentication logs.
- Test restrictions on unauthorized remote connections.

**Status:** Proposed — Not Implemented

---

## Relationship to HIPAA Security Requirements

These Access Control measures support the protection of electronic protected health information by limiting unnecessary access to healthcare systems.

- AC-2 supports user account management.
- AC-3 supports enforcement of approved permissions.
- AC-4 supports network segmentation and controlled information flows.
- AC-17 supports secure remote connectivity.

Together, these controls help reduce unauthorized access risks within the proposed healthcare environment.

However, implementing these controls alone does not establish HIPAA compliance. Additional administrative, physical, and technical safeguards are necessary.

---

## References

Joint Task Force Transformation Initiative. (2013). *Security and privacy controls for federal information systems and organizations* (NIST SP 800-53 Rev. 4). National Institute of Standards and Technology. https://doi.org/10.6028/NIST.SP.800-53r4

Marron, J. (2024). *Implementing the Health Insurance Portability and Accountability Act (HIPAA) Security Rule: A cybersecurity resource guide* (NIST SP 800-66 Rev. 2). National Institute of Standards and Technology. https://doi.org/10.6028/NIST.SP.800-66r2
