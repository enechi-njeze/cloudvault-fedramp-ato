# conmon/ — Continuous Monitoring Package

This folder contains the Continuous Monitoring (ConMon) package for the CloudVault Federal Health Exchange (FHX). Continuous monitoring is the ongoing security program that begins after authorization is granted and continues for the life of the system. It is what keeps the ATO valid.

## Contents

| File | Description | Status |
|---|---|---|
| `conmon-monthly-report-template.md` | Monthly ConMon report template — submitted to the FedRAMP PMO and Agency AO | In Progress |
| `conmon-scan-results-summary.md` | Vulnerability scan results summary — Qualys/Nessus output processed for PMO submission | Planned |
| `conmon-significant-change-log.md` | Log of all significant changes to CloudVault FHX that may impact the authorization boundary | Planned |
| `conmon-annual-assessment-schedule.md` | Schedule of controls requiring annual testing per NIST SP 800-137 | Planned |

## About Continuous Monitoring

A common misconception in federal cybersecurity is that the work ends when the ATO is granted. In reality, the ATO is only the beginning of the continuous monitoring obligation. Under FedRAMP requirements, a CSP must:

- Submit monthly vulnerability scan results to the FedRAMP PMO
- Update the POA&M monthly with remediation progress
- Report significant system changes within 30 days of implementation
- Conduct annual assessments of a subset of controls
- Notify the PMO of any security incidents within defined timeframes

Missing a ConMon submission is treated as a compliance violation. Chronic non-compliance can result in the authorization being placed on probation or revoked entirely.

## ConMon Under Agency ATO vs JAB P-ATO

Under the **Agency ATO**, ConMon reports are submitted to the sponsoring agency's Authorizing Official and their security team. Under the **JAB P-ATO**, reports go to the FedRAMP PMO, which then distributes findings to all leveraging agencies. The JAB track therefore carries a broader obligation — any security weakness becomes visible to DoD, DHS, and GSA simultaneously.

---

*Part of the CloudVault FHX GRC Portfolio | cloudvault-fedramp-ato*
