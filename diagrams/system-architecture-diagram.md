# System Architecture Diagram
## CloudVault Federal Health Exchange (FHX)
### FedRAMP High Authorization Boundary -- AWS GovCloud Deployment

---

**Document Control**

| Field | Value |
|---|---|
| Document ID | CV-FHX-ARCH-2025-001 |
| Version | 1.2 |
| Last Updated | March 15, 2026 |
| Prepared By | Enechi P.C. Njeze, ISSO/ISSM |
| Classification | FedRAMP Controlled Unclassified Information (CUI) |
| Related Document | System Security Plan, Section 2 (System Description) |

> This document contains architecture diagrams rendered in Markdown and ASCII format. In a production engagement, these diagrams would be accompanied by Visio, Lucidchart, or draw.io exports included as SSP Attachment 1 (Architecture Diagrams). Those exports are referenced in [ssp-attachments/ssp-attachment-index.md](../ssp-attachments/ssp-attachment-index.md).

---

## 1. High-Level Architecture Overview

The following diagram represents the CloudVault FHX authorization boundary and its key interconnections. All components within the dashed boundary are in scope for the FedRAMP High authorization.

```
+==================================================================================+
|                    CLOUDVAULT FHX -- FEDRAMP HIGH AUTHORIZATION BOUNDARY         |
|                         AWS GovCloud (US-East Primary)                           |
|                                                                                  |
|  +----------------------------------+   +------------------------------------+   |
|  |     PUBLIC SUBNET (DMZ TIER)     |   |    MANAGEMENT / MONITORING VPC     |   |
|  |                                  |   |                                    |   |
|  |  [AWS WAF v2]                    |   |  [Splunk SIEM]                     |   |
|  |  [AWS Shield Advanced]           |   |  [Tenable.io]                      |   |
|  |  [Application Load Balancer]     |   |  [AWS CloudTrail (all-region)]     |   |
|  |  [CloudFront (API edge)]         |   |  [AWS Config + Config Rules]       |   |
|  +---------|------------------------+   |  [Amazon GuardDuty]                |   |
|            |                           |  [AWS Security Hub]                |   |
|            | (HTTPS/443 only)          |  [AWS Macie (PHI/PII detection)]   |   |
|            v                           +------------------------------------+   |
|  +----------------------------------+                                           |
|  |    PRIVATE SUBNET (APP TIER)     |                                           |
|  |                                  |                                           |
|  |  [Amazon ECS Cluster]            |   +------------------------------------+   |
|  |    - FHX API Services            |   |   IDENTITY AND ACCESS MGMT TIER    |   |
|  |    - Eligibility Engine          |   |                                    |   |
|  |    - Clinical Data Service       |   |  [AWS IAM Identity Center]         |   |
|  |    - Notification Service        |   |  [CyberArk PAM]                    |   |
|  |  [Amazon EC2 Auto-Scaling Group] |   |  [Okta Federal IDP]                |   |
|  |    - App Server Fleet (16 inst.) |   |  [PIV/CAC Integration]             |   |
|  |  [AWS Lambda (event processing)] |   |  [FIDO2/WebAuthn (admin MFA)]      |   |
|  +---------|------------------------+   +------------------------------------+   |
|            |                                                                     |
|            | (Private VPC routing, no internet path)                            |
|            v                                                                     |
|  +----------------------------------+                                           |
|  |    PRIVATE SUBNET (DATA TIER)    |                                           |
|  |                                  |                                           |
|  |  [Amazon RDS PostgreSQL]         |                                           |
|  |    - Multi-AZ, encrypted at rest |                                           |
|  |    - PHI/PII primary datastore   |                                           |
|  |  [Amazon DynamoDB]               |                                           |
|  |    - Session state, metadata     |                                           |
|  |  [Amazon S3 (147 buckets)]       |                                           |
|  |    - PHI/CUI objects (SSE-KMS)   |                                           |
|  |    - Audit logs                  |                                           |
|  |    - Backup archives             |                                           |
|  |  [AWS KMS (CMK)]                 |                                           |
|  |    - All encryption keys         |                                           |
|  |    - Annual rotation enforced    |                                           |
|  +----------------------------------+                                           |
|                                                                                  |
+==================================================================================+
         |                          |                         |
         | AWS Direct Connect       | AWS Direct Connect      | Internet (HTTPS)
         | (FHDO Primary)           | (Agency Interconnects)  | (PIV Auth only)
         v                          v                         v
+------------------+   +----------------------+   +------------------+
|   FHDO AGENCY    |   |  47 FEDERAL AGENCIES |   |  BENEFICIARY     |
|   NETWORK        |   |  (VA, CMS, IHS, etc.)|   |  PORTAL (READ    |
|   (On-premise)   |   |  (Direct Connect)    |   |  ONLY, PIV/AAL2) |
+------------------+   +----------------------+   +------------------+

         |
         v
+==================================================================================+
|                    AWS GovCloud (US-WEST) -- DISASTER RECOVERY                   |
|                                                                                  |
|   [Hot Standby replication of all App Tier and Data Tier components]             |
|   [RTO: 4 hours | RPO: 1 hour]                                                  |
|   [Cross-region S3 replication (SSE-KMS, same CMK key policy)]                  |
|   [RDS Read Replica promoted to primary on DR event]                             |
|   [CloudTrail replication to DR region]                                          |
|                                                                                  |
+==================================================================================+
```

