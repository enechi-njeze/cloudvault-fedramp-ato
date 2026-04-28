# Security Assessment Plan (SAP)

**CloudVault Federal Health Exchange (FHX)**
**Document ID:** CV-FHX-SAP-001
**Version:** 1.0
**Classification:** UNCLASSIFIED // FOR OFFICIAL USE ONLY (FOUO)
**Prepared By:** Enechi P.C. Njeze, Information System Security Officer (ISSO) and Information System Security Manager (ISSM)
**3PAO Lead:** Kristopher A. Wentworth, Lead Assessor, ClearPath Security Assessors LLC
**Reviewed By:** Henry Kline, Deputy Director and Authorizing Official (AO)
**Date:** April 28, 2026
**Status:** APPROVED FOR ASSESSMENT

---

> **Related Documents:**
> System Security Plan: [../docs/system-security-plan.md](../docs/system-security-plan.md)
> FIPS 199 Security Categorization: [./fips199-security-categorization.md](./fips199-security-categorization.md)
> Security Assessment Report: [./security-assessment-report.md](./security-assessment-report.md)
> Authorization Package: [../authorization/README.md](../authorization/README.md)
> Evidence Folder: [../evidence/README.md](../evidence/README.md)

---

## Table of Contents

1. [Purpose and Objectives](#1-purpose-and-objectives)
2. [Regulatory and Standards Basis](#2-regulatory-and-standards-basis)
3. [System Description and Authorization Context](#3-system-description-and-authorization-context)
4. [Assessment Scope](#4-assessment-scope)
5. [Third-Party Assessment Organization (3PAO)](#5-third-party-assessment-organization-3pao)
6. [Assessment Team Roles and Responsibilities](#6-assessment-team-roles-and-responsibilities)
7. [Assessment Methodology](#7-assessment-methodology)
8. [Control Families in Scope](#8-control-families-in-scope)
9. [Assessment Schedule and Milestones](#9-assessment-schedule-and-milestones)
10. [Rules of Engagement](#10-rules-of-engagement)
11. [Evidence Collection Requirements](#11-evidence-collection-requirements)
12. [Risk Scoring and Finding Classification](#12-risk-scoring-and-finding-classification)
13. [Assessment Deliverables](#13-assessment-deliverables)
14. [Communication Plan](#14-communication-plan)
15. [Approval and Signature](#15-approval-and-signature)

---

## 1. Purpose and Objectives

### 1.1 Purpose

This Security Assessment Plan (SAP) defines the scope, methodology, schedule, team structure, and rules of engagement for the independent security assessment of the CloudVault Federal Health Exchange (FHX). The assessment is conducted by ClearPath Security Assessors LLC, an accredited FedRAMP Third-Party Assessment Organization (3PAO), in support of both the Agency Authority to Operate (ATO) determination by Authorizing Official Henry Kline and the Joint Authorization Board (JAB) Provisional Authority to Operate (P-ATO) process.

This document provides the governing framework under which all assessment activities are authorized, constrained, and documented. No assessment activity may be conducted outside the boundaries established in this SAP without written approval from the ISSO and Authorizing Official.

### 1.2 Assessment Objectives

The assessment is designed to satisfy the following objectives:

- Independently verify that security controls documented in the CloudVault FHX System Security Plan (SSP) are implemented correctly, operating as intended, and producing the desired security outcome for the system
- Evaluate all 421 controls in the FedRAMP High baseline against NIST SP 800-53A Rev 5 assessment procedures
- Identify control deficiencies, weaknesses, and gaps that represent risk to the confidentiality, integrity, or availability of information processed by CloudVault FHX
- Provide the Authorizing Official with sufficient evidence to make an informed, risk-based authorization decision
- Produce a Security Assessment Report (SAR) and associated raw test results that meet FedRAMP High documentation requirements for JAB P-ATO submission
- Support the development of an initial Plan of Action and Milestones (POA&M) for any findings requiring remediation

### 1.3 Assessment Type

This is a **full initial assessment** (not a periodic reassessment or significant change assessment). All 421 FedRAMP High baseline controls are subject to assessment. This assessment supports the first-time authorization of CloudVault FHX and will form the foundational security authorization package for all subsequent annual assessments.

---

## 2. Regulatory and Standards Basis

All assessment activities are governed by the following federal standards, guidelines, and program requirements:

| Reference | Title | Role in This Assessment |
|---|---|---|
| NIST SP 800-53A Rev 5 | Assessing Security and Privacy Controls in Information Systems and Organizations | Primary assessment procedures and methods |
| NIST SP 800-53 Rev 5 | Security and Privacy Controls for Information Systems and Organizations | Control baseline being assessed |
| NIST SP 800-37 Rev 2 | Risk Management Framework for Information Systems and Organizations | RMF Step 4 (Assess) framework |
| FIPS 199 | Standards for Security Categorization | Establishes HIGH impact baseline (CV-FHX-FIPS199-001) |
| FedRAMP Security Assessment Framework (SAF) | FedRAMP Program Management Office | 3PAO accreditation and assessment standards |
| FedRAMP High Baseline | FedRAMP PMO | 421-control assessment baseline |
| FedRAMP SAP Template v3.1 | FedRAMP PMO | SAP format and content requirements |
| FedRAMP Penetration Test Guidance | FedRAMP PMO | Penetration testing scope and methodology |
| NIST SP 800-115 | Technical Guide to Information Security Testing and Assessment | Technical testing methodology |
| NIST SP 800-30 Rev 1 | Guide for Conducting Risk Assessments | Risk scoring methodology |
| FISMA 2014 (44 U.S.C. Â§ 3551) | Federal Information Security Modernization Act | Legislative assessment mandate |
| OMB Circular A-130 | Managing Information as a Strategic Resource | Federal information security requirements |

---

## 3. System Description and Authorization Context

### 3.1 System Summary

| Attribute | Value |
|---|---|
| System Name | CloudVault Federal Health Exchange (FHX) |
| System Abbreviation | CloudVault FHX |
| System Owner | Dr. Sandra M. Okafor, Federal Health Data Office |
| ISSO and ISSM | Enechi P.C. Njeze |
| Authorizing Official | Henry Kline, Deputy Director |
| SAISO | Marcus T. Brennan, Federal Health Data Office |
| Cloud Service Provider | Amazon Web Services (AWS GovCloud) |
| Deployment Model | Government Community Cloud |
| Service Model | Infrastructure as a Service (IaaS) and Platform as a Service (PaaS) |
| FedRAMP Baseline | FedRAMP High (421 controls) |
| System Impact Level | HIGH (C:HIGH / I:HIGH / A:HIGH) |
| Authorization Type | Agency ATO and JAB P-ATO (Dual Track) |
| Users | 890,000+ patient records, 47 federal agency connections |
| Data Types | PHI, PII, CUI, FTI, PCI |
| SSP Version | 1.0 (April 28, 2026) |
| FIPS 199 Document | CV-FHX-FIPS199-001 (Approved April 28, 2026) |

### 3.2 Authorization Boundary Summary

The authorization boundary for CloudVault FHX encompasses all system components listed in SSP Section 3, including all application-tier services, data stores, administrative interfaces, and supporting infrastructure hosted within AWS GovCloud (US-East and US-West regions). The boundary does not include:

- AWS shared infrastructure components covered under the AWS GovCloud FedRAMP High ATO (inherited controls apply)
- Federal agency systems connecting via APIs under separate agency ATOs (interconnection agreements documented in SSP Section 7)
- End-user workstations and local networks operated by participating federal agencies

### 3.3 Inherited Controls

CloudVault FHX inherits a set of controls from the AWS GovCloud FedRAMP High authorization. The 3PAO will confirm inherited control status and verify that CloudVault FHX has correctly implemented all customer-responsible portions of shared controls. A full inherited/customer-responsible/hybrid control matrix is included in the SSP and serves as the baseline for assessment scoping in Section 4.

---

## 4. Assessment Scope

### 4.1 In-Scope Components

The following system components and environments are included in this assessment:

| Component | Environment | Assessment Method |
|---|---|---|
| CloudVault FHX Application (all tiers) | AWS GovCloud US-East (Primary) | Interview, Examination, Testing |
| CloudVault FHX Application (all tiers) | AWS GovCloud US-West (DR/Failover) | Interview, Examination, Testing |
| Administrative Management Console | GovCloud US-East | Interview, Examination, Testing |
| Federal Agency API Gateway | GovCloud US-East | Interview, Examination, Penetration Testing |
| Patient Data Repositories (RDS, S3) | GovCloud US-East and US-West | Interview, Examination, Testing |
| Backup and Recovery Systems | GovCloud US-West | Interview, Examination, Testing |
| Identity and Access Management (IAM) | AWS GovCloud IAM | Interview, Examination, Testing |
| Logging and Monitoring Stack (CloudWatch, GuardDuty, Macie) | GovCloud US-East | Interview, Examination, Testing |
| Secrets Management (AWS Secrets Manager, KMS) | GovCloud US-East | Interview, Examination, Testing |
| Continuous Integration and Deployment (CI/CD) Pipeline | GovCloud US-East | Interview, Examination, Testing |
| Network Architecture (VPCs, Security Groups, NACLs) | GovCloud US-East and US-West | Interview, Examination, Penetration Testing |

### 4.2 Out-of-Scope Components

The following are explicitly excluded from this assessment:

- AWS shared infrastructure components covered by the AWS GovCloud FedRAMP High authorization
- Federal agency internal networks and workstations (covered by agency ATOs)
- FedRAMP-authorized third-party services consumed by CloudVault FHX (leveraged authorizations documented in SSP)
- Physical security of AWS GovCloud data centers (covered by AWS physical security FedRAMP controls)

### 4.3 Control Scope

All 421 controls in the FedRAMP High baseline are subject to assessment. Controls are categorized as: Customer-Implemented (fully assessed), Inherited from AWS (status verified), or Shared/Hybrid (customer-responsible portions assessed). The full control responsibility matrix is maintained in the SSP and referenced by the 3PAO throughout the assessment.

---

## 5. Third-Party Assessment Organization (3PAO)

### 5.1 3PAO Identity and Accreditation

| Field | Detail |
|---|---|
| Organization Name | ClearPath Security Assessors LLC |
| FedRAMP Accreditation Status | Accredited 3PAO (A2LA Certificate: 4821.01) |
| Physical Address | 1850 Federal Plaza, Suite 400, Washington, D.C. 20004 |
| Primary POC | Kristopher A. Wentworth, Lead Assessor |
| Phone | (202) 555-0173 |
| Email | k.wentworth@clearpathsec.example.gov |
| Accreditation Body | American Association for Laboratory Accreditation (A2LA) |
| ISO/IEC 17020 Accreditation | Active (Expires December 2027) |
| Conflict of Interest Status | No conflict identified. ClearPath has not provided consulting, design, or implementation services for CloudVault FHX. |

### 5.2 3PAO Independence Certification

ClearPath Security Assessors LLC certifies that it has no organizational, financial, or contractual relationship with the Federal Health Data Office or the CloudVault FHX development or operations teams that would compromise the independence of this assessment. This certification is consistent with FedRAMP 3PAO independence requirements and NIST SP 800-37 Rev 2 Section 2.7.

---

## 6. Assessment Team Roles and Responsibilities

### 6.1 3PAO Assessment Team

| Name | Role | Responsibilities |
|---|---|---|
| Kristopher A. Wentworth | Lead Assessor | Overall assessment leadership, final SAR sign-off, AO briefing, FedRAMP package submission coordination |
| Dr. Priya Subramanian | Senior Technical Assessor | Cloud infrastructure testing, network penetration testing, AWS GovCloud configuration review |
| James T. Hollifield | Security Controls Assessor | Policy and procedure examination, interview facilitation, management and operational control assessment |
| Yolanda M. Ferris | Privacy and Data Security Assessor | PHI/PII/FTI control assessment, HIPAA Security Rule mapping, privacy control (PT family) evaluation |
| Darnell K. Osei | Penetration Test Lead | External and internal penetration testing, API security testing, vulnerability exploitation within authorized scope |
| Mei-Ling Chou | Documentation Specialist | Evidence collection management, test case documentation, SAR compilation and formatting |

### 6.2 CloudVault FHX Assessment Support Team

| Name | Role | Responsibilities |
|---|---|---|
| Enechi P.C. Njeze | ISSO and ISSM | Primary POC for all assessment activities, evidence coordination, interview scheduling, artifact delivery |
| Dr. Sandra M. Okafor | System Owner | Executive sponsor of assessment, final artifact approvals |
| Henry Kline | Authorizing Official | Receives assessment briefings, reviews preliminary SAR findings |
| Marcus T. Brennan | SAISO | Oversight of assessment activities, FISMA compliance coordination |
| Trevor L. Abrams | Cloud Operations Lead | AWS GovCloud environment access, technical interview support, configuration evidence |
| Dr. Angela M. Reeves | Privacy Officer | PT family control support, Privacy Impact Assessment coordination |

### 6.3 Roles of the Authorizing Official During Assessment

The Authorizing Official does not direct or constrain assessment activities. The AO receives briefings at key milestones (kick-off, preliminary findings, final SAR delivery) but does not participate in or influence individual test execution. This separation preserves the integrity of the independent assessment.

---

## 7. Assessment Methodology

### 7.1 NIST SP 800-53A Assessment Methods

All controls are assessed using one or more of the three assessment methods defined in NIST SP 800-53A Rev 5:

**Examine:** Review of policies, procedures, plans, system design documentation, rules of behavior, contingency plans, incident response plans, configuration settings, configuration management plans, audit records, and other relevant documentation and artifacts to verify control implementation.

**Interview:** Structured interviews with system owners, administrators, security personnel, developers, and end users to confirm understanding and consistent application of security controls, procedures, and responsibilities.

**Test:** Direct technical testing and observation of system behavior to verify that controls produce the expected security outcome. Testing includes configuration validation, vulnerability scanning, penetration testing, and functional security testing.

### 7.2 Assessment Depth and Coverage

Each control is assessed using the applicable assessment procedures from NIST SP 800-53A Rev 5, at the depth appropriate to the HIGH impact level. For HIGH-impact systems, assessment procedures require the most rigorous coverage, including:

- Multiple instances of testing across redundant components
- Verification of control behavior under boundary conditions and edge cases
- Cross-validation of documented procedures against actual system behavior
- Independent confirmation of inherited control status with the AWS GovCloud CSP authorization package

### 7.3 Penetration Testing Approach

Penetration testing is conducted in accordance with FedRAMP Penetration Testing Guidance and NIST SP 800-115. The penetration test scope includes:

- External network and perimeter testing (internet-facing components)
- Internal network testing (lateral movement and privilege escalation scenarios)
- Web application testing (OWASP Top 10 methodology, CloudVault FHX application layer)
- API security testing (all 47 federal agency API endpoints and administrative APIs)
- Social engineering simulation (phishing awareness, credential harvesting resistance)
- AWS GovCloud misconfiguration testing (IAM, S3 bucket policies, security group rules)

All penetration testing activities are authorized under the Rules of Engagement in Section 10 and will not be conducted without explicit written authorization from the ISSO and AO.

### 7.4 Vulnerability Scanning

Authenticated vulnerability scanning is conducted against all in-scope components using approved commercial scanning tools. Scanning includes:

- Operating system and middleware vulnerability scanning (all EC2 instances)
- Container image scanning (all Docker/ECS container images)
- Database configuration and vulnerability scanning (RDS instances)
- Network device and security group configuration analysis
- Static application security testing (SAST) of application code repositories
- Dynamic application security testing (DAST) of deployed application endpoints

Scan results are provided to the ISSO within 48 hours of completion and are incorporated into the SAR evidence package.

### 7.5 Evidence of Prior Testing

The 3PAO will review and document all prior security testing conducted by the CloudVault FHX program, including internal vulnerability scans, prior penetration tests, and any security findings from the development and pre-production phases. This evidence is used to inform, but does not substitute for, the independent 3PAO assessment.

---

## 8. Control Families in Scope

All 20 NIST SP 800-53 Rev 5 control families are included in this assessment. The table below identifies each family, the number of controls applicable under the FedRAMP High baseline, the primary assessment method applied, and the lead assessor responsible.

| ID | Control Family | FedRAMP High Controls | Primary Method | Lead Assessor |
|---|---|---|---|---|
| AC | Access Control | 25 | Examine, Interview, Test | Dr. Priya Subramanian |
| AT | Awareness and Training | 6 | Examine, Interview | James T. Hollifield |
| AU | Audit and Accountability | 16 | Examine, Interview, Test | Dr. Priya Subramanian |
| CA | Assessment, Authorization, and Monitoring | 9 | Examine, Interview | Kristopher A. Wentworth |
| CM | Configuration Management | 12 | Examine, Interview, Test | Dr. Priya Subramanian |
| CP | Contingency Planning | 13 | Examine, Interview, Test | James T. Hollifield |
| IA | Identification and Authentication | 12 | Examine, Interview, Test | Dr. Priya Subramanian |
| IR | Incident Response | 10 | Examine, Interview, Test | James T. Hollifield |
| MA | Maintenance | 6 | Examine, Interview | James T. Hollifield |
| MP | Media Protection | 8 | Examine, Interview, Test | Yolanda M. Ferris |
| PE | Physical and Environmental Protection | 20 | Examine, Interview | James T. Hollifield |
| PL | Planning | 7 | Examine, Interview | James T. Hollifield |
| PM | Program Management | 16 | Examine, Interview | Kristopher A. Wentworth |
| PS | Personnel Security | 9 | Examine, Interview | James T. Hollifield |
| PT | PII Processing and Transparency | 8 | Examine, Interview, Test | Yolanda M. Ferris |
| RA | Risk Assessment | 10 | Examine, Interview | Kristopher A. Wentworth |
| SA | System and Services Acquisition | 23 | Examine, Interview | Kristopher A. Wentworth |
| SC | System and Communications Protection | 51 | Examine, Interview, Test | Dr. Priya Subramanian |
| SI | System and Information Integrity | 23 | Examine, Interview, Test | Dr. Priya Subramanian |
| SR | Supply Chain Risk Management | 12 | Examine, Interview | Kristopher A. Wentworth |
| **Total** | **20 Families** | **306 base + 115 enhancements = 421** | | |

> Note: Control counts represent the FedRAMP High baseline as maintained in the FedRAMP PMO's official control catalog. Exact counts are subject to revision per FedRAMP PMO updates. The assessment will capture the current authoritative count at time of assessment execution.

---

## 9. Assessment Schedule and Milestones

### 9.1 Overall Assessment Timeline

The assessment is scheduled across a 16-week period from kick-off to final SAR delivery. This timeline reflects the complexity and scale of a FedRAMP High initial assessment covering 421 controls on a multi-region AWS GovCloud environment serving 47 federal agencies.

| Phase | Activity | Start Date | End Date | Duration |
|---|---|---|---|---|
| Phase 0 | Pre-Assessment Preparation | April 28, 2026 | May 11, 2026 | 2 weeks |
| Phase 1 | Kick-Off and Document Review | May 12, 2026 | May 25, 2026 | 2 weeks |
| Phase 2 | Management Control Assessment (CA, PL, PM, RA, SA, SR, AT, PS) | May 26, 2026 | June 8, 2026 | 2 weeks |
| Phase 3 | Operational Control Assessment (CP, IR, MA, MP, PE, PT) | June 9, 2026 | June 22, 2026 | 2 weeks |
| Phase 4 | Technical Control Assessment (AC, AU, CM, IA, SC, SI) | June 23, 2026 | July 13, 2026 | 3 weeks |
| Phase 5 | Penetration Testing | July 14, 2026 | July 27, 2026 | 2 weeks |
| Phase 6 | Vulnerability Scanning and Remediation Window | July 28, 2026 | August 3, 2026 | 1 week |
| Phase 7 | Preliminary Findings Briefing and Agency Response | August 4, 2026 | August 17, 2026 | 2 weeks |
| Phase 8 | Final SAR Development and Delivery | August 18, 2026 | August 31, 2026 | 2 weeks |

**Total Assessment Duration:** 18 weeks (including 2-week pre-assessment preparation)
**Final SAR Delivery Target:** August 31, 2026
**ATO Decision Target:** September 30, 2026

### 9.2 Key Milestones

| Milestone | Date | Participants |
|---|---|---|
| SAP Approved and Signed | April 28, 2026 | ISSO, AO, 3PAO Lead |
| Pre-Assessment Artifacts Delivered to 3PAO | May 11, 2026 | ISSO (Enechi P.C. Njeze) |
| Assessment Kick-Off Meeting | May 12, 2026 | All assessment team members, AO |
| Phase 2-4 Weekly Status Calls | Weekly (Tuesdays) | ISSO, 3PAO Lead, DevOps Lead |
| Penetration Test Authorization Confirmed | July 13, 2026 | ISSO, AO, 3PAO Pen Test Lead |
| Preliminary Findings Briefing to AO | August 4, 2026 | 3PAO Lead, ISSO, AO, SAISO |
| Agency POA&M Input Deadline | August 10, 2026 | ISSO |
| Draft SAR Delivered to ISSO | August 18, 2026 | 3PAO Lead |
| ISSO Review and Comment Period | August 18, 2026 | August 24, 2026 |
| Final SAR Delivered to AO | August 31, 2026 | 3PAO Lead |
| ATO Package Submitted to JAB | September 15, 2026 | ISSO, AO |

---

## 10. Rules of Engagement

### 10.1 General Rules

The following rules govern all assessment activities and are binding on the 3PAO assessment team, the CloudVault FHX support team, and all subcontractors involved in the assessment:

- All assessment activities are limited to in-scope components as defined in Section 4
- No assessment activity may target out-of-scope systems, agency networks, or production data without express written authorization
- All assessment activities will be conducted during the authorized assessment window defined in Section 9
- Any unintended access, system impact, or data exposure must be reported to the ISSO within 1 hour of discovery
- The 3PAO will not retain copies of sensitive system data (PHI, PII, FTI, CUI) beyond what is strictly necessary for evidence documentation, and all such data will be handled per NIST SP 800-88 and FedRAMP data handling requirements

### 10.2 Penetration Testing Authorization

Penetration testing activities require a separate written authorization signed by the ISSO and the Authorizing Official prior to execution. The penetration test authorization specifies:

- Exact IP address ranges and system components authorized for testing
- Authorized testing windows (dates and times)
- Prohibited activities (denial-of-service simulation, data exfiltration of live PHI)
- Emergency stop procedures and escalation contacts
- Confirmation that AWS GovCloud penetration testing rules have been reviewed and complied with

The penetration test authorization is maintained as a separate exhibit to this SAP and must be signed no later than July 13, 2026 (one business day before testing begins).

### 10.3 Data Handling During Assessment

All data accessed or collected during the assessment will be handled as follows:

- Evidence containing PHI, PII, FTI, or CUI must be anonymized, redacted, or encrypted at rest using AES-256 before being stored in 3PAO assessment systems
- Assessment workstations used on-site or connected to CloudVault FHX environments must be FedRAMP-authorized or assessed to an equivalent standard
- All assessment communication channels must use encrypted transmission (TLS 1.2 or higher)
- Evidence packages submitted to FedRAMP PMO will be transmitted via FedRAMP Secure Repository mechanisms only

### 10.4 Emergency Stop Procedure

If any assessment activity produces unintended consequences including system degradation, data exposure, or security incident indicators, the following emergency stop procedure applies:

1. Assessor immediately ceases the activity causing the issue
2. Assessor notifies ISSO Enechi P.C. Njeze by phone within 15 minutes
3. ISSO notifies AO Henry Kline and activates the CloudVault FHX Incident Response Plan if warranted
4. Assessment activities are suspended pending ISSO and AO determination to resume
5. All circumstances are documented in the assessment log and reflected in the SAR

---

## 11. Evidence Collection Requirements

### 11.1 Pre-Assessment Artifact Package

The following artifacts must be delivered to the 3PAO by May 11, 2026, prior to kick-off:

| Artifact | Owner | Format |
|---|---|---|
| System Security Plan v1.0 (with all attachments) | ISSO | PDF or Markdown |
| FIPS 199 Security Categorization (CV-FHX-FIPS199-001) | ISSO | PDF or Markdown |
| Network and system architecture diagrams | DevOps Lead | Visio, Draw.io, or PDF |
| AWS GovCloud inherited control documentation | DevOps Lead | PDF |
| Most recent vulnerability scan results (within 90 days) | DevOps Lead | CSV or XML |
| Most recent penetration test results (if available) | ISSO | PDF |
| Policies and procedures for all 20 control families | ISSO | PDF or Markdown |
| User accounts and privilege matrix | DevOps Lead | CSV or Excel |
| Configuration baselines for all in-scope components | DevOps Lead | Text or PDF |
| Incident response plan | ISSO | PDF or Markdown |
| Contingency plan and DR test results | ISSO | PDF or Markdown |
| Privacy Impact Assessment | Privacy Officer | PDF |
| Interconnection agreements (ISAs/MOUs for all 47 agencies) | ISSO | PDF |

### 11.2 Evidence Collected During Assessment

Evidence collected by the 3PAO during assessment activities is logged in the assessment workbook and referenced in the SAR. Evidence types include:

- Interview notes and signed attestation statements
- Screenshots of system configuration and control behavior
- Vulnerability scan reports
- Penetration test reports
- Policy and procedure documents reviewed
- Configuration file excerpts
- Audit log samples (anonymized as required)
- System access records and role assignments

### 11.3 Evidence Retention

All assessment evidence is retained by ClearPath Security Assessors LLC for a minimum of three years per FedRAMP program requirements. Evidence containing PHI, PII, or FTI is deleted or destroyed per NIST SP 800-88 media sanitization standards at the end of the retention period.

---

## 12. Risk Scoring and Finding Classification

### 12.1 Finding Severity Levels

All assessment findings are classified using the following severity framework, consistent with FedRAMP SAR requirements and NIST SP 800-30 Rev 1:

| Severity | Risk Level | Definition | POA&M Resolution Requirement |
|---|---|---|---|
| Critical | Very High | Control failure that exposes PHI, PII, FTI, or CUI to immediate unauthorized disclosure or that allows unauthorized system access with no compensating controls | Within 30 days of ATO |
| High | High | Control failure that significantly increases the likelihood of a security incident or materially undermines a required security objective | Within 90 days of ATO |
| Moderate | Moderate | Control deficiency that reduces security posture but does not present immediate risk. Compensating controls may partially mitigate impact | Within 180 days of ATO |
| Low | Low | Minor control gap or documentation deficiency with negligible operational security impact | Within 365 days of ATO |
| Informational | Informational | Observation or recommendation that does not represent a control failure. No POA&M item required | N/A |

### 12.2 Risk Scoring Methodology

Risk scores are calculated using the NIST SP 800-30 Rev 1 formula:

**Risk = Likelihood x Impact**

Where:

- Likelihood is assessed on a scale of Very Low / Low / Moderate / High / Very High based on threat source capability, threat event characterization, and vulnerability severity
- Impact is derived from the FIPS 199 security categorization (HIGH for all three objectives) and the nature of the information exposed or the function disrupted

For each finding, the 3PAO documents: the affected control, the specific deficiency, the threat scenario enabled by the deficiency, the likelihood and impact ratings, the overall risk score, and recommended corrective actions.

### 12.3 False Positive Handling

If the system owner or ISSO believes a finding represents a false positive, the following process applies:

1. ISSO submits written rebuttal with technical evidence to 3PAO Lead within 5 business days of preliminary findings briefing
2. 3PAO Lead reviews rebuttal evidence and either sustains, modifies, or closes the finding within 5 business days
3. Disputed findings that cannot be resolved between ISSO and 3PAO are escalated to the AO for final determination
4. All rebuttals and dispositions are documented in the SAR

---

## 13. Assessment Deliverables

The following deliverables will be produced by ClearPath Security Assessors LLC upon completion of the assessment:

| Deliverable | Description | Delivery Date | Recipient |
|---|---|---|---|
| Weekly Status Reports | Brief status updates during active assessment phases | Weekly (Tuesdays) | ISSO, AO |
| Preliminary Findings Briefing | Verbal and slide-based briefing of significant findings before SAR completion | August 4, 2026 | AO, ISSO, SAISO |
| Penetration Test Report | Full technical report of penetration testing activities, findings, and recommendations | August 10, 2026 | ISSO |
| Vulnerability Scan Reports | Authenticated scan results for all in-scope components | August 10, 2026 | ISSO |
| Draft Security Assessment Report (SAR) | Complete draft SAR with all findings, evidence references, and risk ratings | August 18, 2026 | ISSO |
| Final Security Assessment Report (SAR) | Final SAR incorporating ISSO review and factual corrections | August 31, 2026 | AO, ISSO, FedRAMP PMO |
| Assessment Evidence Package | Complete evidence repository organized by control family | August 31, 2026 | ISSO |
| Executive Summary | Two-page non-technical summary for AO and agency leadership | August 31, 2026 | AO, System Owner |
| Initial POA&M Input | 3PAO-recommended POA&M items based on findings | August 31, 2026 | ISSO |

---

## 14. Communication Plan

### 14.1 Communication Channels

All communication between the 3PAO and CloudVault FHX during the assessment will use the following approved channels:

| Communication Type | Channel | Parties |
|---|---|---|
| Routine assessment coordination | Encrypted email (TLS enforced) | ISSO, 3PAO Lead |
| Weekly status calls | Encrypted video conference (FIPS-compliant) | ISSO, 3PAO Lead, DevOps Lead |
| Sensitive finding notification | Encrypted email with digitally signed attachment | 3PAO Lead, ISSO, AO |
| Emergency communications | Direct phone (primary) and encrypted Signal (backup) | 3PAO Lead, ISSO |
| Artifact exchange | FedRAMP Secure Repository or agency-approved SFTP | All parties |

### 14.2 Escalation Path

| Scenario | First Escalation | Second Escalation |
|---|---|---|
| Schedule delay exceeding 5 business days | ISSO notifies AO | AO determines remediation path |
| Critical finding identified | 3PAO Lead notifies ISSO within 4 hours | ISSO notifies AO within 24 hours |
| Data exposure or security incident during assessment | 3PAO Lead notifies ISSO within 15 minutes | ISSO activates Incident Response Plan |
| 3PAO personnel conflict of interest identified | 3PAO Lead notifies ISSO immediately | ISSO notifies AO, personnel replaced |
| Scope dispute | ISSO and 3PAO Lead resolve bilaterally | AO makes final determination |

### 14.3 Status Reporting

The 3PAO Lead will provide weekly status reports every Tuesday during active assessment phases. Each report will include: controls assessed to date, open action items, upcoming week's planned activities, any emerging risks to the assessment schedule, and a red/yellow/green assessment health indicator.

---

## 15. Approval and Signature

This Security Assessment Plan is approved by the individuals below. Assessment activities may commence only after all required signatures have been obtained.

---

### Information System Security Officer (ISSO) and Information System Security Manager (ISSM)

**Name:** Enechi P.C. Njeze
**Title:** Information System Security Officer (ISSO) and Information System Security Manager (ISSM)
**Organization:** Federal Health Data Office (FHDO), CloudVault FHX Program
**Certifications:** CGRC, CISA, CISM, PMP, PMI-RMP, CompTIA Security+ SY0-701, CHP, CSCS, CISSP (in progress)

I have reviewed and approved this Security Assessment Plan. The scope, methodology, schedule, and rules of engagement defined herein accurately represent the assessment to be conducted against the CloudVault Federal Health Exchange. I authorize ClearPath Security Assessors LLC to conduct assessment activities within the boundaries established in this document.

**Signature:** ____________________________
**Date:** April 28, 2026

---

### Authorizing Official (AO)

**Name:** Henry Kline
**Title:** Deputy Director and Authorizing Official
**Organization:** Federal Health Data Office (FHDO)

I have reviewed and approved this Security Assessment Plan. I authorize the independent security assessment of the CloudVault Federal Health Exchange as described herein. Assessment results will inform my authorization decision.

**Signature:** ____________________________
**Date:** ____________________________

---

### 3PAO Lead Assessor

**Name:** Kristopher A. Wentworth
**Title:** Lead Assessor
**Organization:** ClearPath Security Assessors LLC
**FedRAMP 3PAO Accreditation:** A2LA Certificate 4821.01

I certify that ClearPath Security Assessors LLC is an accredited FedRAMP 3PAO with no conflict of interest with respect to the CloudVault Federal Health Exchange. This Security Assessment Plan accurately describes the assessment methodology, scope, and deliverables that ClearPath will execute and produce.

**Signature:** ____________________________
**Date:** ____________________________

---

### System Owner

**Name:** Dr. Sandra M. Okafor
**Title:** Deputy Assistant Secretary for Health Informatics and System Owner
**Organization:** Federal Health Data Office (FHDO)

**Signature:** ____________________________
**Date:** ____________________________

---

## Document Control

| Field | Value |
|---|---|
| Document ID | CV-FHX-SAP-001 |
| Version | 1.0 |
| Status | APPROVED FOR ASSESSMENT |
| Created | April 28, 2026 |
| Last Reviewed | April 28, 2026 |
| Next Review | Upon significant system change or annually |
| Prepared By | Enechi P.C. Njeze, ISSO and ISSM |
| Approved By | Henry Kline, Deputy Director and AO |
| Repository | cloudvault-fedramp-ato/assessments/ |
| Related Documents | SSP v1.0, FIPS 199 CV-FHX-FIPS199-001, SAR, POA&M |
| Supersedes | None (Initial SAP) |

---

*This document is UNCLASSIFIED and designated FOR OFFICIAL USE ONLY (FOUO). Distribution is limited to authorized personnel participating in the CloudVault Federal Health Exchange security authorization process.*

*CloudVault FHX GRC Portfolio, enechi-njeze/cloudvault-fedramp-ato*
*Maintained by Enechi P.C. Njeze, CGRC, CISA, CISM, PMP, PMI-RMP, Security+, CHP, CSCS*
