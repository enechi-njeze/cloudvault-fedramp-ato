# poam/ -- Plan of Action and Milestones

This folder contains the Plan of Action and Milestones (POA&M) package for the CloudVault Federal Health Exchange (FHX). The POA&M is a FISMA-mandated document that tracks every open security weakness identified during the authorization process and specifies who is responsible for fixing it, how it will be fixed, and by when.

---

## POA&M Artifact Package

This folder provides the complete POA&M artifact package in three formats, mirroring real federal engagement practice where the same tracking data is maintained in multiple formats for different stakeholder audiences.

| File | Format | Description | Audience |
|---|---|---|---|
| [poam-master-tracker.md](./poam-master-tracker.md) | Markdown | Authoritative master tracker with full narrative context, compensating controls register, and milestone history | GitHub review, hiring managers, portfolio display |
| [CV-FHX-POAM-Master-Tracker.xlsx](./CV-FHX-POAM-Master-Tracker.xlsx) | Excel Workbook | Structured spreadsheet tracker formatted for real-world ISSO and AO working sessions, sortable by risk level, due date, and system owner | AO briefings, ISSO daily tracking, ConMon reporting |
| [CV-FHX-POAM-Master-Tracker (1).docx](./CV-FHX-POAM-Master-Tracker%20(1).docx) | Word Document | Formatted document version suitable for formal submission, printing, and inclusion in authorization packages | 3PAO review, agency reporting, formal ATO packages |

> In a real federal engagement, the POA&M is typically maintained in a combination of a live spreadsheet (updated weekly by the ISSO), a formatted document (submitted monthly to the AO), and a system-of-record entry in a GRC tool such as Xacta 360, CSAM, or eMASS. This artifact package demonstrates proficiency across all three formats.

---

## POA&M Summary (as of March 2026 Reporting Period)

| Risk Level | Open Items | Overdue | Closed This Period |
|---|---|---|---|
| Critical | 1 | 0 | 0 |
| High | 3 | 1 | 1 |
| Moderate | 6 | 2 | 2 |
| Low | 4 | 0 | 0 |
| **Total** | **14** | **3** | **3** |

**Overall Risk Posture:** ACCEPTABLE  
**Next Scheduled Review:** April 30, 2026  
**ISSO:** Enechi P.C. Njeze, CGRC, CISA, CISM  

---

## How to Read This POA&M

Each POA&M item is identified by a unique tracking ID (format: CV-FHX-POAM-YYYY-NNN) and contains the following fields, consistent with FedRAMP POA&M requirements and NIST SP 800-53A Rev 5 guidance:

- **POA&M ID:** Unique identifier for lifecycle tracking
- **Finding Source:** Vulnerability scan, penetration test, self-assessment, or audit
- **Control ID:** NIST SP 800-53 Rev 5 control family and control number
- **Weakness Description:** Plain-language summary of the identified gap
- **Risk Level:** Critical / High / Moderate / Low (aligned with FIPS 199 impact categories)
- **Asset Affected:** Specific system component, boundary, or data flow
- **Scheduled Completion Date:** Committed remediation milestone
- **Responsible Individual:** Named federal or contractor POC accountable for remediation
- **Status:** Open / In Progress / Closed / Risk Accepted / Compensating Control Applied
- **Compensating Control:** Interim mitigation measure active while permanent fix is implemented

---

## Key POA&M Items (Selected High-Priority)

| POA&M ID | Control | Weakness | Due Date | Status |
|---|---|---|---|---|
| CV-FHX-POAM-2026-001 | SI-2 | Critical unpatched CVEs on application servers | 2026-03-31 | In Progress |
| CV-FHX-POAM-2026-002 | AC-2 | Orphaned privileged accounts from prior contractor engagement | 2026-04-15 | In Progress |
| CV-FHX-POAM-2026-003 | SC-28 | S3 bucket encryption gap for legacy data migration objects | 2026-05-01 | In Progress |
| CV-FHX-POAM-2026-004 | AU-9 | Audit log integrity controls not fully implemented | 2026-04-30 | In Progress |

---

## Related Documents

- [POA&M Master Tracker (Markdown)](./poam-master-tracker.md) -- full detail with compensating controls
- [ConMon Monthly Report (March 2026)](../conmon/conmon-monthly-report-template.md) -- monthly risk posture summary referencing this POA&M
- [Security Assessment Plan](../assessments/security-assessment-plan.md) -- findings that originated POA&M items
- [System Security Plan](../docs/system-security-plan.md) -- authoritative system description

---

## Regulatory and Policy Basis

This POA&M package was developed in accordance with the following authorities:

- FISMA (44 U.S.C. Chapter 35) -- mandates POA&M maintenance for all federal information systems
- OMB Memorandum M-14-03 -- requires quarterly POA&M reporting to agency CIO
- FedRAMP POA&M Template v3.1 -- format and field requirements for cloud systems
- NIST SP 800-53 Rev 5, CA-5 -- Plan of Action and Milestones control requirement
- NIST SP 800-37 Rev 2 -- RMF Step 4 (Assess) and Step 5 (Authorize) POA&M obligations
- FedRAMP Continuous Monitoring Strategy Guide -- ConMon POA&M update cadence

---

*Maintained by Enechi P.C. Njeze, ISSO / ISSM, CloudVault FHX Program*  
*CGRC | CISA | CISM | PMP | PMI-RMP | CompTIA Security+ SY0-701 | CHP | CSCS*  
*Federal Health Data Office (FHDO) -- Cybersecurity Division*  
*Last Updated: March 31, 2026*