---

## 2. Network Segmentation Detail

CloudVault FHX employs a strict three-tier network segmentation model enforced through AWS VPC architecture, security groups, and Network Access Control Lists (NACLs). No tier is permitted to communicate directly with a non-adjacent tier.

### 2.1 DMZ Tier (Public Subnets)

The DMZ tier is the only tier with internet-facing components. All inbound traffic is inspected by AWS WAF v2 before reaching the load balancer. AWS Shield Advanced provides DDoS mitigation at Layers 3, 4, and 7. Only HTTPS (TCP/443) traffic is permitted inbound. Outbound internet access from the DMZ tier is blocked; all outbound communication routes to the App Tier via internal VPC routing.

| Component | Purpose | Inbound Ports | Outbound |
|---|---|---|---|
| AWS WAF v2 | Layer 7 inspection, OWASP rule set, rate limiting | 443 (from internet) | App Tier ALB |
| AWS Shield Advanced | DDoS mitigation (L3/L4/L7) | All (transparent) | Transparent |
| Application Load Balancer | TLS termination, routing to ECS targets | 443 (from WAF) | App Tier ECS (8443) |
| CloudFront | API edge caching and CDN | 443 (from internet) | ALB (443) |

### 2.2 Application Tier (Private Subnets -- App)

The application tier runs all compute workloads. No direct internet access is permitted. Outbound internet access for patch downloads and AWS service APIs routes through AWS NAT Gateway (logged) or AWS PrivateLink endpoints (preferred). Internal service-to-service communication uses TLS 1.2 minimum (migration to TLS 1.3 in progress per POA&M CV-FHX-POAM-2026-006).

| Component | Purpose | Inbound (from DMZ) | Outbound (to Data) |
|---|---|---|---|
| ECS Cluster (16 services) | Microservices application logic | TCP/8443 (from ALB) | TCP/5432 (RDS), TCP/443 (DynamoDB endpoint) |
| EC2 Auto-Scaling Group | Batch processing, legacy integrations | TCP/8080 (from ALB) | TCP/5432, TCP/443 |
| AWS Lambda | Event-driven processing (HL7, X12) | Event triggers only | TCP/5432, S3 endpoints |
| AWS Systems Manager | Patch management, session manager | SSM endpoint only | SSM, S3 endpoints |

### 2.3 Data Tier (Private Subnets -- Data)

The data tier is isolated from all internet paths. No NAT gateway or internet gateway routes exist for data tier subnets. All data at rest is encrypted using AWS KMS Customer Managed Keys (CMKs) with annual rotation enforced via AWS Config rule. Cross-region replication to US-West occurs over AWS private backbone (never the public internet).

| Component | Encryption at Rest | Encryption in Transit | Backup |
|---|---|---|---|
| RDS PostgreSQL (Multi-AZ) | AES-256 (KMS CMK) | TLS 1.2+ (enforced) | Daily automated, 35-day retention |
| DynamoDB | AES-256 (KMS CMK) | TLS 1.2+ (enforced) | Point-in-time recovery (35 days) |
| S3 (147 buckets) | SSE-KMS (CMK, annual rotation) | TLS 1.2+ (bucket policy enforced) | Versioning + Cross-region replication |
| AWS KMS CMKs | HSM-backed (FIPS 140-2 Level 3) | N/A (key material never exported) | Multi-region key replication |

---

## 3. Data Flow Diagrams

### 3.1 Agency Health Data Exchange Flow

The following describes the end-to-end data flow for an agency-initiated health record exchange request.

```
[Agency System]
     |
     | (1) TLS 1.2+ over AWS Direct Connect
     v
[CloudVault FHX ALB / WAF]
     |
     | (2) WAF inspection, request authenticated via agency service account (IAM)
     v
[ECS: FHX API Gateway Service]
     |
     | (3) Authorization check against RBAC policy engine
     | (4) Audit log entry written to CloudTrail + Splunk
     v
[ECS: Clinical Data Service]
     |
     | (5) Query RDS (patient record lookup by agency-specific identifier)
     v
[RDS PostgreSQL -- PHI/PII Datastore]
     |
     | (6) Encrypted record returned to Clinical Data Service
     v
[ECS: Clinical Data Service]
     |
     | (7) HL7 FHIR R4 response constructed, PII minimized per agency data sharing agreement
     | (8) Response audit log written
     v
[Agency System] <-- TLS 1.2+, response returned
```

