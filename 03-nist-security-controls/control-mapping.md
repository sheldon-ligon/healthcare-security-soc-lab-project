
# NIST Security Control Mapping — Healthcare Network

## Project Overview

This document maps eight selected NIST SP 800-53 Revision 4 security controls to the proposed physician's office network.

The objective is to demonstrate how Access Control (AC) and Audit and Accountability (AU) requirements can be applied to protect electronic protected health information (ePHI), restrict unauthorized access, and support security monitoring.

This mapping builds on the network boundary design from Week 1 and the HIPAA security requirements identified in Week 2.

**Assessment Status:** Proposed — Controls have not been implemented or independently verified.

---

## Network Assets and Security Boundaries

| Network Component | IP Address / VLAN | Security Purpose |
|---|---|---|
| Administrative workstations | VLAN 10 — 10.10.10.0/24 | Scheduling, billing, and administrative operations |
| Clinical workstations | VLAN 20 — 10.10.20.0/24 | Authorized clinical activities |
| Application and database servers | VLAN 30 — 10.10.30.0/24 | Healthcare services and patient information |
| Oracle patient database | 10.10.30.30 | Storage of sensitive patient records |
| Guest wireless | VLAN 40 — 10.10.40.0/24 | Internet-only guest access |
| SIEM-01 | 10.10.50.10 — VLAN 50 | Centralized security monitoring |
| DMZ | VLAN 70 — 10.10.70.0/24 | Segregated externally facing services |
| Firewalls and VPN infrastructure | Network boundary | Traffic filtering, remote access, and security logging |

---

## Access Control (AC) Mapping

| NIST Control | Proposed Implementation | Affected Components | Verification Method |
|---|---|---|---|
| AC-2: Account Management | Individual accounts, role assignments, periodic account reviews, and prompt account disabling | Clinical applications, administrative systems, database accounts | Review account inventory, permissions, and account lifecycle records |
| AC-3: Access Enforcement | Enforce role-based permissions and restrict unauthorized application and database access | Clinical applications, Oracle database, administrative systems | Test authorized and unauthorized access using approved test accounts |
| AC-4: Information Flow Enforcement | Default-deny inter-VLAN policies, approved traffic flows, and guest network isolation | VLANs 10, 20, 30, 40, 50, and 70; firewalls and Layer 3 switch | Review ACLs and firewall rules; test allowed and blocked connections |
| AC-17: Remote Access | Require approved VPN connections, MFA, remote access restrictions, and connection monitoring | Remote-access VPN, site-to-site VPN, internal applications | Review VPN policies, test MFA, and examine authentication logs |

### Access Control Assessment

The proposed AC controls establish requirements for determining who can access healthcare systems and how information can move between network segments.

The Oracle patient database at 10.10.30.30 should be accessible only through approved application services and authorized administrative connections.

Guest wireless devices must remain isolated from internal healthcare systems.

**Assessment Result:** Design requirements identified; implementation evidence not yet collected.

---

## Audit and Accountability (AU) Mapping

| NIST Control | Proposed Implementation | Affected Components | Verification Method |
|---|---|---|---|
| AU-2: Audit Events | Define and enable recording of relevant authentication, account, application, database, and security events | Firewalls, servers, clinical applications, Oracle database | Review audit policy and configurations; generate authorized test events |
| AU-6: Audit Review, Analysis, and Reporting | Centralize selected logs, review suspicious events, and establish investigation procedures | SIEM-01, authentication systems, network devices | Confirm log ingestion, test detection rules, and document investigations |
| AU-8: Time Stamps | Synchronize system clocks and maintain reliable event timestamps | Workstations, servers, firewalls, Oracle database, SIEM-01 | Review time synchronization settings and compare event timestamps |
| AU-9: Protection of Audit Information | Restrict access to audit records, protect log storage, and monitor unauthorized changes | SIEM-01, log storage, database audit records | Review permissions and test protection against unauthorized log modification |

### Audit and Accountability Assessment

The proposed AU controls support the collection, review, and protection of security evidence.

SIEM-01 at 10.10.50.10 would receive selected security events from approved sources to support centralized monitoring and incident investigations.

Security personnel would need documented procedures for reviewing alerts, investigating suspicious behavior, and escalating confirmed incidents.

**Assessment Result:** Monitoring requirements identified; logging and detection capabilities not yet tested.

---

## HIPAA Security Requirement Mapping

The selected NIST controls support several requirements of the HIPAA Security Rule.

