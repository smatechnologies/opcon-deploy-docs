---
sidebar_label: 'Release notes'
---

# OpCon Deploy Release Notes

## Version 22.5

2023 September

:eight_spoked_asterisk: **OPCDEPLOY-1353**: Fixed a performance issue with large databases when browsing records (schedules, transformation rules, scripts, deployments, and packages). 
Previously, all records were retrieved from the database and then added to the selection lists when performing a request. Now, the user is required to enter a text string in the filter field and the filter text is used to retrieve only matched records from the database. User can still input an asterisk (*) as the filter text to fetch all records. 
The filter does not support wild cards. For example, enter 'test' as the filter text to get records whose name includes 'test',

## Version 22.4

2023 August

:eight_spoked_asterisk: **OPCDEPLOY-1354**: Fixed an issue where certain updates to the OpCon API in newer versions (like 22.7.0) resulted in an error in Deploy because it found unrecognized fields being returned by the API, instead of simply ignoring them.

:eight_spoked_asterisk: **OPCDEPLOY-1355**: Fixed an issue where sub-schedule names containing spaces prevented diagram from being created as diagram node name containing spaces was not supported.
 
## Version 22.3

2023 April

:eight_spoked_asterisk: **OPCDEPLOY-1341**: Added new 'Include sub-schedules' option in Checkin Summary Page that will recursively add sub-schedules found during a schedule import to the import process. The import result
of each schedule is displayed in the results view. The message reporting that the schedule version already exists, has been changed to a WARNING message and the color changed to dark yellow. 

:eight_spoked_asterisk: **OPCDEPLOY-1343**: Added 'Update Schedule Versions' button to Package Dialog. When selected, the schedules associated with the package will be updated to the latest version of the schedule in the Deploy database. 

## Version 22.2

2023 March

:eight_spoked_asterisk: **OPCDEPLOY-1338**: Separated reset AutoBuild days and AutoDelete days into two separate rules. Therefore it is now possible to reset either AutoBuild days or AutoDelete days.
it should be noted that this implementation requires matched SMA OpCon ImpEx2 versions (OpCon 22.1 or greater, OpCon 22.0.2 or greater, opCon 21.0.14 or greater and OpCon or greater 20.0.20). 

## Version 22.1

2022 December

:eight_spoked_asterisk: **OPCDEPLOY-1331**: Corrected an error that enabled Job Name Field for Role Name transformation rule.

:eight_spoked_asterisk: **OPCDEPLOY-1332**: Corrected an error when more than one job name field is defined in a set of transformation rules. 

:eight_spoked_asterisk: **OPCDEPLOY-1335**: Changed logging moving large logging entries to DEBUG and corrected log setup to ensure DEBUG is turned off by default.

:eight_spoked_asterisk: **OPCDEPLOY-1336**: Corrected package simulation error when only first schedule in package is compared instead of all schedules in the package.

:eight_spoked_asterisk: **OPCDEPLOY-1339**: Add OpConMFT job-type compatibility check for OpCon version 22.0.

## Version 22.0

2022 December

:eight_spoked_asterisk: **OPCDEPLOY-1319**: Deploy now provides a new batch process File.SMAOpConDeployClient which provides support for extraction of schedules and scripts from either an OpCon system or the Deploy repository. It also supports inserting schedule definitions or script versions from files into the Deploy repository.

:eight_spoked_asterisk: **OPCDEPLOY-1321**: Added backend integration with DevOps to enable retrieval of schedules or script versions from a branch within the repository. 

:eight_spoked_asterisk: **OPCDEPLOY-1320**: Deploy now provides a new batch process Devops.SMAOpConDeployClient which provides support for extraction of schedules and scripts from an OpCon system. It also supports deploying a schedule or script version from files or from a DevOps repository. When Deploying a schedule or script, the definition is first stored in the Deploy repository and then 'deployed' to the target system using the standard Deploy mechanism.

:eight_spoked_asterisk: **OPCDEPLOY-1322**: Added script name change transformation rule. During environment transformation, prefix now added to script to create a unique instance of the script for the defined environment. 

## Version 21.2

2022 September

:white_check_mark: **OPCDEPLOY-1324**: Created updated EM-Core-API library for ImpE2x.

:white_check_mark: **OPCDEPLOY-1317**: Department and Access code are not deployed when we deploy a package.

:white_check_mark: **OPCDEPLOY-1323**: Concurrent deployments create Deadlock on deployment table, resulting in deployment of schedule succeeding, but information in Deploy database
not updated.

:white_check_mark: **OPCDEPLOY-1325**: Script versions not imported correctly when performing a file Import.