### 3.2 Beneficiary Portal Authentication Flow

```
[Beneficiary Browser]
     |
     | (1) HTTPS/443, CloudFront edge
     v
[Okta Federal IDP -- Step-Up Auth]
     |
     | (2) IAL2 identity proofing (first use), AAL2 MFA (returning user)
     | (3) PIV/CAC or FIDO2 authenticator challenge
     v
[Okta Federal IDP -- Token Issuance]
     |
     | (4) JWT access token (15-minute expiry), refresh token (8-hour session max)
     v
[FHX API Gateway Service]
     |
     | (5) Token validation, RBAC authorization (read-only scope for beneficiaries)
     | (6) Audit log: beneficiary ID, timestamp, data elements accessed
     v
[Clinical Data Service -- Read Only]
     |
     | (7) PHI returned scoped to authenticated beneficiary record only
     v
[Beneficiary Browser] <-- Rendered via CloudFront (no PHI cached at edge)
```

### 3.3 Privileged Administrative Access Flow

```
[Administrator Workstation (FHDO FIPS-compliant endpoint)]
     |
     | (1) HTTPS/443 to CyberArk PAM Web Portal (not internet-facing; accessible via agency VPN only)
     v
[CyberArk PAM]
     |
     | (2) PIV/CAC + FIDO2 hardware token MFA (NIST AAL3)
     | (3) Just-In-Time (JIT) access request, approval workflow required for production access
     | (4) Session recording begins automatically
     v
[AWS IAM Identity Center -- Privileged Role Assumed]
     |
     | (5) Time-limited STS credentials issued (maximum 1-hour session)
     v
[Target System Component (EC2, RDS, ECS Task)]
     |
     | (6) All session activity recorded and indexed in CyberArk and Splunk
     | (7) Session terminates automatically at credential expiry
     v
[CyberArk PAM -- Session Record Retained (7 years per NIST SP 800-92)]
```

---

## 4. External Interconnections

The following external connections cross the CloudVault FHX authorization boundary. All interconnections are governed by Interconnection Security Agreements (ISAs) and Memoranda of Understanding (MOUs) as required by NIST SP 800-47 Rev 1 and documented in SSP Attachment 6.

| Connection | Type | Direction | Protocol/Port | Data Types | ISA Reference |
|---|---|---|---|---|---|
| FHDO Agency Network | AWS Direct Connect (dedicated 10 Gbps) | Bidirectional | TLS 1.2+/443 | PHI, PII, CUI | ISA-001 |
| Department of Veterans Affairs | AWS Direct Connect (shared 1 Gbps) | Bidirectional | TLS 1.2+/443 | PHI, PII | ISA-002 |
| Indian Health Service | AWS Direct Connect (shared 1 Gbps) | Bidirectional | TLS 1.2+/443 | PHI, PII | ISA-003 |
| IRS (FTI Exchange) | TLS/SFTP over dedicated MPLS circuit | Inbound only | SFTP/22 | FTI | ISA-004 |
| AWS GovCloud (US-West) DR | AWS private backbone | Bidirectional | Encrypted replication | All | N/A (same boundary) |
| Okta Federal IDP | AWS PrivateLink | Bidirectional | HTTPS/443 | Auth tokens | ISA-005 |
| CyberArk PAM | AWS PrivateLink | Bidirectional | HTTPS/443 | Privileged session data | ISA-006 |
| CISA US-CERT (incident reporting) | Encrypted email / HTTPS | Outbound only | HTTPS/443 | Incident data (no PHI) | N/A |

---

## 5. Component Inventory Summary

A full hardware and software component inventory is maintained as a living document in the CloudVault FHX Configuration Management Database (CMDB) and is reflected in SSP Attachment 12. The following summarizes the in-scope component count at the time of initial authorization.

