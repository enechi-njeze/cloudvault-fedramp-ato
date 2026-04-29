# Assessment Evidence Index
## CloudVault Federal Health Exchange (FHX)
### FedRAMP High Authorization -- Evidence Repository Catalog

---

**Document Control**

| Field | Value |
|---|---|
| Document ID | CV-FHX-EVID-2025-001 |
| Version | 2.1 |
| Last Updated | March 31, 2026 |
| Maintained By | Enechi P.C. Njeze, ISSO/ISSM, CGRC, CISA, CISM |
| 3PAO Evidence Custodian | Kristopher A. Wentworth, ClearPath Security Assessors LLC |
| Evidence Repository | ClearPath Secure Assessment File: FR2024-3PAO-0047 |
| Retention Period | 3 years post-authorization expiration (until February 13, 2031) |
| Related SAR | [assessments/security-assessment-report.md](../assessments/security-assessment-report.md) |

---

## 1. Purpose and Scope

This Evidence Index catalogs all security assessment evidence artifacts collected during the initial FedRAMP High assessment of CloudVault Federal Health Exchange (FHX), covering the assessment period of November 4, 2024 through January 17, 2025. It also tracks ongoing ConMon evidence collected during the authorized operation period (February 2025 through present).

In a real federal engagement, this index would serve as the chain of custody document for all evidence used to support authorization decisions. It enables the ISSO, 3PAO, and Authorizing Official to quickly locate any specific piece of evidence supporting a control determination, and documents the retention status of all artifacts for audit and Inspector General review purposes.

Evidence is maintained in two repositories: the ClearPath Secure Assessment File (FR2024-3PAO-0047) for initial assessment evidence, and the FHDO ISSO SharePoint evidence library for ongoing ConMon evidence. All evidence is access-controlled, version-tracked, and retained per NARA General Records Schedule 3.2 and FedRAMP evidence retention requirements.

---

## 2. Evidence Summary by Category

| Category | Initial Assessment | ConMon (Ongoing) | Total Artifacts |
|---|---|---|---|
| Vulnerability Scan Reports | 14 | 72 (monthly, 18 periods) | 86 |
| Screenshot Evidence Packages | 287 | 144 (estimated) | 431 |
| Interview Notes | 18 | N/A | 18 |
| Configuration Exports | 41 | 41 (quarterly refresh) | 82 |
| Penetration Test Artifacts | 1 package | 1 package (annual) | 2 |
| Policy and Procedure Documents | 47 | 4 (updated) | 51 |
| Closed Finding Remediation Evidence | 36 | 3 (closed post-ATO) | 39 |
| Contingency Plan Test Reports | 0 | 2 (annual + semi-annual) | 2 |
| ConMon Monthly Reports | 0 | 18 | 18 |
| POA&M Version History | 1 | 18 (monthly snapshots) | 19 |
| Incident Response Records | 0 | 11 (all incidents) | 11 |
| **Total** | **444** | **313** | **757** |

---

## 3. Initial Assessment Evidence (November 2024 -- January 2025)

### 3.1 Vulnerability Scan Reports

All vulnerability scans were executed using Tenable Nessus Professional (version 10.6.1) in authenticated mode. Scan credentials were provided under controlled conditions and decommissioned immediately following each scan window.

