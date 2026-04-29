# Authorization to Operate (ATO) Letter
## CloudVault Federal Health Exchange (FHX)
### FedRAMP High Agency Authorization

---

**OFFICIAL AUTHORIZATION DOCUMENT**
**Federal Health Data Office (FHDO)**
**Office of the Deputy Director**
**Washington, D.C. 20201**

---

**ATO Reference Number:** ATO-FHDO-2025-001
**Date of Issuance:** February 14, 2025
**Authorization Type:** Agency Authorization to Operate (ATO)
**Impact Level:** HIGH (Confidentiality: HIGH / Integrity: HIGH / Availability: HIGH)
**Authorization Period:** February 14, 2025 through February 13, 2028 (Three Years)

---

## Authorization Decision

This letter constitutes the official Authorization to Operate (ATO) issued by the Federal Health Data Office (FHDO) Authorizing Official for the CloudVault Federal Health Exchange (FHX), operated by CloudVault Technologies, Inc.

Pursuant to the Federal Information Security Modernization Act of 2014 (FISMA, 44 U.S.C. Chapter 35), Office of Management and Budget (OMB) Circular A-130, "Managing Information as a Strategic Resource," and the FedRAMP Authorization Act (44 U.S.C. Chapter 37), I, Henry Kline, Deputy Director, Federal Health Data Office, hereby authorize the operation of the CloudVault Federal Health Exchange (FHX) at the HIGH impact level for a period of three (3) years from the date of this letter, subject to the conditions set forth herein.

---

## System Identification

| Field | Value |
|---|---|
| System Name | CloudVault Federal Health Exchange (FHX) |
| System Abbreviation | CV-FHX |
| Cloud Service Provider (CSP) | CloudVault Technologies, Inc. |
| Cloud Service Offering (CSO) | CloudVault FHX -- Federal Health Data Platform |
| Deployment Model | Government Community Cloud (AWS GovCloud) |
| Service Model | Software as a Service (SaaS) |
| System Owner | Dr. Sandra M. Okafor, Deputy Assistant Secretary for Health Informatics |
| ISSO / ISSM | Enechi P.C. Njeze, CGRC, CISA, CISM |
| Authorization Boundary | AWS GovCloud (US-East primary, US-West DR), as defined in SSP v1.0 |
| FIPS 199 Categorization | HIGH (C:HIGH / I:HIGH / A:HIGH) |
| Data Types | PHI, PII, CUI, FTI, PCI |
| Active User Population | 47 federal agencies, approximately 890,000 beneficiaries |

---

## Basis for Authorization

This authorization is based on a comprehensive review and acceptance of the following authorization package artifacts, all of which were reviewed by the FHDO Authorizing Official and found to be complete, accurate, and sufficient to support this authorization decision:

| Artifact | Document ID | Version | Date |
|---|---|---|---|
| System Security Plan (SSP) | CV-FHX-SSP-2025-001 | 1.0 | January 24, 2025 |
| FIPS 199 Security Categorization | CV-FHX-FIPS199-2024-001 | 1.0 | October 15, 2024 |
| Security Assessment Plan (SAP) | CV-FHX-SAP-2024-001 | 1.0 | October 28, 2024 |
| Security Assessment Report (SAR) | CV-FHX-SAR-2025-001 | 1.0 | January 31, 2025 |
| Plan of Action and Milestones (POA&M) | CV-FHX-POAM-2025-001 | 1.0 | February 3, 2025 |
| Privacy Impact Assessment (PIA) | CV-FHX-PIA-2024-001 | 1.0 | November 20, 2024 |
| System of Records Notice (SORN) | FHDO-SORN-2024-003 | 1.0 | December 10, 2024 |
| Interconnection Security Agreements (ISAs) | Multiple (see SSP Attachment 6) | Current | January 15, 2025 |
| Rules of Behavior (RoB) | CV-FHX-ROB-2025-001 | 1.0 | January 10, 2025 |

The Security Assessment Report (SAR) was prepared by ClearPath Security Assessors LLC (A2LA Accreditation No. FR2024-3PAO-0047), an accredited Third Party Assessment Organization (3PAO) independent of CloudVault Technologies, Inc. The 3PAO assessed all 421 controls in the FedRAMP High baseline and issued an authorization recommendation of: **AUTHORIZATION RECOMMENDED**.

