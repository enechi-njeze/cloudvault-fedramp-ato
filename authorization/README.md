# authorization/ — ATO Authorization Decision Package

This folder is the **decision hub** of the CloudVault Federal Health Exchange (FHX) authorization package. It contains the formal authorization decision documents produced at the conclusion of the NIST RMF authorization process, and it serves as the navigable master index that links every component of the full authorization package together.

> **How to use this folder:** An Authorizing Official, 3PAO assessor, FedRAMP PMO reviewer, or portfolio visitor can navigate the entire authorization package from this single page. Every linked document either lives in this folder or is cross-referenced via a direct link to its location elsewhere in this repository.

---

## The FedRAMP Authorization Package — What the AO Reviews

Before an Authorizing Official (AO) signs the Authorization to Operate letter, they review a complete authorization package consisting of four core documents. These four documents, taken together, form the evidentiary basis for the AO's formal risk acceptance decision. The AO does not review any one document in isolation — the package is evaluated as an integrated whole.

| # | Document | Purpose in the AO's Decision | Location |
|---|---|---|---|
| 1 | **System Security Plan (SSP)** | Describes what the system does, how every control is implemented, and what the authorization boundary covers. This is the AO's primary reference for understanding the system's security posture. | [→ docs/system-security-plan.md](../docs/system-security-plan.md) |
| 2 | **Security Assessment Plan (SAP)** | Describes how the 3PAO (CyberAudit Partners LLC) planned and scoped their independent assessment of the controls. The AO uses this to evaluate whether the testing approach was sufficiently rigorous. | [→ assessments/security-assessment-plan.md](../assessments/security-assessment-plan.md) |
| 3 | **Security Assessment Report (SAR)** | Documents every finding from the 3PAO's assessment — what they tested, what passed, what failed, and the severity of each finding. The SAR directly drives the POA&M. | [→ assessments/security-assessment-report.md](../assessments/security-assessment-report.md) |
| 4 | **Plan of Action and Milestones (POA&M)** | Tracks every open security weakness identified in the SAR, who is responsible for fixing it, and by when. The AO reviews the POA&M to determine whether residual risks are acceptable before signing the ATO. | [→ poam/poam-master-tracker.md](../poam/poam-master-tracker.md) |

---

## Authorization Decision Documents (this folder)

These are the formal outputs of the AO's review — the signed, dated, binding decisions that legally authorize (or deny) CloudVault FHX to operate.

| File | Document | Description | Status |
|---|---|---|---|
| `ato-authorization-letter.md` | Agency ATO Authorization Letter | Signed by Deputy Director Henry Kline — formally grants CloudVault FHX authorization to operate at HIGH impact. References the SSP version, SAR date, and POA&M status. Specifies authorization term and conditions. | Planned |
| `jab-p-ato-letter.md` | JAB P-ATO Provisional Authorization Letter | Issued by the FedRAMP PMO on behalf of DoD (Col. Diana Marsh), DHS (Frank Osei), and GSA (Carol Whitfield). Enables government-wide reuse by any federal agency without re-assessment. | Planned |
| `risk-acceptance-memo.md` | Risk Acceptance Memo | Formal AO acceptance of residual risks documented in the POA&M. Identifies each HIGH and MODERATE finding the AO has reviewed and accepted pending remediation. | Planned |
| `authorization-decision-memo.md` | Authorization Decision Memo | Executive summary of the AO's risk-based decision — documents the rationale, the key risk factors considered, the boundary reviewed, and the conditions attached to the authorization. | Planned |
| `interconnection-authorization.md` | Interconnection Authorization | Formal authorization for all system interconnections — accepts the risks introduced by data exchanges with all 47 connected federal health agencies via ISAs and MOUs. | Planned |
| `fedramp-pmo-notification.md` | FedRAMP PMO Notification Letter | Formal notification to the FedRAMP PMO of the Agency ATO grant — required within 30 days of authorization under FedRAMP policy. | Planned |

---

## Supporting Package — Cross-Repository Navigation

The authorization decision package does not stand alone. A complete picture of CloudVault FHX's security posture requires the full set of artifacts distributed across this repository. Use the links below to navigate the complete package.

### Core Authorization Documents
| Document | Location |
|---|---|
| System Security Plan (SSP) | [docs/system-security-plan.md](../docs/system-security-plan.md) |
| Control Implementation Summary (CIS) | [docs/control-implementation-summary.md](../docs/control-implementation-summary.md) |
| FIPS 199 Security Categorization | [assessments/fips199-security-categorization.md](../assessments/fips199-security-categorization.md) |
| FIPS 200 Minimum Security Requirements | [assessments/fips200-minimum-requirements.md](../assessments/fips200-minimum-requirements.md) |
| Security Assessment Plan (SAP) | [assessments/security-assessment-plan.md](../assessments/security-assessment-plan.md) |
| Security Assessment Report (SAR) | [assessments/security-assessment-report.md](../assessments/security-assessment-report.md) |

### Risk and Remediation
| Document | Location |
|---|---|
| POA&M Master Tracker | [poam/poam-master-tracker.md](../poam/poam-master-tracker.md) |
| POA&M Template | [poam/poam-template.md](../poam/poam-template.md) |
| Risk Acceptance Log | [poam/risk-acceptance-log.md](../poam/risk-acceptance-log.md) |

### Continuous Monitoring
| Document | Location |
|---|---|
| ConMon Monthly Report Template | [conmon/conmon-monthly-report-template.md](../conmon/conmon-monthly-report-template.md) |
| ConMon Scan Results Summary | [conmon/conmon-scan-results-summary.md](../conmon/conmon-scan-results-summary.md) |
| Significant Change Log | [conmon/conmon-significant-change-log.md](../conmon/conmon-significant-change-log.md) |

### SSP Attachments (Policies, Plans, Appendices)
| Folder | Location |
|---|---|
| All SSP Appendices, Operational Plans, and Control Family Policies | [ssp-attachments/](../ssp-attachments/) |

### JAB P-ATO Track
| Document | Location |
|---|---|
| JAB Prioritization Request | [jab-path/jab-prioritization-request.md](../jab-path/jab-prioritization-request.md) |
| Demand Signals Package | [jab-path/demand-signals-package.md](../jab-path/demand-signals-package.md) |
| JAB vs Agency ATO Comparison | [jab-path/jab-vs-agency-ato-comparison.md](../jab-path/jab-vs-agency-ato-comparison.md) |

### Evidence and Diagrams
| Folder | Location |
|---|---|
| Control Implementation Evidence (all 20 families) | [evidence/](../evidence/) |
| Architecture and Process Diagrams | [diagrams/](../diagrams/) |

---

## Authorization Package Status

| Document | Responsible Party | Target Date | Status |
|---|---|---|---|
| SSP (final version) | ISSO — Marcus J. Reid | TBD | In Progress |
| SAP | 3PAO — CyberAudit Partners LLC | TBD | Planned |
| SAR | 3PAO — CyberAudit Partners LLC | TBD | Planned |
| POA&M (initial) | ISSO — Marcus J. Reid | TBD | In Progress |
| Agency ATO Letter | AO — Deputy Director Henry Kline | TBD | Planned |
| JAB P-ATO Letter | FedRAMP PMO / JAB | TBD | Planned |
| Risk Acceptance Memo | AO — Deputy Director Henry Kline | TBD | Planned |

---

> *The authorization decision is not the end of the security program — it is the beginning of the continuous monitoring obligation. Once the ATO is granted, the documents in the [conmon/](../conmon/) folder govern ongoing compliance.*

---

*Part of the CloudVault FHX GRC Portfolio | cloudvault-fedramp-ato*
