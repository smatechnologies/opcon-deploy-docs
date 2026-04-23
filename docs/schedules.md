---
title: Schedules
description: "Import schedule definitions from OpCon systems or files into the OpCon Deploy central repository, and browse stored versions for deployment."
tags:
  - Procedural
  - Automation Engineer
  - Schedules
---

# Schedules

**Theme:** Build  
**Who Is It For?** Automation Engineer

## What is it?

The Schedules functions support the capabilities required to import and view schedule definitions. Before a schedule definition can be deployed to a target OpCon system, it must be registered with OpCon Deploy.

* Register a new schedule with OpCon Deploy for the first time before it can be deployed
* Capture updated versions when a schedule definition has been modified
* Every import creates a new version — if the definition matches the latest version already in the repository, the import is stopped to prevent duplicates
* Browse and review previously imported versions of any schedule definition

## Import

The import function is used to register a schedule definition with the OpCon Deploy system. During the import process, the schedule definition is selected from a source OpCon system, the schedule definition is extracted from the source OpCon system, converted into an JSON representation, and saved in the central repository.

A check is made during the import process to determine if the definition to be imported matches the latest version in the OpCon Deploy database. If there is a match, the import is terminated and an error message indicating the new definition matches an existing version is displayed.

The import process is divided into two distinct phases with the first phase being the selection phase and the second phase the confirmation phase.

OpCon Deploy requires that each OpCon system participating in the OpCon Deploy environment requires a license. To enforce this, a check is made to determine if the requested system has a valid OpCon Deploy license. If the system does not have a valid license, the following message will be displayed:

![Schedule Import Invalid License Image](../static/img/schedule-import-invalid-license.png)

## Import selection phase

:::note "Prerequisites"
The OpCon system to import from must be defined as a server in OpCon Deploy and must have a valid OpCon Deploy license. See [Servers](administration/servers).
:::

The import process begins with the selection of the OpCon system to import the schedule from. Following that, various dialogs will be presented leading you through the process.

To start the Import, select the Schedules Import function. The Schedule Import (Select a server) dialog appears and you will need to select, from the list, the OpCon system from which to import the schedule and then select the Next button. Only OpCon systems defined in the SMAOpconDeploy database will appear in the list.

![Schedule Import Source Image](../static/img/schedule-import-source-system.png)

Once Next has been selected, the list of schedules will be retrieved from the chosen OpCon system and displayed in the schedules list of the Schedule Import (Select a Schedule to import) dialog. Once the schedule list has been created, you can filter the schedule names on the list by entering a value in the Filter by Schedule Name field. You can select multiple schedules to import from the source OpCon system by selecting the schedule names and then using the **>** button to move the schedule names to the right-hand list. Once schedule(s) has been selected, select the Next or Finish button.

![Schedule Import Schedule Selection Image](../static/img/schedule-import-schedule-selection.png)

Once Next has been selected, the selected schedule(s) will be displayed in the Schedule Import (Summary) dialog appears. This provides a summary of your selections, allows selection of import options and allows a description to be added to the import process.
Supported Import Options:
- **Refresh SAP Job Definitions** indicates if OpCon SAP R3 jobs are encountered in the schedule, then the SAP server job definitions should be extracted from the SAP server (otherwise, uses values in 13100 and 13101 records).
- **Include Sub-Schedules** indicates if container jobs are encountered in the schedule, the associated sub-schedule should be included in the import process. The schedules are checked recursively and each sub-schedule is imported as a separate schedule. The result of all schedule imports is displayed in the results message.
- **Create Package from Schedules** indicates if a Deploy package should be created from the list of schedules. If selected, a package will be created using the **Package Name** field. If the package exists, a package update will be performed creating a new version of the package with the new schedule definition or the current schedule definition if the schedule version is already defined in the Deploy database.

![Schedule Import Summary Image](../static/img/schedule-import-summary.png)

If the schedule(s) has been inserted successfully into the repository, you will get a success message indicating that the schedule has been inserted as version (*n*) for each selected schedule. During the schedule import process a check is made to see if the schedule definition matches the current version in the Deploy database. If this is the case, a warning message will be displayed indicating that the schedule already exists in the database a version (*n*);

![Schedule Import Success Image](../static/img/schedule-import-success-message.png)

## Import file

The Import File function is used to register a schedule definition (contents must be in .JSON format) with the OpCon Deploy system from a file. During the process, the file is selected using the Browse... function. When the file is read in, a check is automatically performed to see if the format is valid.

