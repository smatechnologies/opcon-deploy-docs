---
sidebar_label: 'Release notes'
title: OpCon Deploy release notes
description: "Version history and change details for OpCon Deploy, including new features, improvements, and bug fixes."
tags:
  - Reference
  - System Administrator
  - Automation Engineer
---

# OpCon Deploy release notes

The Deploy client is not paired with a specific OpCon release. If specific OpCon versions are required, they are noted in the release information.

There are no Deploy patch releases — corrections are applied to the main software and a new version is released on a regular basis.

Deploy contains compatibility checks to ensure that features supported in newer OpCon releases are not deployed to older OpCon releases.

The ImpEx2 server portion of Deploy is paired with each specific OpCon release and is part of the OpCon release. The ImpEx2 server for each release is patched and released within the OpCon release cycles.

## 26

### 26.0.0

2026 February

:::note Migration considerations
Deploy 26.0 is matched with OpCon Cloud 25.3 or greater or OpCon Data Center 26.0. It contains the newer OpCon login libraries that support the longer OpCon user passwords. Deploy 26.0 can also communicate with previous OpCon versions, but Deploy 25.2 or lower cannot communicate with OpCon 25.3 or 26.0 systems.

When performing an upgrade, upgrade test environments and Deploy first.
:::

### What's new

:eight_spoked_asterisk: **CON-633**: Add new SAP_Step_Param_Name transformation rule supporting the transformation of the param value of the SAP job definition.

:eight_spoked_asterisk: **CON-632**: During a simulation task, the created schedule definition is written out to the defined configuration `diagramDirectory` in the client `config.ini` file. This function can be used to check generated transformation rules.

:eight_spoked_asterisk: **CON-777**: Support OpConMFT Archive Files and Reprocess Files field types during export and import of OpConMFT job types. Requires matching ImpEx2 26.0.x or 26.1.x versions.

### Why this matters

SAP job transformations become more granular, deployment simulations now produce verifiable output files that can be reviewed before go-live, and OpConMFT file management covers a wider range of field types — together reducing pre-deployment validation effort across all environments.

## 25

### 25.3 (OpCon Cloud)

2025 October

:::note
This is an OpCon Cloud-only version. It supports the new OpCon long user passwords.
:::

:::note ImpEx2 version requirements
Cloud 25.3.0
:::

### What's new

:eight_spoked_asterisk: **OPCDEPLOY-1412**: Included support for long OpCon user passwords.

:eight_spoked_asterisk: **CON-631**: Add new SAP_Step_Param_Name transformation rule supporting the transformation of the param value of the SAP job definition.

### Why this matters

Cloud deployments now support the longer, more secure user passwords introduced in OpCon 25.3, keeping Deploy fully compatible as the platform evolves to stronger credential requirements.

### 25.2

2025 October

:::note Migration considerations
New rule **Merge Schedule Instance Properties** indicates whether schedule instance properties should be merged when the rule **Update Schedule instance properties allowed** is not selected during the deployment process. The default value is false, so existing installations are not affected.
:::

:::note ImpEx2 version requirements
OnPrem 25.0.4 / 23.0.12 / 22.0.22
:::

### What's new

:eight_spoked_asterisk: **OPCDEPLOY-1407**: Implemented new feature to correctly merge Schedule Instance Properties when the rule **Update Schedule instance properties allowed** is not selected.

For more information see the **Merge Schedule Instance Properties** rule in the [Settings](administration/settings) section.

### Why this matters

Teams can now fine-tune how schedule instance properties are merged during deployment, preventing unintended overwrites of target-environment values while still allowing targeted updates where needed.

#### Fixes

:eight_spoked_asterisk: **OPCDEPLOY-1400**: Fixed a problem during package creation when all versions selected when doing a schedule selection refresh.

:eight_spoked_asterisk: **OPCDEPLOY-1409**: Fixed an External Dependencies loss problem during transformation when the Schedule_Named_Instance transformation rule is defined.