| Evidence ID | Scan Date | Scan Type | Target Scope | Critical | High | Medium | Low | Status |
|---|---|---|---|---|---|---|---|---|
| EVID-SCAN-001 | 2024-11-05 | Authenticated OS Scan | EC2 App Tier (32 instances) | 3 | 12 | 28 | 41 | Archived |
| EVID-SCAN-002 | 2024-11-06 | Authenticated OS Scan | EC2 Mgmt Tier (8 instances) | 0 | 2 | 9 | 14 | Archived |
| EVID-SCAN-003 | 2024-11-07 | Database Scan | RDS PostgreSQL (4 instances) | 0 | 1 | 4 | 6 | Archived |
| EVID-SCAN-004 | 2024-11-08 | Container Image Scan | ECS Container Registry (all images) | 2 | 8 | 15 | 22 | Archived |
| EVID-SCAN-005 | 2024-11-10 | Web Application Scan (Burp Suite) | External-facing API endpoints | 0 | 3 | 7 | 11 | Archived |
| EVID-SCAN-006 | 2024-11-12 | Configuration Compliance (SCAP) | All EC2 instances (DISA STIG baseline) | N/A | N/A | 34 non-compliant | 19 non-compliant | Archived |
| EVID-SCAN-007 | 2024-11-15 | S3 Bucket Policy Review | All 147 S3 buckets | 0 | 1 | 3 | 5 | Archived |
| EVID-SCAN-008 | 2024-11-20 | Rescan (post-remediation batch 1) | EC2 App Tier | 0 | 4 | 18 | 30 | Archived |
| EVID-SCAN-009 | 2024-12-04 | Rescan (post-remediation batch 2) | RDS, S3, Container Registry | 0 | 2 | 9 | 17 | Archived |
| EVID-SCAN-010 | 2024-12-15 | Authenticated OS Scan (mid-assessment) | Full scope (all in-scope assets) | 0 | 3 | 14 | 24 | Archived |
| EVID-SCAN-011 | 2025-01-06 | Pre-pentest Baseline Scan | Full scope | 0 | 2 | 10 | 18 | Archived |
| EVID-SCAN-012 | 2025-01-14 | Rescan (post-penetration test) | Full scope | 0 | 2 | 9 | 16 | Archived |
| EVID-SCAN-013 | 2025-01-15 | Final Pre-ATO Scan | Full scope | 0 | 2 | 9 | 16 | Archived |
| EVID-SCAN-014 | 2025-01-17 | Database Final Scan | RDS, DynamoDB | 0 | 0 | 3 | 7 | Archived |

### 3.2 Screenshot Evidence Packages by Control Family

| Evidence ID | Control Family | Controls Covered | Evidence Type | Artifact Count | Status |
|---|---|---|---|---|---|
| EVID-SS-AC | AC -- Access Control | AC-1 through AC-25 | Screenshots, config exports, policy docs | 48 | Archived |
| EVID-SS-AT | AT -- Awareness and Training | AT-1 through AT-6 | Training records, LMS reports, screenshots | 12 | Archived |
| EVID-SS-AU | AU -- Audit and Accountability | AU-1 through AU-16 | CloudTrail config, Splunk dashboards, bucket policies | 31 | Archived |
| EVID-SS-CA | CA -- Assessment, Authorization, Monitoring | CA-1 through CA-9 | Assessment artifacts, authorization docs, ConMon plan | 18 | Archived |
| EVID-SS-CM | CM -- Configuration Management | CM-1 through CM-12 | Baseline configs, CMDB exports, change records | 29 | Archived |
| EVID-SS-CP | CP -- Contingency Planning | CP-1 through CP-13 | CP document, test reports, backup evidence | 22 | Archived |
| EVID-SS-IA | IA -- Identification and Authentication | IA-1 through IA-13 | IAM exports, MFA reports, Okta config | 27 | Archived |
| EVID-SS-IR | IR -- Incident Response | IR-1 through IR-10 | IR plan, incident records, runbooks | 14 | Archived |
| EVID-SS-MA | MA -- Maintenance | MA-1 through MA-6 | Maintenance logs, remote access records | 9 | Archived |
| EVID-SS-MP | MP -- Media Protection | MP-1 through MP-8 | Media sanitization records, encryption evidence | 10 | Archived |
| EVID-SS-PE | PE -- Physical and Environmental Protection | PE-1 through PE-23 | AWS GovCloud compliance reports, datacenter access controls | 14 | Archived |
| EVID-SS-PL | PL -- Planning | PL-1 through PL-11 | SSP, Rules of Behavior, privacy plan | 11 | Archived |
| EVID-SS-PM | PM -- Program Management | PM-1 through PM-32 | Program management plan, risk register | 8 | Archived |
| EVID-SS-PS | PS -- Personnel Security | PS-1 through PS-9 | Background check records, onboarding procedures | 9 | Archived |
| EVID-SS-PT | PT -- PII Processing and Transparency | PT-1 through PT-8 | PIA, SORN, privacy notices | 12 | Archived |
| EVID-SS-RA | RA -- Risk Assessment | RA-1 through RA-10 | FIPS 199, risk assessments, ISCP risk | 13 | Archived |
| EVID-SS-SA | SA -- System and Services Acquisition | SA-1 through SA-23 | Procurement docs, developer security, SDLC evidence | 19 | Archived |
| EVID-SS-SC | SC -- System and Communications Protection | SC-1 through SC-51 | Network diagrams, encryption configs, firewall rules | 36 | Archived |
| EVID-SS-SI | SI -- System and Information Integrity | SI-1 through SI-23 | Scan results, AV configs, integrity monitoring | 28 | Archived |
| EVID-SS-SR | SR -- Supply Chain Risk Management | SR-1 through SR-12 | Vendor assessments, SBOM, supply chain plan | 16 | Archived |

