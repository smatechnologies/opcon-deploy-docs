---
title: Batch processing overview
description: "Overview of the batch processing capabilities in OpCon Deploy — command-line deployments, scheduled batch deployments, file-based integration, and DevOps pipeline integration."
product_area: OpCon Deploy
audience: System Administrator, Automation Engineer
version_introduced: "[see release notes]"
tags:
  - Conceptual
  - System Administrator
  - Automation Engineer
  - Schedules
last_updated: 2026-04-01
doc_type: conceptual
---

**Theme:** Overview | **Who is it for?** System administrators and automation engineers who automate OpCon Deploy operations through the command line, scheduled jobs, file-based triggers, or DevOps pipelines

## What is it?

The Batch Processing section covers all of the ways to drive OpCon Deploy operations without using the interactive client UI. The core batch application (`Batch.SMAOpConDeployClient.exe`) supports deploy, import, simulate, and init operations from the command line. On top of that, OpCon Deploy provides four integration patterns: scheduled deployments triggered by an OpCon job, file-based deployments triggered by placing a definition file in a watched folder, DevOps pipeline integration for CI/CD workflows, and diagram generation triggered in batch.

## When would you use this section?

- Automating deployments as part of a nightly or release-cycle schedule in OpCon
- Integrating OpCon Deploy into a CI/CD pipeline so that schedule definitions are deployed automatically after a build
- Triggering a deployment by dropping a definition file into a monitored directory
- Performing a mass import of schedule definitions from an existing production system during initial setup
- Generating schedule or package diagrams from a batch process rather than the UI

## What is in this section?

| Topic | Description |
|-------|-------------|
| [Batch processing](batch-processing) | Reference for the `Batch.SMAOpConDeployClient.exe` command-line application — supported functions (DEPLOY, IMPORT, SIMULATE, INIT), all arguments, and usage examples |
| [Scheduled batch deployment](scheduled-batch-deployment) | How to trigger batch deployments from an OpCon job using the BATCH_DEPLOY schedule, including job definition and scheduling considerations |
| [Batch deployment implementation](batch-deployment-implementation) | Implementation requirements and setup steps for enabling scheduled batch deployments, including the BatchScheduleServer configuration |
| [Batch file integration](batch-file-integration) | How to trigger deployments by placing a deployment definition file in a directory monitored by OpCon Deploy |
| [Batch DevOps integration](batch-devops-integration) | How to integrate OpCon Deploy operations into a DevOps CI/CD pipeline using the batch application |
| [Batch diagram processing](batch-diagram-processing) | How to generate schedule and package diagrams from a batch process |

## Glossary

| Term | Definition |
|------|------------|
| Batch processing | The capability to perform OpCon Deploy operations (deploy, import, simulate, init) from the command line using `Batch.SMAOpConDeployClient.exe`, without the interactive client UI. |
| DEPLOY function | The batch action that deploys a defined schedule or package from the central repository to a target OpCon system. |
| IMPORT function | The batch action that imports schedule definitions or transformation rules from a source OpCon system into the central repository. |
| SIMULATE function | The batch action that performs a deployment validation check against the target system without making any changes, returning a report of warnings or confirmation that deployment can proceed. |
| INIT function | The batch action used during initial environment setup to populate the OpCon Deploy repository from an existing production OpCon system, setting all schedule definitions to version 1 and marking them as currently deployed. |
| BATCH_DEPLOY schedule | An OpCon schedule that OpCon Deploy uses to run scheduled batch deployments. Jobs representing pending batch deployments are injected into this schedule at the specified deployment time. |
| BatchScheduleServer | The OpCon server definition configured in OpCon Deploy to host the BATCH_DEPLOY schedule. This server must have the batch deployment capability enabled. |

## FAQs

**Q: What is the difference between batch processing and scheduled batch deployment?**

Batch processing refers to running `Batch.SMAOpConDeployClient.exe` directly from the command line or a script. Scheduled batch deployment is a higher-level capability where OpCon Deploy submits a deployment request to an OpCon job that runs at a future date and time, using the BATCH_DEPLOY schedule on the configured BatchScheduleServer.

**Q: Can I run a simulate check in batch before deploying?**

Yes. Run the batch application with `-a SIMULATE` using the same arguments as a DEPLOY call. If no warnings are returned, you can proceed with the DEPLOY call. In a CI/CD pipeline, this is typically done as a gate before the deployment step.

**Q: How do I encrypt the password used in batch command arguments?**

Use the batch application with the `-ep` argument to encrypt a password value. The encrypted value can then be used in the `-p` argument for subsequent batch calls, avoiding plain-text passwords in scripts or pipeline definitions.