:eight_spoked_asterisk: **OPCDEPLOY-1411**: Fixed a problem when the Job_Machine_Name transformation rule is defined and the machine names are not transformed in the Roles `machineInfoList` field.

:eight_spoked_asterisk: **OPCDEPLOY-1413**: Fixed a problem when transforming system properties using the Environment attribute and the system property has a date offset value.

:eight_spoked_asterisk: **OPCDEPLOY-1414**: Fixed a problem with the `archive_status` constraint of the `deploy_deployment_archive` table by adding the Failed status to the constraint.

### 25.1

2025 March

:::note Migration considerations
New rule **Exclude calendars from schedule deployment** removes calendar updates during the deployment process. The default value is false, so existing installations are not affected. Once enabled, calendar definitions will no longer be included in the schedule definitions in the `calendarList` section.
:::

### What's new

:eight_spoked_asterisk: **OC-325**: Support new job type RPA. Due to the specific nature of the RPA scripts being associated with specific agents, the deploy process does not include the scripts in the deployment process. Requires OpCon 25.1.0 or greater.

:eight_spoked_asterisk: **OPCDEPLOY-1398**: Added new fields on the **Check In Summary** screen during the schedule import process to allow for the creation of a package from the selected schedules. The existing **Include Sub-Schedules** option can be used to extract all sub-schedules associated with the selected schedules and include them in the package.

- **Create Package from Schedules** — when selected, creates a package from the list of imported schedules (requires **Package Name**).
- **Package Name** — the name of the package to create.

:eight_spoked_asterisk: **OPCDEPLOY-1403**: Implemented new feature to prevent the update of calendars during the deployment process. When enabled, calendars are no longer included in the schedule import and deployment processes.

For more information see the **Exclude calendars from Schedule Deployment** rule in the [Settings](administration/settings) section.

:eight_spoked_asterisk: **OPCDEPLOY-1405**: Added new argument `-noi` to `Devops.SMAOpConDeployClient.exe` for the schedule and script EXPORT action. This option prevents the exported schedule or script from being inserted into the Deploy database during the EXPORT action.

:eight_spoked_asterisk: **OPCDEPLOY-1406**: Added new argument `-iss` to `Devops.SMAOpConDeployClient.exe` for the schedule EXPORT action. This option includes all sub-schedules associated with the named schedule, creating a single definition file containing all the schedules.

### Why this matters

RPA automation joins the roster of deployable job types; package creation now happens directly from the import workflow in a single step; and calendar and script exclusion rules give CI/CD pipelines precise control over what each deployment touches — reducing both manual effort and unintended side-effects in target environments.

#### Fixes

:eight_spoked_asterisk: **OPCDEPLOY-1404**: Fixed a problem when using `Devops.SMAOpConDeployClient.exe` to deploy a schedule containing embedded scripts. During the deployment process the schedule and scripts are inserted into the Deploy database. When inserting the scripts into the Deploy database, a check for missing script versions is performed causing the NPE as there is no source OpCon system (source is the DevOps repository).

### 25.0

2025 January

:::note Migration considerations
This release of Deploy requires matching OpCon versions 25.0.0, 23.0.9, and 22.0.20. A special ImpEx2 patch for OpCon 22.0.19 can be requested from support.

New rule **Exclude scripts from schedule deployment** separates the deployment of schedules and scripts. The default value is false, so existing installations are not affected. Once enabled, script definitions will no longer be included in the schedule definitions in the `scriptList` section.

- If the rule is not selected, the appropriate script/version will be created as part of the schedule deployment process.
- If the rule is selected, the appropriate script/version must be created before the schedule deployment process.

Transformation **Environment** changes have been added to facilitate the duplication of schedules within a single OpCon system to create a unique execution environment. The defined environment value will now be prefixed to the machine name and the script name, creating a unique instance of the script during the deployment process.
:::

### What's new

