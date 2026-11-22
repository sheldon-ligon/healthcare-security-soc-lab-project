
# Audit and Accountability (AU) — NIST SP 800-53 Rev. 4

## Project Overview

The Audit and Accountability (AU) control family focuses on recording, reviewing, and protecting system activities to support security monitoring and incident investigations.

In the proposed physician's office network, audit controls help identify suspicious behavior involving clinical workstations, administrative systems, servers, and the Oracle patient database.

The proposed SIEM-01 server, located at 10.10.50.10 in VLAN 50, serves as the central security monitoring system.

This document examines four selected controls:

- AU-2: Audit Events
- AU-6: Audit Review, Analysis, and Reporting
- AU-8: Time Stamps
- AU-9: Protection of Audit Information

**Project Status:** Proposed security controls — Not Implemented or Verified

---

## AU-2: Audit Events

### Control Objective

Identify which security-related events should be recorded to support monitoring, investigations, and accountability.

### Proposed Implementation

The physician's office should define a security event logging policy that identifies important activities to monitor.

Recommended events include:

- Successful and unsuccessful login attempts.
- User account creation, modification, and deletion.
- Changes to employee access permissions.
- Access to sensitive patient information.
- Administrative and privileged account activities.
- Firewall connection attempts and denied traffic.
- VPN authentication and connection events.
- Changes to security configurations.

Relevant events should be collected from authentication systems, firewalls, clinical applications, and servers.

### Healthcare Application

The Oracle patient database at 10.10.30.30 contains sensitive patient information.

Database auditing should record relevant authentication attempts, privileged activities, and access to sensitive information according to the organization's audit policy.

These records can help determine whether unauthorized activity occurred.

### SOC Verification Methods

- Review the organization's audit event policy.
- Examine logging configurations on servers and applications.
- Generate authorized test events.
- Confirm that selected events are recorded.
- Verify that the recorded information contains sufficient details for investigation.

**Status:** Proposed — Not Implemented

---

## AU-6: Audit Review, Analysis, and Reporting

### Control Objective

Review and analyze audit records to identify suspicious activities, security incidents, and potential policy violations.

### Proposed Implementation

The proposed SIEM-01 server in VLAN 50 should centralize security logs from approved network devices and systems.

Security monitoring should include:

- Reviewing authentication failures.
- Identifying unusual account activity.
- Monitoring privileged account usage.
- Correlating events across multiple systems.
- Investigating unauthorized access attempts.
- Documenting security findings and escalation decisions.

The organization should establish procedures for reviewing alerts and responding to suspicious events.

### Healthcare Application

A possible security incident may involve repeated unsuccessful login attempts followed by a successful login from an unusual source.

A SOC analyst could use SIEM-01 to correlate authentication events, examine the affected account, and determine whether further investigation is required.

This scenario may indicate compromised credentials, but additional evidence would be needed before confirming an incident.

### SOC Verification Methods

- Confirm that approved log sources are sending events to SIEM-01.
- Generate authorized failed-login test events.
- Verify that the SIEM receives and displays the events.
- Test alert rules for suspicious authentication patterns.
- Document investigation results and escalation procedures.

**Status:** Proposed — Not Implemented

---

## AU-8: Time Stamps

### Control Objective

Ensure that audit records contain reliable timestamps so security personnel can accurately determine when events occurred.

### Proposed Implementation

The physician's office should synchronize system clocks using approved time synchronization services.

Systems requiring synchronized time include:

- Firewalls and network devices.
- Windows and Linux servers.
- Clinical and administrative workstations.
- Oracle database and application servers.
- VPN infrastructure.
- SIEM-01.

Security logs should preserve sufficient timestamp information, including time zone context, to support accurate event correlation.

### Healthcare Application

Suppose an unauthorized login attempt occurs against a clinical application, followed by suspicious database activity.

If the application server and Oracle database use different or inaccurate system times, investigators may have difficulty determining the correct sequence of events.

Accurate timestamps help analysts reconstruct the activity.

### SOC Verification Methods

- Review configured time synchronization sources.
- Verify that systems synchronize with approved time servers.
- Compare timestamps across network devices and servers.
- Generate test events from multiple systems.
- Confirm that SIEM-01 displays the events in the correct chronological order.

**Status:** Proposed — Not Implemented

---

## AU-9: Protection of Audit Information

### Control Objective

Protect audit records and audit tools from unauthorized access, modification, and deletion.

