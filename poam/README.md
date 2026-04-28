# poam/ — Plan of Action and Milestones

This folder contains the Plan of Action and Milestones (POA&M) package for the CloudVault Federal Health Exchange (FHX). The POA&M is a FISMA-mandated document that tracks every open security weakness identified during the authorization process and specifies who is responsible for fixing it, how it will be fixed, and by when.

## Contents

| File | Description | Status |
|---|---|---|
| `poam-master-tracker.md` | Master POA&M tracker — all open findings with risk level, milestones, and responsible parties | In Progress |
| `poam-template.md` | Blank POA&M template formatted to FedRAMP PMO specifications | In Progress |
| `poam-closure-evidence-log.md` | Log of evidence submitted to close completed POA&M items | Planned |
| `risk-acceptance-log.md` | Formal risk acceptance decisions for items not remediated — AO-signed | Planned |

## About the POA&M

The POA&M is one of the three documents — alongside the SSP and the SAR — that the Authorizing Official reviews when making the authorization decision. Under FedRAMP continuous monitoring requirements, the POA&M must be updated monthly and submitted to the FedRAMP PMO. Any POA&M item that is 90 days overdue without an approved extension becomes a compliance violation that can trigger suspension of the authorization.

### POA&M Risk Levels

| Risk Level | CVSS Score Range | Maximum Remediation Window |
|---|---|---|
| **CRITICAL** | 9.0 – 10.0 | 30 days |
| **HIGH** | 7.0 – 8.9 | 30 days |
| **MODERATE** | 4.0 – 6.9 | 90 days |
| **LOW** | 0.1 – 3.9 | 180 days |

### Real-World Consequence of POA&M Non-Compliance

If a CSP (Cloud Service Provider) fails to remediate HIGH or CRITICAL POA&M items within the required window, the FedRAMP PMO can issue a Notice of Deficiency. If the deficiency is not resolved, the authorization can be revoked — meaning all federal agencies using the system must immediately cease operations on it. For CloudVault FHX, serving 47 federal health agencies and 890,000+ patient records, that consequence would be catastrophic to mission continuity.

---

*Part of the CloudVault FHX GRC Portfolio | cloudvault-fedramp-ato*