![Import Schedule Definition from File](../static/img/import-schedule-definition-file.png)

When the file is read in, the information contained in the descriptionList will be displayed in the Description section.

To insert the definition in the repository, select the OK button. A message will be displayed asking confirmation that the schedule must be imported into the repository. If YES is selected, the schedule will be imported into the repository and a completion message will be displayed indicating that the schedule was inserted as version (*n*).

## Browse

The Browse function provides the opportunity to display information about schedule definitions in the repository.

The Browse and filter Schedules imported dialog presents a screen and a **Select** capability that allows you to enter a text string to retrieve specific schedule records or use the displayed default value of asterisk (*) to retrieve all schedule records.
Once the text string has been entered select the **Refresh** button and the schedule information will be displayed. Subsequent requests will result in the new selection being displayed. 

Wildcards are not supported. The text entered in the **Filter** field is checked against the schedule name in the record — for example, entering `GV` returns all schedule records with that character sequence in the name.

![Browse Schedule Definition](../static/img/browse-schedule-definition.png)

Browse and filter Schedules imported dialog presents a list of selected schedule records.

![Browse Schedule Definition](../static/img/browse-schedule-definition1.png)

 This next table describes the information displayed in the dialog.

To update the schedule list in the Browse and filter Schedules imported window, Select the **Refresh** button.

### Browse and filter schedules imported columns

| Column | Description |
| ------ | ----------- |
| Name | The name of the schedule |
| Sub | If the schedule definition contains references to a subschedule |
| Dep. | If the schedule definition contains external dependencies |
| Description | The description entered when importing the definition |
| OpCon Server | The OpCon server that the schedule was imported from |
| OpCon Version | The version of the OpCon system the definition was created on |
| Current Production | If the definition is currently deployed to a production system (will display which version of the schedule is deployed) |
| User | The name of the user that performed the last action on the schedule definition |
| Date | A timestamp when the last action was performed |

The high-level entry in the table will indicate which version is deployed to production and when the versions of the entry are examined, a check mark will indicate which version is deployed to production.

To view the schedule definitions, right-click the definition in the list and select **View Definition** to view the JSON definition.

To search for a value in the JSON, enter the required value in the search field above the definition and select a search direction using the forward or backward buttons. Selecting the X will remove the search result from the definition and the search field.

![View of Schedule Definition Saved in Central Repository](../static/img/view-schedule-definition-repository.png)

## Create diagram

To create a diagram of the Schedule definition, right-click the definition in the list and select **Create Diagram** to create the diagram. The diagram will then be displayed in a PDF form. For more information, see [Package and schedule diagram](package-and-schedule-diagram).

## Exception handling

| Error or symptom | Meaning | How to fix it |
|---|---|---|
| Invalid license message displayed | The source OpCon system does not have a valid OpCon Deploy license | Verify that the OpCon Deploy license is installed and active on the source OpCon system |
| "New definition matches an existing version" error | The schedule definition being imported is identical to the latest version already in the repository | No action needed — the definition is already current. Make changes to the schedule before reimporting. |

## Key terms

**Schedule definition** — the JSON representation of a schedule, including all job definitions, frequencies, and dependencies, stored in the central repository.

**Import** — the process of extracting a schedule definition from a source OpCon system and storing it as a new version in the central repository.

**Version** — a numbered snapshot of a schedule definition. A new version is created each time the schedule is successfully imported.

## FAQs

**What happens if I try to import a schedule that hasn't changed since the last import?**

The import is stopped and an error message is displayed indicating that the new definition matches an existing version. No duplicate version is created in the repository. You do not need to take any action — the existing version is already current. Make changes to the schedule in OpCon before attempting to reimport.

**Are sub-schedules automatically included when I import a schedule that contains container jobs?**

Not by default. On the Schedule Import (Summary) dialog, you must select the **Include Sub-Schedules** option. When selected, any sub-schedule referenced by a container job is included in the import process. Sub-schedules are checked recursively, and each one is imported as a separate schedule. The results of all imports are displayed in the completion message.

**How can I find a version of a schedule that was imported previously?**

Use the Browse function. Enter all or part of the schedule name in the Filter field and select Refresh to display matching schedule records. Expand the entry to see all versions. The Current Production column indicates which version is currently deployed to a production system. You can right-click any version and select View Definition to inspect the stored JSON.

**Related topics:**

- [Packages](packages)
- [Deployments](deployments/deployments)
- [Transformation rules](transformations/transformation-rules)
