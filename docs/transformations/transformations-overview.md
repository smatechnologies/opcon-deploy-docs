---
title: Transformations overview
description: "Overview of the transformation rules system in OpCon Deploy — how transformation rules modify schedule definitions during deployment to match the requirements of each target environment."
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

**Theme:** Overview | **Who is it for?** Automation engineers and system administrators who create and maintain transformation rules to adapt schedule definitions for different OpCon environments

## What is it?

Transformation rules are sets of tag-based substitution instructions applied to a schedule definition during deployment. They allow a single definition stored in the central repository to be deployed correctly to multiple OpCon environments — production, test, development — by replacing environment-specific values such as machine names, batch users, global properties, and frequency definitions at deployment time. Rules can be applied at three levels (server, package, and deployment) and versioned in the repository for consistent reuse.

## When would you use this section?

- Creating a transformation rule to replace machine names or batch users when deploying to a new environment
- Understanding the tag IDs and value structures used to define transformation rules
- Working through tag examples to build correct rule definitions before using them in a deployment
- Using special definitions (environment, Frequency_Use_Existing_Definitions, Move_Schedule_Package) for migration projects or parallel test environments

## What is in this section?

| Topic | Description |
|-------|-------------|
| [Transformation rules](transformation-rules) | How to import, create, edit, and browse transformation rules; the three levels at which rules are applied (server, package, deployment); and how to attach rules to server and package definitions |
| [Transformation tag definitions](transformation-tag-definitions) | Reference for every supported tag ID — the fields each tag transforms, expected value formats, and usage notes |
| [Transformation tag examples](transformation-tag-examples) | Worked examples of transformation rule JSON structures for common tag scenarios |
| [Transformations — special definitions](transformations-special-definitions) | The environment, Frequency_Use_Existing_Definitions, and Move_Schedule_Package special tags used for parallel testing and schedule migration projects |

## Glossary

| Term | Definition |
|------|------------|
| Transformation rule | A named, versioned set of tag-based substitution instructions stored in the OpCon Deploy repository. During deployment, each matching tag value in the schedule definition is replaced with the specified new value. |
| Tag ID | The identifier for a specific field or attribute within a schedule definition that a transformation rule can target, such as machine name, batch user, global property name, or frequency name. |
| currentValue | The existing value in the schedule definition that a transformation tag will match and replace during deployment. |
| newValue | The replacement value that a transformation tag will write into the schedule definition when a currentValue match is found. |
| Server-level rule | A transformation rule attached to a server definition; applied automatically to every deployment targeting that server and takes the highest precedence. |
| Package-level rule | A transformation rule attached to a package definition; applied to every deployment of that package, after server-level rules. |
| environment tag | A special transformation tag that prefixes schedule names, property names, resource names, threshold names, and script names throughout a definition with a specified value, creating an isolated copy for parallel testing within a single OpCon system. |
| Move_Schedule_Package | A special transformation tag that adds, replaces, or removes a prefix on schedule names, frequency names, global property names, resource names, and threshold names to support promoting a schedule through development, test, and production stages. |

## FAQs

**Q: At what point during a deployment are transformation rules applied?**

Transformation rules are applied after the definition is retrieved from the repository and before it is written to the target OpCon system. The rules are applied in level order: server-level rules first, then package-level rules, then deployment-level rules.

**Q: What happens if two rules target the same tag with the same currentValue?**

The rule applied at the higher level takes effect. Lower-level rules that would transform the same tag from the same value are marked as ignored in the transformation rules tree because the value has already been changed by the higher-level rule.

**Q: Can I apply transformation rules to a schedule that is not part of a package?**

Yes. Transformation rules can be applied at the deployment level for individual schedule deployments, in addition to any server-level rules that apply automatically to the target server.
