# SSP Attachment Index
## CloudVault Federal Health Exchange (FHX)
### System Security Plan -- Required Attachments Register

---

**Document Control**

| Field | Value |
|---|---|
| Document ID | CV-FHX-SSP-ATT-2025-001 |
| Version | 1.3 |
| Last Updated | March 31, 2026 |
| Maintained By | Enechi P.C. Njeze, ISSO/ISSM, CGRC, CISA, CISM |
| Parent Document | System Security Plan (SSP) v1.0 -- [docs/system-security-plan.md](../docs/system-security-plan.md) |
| FedRAMP Template Reference | FedRAMP SSP Template v2.1 (High Baseline) |

---

## 1. Purpose

The FedRAMP SSP template requires 12 standard attachments plus any agency-specific addenda. This index catalogs all required SSP attachments for CloudVault Federal Health Exchange (FHX), documents their completion status, identifies where each attachment is maintained, and cross-references the SSP sections and NIST SP 800-53 Rev 5 control families that each attachment supports.

In a production engagement, these attachments are delivered as separate documents alongside the SSP proper, packaged as a complete authorization package. For this portfolio, the major attachments are represented either as full documents in this repository or as detailed index entries demonstrating knowledge of what each attachment must contain.

---

## 2. SSP Attachment Register

### Attachment 1: Information System Architecture Diagrams

| Field | Value |
|---|---|
| Attachment ID | SSP-ATT-01 |
| FedRAMP Template Reference | SSP Attachment 1 |
| Status | Complete |
| Location | [diagrams/system-architecture-diagram.md](../diagrams/system-architecture-diagram.md) |
| Last Updated | March 15, 2026 (v1.2) |
| Controls Supported | PL-2, SA-17, SC-7, AC-4, CP-2 |

**Description:** Architecture diagrams depicting the CloudVault FHX authorization boundary, network topology, data flows, and component relationships. Includes high-level boundary diagram, three-tier VPC segmentation diagram, three data flow diagrams (agency exchange, beneficiary portal, privileged access), and disaster recovery architecture. In a production submission, this attachment would include Visio or Lucidchart exports in addition to the text-based diagrams.

**Required Contents per FedRAMP Guidance:**
- Authorization boundary diagram (clearly showing what is in scope vs. out of scope)
- Network diagram showing interconnections, VPCs, subnets, and routing
- Data flow diagram(s) showing how federal data enters, traverses, and exits the system
- Diagram version history and change log

---

### Attachment 2: Privacy Impact Assessment (PIA)

| Field | Value |
|---|---|
| Attachment ID | SSP-ATT-02 |
| FedRAMP Template Reference | SSP Attachment 2 |
| Status | Complete (external document) |
| Document ID | CV-FHX-PIA-2024-001 |
| Completed Date | November 20, 2024 |
| Author | Dr. Angela M. Reeves, Chief Privacy Officer, FHDO |
| Controls Supported | PT-1 through PT-8, PM-20, PM-21, RA-3 |

**Description:** The Privacy Impact Assessment (PIA) documents the privacy risks associated with CloudVault FHX's collection, use, maintenance, and dissemination of PII for approximately 890,000 beneficiaries across 47 federal agencies. The PIA was completed by the FHDO Chief Privacy Officer in accordance with the E-Government Act of 2002 (Section 208), OMB Memorandum M-03-22, and OMB Circular A-130, Appendix II.

**Key PIA Findings:**
- PII collected: name, date of birth, SSN (eligibility use only), address, health record identifiers, insurance information, FTI elements
- Identified privacy risks: data re-identification risk from combined datasets, unauthorized access by agency personnel, third-party sharing risk
- All risks mitigated by data minimization policy, RBAC, audit logging, ISA requirements, and data use agreements
- Privacy risk rating: MODERATE (residual, after mitigations)
- PIA published at FHDO.gov public website as required by E-Government Act

---

### Attachment 3: Rules of Behavior (RoB)

| Field | Value |
|---|---|
| Attachment ID | SSP-ATT-03 |
| FedRAMP Template Reference | SSP Attachment 3 |
| Status | Complete (external document) |
| Document ID | CV-FHX-ROB-2025-001 |
| Completed Date | January 10, 2025 |
| Review Cycle | Annual (next review: January 2026) |
| Controls Supported | PL-4, PS-6, AC-17, AT-2 |