:eight_spoked_asterisk: **OPCDEPLOY-1390**: Implemented new transformation rules for Job, OS2200 Element Name, and OS2200 Runid definitions. The following rules support name changes using masking (wildcards `?` and `*`):

* `Job_Name_Mask` — transform the job name using a mask.
* `OS2200_Elementname_Mask` — transform the OS2200 element name using a mask.
* `OS2200_Runid_Mask` — transform the OS2200 Runid using a mask.

:eight_spoked_asterisk: **OPCDEPLOY-1392**: Implemented new feature to split the importing and deployment of schedules and scripts. When enabled, scripts are no longer included in the schedule import and deployment processes. Scripts must be imported and deployed using the Deploy **Scripts** import and deploy processes. Individual script deployment does not currently support transformation.

- When specific script versions are required during the schedule deployment process, the script version must be available on the target system.
- When using the **Script Name** transformation during schedule or package deployment, the script name must already exist on the target OpCon system.
- Simulate has been updated to include checking for scripts and versions.

For more information see the **Exclude Script from Schedule Deployment** rule in the [Settings](administration/settings) section.

### Why this matters

Scripts and schedules can now be deployed independently, allowing teams to manage script versioning and promotion on a separate cadence from schedule changes — critical for environments with strict change-control boundaries where a script update should not force a full schedule re-deployment.

#### Fixes

:eight_spoked_asterisk: **OPCDEPLOY-1389**: Fixed a problem when deploying scripts where roles are not set correctly. During the import process, role names are extracted and inserted into the `deploy_script` tables. During deployment, role names are included in the deployment object, resulting in the script having the required roles assigned.

- This change adds a new column `roles` to the `deploy_script` table. Null values are allowed so there is no impact to existing records.

:eight_spoked_asterisk: **OPCDEPLOY-1393**: Fixed a problem when importing a script which has a new version and additional roles — the additional roles are not added to the `deploy_script` table.

#### OpCon fixes

:eight_spoked_asterisk: **OPCON-25833**: Fixed a problem during the script extract process to include a list of roles associated with the script. Fixed a problem during the script deployment process to assign the roles associated with the script.

:eight_spoked_asterisk: **OPCON-25933**: Made enhancements to Windows and Unix job import to support splitting Deploy script and schedule/package deployments. Import routines now check the local OpCon database for script information (script, script type, runner IDs) as the script information is no longer part of the OpConExtract object.

## 23

### 23.3

2024 October

:eight_spoked_asterisk: **OPCDEPLOY-1387**: Fixed a problem during deployment ensuring script versions are placed in the version list in ascending order to prevent problems inserting versions into the OpCon database.

:eight_spoked_asterisk: **OPCDEPLOY-1388**: Fixed a problem during package creation when schedule versions are retained in the selection list, causing duplicates when a refresh is performed and the schedules are part of the subsequent selection.

### 23.2

2024 August

:eight_spoked_asterisk: **OPCDEPLOY-1380**: Fixed a problem during deployment when checking if the deployment has a previous deployment failure.

:eight_spoked_asterisk: **OPCDEPLOY-1382**: Fixed a problem during package creation when newly selected schedule versions are removed from the selection list when the **Refresh** button is selected to search for schedule versions to include in the package.

:eight_spoked_asterisk: **OPCDEPLOY-1383**: Updated database scripts to support SQL-Azure.

:eight_spoked_asterisk: **OPCDEPLOY-1384**: Added a `.l4j.ini` file for the Deploy client increasing the JVM heap size to prevent heap memory thrashing when very large definitions are being deployed.

:eight_spoked_asterisk: **OPCDEPLOY-1385**: Fixed a partial update of resource/threshold names during transformation of Threshold Update resources.

:eight_spoked_asterisk: **OPCDEPLOY-1386**: Fixed the setting of the reset AutoBuild and AutoDelete flags from only for reset to when selected when creating the `importRules` object.

### 23.1

2024 May

### What's new

:eight_spoked_asterisk: **OPCDEPLOY-843**: Fixed a problem when transformation rule names are queried using case sensitivity.