:white_check_mark: **OPCDEPLOY-1326**: during transformation, environment Tag not applied to Event Trigger Job Completion Complex Expression for TH name.

:white_check_mark: **OPCDEPLOY-1325**: Fixed issues with the Import file function when schedule definition file contains embedded script jobs.

:white_check_mark: **OPCDEPLOY-1317**: Corrected merging of Department and Access Code information during package creation.

:white_check_mark: **OPCDEPLOY-1323**: Optimized transaction demarcation during the deploy process. The initial deployment record is created outside the transaction and a new deployment status 'Failed' will be displayed if the deployment fails. If the deployment is restarted and completes successfully, the initial deployment record will be used.

:white_check_mark: **OPCDEPLOY-1326**: Added environment transformation to TH, RM and RU properties when used within Dependency expressions and event complex expressions.

## Version 21.1

2022 February

:white_check_mark: **OPCDEPLOY-1315**: Added more informational logging when working with SAP jobs.
:white_check_mark: **OPCDEPLOY-1309**: Added Auto Build Reset capabilities during Deployment of schedules and packages. When setting the auto build options, first select the Auto Build checkbox and then set the values for Days In Advance and Days. When selecting the Auto Build checkbox, the values are initially set to 1. When not selected, the values are set to 0. To reset the Auto Build and Auto Delete values, select the Auto Build checkbox and set the Days in Advance and Days values to 0. This will remove the the Auto Build and Auto Delete values.

:eight_spoked_asterisk: **OPCDEPLOY1311**: Deploy now allows role names to be part of the transformation, to map them to the names on the target system. Role_Add: This tag is used to add a Role during deployment. The Role name will be added in Role, schedules, scripts and departments. The new Role name must be defined in the target system. This tag supports the following: newValue: Required: Contains the name of the Role to add. All other fields are disabled.

:eight_spoked_asterisk: **OPCDEPLOY-1303**: Deploy now allows role names to be part of the transformation, to map them to the names on the target system. Role_Name: This tag is used to change the name of a Role that is associated with the deployment. The Role name will be updated in Role, schedules, scripts and departments. The new Role name must be defined in the target system. This tag supports the following tag: currentValue (required): Contains the name of the Role to change in the definitions. newValue (required): The value to be inserted in the definition if the currentValue matches the value in the definition. partialUpdate: Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

:white_check_mark: **OPCDEPLOY-1310**: Fixed an issue in Deploy where during package creation, the roles were not merged when deploying to the target system.

:white_check_mark: **OPCDEPLOY-1308**: Fixed the missing dependency links in Deploy in cross schedule dependencies in the diagrams for packages and schedules.

:white_check_mark: **OPCDEPLOY-1307**: Fixed an error in Deploy for transformation of job instance properties when more than 1 rule exists in the transformation file.

:white_check_mark: **OPCDEPLOY-1304**: Corrected an error in Deploy during system properties transformation when environment tag is used. Environment tag value is suffixed to system properties instead of preffixed.

## Version 21.0

2021 October

:white_check_mark: **OPCDEPLOY-1300**: Fixed an issue in Deploy where the API contract for OpCon API was different and Deploy did not account for it resulting in an error when calling the OpCon API.

:white_check_mark: **OPCDEPLOY-1298**: Changed Batch Deploy job action from CANCEL to SKIP to honor job dependencies when a Batch deploy job is cancelled.

:white_check_mark: **OPCDEPLOY-1295**: Fixed an issue in Deploy where adding an environment prefix to a resource name extended its length path the maximum allowed and Deploy kept creating new resources on the target instead of signaling an error.

## Version 20.7

2021 September

:white_check_mark: **OPCDEPLOY-1292**: Fixed an issue in Deploy where an import of a transformation rule whose name exists, threw an "already exists" error, instead of creating a new version for the rule.

:white_check_mark: **OPCDEPLOY-1290**: Fixed an issue in Deploy where a missing previous package (since it was deleted after deployment and a new one with the same name, created) threw an NPE when deploying the new package, when it should simply ignore the missing old package and save the new one as the actively deployed package.

:white_check_mark: **OPCDEPLOY-1263**: Return error message during deployment or simulation start up when a package does not contain at least 1 schedule definition

## Version 20.6

2021 August

:white_check_mark: **OPCDEPLOY-1288**: Fixed an issue in Deploy where only the latest version of a referenced embedded script was being included with a package deployment.

:white_check_mark: **OPCDEPLOY-1283**: Fixed Deploy Installation path in Documentation