**Description:** The Rules of Behavior document establishes the conditions and responsibilities that all users must acknowledge and accept prior to being granted access to CloudVault FHX. All 1,847 authorized users must sign the RoB annually.

**Key RoB Requirements:**
- Users may only access data within their assigned agency scope and authorized role
- PHI and PII must not be downloaded to non-approved endpoints
- Sharing of credentials is prohibited; each user must maintain a unique account
- Security incidents must be reported to the ISSO within 1 hour of identification
- Violations may result in access revocation, disciplinary action, and referral for prosecution under 18 U.S.C. § 641
- Annual reacknowledgment required; non-compliant accounts suspended

**Current Compliance:** 1,847 of 1,847 active users have current signed RoB on file (100% as of March 31, 2026).

---

### Attachment 4: Information System Contingency Plan (ISCP)

| Field | Value |
|---|---|
| Attachment ID | SSP-ATT-04 |
| FedRAMP Template Reference | SSP Attachment 4 |
| Status | Complete (external document) |
| Document ID | CV-FHX-ISCP-2025-001 |
| Completed Date | January 15, 2025 |
| Last Tested | December 12, 2025 (full DR failover test) |
| Controls Supported | CP-1 through CP-13 |

**Description:** The ISCP establishes procedures for recovering CloudVault FHX following a disruption. Recovery objectives are RTO: 4 hours, RPO: 1 hour, MTD: 8 hours.

**Test History:**

| Test Type | Date | Result | RTO Achieved | RPO Achieved |
|---|---|---|---|---|
| Tabletop Exercise | June 15, 2025 | Pass | N/A | N/A |
| Full DR Failover Test | December 12, 2025 | Pass | 3h 42m | 47 min |

---

### Attachment 5: Configuration Management Plan (CMP)

| Field | Value |
|---|---|
| Attachment ID | SSP-ATT-05 |
| FedRAMP Template Reference | SSP Attachment 5 |
| Status | Complete (external document) |
| Document ID | CV-FHX-CMP-2025-001 |
| Completed Date | January 12, 2025 |
| Controls Supported | CM-1 through CM-11, SA-10 |

**Description:** The CMP governs how CloudVault FHX components are configured, changed, and maintained. Establishes the Configuration Control Board (CCB), change approval workflow, configuration baseline documentation, and the SCN submission process.

**Key CMP Elements:**
- All infrastructure defined as code (Terraform, CloudFormation) under version control
- Configuration baselines: DISA STIG (EC2), CIS Benchmark Level 2 (containers), AWS FSBP (AWS services)
- All production changes require CCB approval, automated pipeline validation, and post-deployment configuration scan
- SCN criteria: new AWS services, new interconnections, geographic expansion, authentication infrastructure changes
- Baseline deviation process: documented exception, ISSO approval, compensating control, scheduled remediation

---

### Attachment 6: Interconnection Security Agreements (ISAs)

| Field | Value |
|---|---|
| Attachment ID | SSP-ATT-06 |
| FedRAMP Template Reference | SSP Attachment 6 |
| Status | Complete (6 active ISAs) |
| Controls Supported | CA-3, SC-7, AC-4, MA-4 |

**Active ISAs:**

| ISA Reference | Connecting System | Owner | Connection Type | Data Types | Executed |
|---|---|---|---|---|---|
| ISA-001 | FHDO Agency Network | FHDO | AWS Direct Connect (10 Gbps) | PHI, PII, CUI | 2025-01-15 |
| ISA-002 | VA Health Information Network | Dept. of Veterans Affairs | AWS Direct Connect (1 Gbps) | PHI, PII | 2025-01-15 |
| ISA-003 | IHS Data Exchange Hub | Indian Health Service | AWS Direct Connect (1 Gbps) | PHI, PII | 2025-01-15 |
| ISA-004 | IRS FTI Exchange | Internal Revenue Service | SFTP/MPLS dedicated circuit | FTI only | 2025-01-15 |
| ISA-005 | Okta Federal IDP | Okta, Inc. (FedRAMP Authorized) | AWS PrivateLink | Auth tokens | 2025-01-15 |
| ISA-006 | CyberArk PAM | CyberArk Software (FedRAMP Authorized) | AWS PrivateLink | Privileged session data | 2025-01-15 |

---

### Attachment 7: Incident Response Plan (IRP)

