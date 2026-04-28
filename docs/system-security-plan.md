# System Security Plan (SSP)
# CloudVault Federal Health Exchange (FHX)

---

| Field | Details |
|---|---|
| **Document Title** | System Security Plan |
| **System Name** | CloudVault Federal Health Exchange (FHX) |
| **Version** | 1.0 |
| **Status** | Draft |
| **Classification** | Unclassified, Controlled Unclassified Information (CUI) |
| **Date Prepared** | April 2026 |
| **Next Review Date** | April 2027 |
| **Prepared By** | Marcus J. Reid, Information System Security Officer (ISSO) |
| **Approved By** | Angela Torres, Chief Information Security Officer (CISO) |
| **FedRAMP Baseline** | FedRAMP High, NIST SP 800-53 Rev 5, 421 Controls |

---

## Document Revision History

| Version | Date | Author | Description of Changes |
|---|---|---|---|
| 0.1 | January 2026 | Marcus J. Reid | Initial draft, system identification and boundary sections |
| 0.2 | February 2026 | Marcus J. Reid | Control implementation summary added, architecture section expanded |
| 0.3 | March 2026 | Angela Torres | CISO review and revisions, privacy and interconnection sections added |
| 1.0 | April 2026 | Marcus J. Reid | Final draft submitted for 3PAO review by CyberAudit Partners LLC |

---

## Table of Contents