### 3.3 Interview Records

All interviews were conducted by ClearPath assessment team members and documented in structured interview notes. All notes were reviewed and signed by the interviewee within 5 business days of the interview.

| Evidence ID | Interview Date | Interviewee | Role | Topics Covered | Status |
|---|---|---|---|---|---|
| EVID-INT-001 | 2024-11-07 | Enechi P.C. Njeze | ISSO/ISSM | System overview, security program, AC/AU/CA controls | Signed, Archived |
| EVID-INT-002 | 2024-11-07 | Enechi P.C. Njeze | ISSO/ISSM | POA&M management, ConMon program, incident response | Signed, Archived |
| EVID-INT-003 | 2024-11-08 | Trevor L. Abrams | Cloud Operations Lead | CM, CP, MA, SI controls; patching program | Signed, Archived |
| EVID-INT-004 | 2024-11-08 | Trevor L. Abrams | Cloud Operations Lead | Vulnerability management, AWS Config, monitoring | Signed, Archived |
| EVID-INT-005 | 2024-11-09 | Dr. Angela M. Reeves | Privacy Officer | PT, PL controls; PIA, SORN, data handling | Signed, Archived |
| EVID-INT-006 | 2024-11-10 | FHDO Security Operations | SOC Lead | AU controls, Splunk SIEM, GuardDuty alerting | Signed, Archived |
| EVID-INT-007 | 2024-11-12 | CloudVault DevSecOps Lead | SA-11, SA-15 | SDLC security, code review, pipeline security | Signed, Archived |
| EVID-INT-008 | 2024-11-14 | CloudVault Network Engineer | SC, SI controls | Firewall rules, IDS/IPS, network segmentation | Signed, Archived |
| EVID-INT-009 | 2024-11-15 | CloudVault DBA Lead | SC-28, CP-9 | Database encryption, backup procedures | Signed, Archived |
| EVID-INT-010 | 2024-11-18 | FHDO HR Representative | PS controls | Background checks, onboarding/offboarding | Signed, Archived |
| EVID-INT-011 | 2024-11-20 | CloudVault Incident Response Lead | IR controls | Incident response procedures, tabletop exercise history | Signed, Archived |
| EVID-INT-012 | 2024-11-21 | CloudVault Supply Chain Manager | SR controls | Vendor assessment program, SBOM management | Signed, Archived |
| EVID-INT-013 | 2024-12-02 | Enechi P.C. Njeze | ISSO/ISSM | Follow-up: remediation progress on critical findings | Signed, Archived |
| EVID-INT-014 | 2024-12-05 | Trevor L. Abrams | Cloud Operations Lead | Follow-up: patching SLA compliance, KMS key rotation | Signed, Archived |
| EVID-INT-015 | 2024-12-10 | CloudVault PAM Administrator | IA, AC controls | CyberArk PAM configuration, JIT access workflow | Signed, Archived |
| EVID-INT-016 | 2025-01-07 | Enechi P.C. Njeze | ISSO/ISSM | Pre-authorization review, POA&M finalization | Signed, Archived |
| EVID-INT-017 | 2025-01-08 | Dr. Sandra M. Okafor | System Owner | System mission, ownership acknowledgment | Signed, Archived |
| EVID-INT-018 | 2025-01-10 | Henry Kline | Authorizing Official | AO briefing, risk acceptance discussion | Signed, Archived |

### 3.4 Penetration Test Evidence Package