| Field | Value |
|---|---|
| Attachment ID | SSP-ATT-07 |
| FedRAMP Template Reference | SSP Attachment 7 |
| Status | Complete (external document) |
| Document ID | CV-FHX-IRP-2025-001 |
| Completed Date | January 14, 2025 |
| Controls Supported | IR-1 through IR-10 |

**Notification Timelines:**
- Any security incident: ISSO notified within 1 hour of detection
- US-CERT reportable: reported within 1 hour of determination (FedRAMP ICP)
- PHI breach: FHDO Privacy Officer within 1 hour; HIPAA 60-day external clock starts
- AO notification: within 8 hours of confirmed significant incident

**Performance (18 months):** 11 incidents handled, 11 resolved within SLA, 0 PHI/PII breaches.

---

### Attachment 8: Control Implementation Summary (CIS) Tables

| Field | Value |
|---|---|
| Attachment ID | SSP-ATT-08 |
| FedRAMP Template Reference | SSP Attachment 8 |
| Status | Complete (integrated into SSP) |
| Location | [docs/system-security-plan.md](../docs/system-security-plan.md) |
| Controls Supported | All 421 FedRAMP High controls |

**Description:** CIS tables document how each of the 421 FedRAMP High baseline controls is implemented, the responsible party (CSP, Agency, or Shared), implementation status, and the system components satisfying each control. Integrated directly into the SSP for this portfolio.

---

### Attachment 9: Separation of Duties Matrix

| Field | Value |
|---|---|
| Attachment ID | SSP-ATT-09 |
| FedRAMP Template Reference | SSP Attachment 9 |
| Status | Complete (external document) |
| Document ID | CV-FHX-SOD-2025-001 |
| Completed Date | January 8, 2025 |
| Controls Supported | AC-5, AC-6, PS-2 |

**Key SOD Controls:**

| Conflicting Functions | Separation Mechanism | Enforcement |
|---|---|---|
| Code development vs. production deployment approval | No developer has production deployment approval rights | IAM Identity Center role policy |
| Security administration vs. system administration | ISSO cannot modify production configs; Cloud Ops cannot modify security policies without ISSO co-approval | IAM policy, CyberArk workflow |
| Audit log access vs. system operation | Audit log access restricted to ISSO and SAISO; Cloud Ops cannot delete audit logs | S3 bucket policy, IAM policy |
| PHI access vs. audit function | Agency personnel cannot view audit logs for their own sessions | RBAC policy, AU-9 |
| Financial processing vs. payment approval | PCI dual authorization required for transactions above threshold | Application-layer workflow |

---

### Attachment 10: Laws, Regulations, and Standards

| Field | Value |
|---|---|
| Attachment ID | SSP-ATT-10 |
| Status | Complete (integrated into SSP) |
| Controls Supported | PL-2, CA-2, PM-9 |

**Applicable Authorities:**

| Authority | Applicability |
|---|---|
| FISMA 2014 (44 U.S.C. Chapter 35) | Full system |
| FedRAMP Authorization Act (44 U.S.C. Chapter 37) | Full system |
| HIPAA Security Rule (45 CFR Part 164 Subpart C) | All PHI processing |
| HIPAA Privacy Rule (45 CFR Part 164 Subpart E) | All PHI processing |
| HITECH Act | PHI breach notification |
| Privacy Act of 1974 (5 U.S.C. § 552a) | All PII processing |
| E-Government Act of 2002, Section 208 | PII collection (PIA) |
| IRS Publication 1075 | FTI processing |
| 21st Century Cures Act (P.L. 114-255) | Interoperability |
| PCI DSS v4.0 | Copayment processing |
| OMB Circular A-130 | Full system |
| NIST SP 800-53 Rev 5 | All 421 controls |
| NIST SP 800-63-3 | Authentication (IAL2/AAL2) |
| NIST SP 800-171 Rev 3 | CUI handling |

---

### Attachment 11: Acronyms and Definitions

| Field | Value |
|---|---|
| Attachment ID | SSP-ATT-11 |
| Status | Complete (external document CV-FHX-ACRO-2025-001) |
| Controls Supported | N/A (reference document) |