:eight_spoked_asterisk: **OPCDEPLOY-1301**: Implemented new transformation rules for machine group name to machine name definitions:

* `Job_Machine_Group_Name_to_Machine_Name` — transform a machine group name to a machine name.
* `Job_Machine_Name_to_Machine_Group_Name` — transform a machine name to a machine group name.

:eight_spoked_asterisk: **OPCDEPLOY-1365**: Fixed a problem displaying all versions of a selected item in the selection view when creating or editing packages.

:eight_spoked_asterisk: **OPCDEPLOY-1378**: Implemented support for new GuideWireCloud and ACS job types. Compatibility check implemented to ensure these job types can only be deployed to OpCon versions 23.0 or greater. Requires updated ImpEx2 OpCon versions for OpCon versions 24.2.0 or 23.0.4.

### Why this matters

Machine group and machine name transformations can now be swapped bidirectionally during deployment, and two new cloud-native job types — GuideWireCloud and ACS — are fully supported, expanding the range of workloads Deploy can manage across environments.

### 23.0

2024 February

:eight_spoked_asterisk: **OPCDEPLOY-1374**: Fixed a NPE encountered during File Transfer job transformation when the File_Transfer_Destination_Machine tag is used and a Machine Group is defined instead of a Primary Machine.

:eight_spoked_asterisk: **OPCDEPLOY-1375**: Fixed a NPE encountered during package simulation when transformation is used and the package is a new version that has removed a schedule from the previous version.

:eight_spoked_asterisk: **OPCDEPLOY-1376**: Fixed the missing backslash (`\\`) problem encountered during Windows job partial transformation when the Windows_Command_Line or Windows_Working_Directory tags are used.

## 22

### 22.6

2024 January

### What's new

:eight_spoked_asterisk: **OPCDEPLOY-1360**: Fixed a problem when the transformation rule is Schedule_Instance_Property and the job type is Windows embedded script and there are no script arguments. An attempt is made to check the arguments for the schedule instance property and it fails with a NPE as there are no arguments.

:eight_spoked_asterisk: **OPCDEPLOY-1361**: Implemented new transformation rules for MS SQL job definitions:

* `SQL_Script_Server` — transform the server name field of the MS SQL Script job action.
* `SQL_Script_Database` — transform the database name field of the MS SQL Script job action.
* `SQL_Script_User` — transform the user name field of the MS SQL Script job action.
* `SQL_Script_Filename` — transform the script file name field of the MS SQL Script job action.
* `SQL_Job_Server` — transform the server name field of the MS SQL JOB job action.
* `SQL_Job_Jobname` — transform the job name field of the MS SQL JOB job action.
* `SQL_Job_User` — transform the user name field of the MS SQL JOB job action.
* `SQL_DTExec_Server` — transform the server name field of the MS SQL DTExec job action.
* `SQL_DTExec_Package_Path` — transform the package field of the MS SQL DTExec job action.
* `SQL_DTExec_User` — transform the user name field of the MS SQL DTExec job action.

:::note
This feature requires matching OpCon fix OPCON-22789, included in OpCon releases 23.0.0, 21.0.25, and 22.0.13. If required before those release dates, an OpCon ImpEx2 patch for OpCon releases 21.0 and 22.0 can be requested from support.
:::

:eight_spoked_asterisk: **OPCDEPLOY-1367**: Implemented new global rule **Package update unchanged Schedules**. During package deployment, a check is made to see if the schedule version of the target schedule within the package matches the schedule version of the schedule to be deployed. If the versions match, only the schedule deployment information is updated on the target schedule. If this rule is selected, the target schedule contents will be overwritten.

### Why this matters

Ten new MS SQL transformation rules cover all major job action fields, making it straightforward to promote MS SQL jobs across environments without manual edits. The new package rule also prevents unnecessary schedule overwrites when the deployed version is unchanged, reducing both deployment risk and time.

