# Using OpCon Deploy

This section provides a brief overview on how to implement OpCon Deploy.

 

Schedules are extracted from OpCon systems and stored in the central repository as definitions. The schedule definition is a comprehensive extract from the OpCon environment and includes the following information:

* The complete schedule definition.
* The complete job definitions.
* All global properties discovered during the extraction process defined in the various definitions associated with the schedule and the jobs.
* All resources and thresholds discovered during the extraction process associated with the schedules and jobs.
* All Annual Plan calendars discovered during the extraction process associated with frequencies. It should be noted that only future dates are added to the extraction.
* All internal (between jobs in the schedule) dependencies discovered during the extraction process.
* All expression dependencies discovered during the extraction process.
* All external dependencies (between jobs in the schedule and jobs in other schedules as well as between jobs in other schedules and jobs in the schedule) discovered during the extract process.
* If jobs are defined as embedded script jobs for Windows and UNIX/Linux job types, the script information as well as the script definition are also extracted.
* If OpCon SAP R3 jobs encountered during import, the SAP server job definitions can be extracted from the SAP server and attached to the definition.
* If OpCon SAP R3 jobs encountered during deploy, the OpCon SAP R3 jobs can be automatically linked with the existing SAP jobs, or the SAP jobs can be created on the SAP server and linked with the OpCon SAP R3 jobs.

## JSON (High-Level Overview)

Schedule definitions are extracted from the source OpCon system and stored in JSON format in the Central repository. The following provides a high-level overview of the JSON format:

![JSON Schedule Definition](/img/json-schedule-definition.png)

Schedules can also be grouped into packages and deployed as a consistent unit.

## General Process (High-Level Overview)

In general, a schedule (SCHED_ABC) will be developed on an OpCon environment (DEV) and once the development is complete, the schedule definition will be imported into the OpCon Deploy and stored in JSON format in the Central Repository, as illustrated in the General Processes graphic.

![General Process Image](/img/general-process.png)

Transformation Rules can also be created and imported into the Central Repository. In this case the diagram shows a set of Transformation Rules associated with each OpCon system imported and inserted as version 1.

When SCHED_ABC is imported into the Central Repository a version number is allocated to the schedule definition and the schedule definition is then ready for deployment to OpCon environments. In General Processes graphic, the schedule SCHED_ABC is deployed to two OpCon production environments (PRODA and PRODB). During deployment, the schedule is transformed using specific transformation rules defined for each OpCon system.

## Modifying Definitions (High-Level Overview)

If changes or corrections are required to an existing schedule definition in the Central Repository, the schedule must be deployed to a development OpCon environment (DEV), as illustrated in the Modifying Schedule Definitions graphic.

![Modifying Definitions Image](/img/modifying-schedule-definitions.png)

A schedule definition in the repository is never overwritten, and any changes to an existing schedule definition in the repository will automatically create a new version of the schedule definition. Once the required changes or corrections to SCHED_ABC are completed, the schedule definition must be imported into the Central Repository causing a new version of the schedule definition to be created. This means that the original schedule definition remains as version 1 while the modified schedule definition becomes version 2. The schedule definition SCHED_ABC is then updated on the OpCon environments (PRODA and PRODB) by deploying version 2 of the schedule definition applying the appropriate transformation rules.

Schedule definition deployment is a multi-step process that consists of a selection process and a deployment process which is broken into two distinct phases (check and deploy), as illustrated in the Overview of Deployment Process graphic.

During the selection process, you are required to select the schedule definition to deploy, the target OpCon system to deploy the schedule to, optionally any transformation rules to apply to the schedule definition and an optional description for the deployment:

![Deployment Process Image](/img/overview-deployment-process.png)

## Two-Step Deployment Process

### Check Step

* This process starts by extracting the schedule definition from the repository and applying schedule definitions to the extracted definition. A new deployment object is also created and the schedule definition is saved in the object (Step 1).

* Server transformation rules are automatically added, as defined in the default rules of the production environment (Step 2).

* At this point, package transformation rules will be applied to schedules that are being deployed as part of a package (Step 3).

:::info Note

These rules are only added to schedule definitions in a package deployment. This step will not occur during a schedule deployment.

:::

* Deployment transformation rules are added to the schedule definition (Step 4).

* A compatibility check is performed to determine if the schedule contains some features that are not supported by the target environment (Step 5).

* A check is made to determine if the schedule definition exists in the target OpCon system by retrieving the schedule definition from the target OpCon system (Step 6).

* If the schedule definition does not exist on the target OpCon system, the process continues with the OpCon Deploy Step.
* If the schedule definition exists on the target system, the JSON schedule definition is saved in the deployment object so that it can be used to restore the schedule definition if required at a future time.

* The deployment information is extracted from the schedule definition. If the schedule definition does not contain deployment information, the process stops and an error message is returned to the user. The user then has the option to cancel the deployment or override the error condition. If override is selected, go to the OpCon Deploy Step.

* The deployment record ID is extracted from the deployment information and the deployment record associated with the previous schedule deployment is retrieved from the repository (Steps 7-9).

* If the OpCon server type is a Production server, a MD5 hash is calculated using the JSON retrieved from the target OpCon system. This value is compared to the MD5 value stored in the deployment record retrieved from the repository. 
If the values match, the deployment process continues to the OpCon Deploy Step.

* If the values do not match, it is an indication that local changes were made to the schedule definition without correcting this in the repository. The process stops and an error message is returned to the user. The user then has the option to cancel the deployment or override the error condition. If override is selected, go to the OpCon Deploy Step (Steps 10-11).

* If the OpCon server type is a Non-production server, the process stops and an error message is returned to the user. The user then has the option to cancel the deployment or override the error condition. If override is selected, go to the OpCon Deploy Step.

### OpCon Deploy Step

* This step completes the deployment process by inserting the schedule definition into the target OpCon system. When inserting the schedule definition into the system, an UPDATE function is performed. This means that the schedule definition is overwritten (Step 12).

* The first action is to create the deployment record from the created Deployment object as the deployment record ID is required for the deployment information inserted into the schedule definition documentation field.

* Create the deployment information consisting of the schedule version, a deployment timestamp, the deployment description and name of user that performed the deployment. Insert the deployment information JSON definition at the beginning schedule documentation field (Step 13).

* The schedule is extracted once more so that it can be saved as the deployed definition in the OpCon Deploy database (Step 14).

* Calculate the MD5 value from the schedule definition.

* OpCon Deploy the schedule definition to the target OpCon system.

* Update the deployment record.