Selected key acronyms: AO (Authorizing Official), ATO (Authorization to Operate), ConMon (Continuous Monitoring), CUI (Controlled Unclassified Information), FTI (Federal Tax Information), ISSO (Information System Security Officer), ISSM (Information System Security Manager), JAB (Joint Authorization Board), P-ATO (Provisional ATO), PHI (Protected Health Information), PII (Personally Identifiable Information), POA&M (Plan of Action and Milestones), RBAC (Role-Based Access Control), SAP (Security Assessment Plan), SAR (Security Assessment Report), SAISO (Senior Agency Information Security Officer), SCN (Significant Change Notification), SSP (System Security Plan), 3PAO (Third Party Assessment Organization).

---

### Attachment 12: Hardware and Software Inventory (CMDB)

| Field | Value |
|---|---|
| Attachment ID | SSP-ATT-12 |
| FedRAMP Template Reference | SSP Attachment 12 |
| Status | Complete (living document) |
| Document ID | CV-FHX-CMDB-2025-001 |
| Last Reconciled | March 28, 2026 |
| Controls Supported | CM-8, CM-8(1), CM-8(2), CM-8(3) |

**Inventory Summary (March 28, 2026):**

| Category | Count | Notes |
|---|---|---|
| EC2 Instances (production) | 64 | Auto-scaling baseline; full list in CMDB |
| EC2 Instances (non-production) | 22 | Network-isolated dev/test |
| ECS Services | 16 | SBOM maintained per image |
| Lambda Functions | 34 | Version-pinned deployments |
| RDS Instances | 4 | PostgreSQL 15.4, patch-current |
| DynamoDB Tables | 12 | Managed service |
| S3 Buckets | 147 | Full manifest in CMDB |
| Third-Party Software Components | 312 | SBOM via Syft, quarterly review |
| Open Source Components | 189 | CVE tracking via Dependabot + Tenable |
| Commercial Software Licenses | 23 | All current; vendor security assessments on file |

**SBOM:** Generated automatically with each CI/CD pipeline run in SPDX 2.3 format, retained 3 years per NIST SP 800-161 Rev 1.

---

## 3. Attachment Completion Status Summary

| Attachment | Title | Status | Location |
|---|---|---|---|
| SSP-ATT-01 | Architecture Diagrams | Complete | [diagrams/system-architecture-diagram.md](../diagrams/system-architecture-diagram.md) |
| SSP-ATT-02 | Privacy Impact Assessment | Complete | External (CV-FHX-PIA-2024-001) |
| SSP-ATT-03 | Rules of Behavior | Complete | External (CV-FHX-ROB-2025-001) |
| SSP-ATT-04 | Contingency Plan | Complete | External (CV-FHX-ISCP-2025-001) |
| SSP-ATT-05 | Configuration Management Plan | Complete | External (CV-FHX-CMP-2025-001) |
| SSP-ATT-06 | Interconnection Security Agreements | Complete (6 ISAs) | External -- listed above |
| SSP-ATT-07 | Incident Response Plan | Complete | External (CV-FHX-IRP-2025-001) |
| SSP-ATT-08 | Control Implementation Summary | Complete | [docs/system-security-plan.md](../docs/system-security-plan.md) |
| SSP-ATT-09 | Separation of Duties Matrix | Complete | External (CV-FHX-SOD-2025-001) |
| SSP-ATT-10 | Laws, Regulations, Standards | Complete | Integrated into SSP |
| SSP-ATT-11 | Acronyms and Definitions | Complete | External (CV-FHX-ACRO-2025-001) |
| SSP-ATT-12 | Hardware/Software Inventory (CMDB) | Complete (living) | External CMDB (CV-FHX-CMDB-2025-001) |

**All 12 required SSP attachments: COMPLETE**

---

## 4. ISSO Certification

I certify that all 12 required FedRAMP SSP attachments for CloudVault Federal Health Exchange (FHX) have been completed, are accurate as of the date below, and are maintained in accordance with the FedRAMP SSP template requirements and applicable NIST SP 800-53 Rev 5 controls.

---

**Enechi P.C. Njeze**
Information System Security Officer (ISSO) / Information System Security Manager (ISSM)
CGRC | CISA | CISM | PMP | PMI-RMP | CompTIA Security+ SY0-701 | CHP | CSCS
Federal Health Data Office (FHDO) -- Cybersecurity Division
Date: March 31, 2026

---

*Document ID: CV-FHX-SSP-ATT-2025-001 v1.3*
*Maintained by: Enechi P.C. Njeze, ISSO/ISSM, CGRC, CISA, CISM*
*Federal Health Data Office (FHDO) -- Cybersecurity Division | Last Updated: March 31, 2026*