### 22.5

2023 September

:eight_spoked_asterisk: **OPCDEPLOY-1353**: Fixed a performance issue with large databases when browsing records (schedules, transformation rules, scripts, deployments, and packages).

Previously, all records were retrieved from the database and then added to the selection lists. Now, enter a text string in the filter field — the text is used to retrieve only matched records from the database. Enter an asterisk (`*`) to fetch all records. The filter does not support wildcards. For example, enter `test` to retrieve records whose name includes `test`.

### 22.4

2023 August

:eight_spoked_asterisk: **OPCDEPLOY-1354**: Fixed an issue where certain updates to the OpCon API in newer versions (such as 22.7.0) resulted in an error in Deploy because it found unrecognized fields being returned by the API instead of simply ignoring them.

:eight_spoked_asterisk: **OPCDEPLOY-1355**: Fixed an issue where sub-schedule names containing spaces prevented a diagram from being created — diagram node names containing spaces were not supported.

### 22.3

2023 April

### What's new

:eight_spoked_asterisk: **OPCDEPLOY-1341**: Added new **Include sub-schedules** option on the Check In Summary page that recursively adds sub-schedules found during a schedule import to the import process. The import result of each schedule is displayed in the results view. The message reporting that the schedule version already exists has been changed to a WARNING message with a dark yellow color.

:eight_spoked_asterisk: **OPCDEPLOY-1343**: Added **Update Schedule Versions** button to the Package dialog. When selected, the schedules associated with the package are updated to the latest version of the schedule in the Deploy database.

### Why this matters

Sub-schedules can now be automatically discovered and included during import rather than requiring separate imports for each, and package schedule versions can be bulk-updated to the latest in a single click — reducing the manual effort of keeping packages current as schedules evolve.

### 22.2

2023 March

### What's new

:eight_spoked_asterisk: **OPCDEPLOY-1338**: Separated reset AutoBuild days and AutoDelete days into two separate rules. AutoBuild days and AutoDelete days can now be reset independently.

:::note ImpEx2 version requirements
This implementation requires matched SMA OpCon ImpEx2 versions: OpCon 22.1 or greater, OpCon 22.0.2 or greater, OpCon 21.0.14 or greater, and OpCon 20.0.20 or greater.
:::

### Why this matters

AutoBuild and AutoDelete behavior can now be configured independently per environment, giving operations teams precise control over schedule build windows without inadvertently resetting deletion policies at the same time.

### 22.1

2022 December

:eight_spoked_asterisk: **OPCDEPLOY-1331**: Corrected an error that enabled the Job Name field for the Role Name transformation rule.

:eight_spoked_asterisk: **OPCDEPLOY-1332**: Corrected an error when more than one job name field is defined in a set of transformation rules.

:eight_spoked_asterisk: **OPCDEPLOY-1335**: Changed logging, moving large logging entries to DEBUG, and corrected log setup to ensure DEBUG is turned off by default.

:eight_spoked_asterisk: **OPCDEPLOY-1336**: Corrected package simulation error when only the first schedule in a package is compared instead of all schedules in the package.

:eight_spoked_asterisk: **OPCDEPLOY-1339**: Added OpConMFT job-type compatibility check for OpCon version 22.0.

### 22.0

2022 December

### What's new

:eight_spoked_asterisk: **OPCDEPLOY-1319**: Deploy now provides a new batch process `File.SMAOpConDeployClient`, which supports extraction of schedules and scripts from either an OpCon system or the Deploy repository. It also supports inserting schedule definitions or script versions from files into the Deploy repository.

:eight_spoked_asterisk: **OPCDEPLOY-1321**: Added backend integration with DevOps to enable retrieval of schedules or script versions from a branch within the repository.

:eight_spoked_asterisk: **OPCDEPLOY-1320**: Deploy now provides a new batch process `Devops.SMAOpConDeployClient`, which supports extraction of schedules and scripts from an OpCon system. It also supports deploying a schedule or script version from files or from a DevOps repository. When deploying a schedule or script, the definition is first stored in the Deploy repository and then deployed to the target system using the standard Deploy mechanism.