| Evidence ID | Description | Date | Tester | Status |
|---|---|---|---|---|
| EVID-PT-001 | Rules of Engagement (ROE) signed document | 2025-01-03 | Marcus J. Holloway, ClearPath | Archived |
| EVID-PT-002 | External network penetration test report | 2025-01-10 | Marcus J. Holloway, ClearPath | Archived |
| EVID-PT-003 | Internal network penetration test report | 2025-01-10 | Marcus J. Holloway, ClearPath | Archived |
| EVID-PT-004 | Social engineering (phishing simulation) report | 2025-01-10 | Danielle R. Forsythe, ClearPath | Archived |
| EVID-PT-005 | Penetration test working files (Metasploit logs, Nmap output) | 2025-01-10 | Marcus J. Holloway, ClearPath | Archived |
| EVID-PT-006 | Post-test remediation verification evidence | 2025-01-17 | Kristopher A. Wentworth, ClearPath | Archived |

---

## 4. Continuous Monitoring Evidence (February 2025 -- Present)

### 4.1 Monthly ConMon Evidence Package Index

Each monthly ConMon cycle produces a standardized evidence package submitted to the Authorizing Official with the monthly ConMon report.

| Period | Evidence Package ID | Vuln Scan Complete | POA&M Updated | ConMon Report Submitted | Risk Posture |
|---|---|---|---|---|---|
| Feb 2025 | CONMON-EVID-2025-02 | Yes | Yes | 2025-03-05 | ACCEPTABLE |
| Mar 2025 | CONMON-EVID-2025-03 | Yes | Yes | 2025-04-04 | ACCEPTABLE |
| Apr 2025 | CONMON-EVID-2025-04 | Yes | Yes | 2025-05-05 | ACCEPTABLE |
| May 2025 | CONMON-EVID-2025-05 | Yes | Yes | 2025-06-04 | ACCEPTABLE |
| Jun 2025 | CONMON-EVID-2025-06 | Yes | Yes | 2025-07-07 | ACCEPTABLE |
| Jul 2025 | CONMON-EVID-2025-07 | Yes | Yes | 2025-08-05 | ACCEPTABLE |
| Aug 2025 | CONMON-EVID-2025-08 | Yes | Yes | 2025-09-04 | ACCEPTABLE |
| Sep 2025 | CONMON-EVID-2025-09 | Yes | Yes | 2025-10-06 | ACCEPTABLE |
| Oct 2025 | CONMON-EVID-2025-10 | Yes | Yes | 2025-11-05 | ACCEPTABLE |
| Nov 2025 | CONMON-EVID-2025-11 | Yes | Yes | 2025-12-03 | ACCEPTABLE |
| Dec 2025 | CONMON-EVID-2025-12 | Yes | Yes | 2026-01-06 | ACCEPTABLE |
| Jan 2026 | CONMON-EVID-2026-01 | Yes | Yes | 2026-02-04 | ACCEPTABLE |
| Feb 2026 | CONMON-EVID-2026-02 | Yes | Yes | 2026-03-04 | ACCEPTABLE |
| Mar 2026 | CONMON-EVID-2026-03 | Yes | Yes | 2026-04-03 | ACCEPTABLE |

All 14 consecutive ConMon reports submitted on time. Zero ELEVATED or UNACCEPTABLE risk posture determinations in the authorization period to date.

### 4.2 Incident Response Records