### Proposed Implementation

The physician's office should implement safeguards to protect centralized security logs.

Recommended measures include:

- Restrict SIEM-01 administration to authorized personnel.
- Apply role-based access controls to audit information.
- Protect log transmissions using encrypted connections where supported.
- Prevent unauthorized modification or deletion of stored logs.
- Maintain protected backups or copies of important audit records.
- Monitor changes to logging configurations and audit permissions.

### Healthcare Application

An attacker who gains unauthorized access to a healthcare server may attempt to delete logs to conceal suspicious activity.

Forwarding relevant logs to a separately protected SIEM can help preserve evidence even if the affected server is compromised.

However, the SIEM itself must also be secured against unauthorized access.

### SOC Verification Methods

- Review SIEM administrative permissions.
- Verify that unauthorized accounts cannot modify or delete audit records.
- Examine log storage protections.
- Confirm that approved log transmission methods are protected.
- Test audit record access using authorized test accounts.
- Review monitoring for unauthorized logging configuration changes.

**Status:** Proposed — Not Implemented

---

## Proposed Security Monitoring Architecture

The following systems should forward relevant security events to SIEM-01.

| System | Network Location | Proposed Log Sources |
|---|---|---|
| Administrative workstations | VLAN 10 | Authentication and endpoint security events |
| Clinical workstations | VLAN 20 | Authentication and application security events |
| Application servers | VLAN 30 | Application and operating system logs |
| Oracle patient database | 10.10.30.30 | Database audit and authentication records |
| Firewalls | Network boundary | Allowed and denied traffic, security alerts |
| VPN infrastructure | Network boundary | Remote access and authentication events |
| SIEM-01 | 10.10.50.10 | Centralized collection, correlation, and alerting |

The proposed monitoring architecture supports visibility across multiple network segments while keeping security monitoring infrastructure logically separated from ordinary user systems.

---

## Example SOC Investigation Workflow

The following scenario demonstrates how the selected AU controls could support a security investigation.

### Scenario: Suspicious Authentication Activity

1. An account generates multiple failed login attempts.
2. The authentication system records the events according to the audit policy (AU-2).
3. The events are forwarded to SIEM-01 for review and correlation (AU-6).
4. Accurate timestamps help the analyst reconstruct the sequence of events (AU-8).
5. Protected audit records preserve the evidence needed for further investigation (AU-9).
6. The analyst reviews additional evidence and documents the findings.
7. If suspicious activity is confirmed, the incident is escalated according to organizational procedures.

### Expected Outcome

The organization should be able to identify suspicious authentication behavior, preserve relevant evidence, and support an investigation.

**Note:** This is a proposed investigation scenario. No live incident or test execution is claimed.

---

## Relationship to HIPAA Security Requirements

The Audit and Accountability family supports healthcare security by improving visibility into activities involving electronic protected health information (ePHI).

- **AU-2:** Defines important events that should be audited.
- **AU-6:** Supports security event review and investigation.
- **AU-8:** Provides reliable event timing.
- **AU-9:** Protects audit records against unauthorized changes.

These controls support the HIPAA Security Rule's audit control requirements and can help organizations detect and investigate potential security incidents.

However, centralized logging alone does not establish HIPAA compliance. The organization must also implement appropriate policies, procedures, access restrictions, incident response processes, and other safeguards.

---

## Future Lab Validation

During a future lab implementation, the following activities could provide practical evidence of these controls:

- Configure Windows Security Event logging and Sysmon.
- Forward Windows events to a SIEM.
- Configure approved firewall log forwarding.
- Generate test authentication failures.
- Investigate suspicious login patterns.
- Verify event timestamp consistency.
- Test restrictions on audit log access.
- Document findings with screenshots and sanitized log evidence.

These activities would help demonstrate practical SOC monitoring and investigation skills.

**Current Status:** Proposed — No validation evidence collected.

---

## References

Joint Task Force Transformation Initiative. (2013). *Security and privacy controls for federal information systems and organizations* (NIST SP 800-53 Rev. 4). National Institute of Standards and Technology. https://doi.org/10.6028/NIST.SP.800-53r4

Marron, J. (2024). *Implementing the Health Insurance Portability and Accountability Act (HIPAA) Security Rule: A cybersecurity resource guide* (NIST SP 800-66 Rev. 2). National Institute of Standards and Technology. https://doi.org/10.6028/NIST.SP.800-66r2
