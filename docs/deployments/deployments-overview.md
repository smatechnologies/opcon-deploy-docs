---
title: Deployments overview
description: "Overview of the deployment functions in OpCon Deploy — how to deploy schedule definitions to OpCon systems, review deployment history, and work with SAP jobs."
product_area: OpCon Deploy
audience: Automation Engineer, Operations Staff
version_introduced: "[see release notes]"
tags:
  - Conceptual
  - Automation Engineer
  - Operations Staff
  - Schedules
last_updated: 2026-04-01
doc_type: conceptual
---

**Theme:** Overview | **Who is it for?** Automation engineers who deploy schedule definitions across OpCon environments and operations staff who monitor and manage deployment records

## What is it?

The Deployments section covers everything involved in moving a schedule or package definition from the OpCon Deploy central repository to a target OpCon system. This includes the deploy process itself, the transformation rules tree that previews how rules will be applied, the browse function for reviewing and managing deployment records (including rollback and delete), and guidance on deployments that contain SAP R3 jobs.

## When would you use this section?

- Deploying a schedule or package definition from the repository to a target OpCon system
- Running a simulation before deployment to check for missing machines, batch users, or sub-schedules
- Reviewing the transformation rules tree to verify which rules will be applied and in what order
- Browsing deployment records to find the status of a previous deployment or to initiate a rollback
- Deploying or investigating schedules that contain SAP R3 job definitions

## What is in this section?

| Topic | Description |
|-------|-------------|
| [Deployments](deployments) | The full deploy workflow — selecting a definition, applying transformation rules, running simulate checks, handling production mismatches, and completing or batch scheduling a deployment |
| [Deployments — browse](deployments-browse) | Searching and filtering deployment records; viewing deployed definitions and rollback definitions; performing rollback, delete, and batch deployment cancellation |
| [Transformation rules tree](transformation-rules-tree) | Visual display of transformation rules during deployment, showing the order and level of application (server, package, deployment), relayed transformations, and ignored rules |
| [Working with SAP jobs](../deploy-sap-jobs) | How OpCon Deploy extracts SAP job definitions during import and inserts them on target SAP systems during deployment |

## Glossary

| Term | Definition |
|------|------------|
| Deployment | The process of selecting a versioned schedule or package definition from the central repository and inserting it into a target OpCon system, with optional transformation rule application. |
| Deployment record | An entry created in the OpCon Deploy repository each time a deployment is performed, capturing the deployed definition, the prior definition on the target system, the user, a timestamp, and the deployment status. |
| Simulate | A pre-deployment check that validates the definition against the target system — checking for missing sub-schedules, machines, machine groups, batch users, external dependencies, and agent feature compatibility — without making any changes on the target system. |
| Rollback | An action on an active deployment record that redeploys the definition retrieved from the target system during the original deployment, restoring the previous state. |
| Production mismatch | A warning condition that occurs when the schedule definition currently on a production OpCon system does not match the definition stored in the corresponding deployment record, indicating that a local change may have been made outside of OpCon Deploy. |
| Relay | The chained transformation effect that occurs when a tag value changed by one rule becomes the input for the same tag in a subsequent rule at a different level. |

## FAQs

**Q: What does the Simulate function check?**

Simulate verifies that sub-schedules, machines, machine groups, batch users, and external dependencies referenced in the definition are all present on the target system. It also checks agent feature support for UNIX embedded scripts, file arrival jobs, Windows embedded scripts, and run-in-command-shell jobs. If any warnings are found, deployment is blocked.

**Q: What should I do if I see a production mismatch warning?**

Select **See differences** to review the JSON diff, then decide whether to abort (select **No**) or continue (select **Yes**). The definition retrieved from the target system is stored in the deployment record regardless of which option you choose, so the change is not lost.

**Q: Can I deploy to multiple target systems at the same time?**

Each deployment targets one OpCon system. To deploy the same package or schedule to multiple systems, use the batch processing capability to queue multiple deployments.