| Component Type | Count | Notes |
|---|---|---|
| EC2 Instances (production) | 64 | Auto-scaling group, 16 baseline + burst capacity |
| EC2 Instances (non-production) | 22 | Dev/test environments, network-isolated |
| ECS Services (containerized) | 16 | All production microservices |
| Lambda Functions | 34 | Event processing, scheduled tasks |
| RDS Instances | 4 | Primary + Multi-AZ standby (US-East), read replica + standby (US-West) |
| DynamoDB Tables | 12 | Session state, feature flags, metadata |
| S3 Buckets | 147 | PHI storage, audit logs, backups, static assets |
| KMS Customer Managed Keys | 18 | One key per data classification and service type |
| VPCs | 4 | App-East, Mgmt-East, App-West, Mgmt-West |
| Security Groups | 87 | Principle of least privilege, documented in SSP |
| IAM Roles | 142 | Role-based, no persistent credentials for service accounts |
| IAM Identity Center Users | 1,847 | Agency personnel, reviewed quarterly |
| CyberArk Managed Accounts | 63 | All privileged accounts |
| Lambda@Edge Functions | 3 | CloudFront request/response manipulation |

---

## 6. Disaster Recovery Architecture

CloudVault FHX maintains a hot standby in AWS GovCloud (US-West) with the following recovery objectives established in the Contingency Plan (CP) and tested annually:

| Metric | Target | Last Test Result | Test Date |
|---|---|---|---|
| Recovery Time Objective (RTO) | 4 hours | 3 hours 42 minutes | December 12, 2025 |
| Recovery Point Objective (RPO) | 1 hour | 47 minutes | December 12, 2025 |
| Maximum Tolerable Downtime (MTD) | 8 hours | N/A (design parameter) | N/A |
| Data Replication Lag (S3) | Less than 15 minutes | Average 7 minutes | Ongoing monitoring |
| Data Replication Lag (RDS) | Less than 5 minutes | Average 2.3 minutes | Ongoing monitoring |

DR failover is triggered by automated AWS Route 53 health checks and can also be initiated manually by the Cloud Operations Lead (Trevor L. Abrams) or ISSO. The DR runbook is maintained at [ssp-attachments/](../ssp-attachments/) and is tested via tabletop exercise semi-annually and full failover test annually.

---

## 7. Security Architecture Controls Overlay

The following maps key security architecture controls to the NIST SP 800-53 Rev 5 control families they satisfy, providing traceability between architectural components and the authorization control set.

| Architectural Control | Control Families Satisfied | Implementation |
|---|---|---|
| AWS WAF v2 + Shield Advanced | SC-5, SC-7, SI-3, SI-10 | Network boundary protection, DDoS mitigation |
| Three-tier VPC segmentation | SC-7, AC-4, AC-17 | Enforced network segmentation, no east-west bypass |
| KMS CMK encryption (all data at rest) | SC-28, SC-12, MP-5 | AES-256, FIPS 140-2 Level 3 HSM |
| TLS 1.2+ in transit | SC-8, SC-23 | All data flows, enforced by ALB policy and bucket policy |
| CyberArk PAM + JIT access | AC-2, AC-6, AC-17, IA-2 | Privileged access management, session recording |
| AWS CloudTrail (all-region) + Splunk SIEM | AU-2, AU-3, AU-6, AU-9, AU-12 | Comprehensive audit logging, SIEM correlation |
| Amazon GuardDuty | IR-4, RA-5, SI-4 | Threat detection, anomaly alerting |
| AWS Macie | MP-6, PT-2, RA-5 | PHI/PII discovery and protection |
| AWS Config + Config Rules | CM-6, CM-7, CM-8 | Configuration compliance, drift detection |
| Tenable.io (continuous scanning) | RA-5, SI-2, SI-7 | Vulnerability management, flaw remediation |
| AWS Systems Manager Patch Manager | SI-2, CM-6 | Automated patching, compliance reporting |
| Multi-AZ RDS + Cross-region replication | CP-9, CP-10, CP-6 | Data backup, site recovery, COOP |
| IAM Identity Center + PIV/CAC + FIDO2 | IA-2, IA-2(1), IA-2(2), IA-5, IA-8 | MFA, PIV enforcement, identity assurance |
| AWS Secrets Manager | IA-5(7), SA-3 | No hardcoded credentials, automated rotation |
| Prisma Cloud (container security) | CM-6, CM-7, SI-2, SI-7 | Container image scanning, runtime protection |

---

## 8. Diagram Change History

| Version | Date | Change Description | Author |
|---|---|---|---|
| 1.0 | January 24, 2025 | Initial diagram, aligned to SSP v1.0 | Enechi P.C. Njeze |
| 1.1 | November 5, 2025 | Updated network segmentation following SCN-2025-001 (security group hardening) | Enechi P.C. Njeze |
| 1.2 | March 15, 2026 | Updated component count table; added Prisma Cloud to security overlay | Enechi P.C. Njeze |

---

*Prepared by: Enechi P.C. Njeze, ISSO/ISSM, CGRC, CISA, CISM*
*Federal Health Data Office (FHDO) -- Cybersecurity Division*
*Document ID: CV-FHX-ARCH-2025-001 v1.2 | Last Updated: March 15, 2026*
