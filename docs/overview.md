---
title: Overview
description: "Introduction to OpCon Deploy — what it is, who uses it, and how the application's core concepts fit together."
product_area: OpCon Deploy
audience: System Administrator, Automation Engineer
version_introduced: "[see release notes]"
tags:
  - Conceptual
  - System Administrator
  - Automation Engineer
  - Getting Started
last_updated: 2026-04-01
doc_type: conceptual
---

**Theme:** Overview | **Who is it for?** System administrators and automation engineers who are new to OpCon Deploy or need a high-level understanding of its purpose and structure

## What is it?

OpCon Deploy is a separate application that works with a central repository containing schedule definitions, transformation rules, and all configuration information needed to move schedule definitions between OpCon environments in a controlled, versioned manner. Every import creates a new version of a definition — nothing is ever overwritten — and all deployment activity is fully audited. Transformation rules allow a single definition to be adapted for multiple target environments without duplication.

## When would you use this section?

- Learning what OpCon Deploy is before implementing it in your environment
- Explaining the product to a colleague or stakeholder
- Orienting yourself to the user interface before exploring specific functions
- Reviewing release notes to understand what has changed in the current version

## What is in this section?

| Topic | Description |
|-------|-------------|
| [Getting Started](getting-started) | High-level overview of OpCon Deploy's purpose, core processes (import, deploy, simulate, rollback, batch, delete), and key concepts |
| [Release Notes](release-notes) | Version history and changes for each OpCon Deploy release |
| [Using OpCon Deploy](using-opcon-deploy) | How to log in, navigate the application, and understand the central repository model |
| [User Interface](user-interface) | Description of the main menu, navigation areas, and UI conventions used throughout the application |

## Glossary

| Term | Definition |
|------|------------|
| Central repository | The OpCon Deploy database that stores all schedule definitions, transformation rules, server definitions, and deployment records. |
| Import | The process of extracting a schedule definition from a source OpCon system and storing it in the central repository as a new version. |
| Deployment | The process of selecting a version of a schedule definition from the central repository and inserting it into a target OpCon system, optionally applying transformation rules. |
| Transformation rule | A set of tag-based substitution instructions applied to a schedule definition during deployment so that environment-specific values (machine names, batch users, properties) are replaced with the correct values for the target system. |
| Version | A numbered, immutable snapshot of a schedule or package definition in the central repository. A new version is created each time a definition is imported. |
| Rollback | The process of redeploying the definition that was retrieved from the target system during the original deployment, restoring the schedule or package to its previous state. |

## FAQs

**Q: What is OpCon Deploy?**

OpCon Deploy is a release management tool for OpCon schedule definitions. It stores versioned copies of schedule definitions in a central repository and provides controlled, audited deployment of those definitions across multiple OpCon environments.

**Q: Who uses OpCon Deploy?**

System administrators configure servers, users, and settings. Automation engineers import schedule definitions, create transformation rules, manage packages, and perform deployments. Both roles use the audit and browse functions to review activity.

**Q: Do I need to install OpCon Deploy separately from OpCon?**

Yes. OpCon Deploy is a separate application with its own installer, database, and service. See [Installation](installation) for requirements and setup steps.
