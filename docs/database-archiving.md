---
title: Database archiving
description: "Understand how OpCon Deploy archives schedule, package, transformation rule, and deployment records that are no longer needed in the main tables."
tags:
  - Reference
  - System Administrator
  - System Configuration
---

# Database archiving

**Theme:** Configure  
**Who Is It For?** System Administrator

OpCon Deploy includes the capability to archive records no longer required in the deploy_package, deploy_schedule, deploy_deployment, and deploy_transformation_rule tables.

## When would you use this?

* Reducing database size after many import and deployment cycles have created a large number of stored versions
* Enforcing a version retention policy by removing older versions that are no longer needed while preserving active deployments
* Maintaining performance of the OpCon Deploy repository over time as record counts grow

* Archiving is performed using a designated value that indicates how many versions should be maintained in the main tables. The value is set using the Settings function (Number of versions to retain). The default value is 5
* Archiving is a complex process that checks the various tables to determine if the version is still active as an active version cannot be archived
* During the archiving process, if a deployment record is associated with the schedule or package version that is being archived, the deployment record will also be archived

A schedule (```DEPLOY_UTILITIES.json```) containing the job definitions for the archive process is available in the templates directory of the client software. The machine name, directory, frequency, and user code that the jobs run under need to be transformed to match the target environment. The global property SMADeployPath should be set to the client installation directory so the programs can be run.

It is recommended that the jobs are scheduled on a weekly basis.

## ArchiveS.SMAOpConDeployClient.exe

This program is used to archive schedule definitions and associated deployment definitions.

During the processing a list of all schedules is retrieved from the database. An initial check is made to determine if the number of schedule versions currently in the database for the individual schedule exceeds the designated value. If the number of versions exceeds the designated value, the processing for the schedule continues.

A list of schedule versions to be archived is then extracted from the database and a check is made to determine if the schedule version is part of a package. If the schedule version is part of a package, processing stops as the version will then be handled by the ArchiveP program (archives packages).

A check is then made to determine if the version is still an active deployment as active deployments cannot be archived. If the version is an active deployment, processing stops.

If the version is not part of a package or not active it is marked for archive.

A check is then made if a deployment record for the schedule version exists in the deploy_deployment table. If a record exists, it is marked for archive.

When checking is complete, the records marked for archive are processed.

## ArchiveP.SMAOpConDeployClient.exe

This program is used to archive package definitions and associated schedule and deployment definitions.

During the processing a list of all packages is retrieved from the database. An initial check is made to determine if the number of package versions currently in the database for the individual package exceeds the designated value. If the number of versions exceeds the designated value, the processing for the package continues.

A list of package versions to be archived is then extracted from the database and a check is made to determine if the package version is still an active deployment as active deployments cannot be archived. If the version is an active deployment, processing stops.

If the version is not active, it is marked for archive.

A check is then made if a deployment record for the package version exists in the deploy_deployment table. If a record exists, it is marked for archive.

The schedule versions associated with the package are then marked for archive. When checking is complete, the records marked for archive are processed.

## ArchiveT.SMAOpConDeployClient.exe

This program is used to archive transformation rules.

During the processing a list of all transformation rules is retrieved from the database. An initial check is made to determine if the number of transformation rule versions currently in the database for the individual transformation rule exceeds the designated value. If the number of versions exceeds the designated value, the processing for the transformation rule continues.

A list of transformation rule versions to be archived is then extracted from the database and a check is made to determine if the transformation version is part of a server, package or deployment definition, it cannot be removed. If the deployment, server or package records are removed, the transformation rule will no longer be linked and will be available for removal.

## Arguments

The ArchiveP.SMAOpConDeployClient.exe, ArchiveS.SMAOpConDeployClient.exe, and ArchiveT.SMAOpConDeployClient.exe programs support the following arguments:

**-u**	

* Required argument which defines the OpCon Deploy user that will perform the action
    * The required user must be the OpCon Deploy user—not an OpCon or database user—and must be part of the administration group

**-p**

* Required argument that consists of the password of the user that is defined in the -u argument
    * The password must be encrypted using the encryption tool provided by the Enterprise Manager


## Examples

```
C:\test\deploy\ArchiveP.SMAOpConDeployClient.exe -u admin -p lBsC5ohnSf2P7/Ku81FiGw==
```
 
```
C:\test\deploy\ArchiveS.SMAOpConDeployClient.exe -u admin -p lBsC5ohnSf2P7/Ku81FiGw==
```
 
```
C:\test\deploy\ArchiveT.SMAOpConDeployClient.exe -u admin -p lBsC5ohnSf2P7/Ku81FiGw==
```

## Exception handling

| Error or symptom | Meaning | How to fix it |
|---|---|---|
| Archive program fails to start or reports a database connection error | The archive program cannot connect to the OpCon Deploy database, likely due to incorrect credentials or database unavailability | Confirm that the OpCon Deploy database is running and that the `-u` and `-p` arguments supply a valid Deploy administration user and encrypted password |
| A schedule version is skipped and not archived | The version is still recorded as an active deployment in the deploy_deployment table and cannot be archived | Roll back or remove the active deployment for that version before running the archive program again |
| A schedule version is skipped because it is part of a package or server/deployment definition | The version is linked to an active package or is referenced by a server or deployment definition, preventing removal | Use ArchiveP.SMAOpConDeployClient.exe to archive the package first, or remove the server/deployment definition references so the transformation rule version is no longer linked |

## Key terms

**Archive** — the process of moving schedule, package, transformation rule, and deployment records that are no longer needed in the main tables to archive tables, triggered when the number of stored versions for an item exceeds the configured retention value.

**Versions to retain** — the configurable count (default 5) that determines how many versions of each schedule, package, or transformation rule are kept in the main tables; versions beyond this count become candidates for archiving, provided they are not active.

**Active deployment** — a deployment record whose status marks a schedule or package version as currently deployed to a target OpCon system; active deployments cannot be archived because removing them would destroy the rollback information needed to restore the previous state.

**Related topics:**

- [Settings](administration/settings)
- [Batch processing](batch-processing)
