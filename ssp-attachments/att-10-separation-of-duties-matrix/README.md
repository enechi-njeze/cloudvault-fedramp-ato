# Attachment 10: Separation of Duties Matrix

**CloudVault Federal Health Exchange (FHX)**
**SSP Appendix A, Attachment 10**
**Document ID:** CV-FHX-ATT-10-SOD
**Prepared By:** Enechi P.C. Njeze, ISSO/ISSM

---

## Purpose

This folder contains the Separation of Duties (SOD) Matrix for CloudVault FHX. The SOD Matrix documents the access and privilege restrictions that prevent any single individual from having the ability to perform two or more conflicting sensitive functions without detection or accountability. It satisfies FedRAMP High requirements under AC-5 (Separation of Duties) and PS-2 (Position Risk Designation).

## Required Artifacts

Upload the following files to this folder:

| Artifact | Description | Format |
|---|---|---|
| Separation of Duties Matrix | Full SOD matrix mapping all roles to functions with conflict identification | Excel or PDF |
| Role and Privilege Definitions | Definitions of all system roles and associated access privileges | Word or PDF |
| Privileged User Listing | Current list of privileged users, roles assigned, and approval date | Excel or PDF |
| Least Privilege Analysis | Documentation that each role has only the minimum access required for its function | Word or PDF |

## SOD Conflict Categories

The SOD Matrix must address the following conflict categories at minimum:

| Conflict Type | Example | Control |
|---|---|---|
| Development vs. Production | Same person cannot deploy code and approve production releases | AC-5, CM-3 |
| Security vs. Audit | ISSO cannot also serve as sole auditor of ISSO actions | AC-5, AU-9 |
| System Administration vs. Audit | System admin cannot manage or delete their own audit logs | AC-5, AU-9 |
| Financial Authorization | Same person cannot initiate and approve financial transactions | AC-5 |
| Key Management | Same person cannot generate and escrow cryptographic keys | AC-5, SC-12 |
| Account Management | Same person cannot create accounts and approve account creation | AC-5, AC-2 |

## Key Roles Covered

The CloudVault FHX SOD Matrix covers the following roles: System Owner, ISSO/ISSM, System Administrator, Database Administrator, Application Developer, Security Analyst, Auditor, Help Desk, Change Manager, and Third-Party Assessor.

## Related Documents

- [SSP Attachment Index](../ssp-attachment-index.md)
- [System Security Plan](../../docs/system-security-plan.md)
- [Information Security Policies](../att-04-information-security-policies/README.md)
- [Evidence Folder: AC and PS Family Evidence](../../evidence/evidence-index.md)

## FedRAMP Requirement

AC-5 requires that duties of individuals be separated to reduce the risk of malevolent activity, error, and fraud. For FedRAMP High systems handling PHI, PII, and FTI, the SOD Matrix is scrutinized closely because a single insider threat could affect hundreds of thousands of patient records across 47 agencies. The matrix must be reviewed annually and updated within 30 days of any role change.

---

*Enechi P.C. Njeze, CGRC, CISA, CISM, PMP, PMI-RMP, Security+, CHP, CSCS*
*Information System Security Officer (ISSO) and Information System Security Manager (ISSM)*
*CloudVault Federal Health Exchange (FHX)*
