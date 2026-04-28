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
