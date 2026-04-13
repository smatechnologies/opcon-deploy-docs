---
title: Working with SAP jobs
description: "Understand how OpCon Deploy extracts and inserts SAP job definitions when importing and deploying schedules that contain SAP R3 jobs."
tags:
  - Conceptual
  - Automation Engineer
  - Jobs
---

# Working with SAP jobs

**Theme:** Build  
**Who Is It For?** Automation Engineer

## What is it?

OpCon Deploy supports schedules that contain SAP R3 jobs. When importing a schedule, OpCon Deploy can extract the associated SAP job definition directly from the SAP system and include it in the stored definition. When deploying, it can create or link the SAP job on the target SAP system automatically. This ensures that SAP job definitions travel with their OpCon schedule through the deployment pipeline rather than requiring manual recreation on each target system.

## How it works

The OpCon environment supports the scheduling of SAP jobs defined within the SAP environment.

To extract and insert SAP job definitions, the **Refresh SAP Job Definitions** and **Import SAP Job Definitions** options must be selected during the import or deploy process.

SAP job definitions are saved in the OpCon JMASTER_AUX table using field codes 13100 for the query details and field code 13101 for the step details. There will be one field code 13101 record for each defined step starting at sequence number 1. This data is not visible from Enterprise Manager as the field codes do not exist in the OpCon implementation. These field codes have no impact on job execution and are removed when the OpCon SAP job is deleted.

While OpCon Deploy can import and deploy SAP job definitions, it cannot import or deploy the ABAP program. The ABAP program must be available on the target SAP system before deploying.

When importing an OpCon SAP job definition and **Refresh SAP Job Definitions** has been selected, the SAP job definition associated with the OpCon SAP job will be extracted from the SAP system, saved in the OpCon database using field codes 13100 and 13101, and included in the schedule definition. If **Refresh SAP Job Definitions** is not selected, field codes 13100 and 13101 will be checked for SAP job definitions and included in the schedule definition if found.

When deploying an OpCon SAP job definition and **Insert SAP Job Definitions** has been selected, the SAP job definition associated with the OpCon SAP job will be used to create a new job in the SAP system. Before creating the job, a check is made to see if the job already exists in the SAP system. If the job already exists, the SAP job definition is linked with the OpCon SAP job definition. Otherwise, the SAP job is created and the new SAP job definition is linked with the OpCon SAP job definition. The SAP job definitions will be saved in the target OpCon database using field codes 13100 and 13101.

## Key terms

**SAP job definition** — the query and step details extracted from the SAP system and stored alongside the OpCon SAP R3 job in the JMASTER_AUX table using field codes 13100 and 13101; this data travels with the schedule through the OpCon Deploy pipeline so that the SAP job can be recreated or linked on a target SAP system without manual intervention.

**Refresh SAP Job Definitions** — an import option that instructs OpCon Deploy to reach out to the SAP system and extract the current SAP job definition for each OpCon SAP R3 job encountered, saving the result into the OpCon database before including it in the stored schedule definition.

**Insert SAP Job Definitions** — a deployment option that instructs OpCon Deploy to use the stored SAP job definition to create a new SAP job on the target SAP system (or link to one that already exists) and associate it with the corresponding OpCon SAP R3 job during the deploy step.

**Related topics:**

- [Deployments](deployments/deployments)
- [Schedules](schedules)
