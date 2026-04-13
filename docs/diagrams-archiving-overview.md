---
title: Diagrams and archiving overview
description: "Overview of the visual diagram and database archiving tools available in OpCon Deploy."
product_area: OpCon Deploy
audience: Automation Engineer, System Administrator
version_introduced: "[see release notes]"
tags:
  - Conceptual
  - Automation Engineer
  - System Administrator
  - System Configuration
last_updated: 2026-04-01
doc_type: conceptual
---

**Theme:** Overview | **Who is it for?** Automation engineers who want to visualize schedule structures and system administrators who manage the OpCon Deploy database

## What is it?

This section covers two supporting tools in OpCon Deploy: the diagram generator, which creates PDF visualizations of package and schedule structures to aid review and documentation; and the database archiving function, which moves older deployment, server, and package records out of active tables and into archive tables to control database growth.

## When would you use this section?

- Generating a visual diagram of a package before deployment to verify the schedule and job structure
- Creating header-level diagrams to share with stakeholders who need a high-level view of dependencies
- Archiving old deployment records to reduce the size of the active database tables
- Reviewing the criteria used to determine which records are eligible for archiving

## What is in this section?

| Topic | Description |
|-------|-------------|
| [Package and schedule diagram](package-and-schedule-diagram) | How to generate full and header-level PDF diagrams of schedule and package definitions, including job, resource, and dependency layouts |
| [Database archiving](database-archiving) | How the archiving function works, which record types and statuses are eligible, and how to run the archive process |

## Glossary

| Term | Definition |
|------|------------|
| Package diagram | A PDF document generated from a package definition that shows all schedules, jobs, resources, and job dependencies within the package. |
| Header diagram | A simplified PDF diagram that shows only the schedule header and container jobs, plus any job dependencies between them. |
| Archive | The process of moving inactive or rolled-back deployment records, deleted server records, and deleted package records from the active OpCon Deploy tables into corresponding archive tables. |
| Active record | A deployment, server, or package record in a status that makes it ineligible for archiving; active deployment records cannot be archived. |

## FAQs

**Q: What format are the diagrams exported in?**

Diagrams are generated and displayed in PDF format.

**Q: Does archiving delete records permanently?**

No. The archive process moves records to archive tables within the same database. The records are no longer visible in the active browse views but are not deleted from the database.

**Q: Which deployment statuses are eligible for archiving?**

Inactive, rolled-back, and cancelled deployment records are eligible. Active deployment records cannot be archived. Server records that have been deleted and package records that have been deleted are also eligible.