:white_check_mark: **OPCDEPLOY-1279**: Fixed an issue in Deploy where the environment tag for transformation rules was not applied to global properties appearing in schedule named instance exceptions. Fixed an issue in Deploy where properties with the environment tag applied did not import if the transformation rule was using partial update.

:white_check_mark: **OPCDEPLOY-1275**: Deploy now allows a non-admin user who has a (new) required privilege, to associate a schedule to another package after removing it from one. This is done by preventing filtering of schedules associated with a package version in the display area of the UI, if the user's new permission is set.

:white_check_mark: **OPCDEPLOY-1272**: Fixed an issue in saving transformation rules where job name is unsupported for certain tag ids.

:white_check_mark: **OPCDEPLOY-1151**: Fixed an issue with archiving Deploy entities where a "string data truncation" or "foreign key reference constraint violation" error was thrown.

## Version 20.5

2021 June

:white_check_mark: **OPCDEPLOY-1273**: Fixed an issue where objects like departments that had a transformation on them were not properly deployed to the target. The target had both the pre and post transformed objects created in it.

:white_check_mark: **OPCDEPLOY-1250**: Fixed an issue in Deploy where an old null definition in the deployment record would cause null pointer exceptions on actions like 'rollback'.

:white_check_mark: **OPCDEPLOY-1246**: Fixed an issue in batch Deploy where concurrent executions sometimes resulted in SQL deadlocks.

## Version 20.4

2021 May

:white_check_mark: **OPCDEPLOY-1223**: Fixed issues with diagram generation where the output was not generated if the schedule or job names had invalid/blank characters in them.

## Version 20.3

2021 April

:white_check_mark: **OPCDEPLOY-1257**: Fixed an issue that allows Deploy to correctly prefix a schedule name with the correct environment code in event strings.

:white_check_mark: **OPCDEPLOY-1253**: Fixed an issue where Deploy UI could not handle different resolution scales on some screens like Build Options

:white_check_mark: **OPCDEPLOY-1125**: Fixed an issue in Deploy client where if a user typed a regular expression character in a filter text box it threw a Pattern Syntax Exception.

:white_check_mark: **OPCDEPLOY-1111**: Fixed an issue where a new version of a schedule with modifications to schedule documentation could not be imported

:white_check_mark: **OPCDEPLOY-952**: Fixed an issue in Deploy where if an embedded script had two or more runners associated with it, then deployment of a schedule with a job referencing that script gave null pointer exceptions.

:white_check_mark: **OPCDEPLOY-507**: Fixed an issue in Deploy where importing a script with a missing version in OpCon (because it may have been deleted) caused an error in Deploy due to a missing server name field, which is required.

## Version 20.2

2021 February

:eight_spoked_asterisk: **OPCDEPLOY-1195**: ImpEx2 server component is no longer packaged with Deploy. It is packaged with OpCon as it is tied to an OpCon version and will be available as a separate installer.

:white_check_mark: **OPCDEPLOY-1242**: Fixed an issue that caused NPE exception, if an error occurs, or password was incorrect, for OpCon Rest API.

:white_check_mark: **OPCDEPLOY-1228**: Fixed an issue where Diagram.SMAOpConDeployClient.exe was not included in the install package.

:white_check_mark: **OPCDEPLOY-1134**: Improved error message content in Import Scripts and Import Schedules wizards when either the OpCon API or Impex API are unreachable.

## Version 20.1

2021 January

:white_check_mark: **OPCDEPLOY-1129**: Updated the Installation chapter of the product documentation to remove reference to PostgreSQL.

:white_check_mark: **OPCDEPLOY-1143**: Fixed a case sensitivity issue that occurs when comparing Windows user names with different cases in transformation rules for Windows job details.

:white_check_mark: **OPCDEPLOY-1134**: Improved error message content in Import Scripts and Import Schedules wizards when either the OpCon API or Impex API are unreachable.

:white_check_mark: **OPCDEPLOY-1128**: Improved the error message displayed when the Deploy user does not have sufficient permissions to update a schedule.

:white_check_mark: **OPCDEPLOY-1097**: Fixed an issue with an Out of Bounds exception being thrown when importing a script with a missing script runner.

:white_check_mark: **OPCDEPLOY-1090**: Fixed an issue with Null Pointer Exceptions in Transformation Rules.

:white_check_mark: **OPCDEPLOY-714**: Fixed an issue where the schedule in the target OpCon environment was not being checked for the sub-schedule indicator setting when a sub-schedule was included in a deployment simulation.

## Version 20.0

2020 November

:eight_spoked_asterisk: **OPCDEPLOY-1056**: Added the ability to generate diagrams of schedules and packages through a command line interface.

