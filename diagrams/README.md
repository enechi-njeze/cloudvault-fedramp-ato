# diagrams/ — Architecture and Process Diagrams

This folder contains all visual diagrams for the CloudVault Federal Health Exchange (FHX) FedRAMP authorization package. Diagrams are required by the FedRAMP PMO as part of the SSP and are reviewed by both the 3PAO and the Authorizing Official during the authorization process.

## Planned Diagrams

| Filename | Description | Tool | Status |
|---|---|---|---|
| `authorization-boundary-diagram.png` | FedRAMP Authorization Boundary — shows what is inside and outside the boundary with AWS GovCloud components | Eraser.io | Planned |
| `dual-ato-lifecycle-flow.png` | Dual ATO Lifecycle Process Flow — Agency ATO and JAB P-ATO tracks side by side with milestones and timelines | Eraser.io | Planned |
| `phi-pii-data-flow-diagram.png` | PHI and PII Data Flow Diagram — all data flows between external entities, internal processes, and data stores | Eraser.io | Planned |
| `nist-rmf-steps-diagram.png` | NIST RMF 6-Step Process showing CloudVault FHX progression through each step | Eraser.io | Planned |
| `aws-govcloud-architecture.png` | AWS GovCloud architecture showing VPCs, subnets, security groups, and service components | Eraser.io | Planned |

## About the Authorization Boundary Diagram

The Authorization Boundary Diagram is one of the most scrutinized documents in a FedRAMP package. It defines the precise technical and logical perimeter of what is being authorized. Everything inside the boundary must be documented, tested, and evidenced. Everything outside must be documented as an external dependency with appropriate interconnection security agreements (ISAs) or memoranda of understanding (MOUs).

If the boundary diagram is missing, incomplete, or inconsistent with the SSP, the 3PAO will flag it as a finding — and the authorization cannot proceed until it is corrected.

## About the Data Flow Diagram

The Data Flow Diagram (DFD) documents every pathway that PHI, PII, CUI, FTI, and PCI travels within and across the CloudVault FHX system. Auditors use this diagram to verify that encryption is applied at every transmission point, that data at rest is protected, and that no data leaves the authorization boundary without appropriate controls. It is also the primary reference document for privacy impact assessments.

---

*Part of the CloudVault FHX GRC Portfolio | cloudvault-fedramp-ato*