---

## Assessment Findings Summary

The independent assessment identified 50 findings. Prior to this authorization, 36 findings were remediated and verified closed by the 3PAO. The remaining 14 findings have been accepted into the Plan of Action and Milestones (POA&M) and are subject to the remediation conditions set forth in Section 6 of this letter.

| Risk Level | Total Found | Remediated Pre-ATO | Open (POA&M) |
|---|---|---|---|
| Critical | 2 | 2 | 0 |
| High | 8 | 6 | 2 |
| Moderate | 18 | 13 | 5 |
| Low | 22 | 15 | 7 |
| **Total** | **50** | **36** | **14** |

The Authorizing Official has reviewed the residual risk associated with all 14 open POA&M items and determined that the residual risk is ACCEPTABLE for mission operations.

**Overall Risk Acceptance Statement:** The residual risk associated with operating CloudVault Federal Health Exchange (FHX) under this authorization is determined to be LOW TO MODERATE and is ACCEPTABLE given the operational necessity of the system, the effectiveness of compensating controls for all open High findings, and the demonstrated remediation trajectory of the CloudVault FHX security team.

---

## Authorization Conditions

This ATO is granted subject to the following mandatory conditions. Failure to comply with any condition may result in suspension or revocation of this authorization at the discretion of the Authorizing Official.

### Condition 1: POA&M Remediation Timelines

All open POA&M items must be remediated within the following timeframes, measured from the date of this letter:

- **High risk findings:** Closed within 90 days (by May 15, 2025)
- **Moderate risk findings:** Closed within 180 days (by August 13, 2025)
- **Low risk findings:** Closed within 365 days (by February 14, 2026)

Failure to close High risk findings within 90 days will trigger an immediate review by the Authorizing Official and may result in an authorization suspension pending remediation.

### Condition 2: Continuous Monitoring Reporting

The ISSO must submit monthly Continuous Monitoring (ConMon) reports to the Authorizing Official no later than the 5th business day of each calendar month, covering the prior month's security posture. Each ConMon report must include:

- Updated POA&M with current status of all open items
- Results of monthly vulnerability scans
- Summary of any security incidents or significant changes
- ISSO certification of risk posture (ACCEPTABLE / ELEVATED / UNACCEPTABLE)

### Condition 3: Significant Change Notification

Any significant change to the CloudVault FHX authorization boundary, architecture, or data types must be reported to the FHDO SAISO and Authorizing Official prior to implementation via the FedRAMP Significant Change Notification (SCN) process. Examples of significant changes include the addition of new cloud services, expansion to new geographic regions, changes to data interconnections, or material changes to authentication infrastructure.

### Condition 4: Annual Assessment

An annual security assessment of a defined control subset, consistent with FedRAMP Continuous Monitoring Strategy Guide requirements, must be conducted by ClearPath Security Assessors LLC (or another A2LA-accredited 3PAO) within 365 days of this authorization and annually thereafter. Annual assessment results must be provided to the Authorizing Official within 60 days of assessment completion.

### Condition 5: Annual Penetration Test

An annual penetration test, consistent with FedRAMP High penetration testing guidance, must be conducted by an appropriately qualified independent testing team within 365 days of this authorization and annually thereafter. Penetration test results must be incorporated into the POA&M within 30 days of receipt.

### Condition 6: Incident Reporting

All security incidents affecting CloudVault FHX must be reported to the FHDO SAISO and US-CERT within the timeframes specified in NIST SP 800-61 Rev 2 and FedRAMP Incident Communications Procedures. PHI breach incidents must additionally be reported in accordance with HIPAA Breach Notification Rule requirements (45 CFR Part 164 Subpart D) and the FHDO Privacy Officer must be notified within 1 hour of breach identification.

### Condition 7: JAB P-ATO Coordination

CloudVault Technologies, Inc. has submitted a formal JAB Prioritization Request (CV-FHX-JAB-PR-2026-001) for JAB P-ATO consideration. FHDO supports this prioritization request. CloudVault Technologies, Inc. must notify FHDO of any material changes to the JAB submission and must provide FHDO with a copy of any JAB reviewer findings or requests for clarification within 5 business days of receipt.