| Evidence ID | Incident Date | Severity | Description | Resolution Time | PHI/PII Breach | US-CERT Reported |
|---|---|---|---|---|---|---|
| EVID-IR-001 | 2025-03-12 | Low | Unauthorized login attempt (blocked by MFA) | 2.1 hours | No | No |
| EVID-IR-002 | 2025-04-28 | Medium | Elevated GuardDuty finding (recon activity from external IP) | 4.3 hours | No | No |
| EVID-IR-003 | 2025-06-15 | Low | S3 bucket access from unusual geographic region (authorized user, traveling) | 1.7 hours | No | No |
| EVID-IR-004 | 2025-07-20 | Medium | Automated alert: Macie detected potential PHI in non-PHI bucket (false positive) | 3.2 hours | No | No |
| EVID-IR-005 | 2025-08-30 | Low | Service account password approaching expiration (remediated before expiry) | 0.9 hours | No | No |
| EVID-IR-006 | 2025-09-11 | Medium | ECS container crash loop affecting 2 services (availability incident, not security) | 2.8 hours | No | No |
| EVID-IR-007 | 2025-10-05 | Low | GuardDuty finding: EC2 instance querying unusual external domain (dev environment) | 1.5 hours | No | No |
| EVID-IR-008 | 2025-11-18 | Low | Attempted brute force on administrative login page (blocked by WAF rate limit) | 1.1 hours | No | No |
| EVID-IR-009 | 2025-12-22 | Medium | AWS Config rule violation: security group rule added outside change management | 3.6 hours | No | No |
| EVID-IR-010 | 2026-01-14 | Low | User account locked after 5 failed MFA attempts (legitimate user, device issue) | 0.8 hours | No | No |
| EVID-IR-011 | 2026-03-03 | Medium | Tenable scan flagged 3 new High CVEs on EC2 batch processing instance | 5.2 hours | No | No |

All 11 incidents resolved within FedRAMP High SLA. Zero PHI or PII breaches in the authorization period.

---

## 5. Evidence Chain of Custody

All assessment evidence is governed by the following chain of custody requirements, consistent with FedRAMP evidence handling guidance and NIST SP 800-115, "Technical Guide to Information Security Testing and Assessment."

### 5.1 Initial Assessment Evidence (ClearPath Custody)

Evidence collected during the initial assessment is maintained exclusively by ClearPath Security Assessors LLC under assessment file FR2024-3PAO-0047. Evidence is stored in an encrypted, access-controlled repository accessible only to the assessment team and retained for a minimum of 3 years post-authorization expiration.

Access to this evidence by CloudVault FHX or FHDO personnel requires a formal written request to ClearPath, reviewed and approved by the Lead Assessor (Kristopher A. Wentworth). In the event of an Inspector General review, GAO audit, or federal litigation, ClearPath will provide certified copies of all evidence artifacts upon receipt of a valid legal process or formal agency request.

### 5.2 ConMon Evidence (FHDO ISSO Custody)

Ongoing ConMon evidence is maintained by the ISSO (Enechi P.C. Njeze) in the FHDO Cybersecurity Division SharePoint evidence library. Access is restricted to ISSO, ISSM, SAISO (Marcus T. Brennan), and the Authorizing Official. Quarterly access reviews are conducted to ensure no unauthorized access.

### 5.3 Retention Schedule

| Evidence Type | Retention Period | Disposition Authority |
|---|---|---|
| Initial 3PAO assessment evidence | 3 years post-ATO expiration (until February 13, 2031) | NARA GRS 3.2, Item 030 |
| ConMon monthly reports | 3 years post-ATO expiration | NARA GRS 3.2, Item 030 |
| Vulnerability scan reports | 3 years post-ATO expiration | NARA GRS 3.2, Item 030 |
| Incident response records | 6 years post-incident closure | NARA GRS 5.7, Item 020 |
| PHI breach records (if any) | 6 years per HIPAA (45 CFR 164.530(j)) | HIPAA, NARA |
| Penetration test reports | 3 years post-ATO expiration | NARA GRS 3.2, Item 030 |

---

## 6. Evidence Index Certification

I, the undersigned ISSO/ISSM, certify that this Evidence Index accurately reflects the assessment evidence collected and maintained in support of the CloudVault Federal Health Exchange (FHX) FedRAMP High authorization. All evidence referenced herein has been verified as present in the designated custody location as of the date of last update.

---

**Enechi P.C. Njeze**
Information System Security Officer (ISSO) / Information System Security Manager (ISSM)
CGRC | CISA | CISM | PMP | PMI-RMP | CompTIA Security+ SY0-701 | CHP | CSCS
Federal Health Data Office (FHDO) -- Cybersecurity Division
Date of Last Certification: March 31, 2026

---

*Document ID: CV-FHX-EVID-2025-001 v2.1 | Maintained by Enechi P.C. Njeze, ISSO/ISSM*
*Federal Health Data Office (FHDO) -- Cybersecurity Division | Last Updated: March 31, 2026*