1. [System Identification](#1-system-identification)
2. [System Description](#2-system-description)
3. [Authorization Boundary](#3-authorization-boundary)
4. [System Architecture Overview](#4-system-architecture-overview)
5. [Data Types and Sensitivity](#5-data-types-and-sensitivity)
6. [User Types and Roles](#6-user-types-and-roles)
7. [System Interconnections](#7-system-interconnections)
8. [Applicable Laws and Regulations](#8-applicable-laws-and-regulations)
9. [Key Personnel and Points of Contact](#9-key-personnel-and-points-of-contact)
10. [Control Implementation Summary](#10-control-implementation-summary)

---

## 1. System Identification

### 1.1 Basic System Information

| Field | Details |
|---|---|
| **System Name** | CloudVault Federal Health Exchange (FHX) |
| **System Abbreviation** | FHX |
| **System Owner Organization** | Federal Health Systems Division, U.S. Department of Health and Human Services |
| **Cloud Service Provider (CSP)** | CloudVault Technologies, Inc. |
| **Cloud Service Model** | Software as a Service (SaaS) |
| **Deployment Model** | Government Community Cloud |
| **Cloud Platform** | Amazon Web Services (AWS) GovCloud |
| **Primary Region** | us-gov-east-1 |
| **Secondary Region** | us-gov-west-1 (Disaster Recovery) |
| **System Version** | FHX Release 4.2.1 |
| **Unique System Identifier** | FHX-GOV-2021-0047 |

### 1.2 Security Categorization

| Security Objective | Impact Level | Rationale |
|---|---|---|
| **Confidentiality** | HIGH | System processes PHI, PII, CUI, FTI, and PCI for 47 federal health agencies. Unauthorized disclosure would cause severe harm to individuals and violate multiple federal statutes. |
| **Integrity** | HIGH | Clinical decision-making and patient safety depend on the accuracy and completeness of health records. Unauthorized modification could result in incorrect treatment decisions and direct harm to patients. |
| **Availability** | HIGH | Healthcare providers require continuous access to patient records, including during medical emergencies. System downtime during critical care events constitutes a life-safety risk. |
| **Overall Categorization** | **HIGH** | Per FIPS 199: {HIGH} = (Confidentiality: HIGH, Integrity: HIGH, Availability: HIGH) |

The security categorization was formally documented in the FIPS 199 Security Categorization Worksheet, located at [assessments/fips199-security-categorization.md](../assessments/fips199-security-categorization.md), and approved by the Authorizing Official, Deputy Director Henry Kline.

### 1.3 Authorization Information

| Field | Details |
|---|---|
| **Authorization Type** | Dual track: Agency ATO and JAB Provisional ATO (P-ATO) |
| **Agency ATO Authorizing Official** | Deputy Director Henry Kline |
| **JAB Representatives** | Col. Diana Marsh (DoD), Frank Osei (DHS), Carol Whitfield (GSA) |
| **FedRAMP Authorization Status** | In Progress |
| **Previous ATO Expiration** | N/A (initial authorization) |
| **3PAO** | CyberAudit Partners LLC, FedRAMP-accredited |

---

## 2. System Description

### 2.1 Purpose and Mission

The CloudVault Federal Health Exchange (FHX) is a federally operated, cloud-based health data exchange platform designed to enable the secure collection, storage, processing, and sharing of health information across federal government agencies. The system serves as the central interoperability hub connecting 47 federal health agencies, enabling authorized healthcare providers, case managers, and federal administrators to access and exchange patient health records in real time.

FHX was established to address a critical gap in federal health data infrastructure: the inability of federal agencies to securely share patient information across organizational boundaries. Before FHX, patient records were siloed within individual agency systems, leading to duplicated testing, incomplete medical histories, delayed treatment decisions, and significant administrative burden on both providers and patients. FHX eliminates these barriers while maintaining the highest standards of data protection required by federal law.

### 2.2 System Functions

The CloudVault FHX platform provides the following core functions:

**Patient Record Management:** FHX maintains a longitudinal health record for each enrolled patient, aggregating clinical data from all connected agency systems into a unified, structured patient profile. Records include diagnoses, medications, allergies, immunization history, laboratory results, imaging reports, and care plans.

**Secure Data Exchange:** The system enables real-time, bi-directional exchange of health information between authorized federal agencies using industry-standard health interoperability protocols (HL7 FHIR R4). All data in transit is encrypted using TLS 1.3 and all data at rest is encrypted using AES-256.

**Clinical Decision Support:** FHX provides authorized clinicians with decision support tools including drug interaction alerts, evidence-based care recommendations, and patient risk stratification based on longitudinal record analysis.

**Federal Reporting and Analytics:** The system generates required federal health reporting outputs for compliance with the Centers for Medicare and Medicaid Services (CMS), the Department of Veterans Affairs (VA), the Indian Health Service (IHS), and other federal health oversight bodies.

**Audit and Compliance:** Every access event, data modification, and system transaction is logged to a tamper-evident audit trail retained for a minimum of seven years in compliance with NARA General Records Schedule 3.2.

### 2.3 System Scale and Scope

| Metric | Value |
|---|---|
| **Federal Agencies Served** | 47 |
| **Patient Records** | 890,000+ |
| **System Endpoints** | 12,000+ |
| **Active Users** | Approximately 28,000 |
| **Daily Transactions** | Approximately 1.4 million |
| **Data Volume** | 47 TB active, 290 TB archived |
| **Uptime Requirement** | 99.9% (approximately 8.7 hours downtime per year maximum) |

---

## 3. Authorization Boundary

### 3.1 Boundary Description

The FedRAMP authorization boundary for CloudVault FHX encompasses all hardware, software, data, personnel, and facilities owned or controlled by CloudVault Technologies, Inc. that are used to deliver the FHX service to federal agency customers. The boundary includes all components hosted in AWS GovCloud (us-gov-east-1 and us-gov-west-1) that are under the direct operational control of the CloudVault FHX team.

The boundary explicitly excludes federal agency customer environments, end-user workstations, agency network infrastructure, and internet service provider (ISP) components, even where those components are used to access FHX. These external components represent the customer responsibility layer and are governed by individual agency ATOs and interconnection security agreements.

### 3.2 Components Within the Authorization Boundary

| Component | Type | Description |
|---|---|---|
| FHX Application Servers | Compute (AWS EC2) | Application logic tier hosting the FHX web services, APIs, and clinical decision support engine |
| FHX Database Cluster | Data (AWS RDS) | Primary relational database storing patient records, audit logs, and system configuration |
| FHX Data Warehouse | Data (AWS Redshift) | Analytical data store for federal reporting and population health analytics |
| Object Storage | Data (AWS S3) | Encrypted storage for medical imaging files, documents, and backup archives |
| API Gateway | Network (AWS API Gateway) | Managed API endpoint layer governing all inbound and outbound data exchange |
| Identity and Access Management | Security (AWS IAM, Identity Center) | Centralized identity, authentication, and authorization management for all user types |
| Web Application Firewall | Security (AWS WAF) | Layer 7 traffic filtering and DDoS protection for all public-facing endpoints |
| Load Balancers | Network (AWS ALB) | Application load balancing across availability zones within each GovCloud region |
| Virtual Private Cloud | Network (AWS VPC) | Isolated network environment with defined subnets, routing tables, and security groups |
| Key Management Service | Security (AWS KMS) | FIPS 140-2 validated key management for all encryption operations |
| CloudTrail and Config | Logging (AWS) | Continuous audit logging and configuration compliance monitoring |
| GuardDuty and Security Hub | Security (AWS) | Threat detection, security findings aggregation, and compliance dashboard |
| DR Environment | Compute and Data (us-gov-west-1) | Full standby environment in the secondary GovCloud region for disaster recovery |

### 3.3 Components Outside the Authorization Boundary

| Component | Owner | Relationship to FHX |
|---|---|---|
| Federal Agency Networks | Individual agencies | Provide network connectivity for authorized users to reach FHX endpoints |
| Agency End-User Workstations | Individual agencies | Devices used by clinicians and administrators to access the FHX web interface |
| Internet Service Providers | Commercial ISPs | Carry network traffic between agency locations and FHX GovCloud endpoints |
| AWS GovCloud Infrastructure | Amazon Web Services | Underlying physical infrastructure is covered by the AWS FedRAMP High P-ATO |
| Agency Identity Providers | Individual agencies | Some agencies use their own PIV/CAC identity providers federated to FHX via SAML 2.0 |

> **Note on AWS Inheritance:** CloudVault FHX inherits a set of controls from the AWS GovCloud FedRAMP High P-ATO. These inherited controls cover the physical and environmental protection of AWS data centers, physical media protection, and foundational network infrastructure. The controls inherited from AWS are identified in the Control Origination Worksheet at [ssp-attachments/appendix-d-control-origination.md](../ssp-attachments/appendix-d-control-origination.md).

---

## 4. System Architecture Overview

### 4.1 Architecture Summary

CloudVault FHX is deployed in a multi-tier, multi-availability-zone architecture within AWS GovCloud. The architecture is designed to meet the FedRAMP High availability requirement and to enforce defense-in-depth security at every layer. The system operates across two GovCloud regions: us-gov-east-1 serves as the primary production environment, and us-gov-west-1 provides a warm standby disaster recovery environment with an RTO of 4 hours and an RPO of 1 hour.

### 4.2 Network Architecture

The FHX network is segmented into four distinct tiers, each implemented as a separate VPC subnet with dedicated security groups and network ACLs:

**Public Subnet (DMZ):** Contains the AWS Application Load Balancer and WAF. This tier receives inbound HTTPS traffic from authorized federal agency users and external systems. No application logic or data resides in this tier.

**Application Subnet:** Contains the FHX application servers (EC2 Auto Scaling group), the API Gateway integration layer, and the clinical decision support engine. This tier communicates with the DMZ tier for inbound requests and with the data tier for database operations. No direct internet access is permitted from this subnet.

**Data Subnet:** Contains the RDS database cluster (multi-AZ), the Redshift data warehouse, and the S3 bucket endpoints. This tier has no inbound connectivity from the public subnet. All access from the application tier is governed by security group rules restricting traffic to specific ports and protocols.

**Management Subnet:** Contains the AWS Systems Manager endpoints, CloudTrail collectors, GuardDuty sensors, and Security Hub aggregation points. This tier is isolated from all application and data traffic and is accessible only through AWS PrivateLink.

### 4.3 Data Flow Summary

All data entering FHX from external federal agency systems is encrypted in transit using TLS 1.3 with FIPS 140-2 validated cipher suites. Data is decrypted at the application tier, processed, and stored in the data tier encrypted at rest using AES-256 keys managed by AWS KMS with FIPS 140-2 validated hardware security modules (HSMs). No unencrypted patient data traverses any network segment within the FHX environment.

The full data flow diagram showing all external entities, data stores, and data exchanges is located at [diagrams/phi-pii-data-flow-diagram.png](../diagrams/phi-pii-data-flow-diagram.png).

---

## 5. Data Types and Sensitivity

### 5.1 Information Types Inventory

CloudVault FHX processes the following categories of sensitive federal information, all classified at HIGH sensitivity:

| Data Type | Full Name | Federal Standard | Sensitivity | Volume |
|---|---|---|---|---|
| **PHI** | Protected Health Information | HIPAA Privacy Rule, 45 CFR Part 164 | HIGH | 890,000+ patient records |
| **PII** | Personally Identifiable Information | OMB M-07-16, NIST SP 800-122 | HIGH | Contained within all patient records |
| **CUI** | Controlled Unclassified Information | 32 CFR Part 2002, CUI Registry | HIGH | Federal case management records and inter-agency referrals |
| **FTI** | Federal Tax Information | IRS Publication 1075, IRC Section 6103 | HIGH | Income and eligibility data for means-tested health programs |
| **PCI** | Payment Card Industry Data | PCI DSS v4.0 | HIGH | Co-pay and patient billing records for applicable programs |

### 5.2 Data Sensitivity Justification

The combination of data types processed by FHX creates an exceptionally sensitive information environment. A single patient record within FHX may contain PHI (medical diagnoses and treatment history), PII (name, date of birth, Social Security number, address), FTI (income data used for program eligibility), and payment data. The aggregation of these data types within a single system elevates the potential impact of a breach well beyond what any individual data type would represent in isolation.

This aggregation risk is a primary driver of the HIGH confidentiality impact classification and a key factor in the Authorizing Official's risk assessment.

### 5.3 Data Retention

| Data Category | Retention Period | Authority |
|---|---|---|
| Patient Health Records | Minimum 7 years from last activity | NARA GRS 3.2, HIPAA |
| Audit Logs | Minimum 7 years | NARA GRS 3.2 |
| System Backups | 90 days rolling | CloudVault FHX Data Management Policy |
| Archived Records | 25 years | NARA General Records Schedule |

---

## 6. User Types and Roles

### 6.1 User Categories

CloudVault FHX supports four categories of users, each with a defined access profile, authentication requirement, and role-based permission set.

| User Type | Description | Authentication Requirement | Approximate Count |
|---|---|---|---|
| **Federal Clinicians** | Licensed healthcare providers employed by federal agencies (VA, IHS, MHS, BOP Health Services) who access and update patient health records | PIV/CAC card plus PIN, or MFA with FIPS 140-2 validated authenticator | 14,000 |
| **Federal Administrators** | Agency health program administrators, case managers, and eligibility workers who manage patient enrollment, referrals, and program participation | PIV/CAC card plus PIN | 10,000 |
| **System Administrators** | CloudVault FHX platform administrators responsible for infrastructure operations, patching, configuration management, and monitoring | PIV/CAC card plus PIN, plus privileged access workstation (PAW) | 45 |
| **Security Personnel** | ISSO, security engineers, and authorized 3PAO assessors with read-only access to audit logs, security dashboards, and configuration data | PIV/CAC card plus PIN, plus time-limited session tokens | 28 |

### 6.2 Privilege Levels

| Privilege Level | Description | Controls Applied |
|---|---|---|
| **Read-Only** | View patient records for authorized patients only. No creation, modification, or deletion of data. | Least privilege, patient consent verification, audit logging |
| **Read/Write (Clinical)** | Create and update clinical records for authorized patients. Cannot delete records or modify audit logs. | Clinical license verification, patient assignment controls, audit logging |
| **Administrative** | Manage patient enrollment, program assignments, and referrals. Cannot access clinical record content beyond demographic data. | Role separation from clinical users, supervisory approval for sensitive actions |
| **System Administration** | Configure and maintain platform infrastructure. No access to patient data. | Privileged Access Workstation (PAW) requirement, session recording, just-in-time access |
| **Security Administration** | Read-only access to security logs, dashboards, and configuration compliance data. | Time-limited access tokens, dual-person integrity for sensitive operations |

---

## 7. System Interconnections

CloudVault FHX maintains formal interconnections with external federal systems. Each interconnection is governed by a signed Interconnection Security Agreement (ISA) or Memorandum of Understanding (MOU) that defines the data exchanged, the protocols used, the security controls applied, and the responsibilities of each party. All interconnection documents are maintained at [ssp-attachments/interconnection-security-agreements.md](../ssp-attachments/interconnection-security-agreements.md).

### 7.1 Interconnected Systems

| System | Owning Agency | Data Exchanged | Protocol | Agreement Type |
|---|---|---|---|---|
| Veterans Health Information Systems and Technology Architecture (VistA) | Department of Veterans Affairs (VA) | Patient health records, appointment data, medication lists | HL7 FHIR R4 over HTTPS/TLS 1.3 | ISA |
| Indian Health Service Electronic Health Record (IHS EHR) | Indian Health Service (IHS) | Patient clinical records, referral data, lab results | HL7 FHIR R4 over HTTPS/TLS 1.3 | ISA |
| Military Health System Genesis (MHS Genesis) | Defense Health Agency (DHA) | Active duty and dependent health records, deployment health data | HL7 FHIR R4 over HTTPS/TLS 1.3 | ISA |
| Federal Employee Health Benefits (FEHB) Data Portal | Office of Personnel Management (OPM) | Enrollment and eligibility data, insurance coverage records | REST API over HTTPS/TLS 1.3 | ISA |
| CMS Medicaid and Medicare Data Systems | Centers for Medicare and Medicaid Services (CMS) | Eligibility data, claims summaries, program enrollment | REST API over HTTPS/TLS 1.3 | MOU |
| IRS Disclosure Office (FTI) | Internal Revenue Service (IRS) | Federal tax information for income-based program eligibility | Secure File Transfer, SFTP with FIPS ciphers | ISA with IRS 1075 addendum |
| Federal Identity, Credential, and Access Management (FICAM) | General Services Administration (GSA) | PIV/CAC identity assertions, federated authentication tokens | SAML 2.0 over HTTPS | MOU |

---

## 8. Applicable Laws and Regulations

The CloudVault FHX system is subject to the following federal laws, regulations, executive orders, standards, and guidance documents. Compliance with each is required as a condition of operating as a federal information system and as a FedRAMP High authorized cloud service provider.

| Category | Document | Relevance to CloudVault FHX |
|---|---|---|
| **Federal Information Security** | Federal Information Security Modernization Act (FISMA) 2014 | Requires all federal information systems to undergo a formal risk-based authorization and maintain a continuous monitoring program |
| **Federal Information Security** | NIST SP 800-53 Rev 5 | Defines the 421 security and privacy controls that form the FedRAMP High control baseline for FHX |
| **Federal Information Security** | NIST SP 800-37 Rev 2 | Defines the Risk Management Framework (RMF) process followed for FHX authorization |
| **Federal Information Security** | FIPS 199 | Establishes the HIGH impact categorization for FHX based on the sensitivity of PHI, PII, CUI, FTI, and PCI |
| **Federal Information Security** | FIPS 200 | Defines the minimum security requirements that FHX must meet across 17 security areas |
| **Cloud Authorization** | FedRAMP Authorization Act (2022) | Establishes the statutory basis for FedRAMP and the JAB P-ATO track |
| **Health Information** | Health Insurance Portability and Accountability Act (HIPAA), 45 CFR Parts 160 and 164 | Governs the collection, use, disclosure, and protection of Protected Health Information (PHI) |
| **Health Information** | Health Information Technology for Economic and Clinical Health Act (HITECH) | Strengthens HIPAA enforcement and breach notification requirements for electronic PHI |
| **Health Information** | NIST SP 800-66 Rev 2 | Provides implementation guidance for the HIPAA Security Rule |
| **Tax Information** | Internal Revenue Code Section 6103 | Restricts disclosure of Federal Tax Information (FTI) and requires specific safeguards |
| **Tax Information** | IRS Publication 1075 | Defines security requirements for federal agencies and contractors that receive FTI |
| **Privacy** | Privacy Act of 1974, 5 U.S.C. 552a | Governs federal agency collection and maintenance of records about individuals |
| **Privacy** | OMB Circular A-130 | Establishes federal policy for information resources management and privacy protection |
| **Privacy** | E-Government Act of 2002, Section 208 | Requires Privacy Impact Assessments (PIAs) for systems collecting PII |
| **Payment Card** | PCI DSS v4.0 | Governs the handling of payment card data for applicable billing functions |
| **Cybersecurity** | Executive Order 14028 (Improving the Nation's Cybersecurity) | Requires Zero Trust architecture adoption, MFA enforcement, and EDR deployment |
| **Records** | NARA General Records Schedule (GRS) 3.2 | Establishes minimum retention periods for health records and audit logs |
| **Acquisition** | FAR Clause 52.239-1 | Privacy and Security Safeguards clause required in all FHX-related contracts |

---

## 9. Key Personnel and Points of Contact

| Role | Name | Organization | Responsibilities |
|---|---|---|---|
| **System Owner** | Dr. Patricia Owens | Federal Health Systems Division | Accountable executive for FHX mission, resources, and risk decisions |
| **Authorizing Official (Agency ATO)** | Deputy Director Henry Kline | Federal Health Systems Division | Formal risk acceptance authority for the Agency ATO |
| **JAB Representative, DoD** | Col. Diana Marsh | Department of Defense | DoD review and concurrence for JAB P-ATO |
| **JAB Representative, DHS** | Frank Osei | Department of Homeland Security | DHS review and concurrence for JAB P-ATO |
| **JAB Representative, GSA** | Carol Whitfield | General Services Administration | GSA review and concurrence for JAB P-ATO |
| **Chief Information Security Officer** | Angela Torres | CloudVault Technologies, Inc. | Security program oversight, policy approval, SSP approval |
| **Information System Security Officer** | Marcus J. Reid | CloudVault Technologies, Inc. | Day-to-day security operations, SSP maintenance, ConMon submissions |
| **Privacy Officer** | Sandra Voss | Federal Health Systems Division | Privacy compliance, PIA maintenance, breach notification |
| **3PAO Lead Assessor** | Assigned by CyberAudit Partners LLC | CyberAudit Partners LLC | Independent security assessment, SAP and SAR authorship |
| **FedRAMP PMO Contact** | FedRAMP PMO Help Desk | General Services Administration | FedRAMP package review, PMO liaison, ConMon oversight |

---

## 10. Control Implementation Summary

This section provides a summary-level view of the implementation status of all 20 NIST SP 800-53 Rev 5 control families within the FedRAMP High baseline for CloudVault FHX. Detailed control-by-control implementation statements for all 421 controls are maintained in the Control Implementation Summary (CIS) at [docs/control-implementation-summary.md](control-implementation-summary.md).

### 10.1 Control Family Implementation Overview

| ID | Control Family | Controls in Baseline | Implementation Status | Primary Responsible Party | Key Implementation Notes |
|---|---|---|---|---|---|
| AC | Access Control | 25 | In Progress | CloudVault ISSO | AWS IAM Identity Center with PIV/CAC federation, least privilege role assignments, privileged access workstations for administrators |
| AT | Awareness and Training | 6 | In Progress | CloudVault ISSO | Annual security awareness training for all 28,000 users, role-based training for privileged users and security personnel |
| AU | Audit and Accountability | 16 | In Progress | CloudVault ISSO | AWS CloudTrail (all API calls), VPC Flow Logs, application audit logs retained 7 years, SIEM integration via AWS Security Hub |
| CA | Assessment, Authorization, and Monitoring | 9 | In Progress | CloudVault ISSO | Dual-track FedRAMP authorization in progress, continuous authorization monitoring via ConMon program |
| CM | Configuration Management | 12 | In Progress | CloudVault ISSO | CIS Benchmark hardened AMIs, AWS Config for drift detection, formal change management process per CMP |
| CP | Contingency Planning | 13 | In Progress | CloudVault ISSO | Multi-AZ primary deployment, warm standby DR in us-gov-west-1, RTO: 4 hours, RPO: 1 hour, annual DR test required |
| IA | Identification and Authentication | 12 | In Progress | CloudVault ISSO | PIV/CAC card with PIN for all federal users, FIPS 140-2 validated MFA, hardware token for privileged accounts |
| IR | Incident Response | 10 | In Progress | CloudVault ISSO | Documented IRP aligned to NIST SP 800-61 Rev 2, 24/7 SOC monitoring, FedRAMP breach notification within 1 hour |
| MA | Maintenance | 6 | In Progress | CloudVault ISSO | All maintenance performed by vetted personnel, remote maintenance logged and supervised, no maintenance during peak hours without AO approval |
| MP | Media Protection | 8 | In Progress | CloudVault ISSO | No physical media in scope (cloud-native), S3 and EBS encryption at rest, AWS KMS key management, NIST SP 800-88 sanitization for decommissioned instances |
| PE | Physical and Environmental Protection | 20 | Inherited (AWS) | Amazon Web Services | Physical controls fully inherited from AWS GovCloud FedRAMP High P-ATO. AWS SOC 2 Type II and ISO 27001 reports on file. |
| PL | Planning | 11 | In Progress | CloudVault ISSO | SSP (this document), Privacy Impact Assessment, Rules of Behavior, and Security CONOPS maintained and reviewed annually |
| PM | Program Management | 32 | In Progress | Angela Torres (CISO) | Formal information security program, risk management strategy, threat intelligence integration, supply chain risk management plan |
| PS | Personnel Security | 9 | In Progress | CloudVault ISSO | NACI background checks for all personnel with FHX access, position risk designations, immediate access revocation upon separation |
| PT | PII Processing and Transparency | 8 | In Progress | Sandra Voss (Privacy Officer) | Privacy notices displayed at all data collection points, PIA maintained and reviewed annually, SORN published in Federal Register |
| RA | Risk Assessment | 10 | In Progress | CloudVault ISSO | Annual risk assessment, continuous vulnerability scanning via Qualys and Nessus, threat modeling reviewed quarterly |
| SA | System and Services Acquisition | 23 | In Progress | Angela Torres (CISO) | Security requirements in all procurement contracts, developer security training, software composition analysis for all third-party components |
| SC | System and Communications Protection | 44 | In Progress | CloudVault ISSO | TLS 1.3 for all data in transit, AES-256 for all data at rest, VPC isolation, WAF, network segmentation across four tiers |
| SI | System and Information Integrity | 23 | In Progress | CloudVault ISSO | Anti-malware on all endpoints, automated patch management with 30-day HIGH remediation SLA, file integrity monitoring, spam protection |
| SR | Supply Chain Risk Management | 12 | In Progress | Angela Torres (CISO) | Vendor risk assessments for all third-party components, software provenance verification, ICT supply chain monitoring program |

### 10.2 Control Origination Summary

The controls listed above are implemented through a combination of origination types. The table below summarizes how each origination type applies to FHX:

| Origination Type | Description | Example Controls |
|---|---|---|
| **CSP Provided** | CloudVault Technologies fully implements and manages the control | AU-2 (Audit Events), IR-4 (Incident Handling), SI-2 (Flaw Remediation) |
| **CSP Provided, Customer Configured** | CloudVault provides the capability; each agency customer configures it for their users | AC-2 (Account Management), IA-2 (Multi-Factor Authentication) |
| **Customer Provided** | The agency customer is fully responsible for implementing the control in their environment | PE-2 (Physical Access Authorizations at agency offices), PS-3 (Personnel Screening) |
| **Inherited (AWS)** | Control is fully inherited from the AWS GovCloud FedRAMP High P-ATO | PE-1 through PE-20 (Physical and Environmental Protection), MA-2 (Controlled Maintenance) |
| **Hybrid** | Both CloudVault and the customer share responsibility for implementing the control | CA-3 (Information Exchange), SA-9 (External System Services) |

---

## Document Approval

| Role | Name | Signature | Date |
|---|---|---|---|
| **ISSO** | Marcus J. Reid | *Pending final signature* | April 2026 |
| **CISO** | Angela Torres | *Pending final signature* | April 2026 |
| **System Owner** | Dr. Patricia Owens | *Pending final signature* | April 2026 |
| **Authorizing Official** | Deputy Director Henry Kline | *Pending authorization decision* | TBD |

---

> This System Security Plan is a controlled document. It contains Controlled Unclassified Information (CUI) and must be handled in accordance with the CloudVault FHX Information Handling Policy and applicable federal CUI requirements under 32 CFR Part 2002.

*Part of the CloudVault FHX GRC Portfolio | cloudvault-fedramp-ato | Version 1.0 | April 2026*