---

## Authorization Scope and Limitations

### In Scope

This authorization covers all system components within the CloudVault FHX authorization boundary as defined in the System Security Plan (SSP) v1.0, Section 2, including all production and disaster recovery infrastructure in AWS GovCloud (US-East and US-West), all data processed within the boundary, and all personnel with authorized access to the system.

### Out of Scope

This authorization does not cover: AWS managed infrastructure below the virtualization layer (covered by AWS GovCloud Agency ATO); FHDO agency end-user workstations and local area networks (covered by FHDO enterprise authorization); third-party SaaS integrations not within the CloudVault FHX boundary; or any future system components added without prior Significant Change Notification approval.

### Reciprocity

FHDO encourages other federal agencies with a mission need for CloudVault FHX services to leverage this authorization through reciprocity in accordance with OMB Memorandum M-11-11 and FedRAMP reciprocity guidance, pending the grant of a JAB P-ATO. Agencies seeking to use this authorization for reciprocity should contact the FHDO SAISO to obtain a copy of the authorization package.

---

## Authorization Review and Renewal

This authorization expires on **February 13, 2028**, unless revoked earlier or renewed. No later than 180 days prior to expiration (by August 17, 2027), the ISSO must initiate the reauthorization process, including scheduling a full 3PAO assessment and preparing an updated authorization package for Authorizing Official review.

The Authorizing Official may review and reassess this authorization at any time based on: material changes to the system, significant increases in threat activity, findings from Inspector General or GAO reviews, unacceptable ConMon risk posture, or failure to comply with any authorization condition.

---

## Authorizing Official Signature

The undersigned, as the designated Authorizing Official for the Federal Health Data Office, hereby grants this Authorization to Operate to CloudVault Federal Health Exchange (FHX) effective February 14, 2025.

---

**Henry Kline**
Deputy Director
Federal Health Data Office (FHDO)
U.S. Department of Health and Human Services
Washington, D.C. 20201
Date: February 14, 2025

---

## ISSO and System Owner Acknowledgment

The undersigned acknowledge receipt of this Authorization to Operate and accept responsibility for maintaining the security posture of CloudVault Federal Health Exchange (FHX) in accordance with all conditions set forth herein.

---

**Enechi P.C. Njeze**
Information System Security Officer (ISSO) / Information System Security Manager (ISSM)
CGRC | CISA | CISM | PMP | PMI-RMP | CompTIA Security+ SY0-701 | CHP | CSCS
Federal Health Data Office (FHDO) -- Cybersecurity Division
Date: February 14, 2025

---

**Dr. Sandra M. Okafor**
System Owner, Deputy Assistant Secretary for Health Informatics
Federal Health Data Office (FHDO)
Date: February 14, 2025

---

## Related Authorization Documents

| Document | Location |
|---|---|
| System Security Plan (SSP) v1.0 | [docs/system-security-plan.md](../docs/system-security-plan.md) |
| FIPS 199 Security Categorization | [assessments/fips199-security-categorization.md](../assessments/fips199-security-categorization.md) |
| Security Assessment Plan (SAP) | [assessments/security-assessment-plan.md](../assessments/security-assessment-plan.md) |
| Security Assessment Report (SAR) | [assessments/security-assessment-report.md](../assessments/security-assessment-report.md) |
| POA&M Master Tracker | [poam/poam-master-tracker.md](../poam/poam-master-tracker.md) |
| ConMon Monthly Report | [conmon/conmon-monthly-report-template.md](../conmon/conmon-monthly-report-template.md) |
| JAB Prioritization Request | [jab-path/jab-prioritization-request.md](../jab-path/jab-prioritization-request.md) |

---

*ATO Reference: ATO-FHDO-2025-001 | Issued: February 14, 2025 | Expires: February 13, 2028*
*Federal Health Data Office (FHDO) | Office of the Deputy Director | Washington, D.C. 20201*
*Maintained by: Enechi P.C. Njeze, ISSO/ISSM, CGRC, CISA, CISM*
