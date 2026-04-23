---
title: Administration overview
description: "Overview of the OpCon Deploy administration functions — user management, server configuration, audit queries, and global settings."
product_area: OpCon Deploy
audience: System Administrator
version_introduced: "[see release notes]"
tags:
  - Conceptual
  - System Administrator
  - System Configuration
last_updated: 2026-04-01
doc_type: conceptual
---

**Theme:** Overview | **Who is it for?** System administrators responsible for configuring and maintaining the OpCon Deploy environment

## What is it?

OpCon Deploy administration covers the four configuration areas required to operate the system: user management (creating user accounts and assigning roles that control what each user can do), server management (registering the OpCon systems that will participate in deployments and controlling their capabilities), audit queries (reviewing the chronological record of every action performed in the system), and global settings (applying system-wide default behaviors for transformation rules, script handling, and version retention).

## When would you use this section?

- Setting up a new OpCon Deploy user and assigning the appropriate role
- Registering a new OpCon system as a server so schedules can be imported from or deployed to it
- Configuring a server as a production system to enable production-level deploy checks
- Attaching default transformation rules to a server so they are applied automatically to every deployment targeting that server
- Investigating a specific user's activity or reviewing a history of deployment and configuration changes
- Configuring global rules that apply system-wide, such as the number of definition versions to retain

:::note
User and server configuration changes affect all users and all deployments. Plan significant changes during a maintenance window and communicate them to the team beforehand.
:::

## What is in this section?

| Topic | Description |
|-------|-------------|
| [Users](users) | Creating and managing OpCon Deploy user accounts, assigning roles (Administrator, Deployer, Viewer), mapping users to OpCon user credentials, and understanding role-based access |
| [Servers](servers) | Registering OpCon systems in OpCon Deploy, setting server type (production vs. non-production), configuring connection credentials, and attaching default transformation rules |
| [Audits](audits) | Querying the audit log by category, user, date range, or message content to review a chronological record of all user actions |
| [Settings](settings) | Configuring global rules that apply system-wide, including external dependency handling, script deployment behavior, and the number of definition versions to retain |

## Glossary

| Term | Definition |
|------|------------|
| User role | The permission level assigned to an OpCon Deploy user account. Valid roles are Administrator (full access including user and server management), Deployer (can import and deploy but not manage users or servers), and Viewer (read-only access). |
| Server | An OpCon system registered in OpCon Deploy, identified by its REST API connection details and classified as either a production or non-production system. |
| Production server | A server type designation that enables stricter deployment checks — including a comparison of the current definition on the system against the stored deployment record — to detect unauthorized local changes before deployment. |
| Global rule | A system-wide configuration option in OpCon Deploy Settings that applies to all imports and deployments unless overridden at a lower level. |
| Audit category | The classification assigned to each entry in the audit log. Valid values are Deployment, Package, Schedule, Server, TransformationRule, User, and GlobalRule. |

## FAQs

**Q: Who can perform administration tasks in OpCon Deploy?**

Users assigned the Administrator role can access all administration functions, including user management, server management, audit queries, and settings. Deployer and Viewer roles do not have access to administration functions.

**Q: What is the difference between a production and a non-production server?**

Production servers trigger an additional deploy check that compares the current schedule definition on the target system against the definition stored in the deployment record, flagging any discrepancies as a production mismatch. Non-production servers only check whether the schedule already exists on the system.

**Q: Can I see who changed a server definition or modified a user account?**

Yes. All configuration changes — including server and user modifications — are recorded in the audit log with a timestamp and the name of the user who performed the action. Use the Audits function to query by category (Server or User) to find specific records.