:eight_spoked_asterisk: **OPCDEPLOY-1322**: Added script name change transformation rule. During environment transformation, a prefix is now added to the script to create a unique instance of the script for the defined environment.

### Why this matters

Deploy can now participate fully in DevOps and CI/CD pipelines: schedules and scripts can be extracted from and deployed to OpCon directly from a source-control branch, enabling automated promotion workflows without manual intervention through the Deploy UI.

## 21

### 21.2

2022 September

:white_check_mark: **OPCDEPLOY-1324**: Created updated EM-Core-API library for ImpEx2.

:white_check_mark: **OPCDEPLOY-1317**: Department and Access code are not deployed when deploying a package.

:white_check_mark: **OPCDEPLOY-1323**: Concurrent deployments create a deadlock on the deployment table, resulting in the deployment of a schedule succeeding but the information in the Deploy database not being updated.

:white_check_mark: **OPCDEPLOY-1325**: Script versions not imported correctly when performing a file import.

:white_check_mark: **OPCDEPLOY-1326**: During transformation, environment tag not applied to Event Trigger Job Completion Complex Expression for TH name.

:white_check_mark: **OPCDEPLOY-1325**: Fixed issues with the Import file function when the schedule definition file contains embedded script jobs.

:white_check_mark: **OPCDEPLOY-1317**: Corrected merging of Department and Access Code information during package creation.

:white_check_mark: **OPCDEPLOY-1323**: Optimized transaction demarcation during the deploy process. The initial deployment record is created outside the transaction and a new deployment status **Failed** will be displayed if the deployment fails. If the deployment is restarted and completes successfully, the initial deployment record will be used.

:white_check_mark: **OPCDEPLOY-1326**: Added environment transformation to TH, RM, and RU properties when used within Dependency expressions and event complex expressions.

### 21.1

2022 February

### What's new

:eight_spoked_asterisk: **OPCDEPLOY-1311**: Deploy now allows role names to be part of the transformation, to map them to the names on the target system. Role_Add: This tag is used to add a Role during deployment. The Role name will be added in Role, schedules, scripts, and departments. The new Role name must be defined in the target system. This tag supports the following: `newValue` (required): Contains the name of the Role to add. All other fields are disabled.

:eight_spoked_asterisk: **OPCDEPLOY-1303**: Deploy now allows role names to be part of the transformation, to map them to the names on the target system. Role_Name: This tag is used to change the name of a Role that is associated with the deployment. The Role name will be updated in Role, schedules, scripts, and departments. The new Role name must be defined in the target system. This tag supports the following: `currentValue` (required): Contains the name of the Role to change in the definitions. `newValue` (required): The value to be inserted in the definition if the `currentValue` matches the value in the definition. `partialUpdate`: Indicates if the match to be performed is against the complete definition or a partial definition (`true` or `false`; default is `false`).

:eight_spoked_asterisk: **OPCDEPLOY-1309**: Added Auto Build Reset capabilities during deployment of schedules and packages. When setting the auto build options, first select the **Auto Build** option and then set the values for Days In Advance and Days. When selecting the **Auto Build** option, the values are initially set to 1. When not selected, the values are set to 0. To reset the Auto Build and Auto Delete values, select the **Auto Build** option and set the Days in Advance and Days values to 0. This removes the Auto Build and Auto Delete values.

### Why this matters

Role names can now be added or remapped as part of deployment transformation, so schedules that reference environment-specific roles deploy correctly to target systems without manual post-deployment edits. Auto Build reset is also now fully controllable during deployment.

#### Fixes

:white_check_mark: **OPCDEPLOY-1315**: Added more informational logging when working with SAP jobs.

:white_check_mark: **OPCDEPLOY-1310**: Fixed an issue in Deploy where during package creation, the roles were not merged when deploying to the target system.

