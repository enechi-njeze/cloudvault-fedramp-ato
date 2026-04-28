# assessments/ — Security Assessment Materials

This folder contains all security assessment artifacts for the CloudVault Federal Health Exchange (FHX) FedRAMP High authorization, including system categorization, 3PAO assessment planning and reporting documents.

## Contents

| File | Description | Status |
|---|---|---|
| `fips199-security-categorization.md` | FIPS 199 Security Categorization — establishes HIGH impact for C, I, and A | In Progress |
| `fips200-minimum-requirements.md` | FIPS 200 Minimum Security Requirements — maps 17 security areas to FedRAMP High baseline | Planned |
| `security-assessment-plan.md` | Security Assessment Plan (SAP) — describes how CyberAudit Partners LLC will test controls | Planned |
| `security-assessment-report.md` | Security Assessment Report (SAR) — 3PAO findings from control testing | Planned |
| `penetration-test-rules-of-engagement.md` | Rules of Engagement for 3PAO penetration testing on AWS GovCloud environment | Planned |

## About FIPS 199 Security Categorization

FIPS 199 (Federal Information Processing Standard 199) is the federal standard that determines whether a system is classified as LOW, MODERATE, or HIGH impact. Every federal system must be formally categorized before any other authorization activity can begin — it is Step 1 of the NIST Risk Management Framework.

For CloudVault FHX, the categorization is: **{HIGH} = (Confidentiality: HIGH, Integrity: HIGH, Availability: HIGH)**

This HIGH classification is driven by the nature of the data (PHI, PII, CUI, FTI, PCI) and the life-safety implications of the system. An availability failure during a medical emergency, or a confidentiality breach of federal health records, would constitute a severe impact to mission, operations, and individuals.

## About the SAP and SAR

The Security Assessment Plan (SAP) is produced by the 3PAO — in this case, CyberAudit Partners LLC — before testing begins. It describes which controls will be tested, how they will be tested, and the testing schedule. The SAR documents the actual findings. Any control that is not fully implemented appears in the SAR and must be addressed in the POA&M.

---

*Part of the CloudVault FHX GRC Portfolio | cloudvault-fedramp-ato*
