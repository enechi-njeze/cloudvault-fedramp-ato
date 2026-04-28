# FIPS 199 Security Categorization

**CloudVault Federal Health Exchange (FHX)**
**Document ID:** CV-FHX-FIPS199-001
**Version:** 1.0
**Classification:** UNCLASSIFIED // FOR OFFICIAL USE ONLY (FOUO)
**Prepared By:** Enechi P.C. Njeze, Information System Security Officer (ISSO) and Information System Security Manager (ISSM)
**Reviewed By:** Henry Kline, Deputy Director and Authorizing Official (AO)
**Date:** April 28, 2026
**Status:** APPROVED

---

> **Related Documents:**
> System Security Plan: [../docs/system-security-plan.md](../docs/system-security-plan.md)
> Assessments Folder: [../assessments/README.md](../assessments/README.md)
> Authorization Package: [../authorization/README.md](../authorization/README.md)

---

## Table of Contents

1. [Purpose and Scope](#1-purpose-and-scope)
2. [Regulatory and Standards Basis](#2-regulatory-and-standards-basis)
3. [System Description Summary](#3-system-description-summary)
4. [Information Types Processed by CloudVault FHX](#4-information-types-processed-by-cloudvault-fhx)
5. [Security Objective Analysis: Confidentiality](#5-security-objective-analysis-confidentiality)
6. [Security Objective Analysis: Integrity](#6-security-objective-analysis-integrity)
7. [Security Objective Analysis: Availability](#7-security-objective-analysis-availability)
8. [Overall System Security Categorization](#8-overall-system-security-categorization)
9. [Impact Justification and Risk Rationale](#9-impact-justification-and-risk-rationale)
10. [Approval and Signature](#10-approval-and-signature)

---

## 1. Purpose and Scope

### 1.1 Purpose

This document establishes the formal security categorization of the CloudVault Federal Health Exchange (FHX) in accordance with Federal Information Processing Standard (FIPS) Publication 199, *Standards for Security Categorization of Federal Information and Information Systems* (February 2004). Security categorization is the foundational step of the NIST Risk Management Framework (RMF) and determines the minimum security controls baseline applied to protect federal information systems.

The security categorization defined in this document:

- Serves as the authoritative basis for the FedRAMP High control baseline selection (421 controls from NIST SP 800-53 Rev 5)
- Supports the Agency Authority to Operate (ATO) determination by Authorizing Official Henry Kline, Deputy Director
- Supports the Joint Authorization Board (JAB) Provisional Authority to Operate (P-ATO) process
- Establishes the system impact level for all associated security assessments, continuous monitoring activities, and system change management decisions

### 1.2 Scope

This categorization applies to all components of the CloudVault FHX system boundary as defined in the System Security Plan (SSP) Section 3, including:

- All application tiers hosted in AWS GovCloud (US-East and US-West regions)
- All data stores, databases, and backup repositories
- All federal agency API interconnections (47 agency connections)
- All administrative, privileged, and user access channels
- All supporting infrastructure components within the authorization boundary

This document does not extend to systems operated by interconnected federal agencies under separate ATOs. Those systems are governed by their own respective security categorization determinations.

---

## 2. Regulatory and Standards Basis

The categorization methodology applied in this document derives from the following federal statutes, regulations, and standards:

| Reference | Title | Applicability |
|---|---|---|
| FIPS 199 | Standards for Security Categorization of Federal Information and Information Systems | Primary categorization standard |
| NIST SP 800-60 Vol I | Guide for Mapping Types of Information and Information Systems to Security Categories | Information type identification methodology |
| NIST SP 800-60 Vol II | Appendices to SP 800-60 (Information Type Taxonomy) | Specific impact ratings by information type |
| NIST SP 800-53 Rev 5 | Security and Privacy Controls for Information Systems and Organizations | Control baseline selection |
| NIST SP 800-37 Rev 2 | Risk Management Framework for Information Systems and Organizations | RMF Step 1 (Categorize) |
| FISMA 2014 (44 U.S.C. Â§ 3551) | Federal Information Security Modernization Act | Legislative authority |
| HIPAA 45 C.F.R. Parts 164 | Health Insurance Portability and Accountability Act Security Rule | PHI protection requirements |
| Privacy Act of 1974 | 5 U.S.C. Â§ 552a | PII protection requirements |
| IRS Publication 1075 | Tax Information Security Guidelines | FTI protection requirements (HIGH baseline) |
| OMB Circular A-130 | Managing Information as a Strategic Resource | Federal information governance |
| FedRAMP Security Assessment Framework | FedRAMP High Baseline Controls | Cloud authorization requirements |

### 2.1 Categorization Formula

Per FIPS 199, the security category (SC) for an information system is expressed as:

**SC Information System = {(Confidentiality, impact), (Integrity, impact), (Availability, impact)}**

Where impact values are: LOW, MODERATE, or HIGH.

The overall system impact level equals the **highest impact value** across all three security objectives, for the **highest-impact information type** processed by the system. This is the "high-water mark" principle.

---

## 3. System Description Summary

| Attribute | Value |
|---|---|
| System Name | CloudVault Federal Health Exchange (FHX) |
| System Abbreviation | CloudVault FHX |
| System Owner | Federal Health Data Office (FHDO) |
| ISSO and ISSM | Enechi P.C. Njeze |
| Authorizing Official | Henry Kline, Deputy Director |
| System Type | Federal Cloud-Based Health Data Exchange |
| Deployment Model | AWS GovCloud (US-East and US-West) |
| Operating Status | Operational |
| Authorization Track | Agency ATO and JAB P-ATO (Dual Track) |
| FedRAMP Baseline | FedRAMP High (421 controls) |
| Users Served | 890,000+ patient records across 47 federal agencies |
| Data Classification | PHI, PII, CUI, FTI, PCI |
| Lifecycle Phase | Operations and Maintenance |

CloudVault FHX is the centralized federal health data exchange platform enabling secure, real-time sharing of electronic health records and clinical data among participating federal agencies, including the Department of Veterans Affairs (VA), Department of Defense (DoD), Indian Health Service (IHS), and 44 additional federal health programs. The platform stores and transmits among the most sensitive categories of information in the federal government's custody, including Protected Health Information (PHI), Federal Tax Information (FTI), and Personally Identifiable Information (PII) for over 890,000 patients.

---

## 4. Information Types Processed by CloudVault FHX

The information types below are identified using the NIST SP 800-60 Vol II taxonomy. Each type is mapped to its provisional impact ratings for Confidentiality, Integrity, and Availability. Where operational factors justify raising an impact level above the provisional rating, an adjusted value is assigned with documented rationale.

### 4.1 Health and Clinical Information

| Information Type | SP 800-60 Identifier | Prov. C | Prov. I | Prov. A | Adj. C | Adj. I | Adj. A | Adjustment Rationale |
|---|---|---|---|---|---|---|---|---|
| Patient Medical Records (PHI/EHR) | C.3.1.1 | HIGH | HIGH | MODERATE | HIGH | HIGH | HIGH | System serves 890,000+ patients. Extended unavailability (>4 hours) directly impairs clinical decision-making across VA, DoD, and IHS, threatening patient safety. Availability raised to HIGH. |
| Clinical Decision Support Data | C.3.1.2 | HIGH | HIGH | MODERATE | HIGH | HIGH | HIGH | Real-time clinical alerts and drug interaction data require continuous availability for safe patient care across 47 agencies. Availability raised to HIGH. |
| Health Benefits Eligibility | C.3.1.3 | HIGH | MODERATE | MODERATE | HIGH | HIGH | HIGH | Integrity compromise could deny or misdirect care to vulnerable populations. Availability raised to HIGH due to real-time eligibility verification requirements. |
| Mental Health and Substance Abuse Records | C.3.1.4 | HIGH | HIGH | LOW | HIGH | HIGH | HIGH | 42 C.F.R. Part 2 mandates heightened protection. Highly sensitive disclosure risk. Availability raised to HIGH for consistency with system-wide classification. |

### 4.2 Personally Identifiable Information (PII)

| Information Type | SP 800-60 Identifier | Prov. C | Prov. I | Prov. A | Adj. C | Adj. I | Adj. A | Adjustment Rationale |
|---|---|---|---|---|---|---|---|---|
| Social Security Numbers | C.3.5.8 | HIGH | HIGH | MODERATE | HIGH | HIGH | HIGH | Breach of SSN data for 890,000+ individuals constitutes a catastrophic PII exposure event. Availability raised to HIGH. |
| Personal Identity and Demographic Data | C.3.5.1 | MODERATE | MODERATE | MODERATE | HIGH | HIGH | HIGH | Combined with health data, demographic PII creates highly sensitive data profiles. Confidentiality raised to HIGH per Privacy Act sensitivity analysis. |
| Financial Account Information | C.3.5.3 | HIGH | HIGH | MODERATE | HIGH | HIGH | HIGH | PCI-scoped data requires HIGH baseline per PCI-DSS v4.0 and FIPS 199 high-water mark analysis. |

### 4.3 Federal Tax Information (FTI)

| Information Type | SP 800-60 Identifier | Prov. C | Prov. I | Prov. A | Adj. C | Adj. I | Adj. A | Adjustment Rationale |
|---|---|---|---|---|---|---|---|---|
| Federal Tax Information (FTI) | C.3.5.6 | HIGH | HIGH | MODERATE | HIGH | HIGH | HIGH | IRS Publication 1075 mandates HIGH confidentiality and integrity. Tax data is used for income-based benefits eligibility. Availability raised to HIGH for benefit determination continuity. |
| Income and Benefits Eligibility Data | C.3.5.9 | MODERATE | HIGH | MODERATE | HIGH | HIGH | HIGH | Combination with FTI elevates overall sensitivity. Incorrect income data affects access to critical federal health benefits. |

### 4.4 Controlled Unclassified Information (CUI)

| Information Type | SP 800-60 Identifier | Prov. C | Prov. I | Prov. A | Adj. C | Adj. I | Adj. A | Adjustment Rationale |
|---|---|---|---|---|---|---|---|---|
| CUI Health Information | C.2.8.6 | HIGH | HIGH | MODERATE | HIGH | HIGH | HIGH | CUI Registry category HLTH applies. NARA CUI policy and DoD 5400.11 govern handling. Availability raised to HIGH. |
| CUI Law Enforcement Data | C.2.8.5 | HIGH | HIGH | LOW | HIGH | HIGH | HIGH | Law enforcement sensitive data accessed by certain authorized federal users. Availability raised to HIGH for system-wide consistency. |

### 4.5 System and Administrative Information

| Information Type | SP 800-60 Identifier | Prov. C | Prov. I | Prov. A | Adj. C | Adj. I | Adj. A | Adjustment Rationale |
|---|---|---|---|---|---|---|---|---|
| System Audit and Accountability Logs | C.3.5.7 | MODERATE | HIGH | HIGH | HIGH | HIGH | HIGH | Audit logs are required for breach investigation and federal legal proceedings. Compromise or unavailability impairs incident response across 47 agencies. Confidentiality raised to HIGH. |
| Identity Credential and Access Data | C.3.5.4 | HIGH | HIGH | HIGH | HIGH | HIGH | HIGH | Credential data governs access to all PHI and FTI in the system. Provisionally HIGH across all three objectives. |
| System Configuration and Architecture Data | C.3.5.11 | MODERATE | HIGH | MODERATE | HIGH | HIGH | HIGH | Disclosure of system architecture could enable targeted attacks against the health data infrastructure. Confidentiality raised to HIGH. |

---

## 5. Security Objective Analysis: Confidentiality

### 5.1 Definition

Confidentiality refers to preserving authorized restrictions on information access and disclosure, including means for protecting personal privacy and proprietary information (44 U.S.C. Â§ 3542).

### 5.2 Potential Impact of Confidentiality Breach

A loss of confidentiality on CloudVault FHX would involve unauthorized disclosure of PHI, PII, FTI, and CUI belonging to 890,000+ federal beneficiaries.

**Potential consequences include:**

- Criminal prosecution under HIPAA, the Privacy Act, and the Internal Revenue Code (IRC Â§ 6103) for unauthorized disclosure of FTI
- Significant harm to individuals through identity theft, discrimination, financial fraud, or denial of benefits
- Reputational damage to participating federal agencies and the federal government's health data infrastructure
- Loss of public trust in federal electronic health record sharing programs
- Congressional oversight, OIG investigation, and potential program shutdown
- Substantial financial penalties: HIPAA civil monetary penalties up to $1.9 million per violation category per year, and potential criminal fines under IRC Â§ 7213 for FTI misuse

**Confidentiality Impact Level: HIGH**

This determination is consistent with NIST SP 800-60 Vol II provisional ratings for PHI (C.3.1.1), SSN data (C.3.5.8), FTI (C.3.5.6), and CUI. The aggregate effect of a confidentiality breach across all information types processed by this system constitutes a severe and irreversible adverse impact on organizational operations, assets, individuals, and national health policy.

---

## 6. Security Objective Analysis: Integrity

### 6.1 Definition

Integrity refers to guarding against improper information modification or destruction, including ensuring information non-repudiation and authenticity (44 U.S.C. Â§ 3542).

### 6.2 Potential Impact of Integrity Breach

A loss of integrity on CloudVault FHX would involve unauthorized modification, corruption, or destruction of health records, clinical decision support data, eligibility determinations, or system audit logs.

**Potential consequences include:**

- Direct patient harm or death resulting from corrupted clinical records or misdirected treatment decisions
- Fraudulent modification of eligibility data, resulting in wrongful denial or improper authorization of federal health benefits
- Corruption of FTI used in income-based program eligibility, generating incorrect benefit determinations for hundreds of thousands of beneficiaries
- Destruction or tampering of audit logs, impairing breach investigation, legal proceedings, and forensic analysis
- Loss of non-repudiation for clinical and financial transactions, undermining legal admissibility of federal health records
- Regulatory findings, potential decertification of the electronic health record system, and agency-level corrective action plans

**Integrity Impact Level: HIGH**

The high-water mark across information types processed by the system consistently produces HIGH integrity impact ratings. Clinical data integrity is directly tied to patient safety at scale. Financial and eligibility data integrity governs federal benefits for a population of more than 890,000 individuals. The potential for patient harm and legal liability from an integrity failure supports the HIGH determination without exception.

---

## 7. Security Objective Analysis: Availability

### 7.1 Definition

Availability refers to ensuring timely and reliable access to and use of information (44 U.S.C. Â§ 3542).

### 7.2 Potential Impact of Availability Breach

A loss of availability on CloudVault FHX would render the platform inaccessible to clinical users, federal agency systems, and health benefit administrators across 47 federal agencies.

**Potential consequences include:**

- Interruption of real-time clinical care coordination, including emergency care, prescription processing, and surgical planning
- Inability of healthcare providers to access patient medication histories, allergy data, or prior authorizations, creating direct risk of adverse medical events
- Disruption to federal benefits eligibility processing, delaying or denying health coverage for federal beneficiaries
- Cascading outage effects across 47 interconnected federal agency systems that depend on CloudVault FHX as a shared authoritative data source
- Breach of federal service level agreements and inter-agency memoranda of understanding (MOUs), creating legal liability
- Congressional oversight, OIG audit findings, and potential budgetary consequences for the Federal Health Data Office

**Availability Impact Level: HIGH**

CloudVault FHX operates as a mission-critical shared service for the federal health enterprise. The real-time clinical use cases supported by this system, combined with the breadth of agency dependency, produce a HIGH availability impact rating. Any extended outage (operationally defined as greater than 4 hours in the FHX Service Level Agreement) constitutes a severe adverse impact on the ability of federal agencies to deliver health services.

---

## 8. Overall System Security Categorization

### 8.1 High-Water Mark Determination

The security categorization for CloudVault FHX is determined by applying the FIPS 199 high-water mark principle across all information types and all three security objectives:

| Security Objective | Individual Information Type Ratings | High-Water Mark |
|---|---|---|
| Confidentiality | HIGH (PHI, SSN, FTI, CUI) | **HIGH** |
| Integrity | HIGH (PHI, Clinical, FTI, Audit Logs) | **HIGH** |
| Availability | HIGH (Clinical, Multi-Agency Dependency) | **HIGH** |

### 8.2 Formal Categorization Statement

In accordance with FIPS 199 and NIST SP 800-37 Rev 2 Step 1, the formal security categorization for the CloudVault Federal Health Exchange is:

---

**SC CloudVault FHX = {(Confidentiality, HIGH), (Integrity, HIGH), (Availability, HIGH)}**

**Overall System Impact Level: HIGH**

**Abbreviated Notation: {HIGH} = (HIGH, HIGH, HIGH)**

---

### 8.3 FedRAMP Baseline Implication

A HIGH overall system impact level requires application of the **FedRAMP High** security control baseline, consisting of **421 security and privacy controls** drawn from NIST SP 800-53 Rev 5. This represents the most stringent federal cloud authorization baseline available and reflects the sensitivity and criticality of health, tax, and personal data managed by CloudVault FHX.

| FedRAMP Baseline | Total Controls | Applicable to CloudVault FHX |
|---|---|---|
| FedRAMP Low | 125 controls | No |
| FedRAMP Moderate | 325 controls | No |
| FedRAMP High | 421 controls | **Yes, required** |

---

## 9. Impact Justification and Risk Rationale

### 9.1 Why This System Cannot Be Rated Below HIGH

Several factors collectively produce a HIGH impact rating that cannot reasonably be lowered:

**Scale of sensitive data:** 890,000+ patient records representing PHI under HIPAA, PII under the Privacy Act, and FTI under IRC Â§ 6103 create a large-scale exposure surface. A single breach event would likely constitute one of the largest federal health data incidents in history.

**Legal mandates for HIGH protection:** IRS Publication 1075 independently mandates HIGH confidentiality and integrity for any system processing FTI. This alone would produce a HIGH rating regardless of other data types.

**Clinical safety dependency:** Real-time clinical decision support and emergency care coordination create a patient safety dependency that mandates HIGH availability. Downtime is not a recoverable business inconvenience, it is a clinical risk event.

**Multi-agency operational integration:** 47 federal agencies depend on this system. A failure does not affect one organization, it cascades through the federal health enterprise simultaneously.

**PHI regulatory floor:** HIPAA's Security Rule, while not explicitly adopting FIPS 199 terminology, requires security measures commensurate with the likelihood and magnitude of risk to PHI. The volume and sensitivity of the PHI stored and transmitted by CloudVault FHX supports a HIGH categorization under any reasonable threat and impact analysis.

### 9.2 Comparison to Similar Federal Systems

For reference, the following federal systems with similar profiles carry HIGH impact categorizations:

| Comparable System Type | Typical Categorization | Notes |
|---|---|---|
| VA Health Information Exchange | HIGH | PHI, large patient population |
| DoD Military Health System | HIGH | PHI, CUI, national security sensitivity |
| CMS Medicare/Medicaid Data Systems | HIGH | PHI, PII, FTI combination |
| IRS Individual Tax Systems | HIGH | FTI mandates HIGH independently |
| SSA Benefits Processing Systems | HIGH | PII, financial data at scale |

CloudVault FHX combines the data sensitivity characteristics of all categories above into a single shared platform, reinforcing the HIGH categorization at every level of analysis.

---

## 10. Approval and Signature

This FIPS 199 Security Categorization has been reviewed and approved by the individuals identified below. Approval of this document authorizes commencement of NIST RMF Step 2 (Select Controls) based on the FedRAMP High baseline.

---

### Information System Security Officer (ISSO) and Information System Security Manager (ISSM)

**Name:** Enechi P.C. Njeze
**Title:** Information System Security Officer (ISSO) and Information System Security Manager (ISSM)
**Organization:** Federal Health Data Office (FHDO), CloudVault FHX Program
**Certifications:** CGRC, CISA, CISM, PMP, PMI-RMP, CompTIA Security+ SY0-701, CHP, CSCS, CISSP (in progress)

I have conducted a thorough analysis of all information types processed, stored, and transmitted by the CloudVault Federal Health Exchange. The security categorization documented herein accurately reflects the potential impact of a loss of confidentiality, integrity, or availability on organizational operations, organizational assets, individuals, other federal agencies, and the nation.

**Signature:** ____________________________
**Date:** April 28, 2026

---

### System Owner

**Name:** Dr. Sandra M. Okafor
**Title:** System Owner
**Organization:** Federal Health Data Office (FHDO)

I have reviewed and concur with the security categorization presented in this document. This categorization aligns with the operational and mission requirements of the CloudVault Federal Health Exchange and the data stewardship obligations of the Federal Health Data Office.

**Signature:** ____________________________
**Date:** ____________________________

---

### Authorizing Official (AO)

**Name:** Henry Kline
**Title:** Deputy Director and Authorizing Official
**Organization:** Federal Health Data Office (FHDO)

I have reviewed and approved the FIPS 199 Security Categorization for the CloudVault Federal Health Exchange. This determination establishes the HIGH impact level and mandates the FedRAMP High control baseline for all subsequent security authorization activities.

**Signature:** ____________________________
**Date:** ____________________________

---

### Senior Agency Information Security Officer (SAISO) Concurrence

**Name:** Marcus T. Brennan
**Title:** Senior Agency Information Security Officer
**Organization:** Federal Health Data Office (FHDO)

**Signature:** ____________________________
**Date:** ____________________________

---

## Document Control

| Field | Value |
|---|---|
| Document ID | CV-FHX-FIPS199-001 |
| Version | 1.0 |
| Status | APPROVED |
| Created | April 28, 2026 |
| Last Reviewed | April 28, 2026 |
| Next Review Date | April 28, 2027 |
| Prepared By | Enechi P.C. Njeze, ISSO and ISSM |
| Approved By | Henry Kline, Deputy Director and AO |
| Repository | cloudvault-fedramp-ato/assessments/ |
| Related Documents | SSP v1.0, SAP, assessments/README.md |
| Review Trigger | Any significant change to system boundary, data types, or operational environment |

---

*This document is UNCLASSIFIED and designated FOR OFFICIAL USE ONLY (FOUO). Distribution is limited to authorized personnel with a need to know in connection with the CloudVault Federal Health Exchange federal authorization process.*

*CloudVault FHX GRC Portfolio, enechi-njeze/cloudvault-fedramp-ato*
*Maintained by Enechi P.C. Njeze, CGRC, CISA, CISM, PMP, PMI-RMP, Security+, CHP, CSCS*