:eight_spoked_asterisk: **OPCDEPLOY-1004**: Added additional parameters to BatchDeploy.

:eight_spoked_asterisk: **OPCDEPLOY-1003**: Added two new buttons, "Create Diagram" and "Create Header Diagram" to the Package Dialog screen.

:eight_spoked_asterisk: **OPCDEPLOY-1002**: Added the ability to generate a diagram of a schedule definition.

:eight_spoked_asterisk: **OPCDEPLOY-1001**: Created a routine DiagramRunnable that receives the data from the DiagramOperation.

:eight_spoked_asterisk: **OPCDEPLOY-1000**: Created a routine Diagram Operation that receives the data from the DiagramAction and Package buttons.

:eight_spoked_asterisk:	**OPCDEPLOY-999**: Created a Diagram Service which generates the PDF file to be displayed by the DiagramOperation.

:eight_spoked_asterisk:	**OPCDEPLOY-998**: Added the values graphwizDirectory and diagramDirectory to the config.ini file.

:eight_spoked_asterisk:	**OPCDEPLOY-960**: Updated transformation rules to add a rule allowing schedule start times to be changed when deploying to different environments.

:eight_spoked_asterisk:	**OPCDEPLOY-958**: Updated transformation rules to add a rule allowing schedule build times to be changed when deploying to different environments.

:eight_spoked_asterisk:	**OPCDEPLOY-896**: Improved performance of Deployment Browse dialog.

:eight_spoked_asterisk:	**OPCDEPLOY-878**: Updated the OpCon Deploy Login dialog to display a clickable hyperlink to the "Terms of Use" for the product.

:eight_spoked_asterisk:	**OPCDEPLOY-859**: OpCon Deploy ImpEx server is now available as a Docker Image.

:eight_spoked_asterisk:	**OPCDEPLOY-857**: Updated to include the Impex2 Server component of OpCon Deploy in the Docker container for OpCon.

:eight_spoked_asterisk:	**OPCDEPLOY-767**: Added support for Windows Authentication to SQL Server for OpCon Deploy client program connections to the OpCon Deploy database.

:eight_spoked_asterisk:	**OPCDEPLOY-766**: Added support for Windows Authentication to SQL Server for database installations and upgrades.

:eight_spoked_asterisk:	**OPCDEPLOY-745**: Added the ability to delete a package.

:eight_spoked_asterisk:	**OPCDEPLOY-744**: Added the ability to rename a package.

:eight_spoked_asterisk:	**OPCDEPLOY-742**: Added the ability to rename a transformation rule.

:eight_spoked_asterisk:	**OPCDEPLOY-741**: Added the ability to grant read-only access to the audit logs for non-Admin Deploy users.

:eight_spoked_asterisk:	**OPCDEPLOY-739**: Added a check box to the User management screen to allow an administrator to choose whether a user should have access to the audit logs or not. The default setting is True (Checked).

:eight_spoked_asterisk:	**OPCDEPLOY-671**: Added support for Windows Server 2019 to OpCon Deploy.

:eight_spoked_asterisk:	**OPCDEPLOY-563**: Added a screen displaying the levels at which transformation rules are added and highlighting how transformation rules applied at a higher level supersede rules at a lower level.

:eight_spoked_asterisk:	**OPCDEPLOY-500**: Added the ability to generate a diagram of a schedule definition or of all schedule definitions within a package.

:white_check_mark: **OPCDEPLOY-1080**: Fixed an issue where a NullPointerException was encountered when checking deployDeployment table during Simulate/Deploy.

:white_check_mark: **OPCDEPLOY-1079**: Fixed an issue where the result from extractOpConPackage is not checked for a null value.

:white_check_mark: **OPCDEPLOY-1076**: Fixed an issue where an exception will be thrown if the IBMi Use Call Script Transformation rule is used on a job that the Use Call Script was optional and not provided.

:white_check_mark: **OPCDEPLOY-1075**: Fixed an issue where Impex could fail on Schedules that require a lot of machine feature checks.

:white_check_mark: **OPCDEPLOY-1070**: Fixed an issue where a new version of a schedule with modifications could not be imported.

:white_check_mark: **OPCDEPLOY-1026**: Corrected deployment name column to match transformed names.

:white_check_mark: **OPCDEPLOY-1023**: Fixed an issue with the transformation rules where schedule or job name contains wildcard *.

:white_check_mark: **OPCDEPLOY-963**: Fixed a Null Pointer Exception when deploying a package with a single schedule to a production server.