:white_check_mark: **OPCDEPLOY-1308**: Fixed the missing dependency links in Deploy in cross-schedule dependencies in the diagrams for packages and schedules.

:white_check_mark: **OPCDEPLOY-1307**: Fixed an error in Deploy for transformation of job instance properties when more than one rule exists in the transformation file.

:white_check_mark: **OPCDEPLOY-1304**: Corrected an error in Deploy during system properties transformation when environment tag is used. Environment tag value is suffixed to system properties instead of prefixed.

### 21.0

2021 October

:white_check_mark: **OPCDEPLOY-1300**: Fixed an issue in Deploy where the API contract for OpCon API was different and Deploy did not account for it, resulting in an error when calling the OpCon API.

:white_check_mark: **OPCDEPLOY-1298**: Changed Batch Deploy job action from CANCEL to SKIP to honor job dependencies when a batch deploy job is cancelled.

:white_check_mark: **OPCDEPLOY-1295**: Fixed an issue in Deploy where adding an environment prefix to a resource name extended its length past the maximum allowed and Deploy kept creating new resources on the target instead of signaling an error.

## 20

### 20.7

2021 September

:white_check_mark: **OPCDEPLOY-1292**: Fixed an issue in Deploy where an import of a transformation rule whose name already exists threw an "already exists" error instead of creating a new version for the rule.

:white_check_mark: **OPCDEPLOY-1290**: Fixed an issue in Deploy where a missing previous package (deleted after deployment, with a new one of the same name created) threw an NPE when deploying the new package — it should simply ignore the missing old package and save the new one as the actively deployed package.

:white_check_mark: **OPCDEPLOY-1263**: Return error message during deployment or simulation start-up when a package does not contain at least one schedule definition.

### 20.6

2021 August

:white_check_mark: **OPCDEPLOY-1288**: Fixed an issue in Deploy where only the latest version of a referenced embedded script was being included with a package deployment.

:white_check_mark: **OPCDEPLOY-1283**: Fixed Deploy installation path in documentation.

:white_check_mark: **OPCDEPLOY-1279**: Fixed an issue in Deploy where the environment tag for transformation rules was not applied to global properties appearing in schedule named instance exceptions. Fixed an issue in Deploy where properties with the environment tag applied did not import if the transformation rule was using partial update.

:white_check_mark: **OPCDEPLOY-1275**: Deploy now allows a non-admin user who has a required privilege to associate a schedule to another package after removing it from one. This is done by preventing filtering of schedules associated with a package version in the display area of the UI, if the user's new permission is set.

:white_check_mark: **OPCDEPLOY-1272**: Fixed an issue in saving transformation rules where job name is unsupported for certain tag IDs.

:white_check_mark: **OPCDEPLOY-1151**: Fixed an issue with archiving Deploy entities where a "string data truncation" or "foreign key reference constraint violation" error was thrown.

### 20.5

2021 June

:white_check_mark: **OPCDEPLOY-1273**: Fixed an issue where objects like departments that had a transformation applied were not properly deployed to the target. The target had both the pre- and post-transformed objects created in it.

:white_check_mark: **OPCDEPLOY-1250**: Fixed an issue in Deploy where an old null definition in the deployment record would cause null pointer exceptions on actions like rollback.

:white_check_mark: **OPCDEPLOY-1246**: Fixed an issue in batch Deploy where concurrent executions sometimes resulted in SQL deadlocks.

### 20.4

2021 May

:white_check_mark: **OPCDEPLOY-1223**: Fixed issues with diagram generation where the output was not generated if the schedule or job names had invalid or blank characters in them.

### 20.3

2021 April

:white_check_mark: **OPCDEPLOY-1257**: Fixed an issue that allows Deploy to correctly prefix a schedule name with the correct environment code in event strings.

:white_check_mark: **OPCDEPLOY-1253**: Fixed an issue where the Deploy UI could not handle different resolution scales on some screens such as Build Options.