| HIPAA Security Area | Relevant NIST Controls | Proposed Security Measures |
|---|---|---|
| Access Control — 45 CFR § 164.312(a) | AC-2, AC-3 | Individual accounts, approved permissions, and restricted access to ePHI |
| Audit Controls — 45 CFR § 164.312(b) | AU-2, AU-6, AU-8, AU-9 | Security event recording, monitoring, reliable timestamps, and audit protection |
| Information Access Management — 45 CFR § 164.308(a)(4) | AC-2, AC-3 | Role-based permissions and account access reviews |
| Transmission Security — 45 CFR § 164.312(e) | AC-4, AC-17 | Controlled network communications and encrypted VPN connections |
| Security Incident Procedures — 45 CFR § 164.308(a)(6) | AU-2, AU-6, AU-9 | Investigation evidence, event review, and incident escalation support |

**Note:** This table shows how the selected controls can support HIPAA security requirements. It is not a complete HIPAA compliance assessment or an official one-to-one regulatory crosswalk.

Additional safeguards are required to address the full HIPAA Security Rule.

---

## Example Security Validation Scenarios

The following scenarios describe how selected controls could be tested during a future lab implementation.

### Scenario 1: Unauthorized Database Access

**Related Controls:** AC-3, AC-4, AU-2, AU-6

**Test Objective:** Determine whether an unauthorized workstation can directly connect to the Oracle patient database.

**Proposed Test:**

1. Configure approved firewall and inter-VLAN access rules.
2. Use an authorized test workstation to attempt a database connection that should be denied.
3. Verify that the connection is blocked.
4. Review relevant firewall and database audit records.
5. Confirm that the recorded events can be investigated through SIEM-01, where configured.

**Expected Result:** Unauthorized connections are blocked and relevant security events are available for review.

**Status:** Not Tested

### Scenario 2: Suspicious Login Activity

**Related Controls:** AC-2, AC-3, AU-2, AU-6, AU-8

**Test Objective:** Verify that suspicious authentication activity can be recorded and investigated.

**Proposed Test:**

1. Generate several authorized failed-login test events.
2. Confirm that the authentication system records the attempts.
3. Verify that SIEM-01 receives the relevant events.
4. Review timestamps and correlate the authentication activity.
5. Document whether the activity meets the organization's alert criteria.

**Expected Result:** Authentication events are recorded with reliable timestamps and can be reviewed by security personnel.

**Status:** Not Tested

### Scenario 3: Unauthorized Audit Log Modification

**Related Controls:** AC-3, AU-9

**Test Objective:** Verify that ordinary user accounts cannot modify or delete protected audit records.

**Proposed Test:**

1. Configure restricted permissions for audit log storage.
2. Use an authorized nonprivileged test account.
3. Attempt to modify or delete a designated test audit record.
4. Verify that the unauthorized action is denied.
5. Review available security events associated with the attempt.

**Expected Result:** Unauthorized modification or deletion of protected audit records is prevented.

**Status:** Not Tested

---

## Control Assessment Summary

| Control | Design Documented | Implemented | Verified |
|---|---|---|---|
| AC-2 | Yes | No | No |
| AC-3 | Yes | No | No |
| AC-4 | Yes | No | No |
| AC-17 | Yes | No | No |
| AU-2 | Yes | No | No |
| AU-6 | Yes | No | No |
| AU-8 | Yes | No | No |
| AU-9 | Yes | No | No |

### Current Assessment

- **8 controls** selected and mapped to the proposed network.
- **8 controls** documented at the design level.
- **0 controls** verified through implementation testing.
- Future lab validation is required before claiming operational effectiveness.

---

## Future SOC Portfolio Development

The next stage of this project could involve implementing selected controls in a controlled lab environment.

Potential activities include:

- Configuring VLAN and firewall restrictions using pfSense.
- Implementing role-based access restrictions on test systems.
- Forwarding Windows Security and Sysmon events to Splunk.
- Configuring Wazuh or another SIEM for additional monitoring.
- Investigating suspicious authentication activity.
- Testing log access restrictions.
- Collecting screenshots, sanitized logs, and configuration evidence.
- Documenting findings and corrective actions.

These activities would turn the proposed control mapping into a practical security validation project.

---

## References

Joint Task Force Transformation Initiative. (2013). *Security and privacy controls for federal information systems and organizations* (NIST SP 800-53 Rev. 4). National Institute of Standards and Technology. https://doi.org/10.6028/NIST.SP.800-53r4

Marron, J. (2024). *Implementing the Health Insurance Portability and Accountability Act (HIPAA) Security Rule: A cybersecurity resource guide* (NIST SP 800-66 Rev. 2). National Institute of Standards and Technology. https://doi.org/10.6028/NIST.SP.800-66r2

U.S. Department of Health and Human Services. (n.d.). *Summary of the HIPAA Security Rule*. https://www.hhs.gov/hipaa/for-professionals/security/laws-regulations/index.html
