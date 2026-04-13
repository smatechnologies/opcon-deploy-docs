---
title: Scripts overview
description: "Overview of the script management and deployment functions in OpCon Deploy — how embedded scripts are stored, versioned, and deployed alongside schedule definitions."
product_area: OpCon Deploy
audience: Automation Engineer
version_introduced: "[see release notes]"
tags:
  - Conceptual
  - Automation Engineer
  - Jobs
last_updated: 2026-04-01
doc_type: conceptual
---

**Theme:** Overview | **Who is it for?** Automation engineers who use embedded scripts in OpCon jobs and need to manage script versions across environments

## What is it?

The Scripts section covers how OpCon Deploy handles embedded scripts — the reusable scripts stored in the OpCon script repository and referenced by jobs. The script management function controls how OpCon Deploy includes or excludes scripts when importing and deploying schedules. The scripts import and deploy function allows scripts to be transferred between OpCon systems directly, independently of schedule deployments.

## When would you use this section?

- Configuring whether embedded scripts are included or excluded when schedule definitions are imported
- Deploying a script to a new OpCon system before deploying schedules that reference it
- Reviewing which scripts are stored in the OpCon Deploy repository and their version history
- Troubleshooting a deployment failure caused by a missing or mismatched script on a target system

## What is in this section?

| Topic | Description |
|-------|-------------|
| [Script management](script-management) | Settings that control how OpCon Deploy handles embedded scripts during import and deployment, including the global rule for excluding scripts from schedule deployments |
| [Scripts — import and deploy](scripts) | How to import scripts from an OpCon system into the OpCon Deploy repository and deploy stored script versions to target OpCon systems |

## Glossary

| Term | Definition |
|------|------------|
| Script repository | The OpCon system feature that stores reusable scripts centrally and makes them available for use in job definitions as embedded scripts. |
| Embedded script | A script stored in the OpCon script repository and referenced by a job definition; the script is sent to the target agent at runtime rather than being stored on the agent's file system. |
| Script version | A numbered snapshot of a script stored in the OpCon Deploy repository. A new version is created each time the script is imported and differs from the latest stored version. |
| Exclude Script from Schedule Deployment | A global rule in OpCon Deploy settings that prevents embedded scripts from being included in or deployed with schedule definitions, leaving script management to a separate process. |

## FAQs

**Q: Are embedded scripts automatically included when I import a schedule?**

By default, yes — if the schedule contains jobs with embedded scripts, those scripts are included in the schedule definition. If the **Exclude Script from Schedule Deployment** global rule is enabled in Settings, scripts are excluded from all schedule imports and deployments.

**Q: Can I deploy a script to multiple OpCon systems at once?**

Scripts are deployed to one target system at a time through the Scripts deploy function. For mass deployments, use the batch processing capability.

**Q: What happens if a script referenced by a deployed schedule does not exist on the target system?**

The Simulate function checks whether scripts referenced in the schedule are available on the target system. A warning is generated for any missing scripts, and deployment is blocked until the issue is resolved.
