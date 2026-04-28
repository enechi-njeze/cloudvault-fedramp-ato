# ssp-attachments/ — SSP Supporting Exhibits and Attachments

This folder contains all supporting exhibits, appendices, plans, policies, and procedures formally referenced within the System Security Plan (SSP) for the CloudVault Federal Health Exchange (FHX). In a real FedRAMP High engagement, every document listed below must be present, version-controlled, and consistent with the SSP body before the authorization package can be submitted to the 3PAO or the FedRAMP PMO.

> **Note:** A FedRAMP High SSP package is not a single document — it is a suite of interlinked artifacts. The attachments below represent the full complement of required and expected supporting materials. A 3PAO (CyberAudit Partners LLC) will cross-reference each attachment against the SSP narrative during assessment. Gaps or inconsistencies between the SSP and its attachments are treated as findings.

---

## Part 1 — Standard FedRAMP SSP Appendices

These are the named appendices required by the FedRAMP SSP template. Each appendix has a designated letter and a specific, non-negotiable purpose.

| Filename | Appendix | Description | Status |
|---|---|---|---|
| `appendix-a-acronyms-glossary.md` | Appendix A | Acronyms and glossary — all abbreviations used throughout the SSP defined in plain English | Planned |
| `appendix-b-related-laws-regulations.md` | Appendix B | Applicable laws, regulations, standards, and guidance documents (FISMA, HIPAA, IRS 1075, EO 14028, etc.) | Planned |
| `appendix-c-security-controls.md` | Appendix C | Control Implementation Summary (CIS) — condensed table of all 421 controls, implementation status, and responsible parties | In Progress |
| `appendix-d-control-origination.md` | Appendix D | Control origination worksheet — designates each control as CSP-provided, customer-configured, hybrid, or inherited from AWS GovCloud | Planned |
| `appendix-e-digital-identity.md` | Appendix E | Digital Identity Worksheet — NIST SP 800-63 IAL/AAL/FAL level determinations for all CloudVault FHX user types | Planned |
| `appendix-f-rules-of-behavior.md` | Appendix F | Rules of Behavior (ROB) — mandatory acceptable use agreement signed by all federal employees, contractors, and system users | Planned |
| `appendix-g-information-system-laws.md` | Appendix G | Federal information system laws and requirements specific to PHI, PII, CUI, FTI, and PCI data types | Planned |
| `appendix-h-integrated-inventory.md` | Appendix H | Integrated Inventory Workbook — complete hardware and software inventory of all components within the authorization boundary | Planned |
| `appendix-i-cryptographic-modules.md` | Appendix I | FIPS 140-2/140-3 validated cryptographic modules list — all encryption implementations with NIST validation certificate numbers | Planned |
| `appendix-j-ato-letters.md` | Appendix J | ATO letters and previous authorization decisions — cross-referenced to the authorization/ folder | Planned |
| `appendix-k-fips199-categorization.md` | Appendix K | FIPS 199 Security Categorization Worksheet — cross-referenced to assessments/fips199-security-categorization.md | Planned |
| `appendix-l-cis-worksheet.md` | Appendix L | Customer Implementation Summary — customer responsibilities for each hybrid and customer-configured control | Planned |
| `appendix-m-poam.md` | Appendix M | POA&M summary reference — cross-referenced to poam/poam-master-tracker.md | Planned |

---

## Part 2 — Required Operational Plans and Procedures

These are standalone operational documents required by FedRAMP High and NIST SP 800-53 Rev 5. Each one is a living document that must be tested, reviewed annually, and updated when the system changes. A 3PAO will request all of these during assessment and will verify that they have been exercised — not just written.

| Filename | Document | NIST Control Family | Status |
|---|---|---|---|
| `configuration-management-plan.md` | Configuration Management Plan (CMP) — governs all changes to CloudVault FHX hardware, software, firmware, and documentation | CM | Planned |
| `contingency-plan.md` | Contingency Plan (CP) / Business Continuity and Disaster Recovery Plan — RTO/RPO targets, recovery procedures, and test schedule for AWS GovCloud failover | CP | Planned |
| `incident-response-plan.md` | Incident Response Plan (IRP) — detection, analysis, containment, eradication, recovery, and post-incident procedures aligned to NIST SP 800-61 Rev 2 | IR | Planned |
| `security-awareness-training-plan.md` | Security Awareness and Training Plan — annual training schedule, role-based training requirements, and completion tracking for all 12,000+ endpoints | AT | Planned |
| `personnel-security-procedures.md` | Personnel Security Procedures — position risk designation, background check requirements, and access termination procedures | PS | Planned |
| `physical-security-procedures.md` | Physical and Environmental Protection Procedures — AWS GovCloud facility controls, visitor procedures, and environmental monitoring | PE | Planned |
| `media-protection-procedures.md` | Media Protection Procedures — media handling, sanitization (NIST SP 800-88), and transport authorization for all data at HIGH sensitivity | MP | Planned |
| `maintenance-procedures.md` | System Maintenance Procedures — scheduled and emergency maintenance windows, remote maintenance controls, and sanitization requirements | MA | Planned |
| `supply-chain-risk-management-plan.md` | Supply Chain Risk Management Plan (SCRMP) — vendor risk assessment procedures, software provenance controls, and ICT supply chain monitoring | SR | Planned |

