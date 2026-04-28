# authorization/ — ATO Decision Documents

This folder contains the final authorization decision documents for the CloudVault Federal Health Exchange (FHX). These are the formal outputs of the authorization process — the documents that the Authorizing Official signs to legally permit (or deny) the system's operation.

## Contents

| File | Description | Status |
|---|---|---|
| `ato-authorization-letter.md` | Agency ATO Authorization Letter — signed by Deputy Director Henry Kline, granting CloudVault FHX authorization to operate | Planned |
| `jab-p-ato-letter.md` | JAB P-ATO Provisional Authorization Letter — issued by the FedRAMP PMO on behalf of DoD, DHS, and GSA | Planned |
| `risk-acceptance-memo.md` | Risk Acceptance Memo — formal AO acceptance of residual risks identified in the POA&M | Planned |
| `interconnection-authorization.md` | Authorization for system interconnections — formally accepts risks from all ISA/MOU-governed connections | Planned |
| `authorization-decision-memo.md` | Authorization Decision Memo — summary of the AO's risk-based decision with supporting rationale | Planned |

## About the Authorization Letter

The ATO Authorization Letter is the single most important output of the entire authorization process. It is a formal, signed, dated document in which the Authorizing Official — a senior federal executive with the legal authority and accountability to accept organizational risk — states that the system has been assessed, that the residual risks are acceptable, and that the system is approved to operate.

Without this letter, the system cannot legally process, store, or transmit federal data. The letter references the SSP version, the SAR date, the POA&M status, and the authorization boundary. It also specifies the authorization term (typically 3 years for FedRAMP) and any conditions attached to the authorization.

## Authorization Conditions

The ATO letter may include conditions — specific requirements the CSP must meet to maintain authorization. Common conditions for a system at CloudVault FHX's scale and sensitivity include:

- Monthly ConMon submissions must be maintained without interruption
- All HIGH and CRITICAL POA&M items must be remediated within 30 days
- Any significant changes to the authorization boundary must be pre-approved
- Annual penetration testing by the 3PAO must be completed on schedule

Failure to comply with any condition can result in the authorization being suspended or revoked.

---

*Part of the CloudVault FHX GRC Portfolio | cloudvault-fedramp-ato*