:white_check_mark: **OPCDEPLOY-957**: Fixed an issue with completed schedules being rebuilt when the "Rebuild Schedules in Daily" option is selected on a deployment.

:white_check_mark: **OPCDEPLOY-953**: Fixed several typographical errors in the DEPLOY_UTILITIES schedule.

:white_check_mark: **OPCDEPLOY-902**: If a deployment contains a feature that a requested machine does not have, the deployment will now be stopped. Impex will return an error message.

:white_check_mark: **OPCDEPLOY-880**: Fixed inconsistent values in the "Current Production" column of the Schedule Browse form.

:white_check_mark: **OPCDEPLOY-870**: Fixed an issue where a Violation of PRIMARY KEY Constraint occurs if the UNIX Job Sub-type is changed.

:white_check_mark: **OPCDEPLOY-856**: Fixed an issue where original_name column was not being populated during initial import.

:white_check_mark: **OPCDEPLOY-850**: Fixed an issue where the machine information was not set correctly when changing a job type from Null Job to UNIX.

:white_check_mark: **OPCDEPLOY-849**: Fixed an issue where an error was returned from Cayenne when trying to change a job type to Windows.

:white_check_mark: **OPCDEPLOY-837**: Clarified documentation relating to the archiving of schedules, packages and transformation rules.

:white_check_mark: **OPCDEPLOY-817**: Fixed Deploy user textbox FieldLengthValidation class issue. Existing user information can now be updated without re-entering password.

:white_check_mark: **OPCDEPLOY-799**: Fixed an issue for when deployment simulations are performed, a check will now be performed on the machines on the target OpCon system to verify that they have all the required features.

:white_check_mark: **OPCDEPLOY-786**: Fixed an issue where the value of the jobName on a zOSDataSet was null on export by ensuring a null value is exported as an empty string.

:white_check_mark: **OPCDEPLOY-756**: Fixed an issue where a schedule with a sub-schedule which contains another sub-sub-schedule displays the name of the sub-schedule in the simulation results.

:white_check_mark: **OPCDEPLOY-724**: Fixed an issue where when trying to do a partial update in TagID "Event", an error would occur only if the substring to be exchanged was in the middle of the entire string.

:white_check_mark: **OPCDEPLOY-723**: Fixed a bug in the "Create/Edit a transformation" screen where an error was raised when using the "Frequency: use existing definition" Tag ID because the Current Value and New Value fields were NULL and should have been set to an empty string.

:white_check_mark: **OPCDEPLOY-721**: Fixed an issue where sub-schedules could not be imported using the Import File option.

:white_check_mark: **OPCDEPLOY-718**: Fixed an issue where resource updates with a transformation rule caused an application crash.

:white_check_mark: **OPCDEPLOY-633**: Fixed StringIndexOutOfBoundsException when scheduling a batch deployment with transformation rules.

:white_check_mark: **OPCDEPLOY-609**: Fixed an issue with Deployment where jobs' Threshold/Resource dependencies did not get updated.

:white_check_mark: **OPCDEPLOY-608**: Deploy will not allow named instances containing the (*) character to be deployed.

:white_check_mark: **OPCDEPLOY-603**: Fixed an issue with deployment simulations failing with a null pointer exception.

:white_check_mark: **OPCDEPLOY-597**: Fixed an issue where the deployment process stopped if the user selected "Cancel" on the Deploy or Batch Deploy confirmation dialog.

:white_check_mark: **OPCDEPLOY-596**: Fixed a layout issue with the Deployment records window where long character strings in the "Filter deployment records" drop-down lists caused the Filter frame to expand too widely and the records table did not display fully or was hidden completely.

:white_check_mark: **OPCDEPLOY-593**: Added a Refresh button on following windows:
* Audit records
* Schedules
* Scripts
* Transformation Rules

:white_check_mark: **OPCDEPLOY-533**: Fixed a layout issue with the Audit Window when the OpCon Deploy user name contains many characters.

:white_check_mark: **OPCDEPLOY-524**: Fixed an issue with script imports where all versions were incorrectly marked as already imported even though only some versions may have been imported.

:white_check_mark: **OPCDEPLOY-509**: Fixed an issue where the auto build settings were erroneously applied to sub-schedules during schedule or package deployment.

:white_check_mark: **OPCDEPLOY-506**: Fixed unexpected error message when importing scripts of non-unique script versions.

:white_check_mark: **OPCDEPLOY-505**: Fixed an issue where environment variables used in a schedule were not transferred during an export/import.

:white_check_mark: **OPCDEPLOY-452**: Fixed an issue where the OpCon Deploy client process sometimes stays open after window closes.