---

## Part 3 — Individual Control Family Policies

For a FedRAMP High system, each major control family requires a dedicated, standalone policy document. Policies must be approved by the CISO (Angela Torres), distributed to all applicable personnel, and reviewed at least annually. The 3PAO verifies policy existence, currency, and distribution as part of the assessment.

| Filename | Policy | Control Family | Status |
|---|---|---|---|
| `policy-access-control.md` | Access Control Policy and Procedures | AC | Planned |
| `policy-awareness-training.md` | Awareness and Training Policy and Procedures | AT | Planned |
| `policy-audit-accountability.md` | Audit and Accountability Policy and Procedures | AU | Planned |
| `policy-assessment-authorization.md` | Assessment, Authorization, and Monitoring Policy | CA | Planned |
| `policy-configuration-management.md` | Configuration Management Policy and Procedures | CM | Planned |
| `policy-contingency-planning.md` | Contingency Planning Policy and Procedures | CP | Planned |
| `policy-identification-authentication.md` | Identification and Authentication Policy and Procedures | IA | Planned |
| `policy-incident-response.md` | Incident Response Policy and Procedures | IR | Planned |
| `policy-maintenance.md` | Maintenance Policy and Procedures | MA | Planned |
| `policy-media-protection.md` | Media Protection Policy and Procedures | MP | Planned |
| `policy-physical-environmental.md` | Physical and Environmental Protection Policy | PE | Planned |
| `policy-planning.md` | Planning Policy and Procedures | PL | Planned |
| `policy-program-management.md` | Information Security Program Management Policy | PM | Planned |
| `policy-personnel-security.md` | Personnel Security Policy and Procedures | PS | Planned |
| `policy-pii-processing.md` | PII Processing and Transparency Policy | PT | Planned |
| `policy-risk-assessment.md` | Risk Assessment Policy and Procedures | RA | Planned |
| `policy-system-acquisition.md` | System and Services Acquisition Policy | SA | Planned |
| `policy-system-communications.md` | System and Communications Protection Policy | SC | Planned |
| `policy-system-integrity.md` | System and Information Integrity Policy | SI | Planned |
| `policy-supply-chain.md` | Supply Chain Risk Management Policy | SR | Planned |

---

## Part 4 — Privacy and Interconnection Documents

| Filename | Document | Description | Status |
|---|---|---|---|
| `privacy-threshold-analysis.md` | Privacy Threshold Analysis (PTA) | Initial assessment of whether a Privacy Impact Assessment (PIA) is required given PHI/PII data types | Planned |
| `privacy-impact-assessment.md` | Privacy Impact Assessment (PIA) | Full PIA — required because CloudVault FHX processes PHI, PII, FTI, and PCI at HIGH sensitivity | Planned |
| `interconnection-security-agreements.md` | Interconnection Security Agreements (ISAs) | Formal ISAs governing data exchanges with all 47 connected federal health agencies | Planned |
| `memoranda-of-understanding.md` | Memoranda of Understanding (MOUs) | MOUs with external system owners and data providers | Planned |
| `system-conops.md` | System Concept of Operations (CONOPS) | Operational narrative describing how CloudVault FHX functions in its federal health exchange mission context | Planned |

---

## Attachment Completeness Summary

| Category | Documents | Status |
|---|---|---|
| Standard FedRAMP Appendices (A–M) | 13 | Planned / In Progress |
| Operational Plans and Procedures | 9 | Planned |
| Individual Control Family Policies (all 20 families) | 20 | Planned |
| Privacy and Interconnection Documents | 5 | Planned |
| **Total** | **47** | **In Progress** |

---

> In a real FedRAMP High engagement, the SSP attachment package alone runs to hundreds of pages across dozens of documents. The completeness, currency, and internal consistency of these attachments are what distinguish a submission-ready authorization package from one that will be returned with deficiencies.

---

*Part of the CloudVault FHX GRC Portfolio | cloudvault-fedramp-ato*
