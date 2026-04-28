# evidence/ — Control Implementation Evidence

This folder contains the control implementation evidence artifacts for the CloudVault Federal Health Exchange (FHX). Evidence is the tangible, verifiable proof that a security control is actually implemented and operating as described in the SSP. Without evidence, a control is considered "not implemented" during 3PAO assessment — regardless of what the SSP says.

## Evidence Organization

Evidence in this repository is organized by NIST SP 800-53 Rev 5 control family:

| Folder | Control Family | Example Evidence Types |
|---|---|---|
| `AC/` | Access Control | IAM policy screenshots, MFA enrollment reports, privileged access reviews |
| `AU/` | Audit and Accountability | CloudTrail log samples, SIEM alert rules, audit policy configurations |
| `CA/` | Assessment, Authorization, and Monitoring | Assessment schedules, authorization letters, ConMon reports |
| `CM/` | Configuration Management | Baseline configuration files, SCM scan results, change tickets |
| `CP/` | Contingency Planning | BCP/DR test results, backup verification logs, RTO/RPO test evidence |
| `IA/` | Identification and Authentication | MFA screenshots, PIV/CAC implementation docs, password policy configs |
| `IR/` | Incident Response | IR playbooks, test exercise reports, incident tickets (sanitized) |
| `SC/` | System and Communications Protection | TLS certificates, encryption configurations, network diagrams |
| `SI/` | System and Information Integrity | AV scan results, patch management reports, integrity monitoring alerts |

## What Makes Evidence Audit-Ready

For evidence to satisfy a 3PAO assessor during a FedRAMP High assessment, it must be:

1. **Dated** — Evidence must be recent (typically within 3–6 months of the assessment)
2. **Attributed** — It must clearly show which system component it applies to
3. **Complete** — It must demonstrate the control is fully implemented, not partially
4. **Consistent** — It must match what the SSP says is implemented

A common reason authorizations are delayed is that CSPs submit evidence that is outdated, belongs to the wrong system, or contradicts the SSP narrative. Maintaining this evidence folder with current, organized artifacts eliminates that risk.

---

*Part of the CloudVault FHX GRC Portfolio | cloudvault-fedramp-ato*
