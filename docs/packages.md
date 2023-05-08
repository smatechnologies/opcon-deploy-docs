# Packages

A package consists of a group of schedule definitions that can be deployed as a single unit to an OpCon system. Once a schedule definition is included in a package, it cannot be deployed as a single entity to the production system. A schedule can only belong to a single package per OpCon system.

When deploying a package, a check is made to determine if the schedule definition in the package matches the definition already deployed in the target OpCon system. If there is a match, only the schedule deployment information is updated to reflect the new package version.

The Packages functions support the capabilities required to manage package definitions.

## Manage

The Manage function allows packages to be managed in the OpCon Deploy system. It is possible to Add or Update (Save) package information.

![Package Management Dialog Image](/img/package-management-dialog.png)

### Select Package Section

When working with the View or edit Packages dialog, the information of an existing package can be displayed by selecting the package from the Name drop-down list. Once the package name has been selected, a list of versions of the package will appear in the Version drop-down list. If the package is deployed to production, the version that is deployed to production will be indicated on the drop-down list. When a version has been selected, the information is displayed in the View/edit package section of the dialog.

When a package is selected, the Create Diagram, the Create Header Diagram and the Update Schedule Versions buttons are activated, making it possible to create a diagram from the package definition or update the schedule version of all schedules associated with the package to the latest version in the Deploy database. When a diagram has been selected, it is displayed in PDF format.

The Create Diagram button creates a complete diagram of the schedules, including: jobs, resources, and dependencies. The Create Header Diagram button creates a diagram which displays the schedule header with container jobs only. If job dependencies exist between the jobs on the schedules, these dependencies will be displayed. Please refer to the topic Package and Schedule Diagram for more information.

If changes are made to the package information, then the Save and Cancel buttons will be enabled.

Updating the Schedule Versions of a package

Clicking the Update Schedule Versions button will bring up the Update Schedule Versions confirmation message:

![Update Package Schedule Versions Confirmation Message](/img/update-package-schedule-versions-confirmation.png)

Confirming the message will update the version of schedules associated with the package to the latest version of the schedule in the Deploy database. If the schedule version is the already the latest version, no changes are made.

A completion message is displayed in the upper message bar.

If changes have been made, the Save and Cancel buttons will be enabled. To save the changes and create a new package version, click on the Save button.

Deleting a Package

Clicking the Delete button to delete a package will bring up the Delete Package confirmation message:

![Delete Package Confirmation Message Image](/img/delete-package-confirmation.png)

Return to the View or Edit Packages screen by selecting Cancel.

If a user wants to continue with deleting a package and the package selected has versions in production, a secondary confirmation message will prompt the user to cross-reference with active packages and schedules:

![Delete Package 2nd Confirmation Message](/img/delete-package-second-confirmation.png)

Clicking "Yes" displays the list of schedules used in active packages for cross-referencing:

![Cross-Reference for Package](/img/cross-reference-for-package.png)

 The user can close this menu to return to the previous confirmation window.

From the 2nd Confirmation Message window, select Force Delete to complete deleting the package. Clicking Cancel Delete returns the user to the View or Edit Packages window.

Once a package is deleted, the package entry in the Deployment Browser will no longer allow users to select "Rollback this deployment" or "Delete this deployment". These options will now be grayed out:

![Deployment Browser](/img/deployment-browser.png)

However, Batch deployments in progress may still be canceled in this window. If they are not canceled, the Batch Deploy job will fail when the Deploy CLI cannot find the package.

### Renaming a Package

There are some circumstances in which users may need to rename packages. For example, changes to naming conventions would require package names to be updated. Packages may be renamed on the View or edit Packages dialog. On this screen, select a package from the Name drop-down field. The name and description of the package will be displayed, including Default transformation rules and Schedules that have been selected.

Rename the package by updating the Package name field and clicking Save.

:::info Note

If a package is renamed, all package versions will be renamed as well. Also, renaming a package does not create a new version unless there are other updates that have been made to the package.

:::
 

## View/Edit Package Section

This table contains descriptions of each field in the View/edit package section of the View or edit Packages dialog

### View/Edit Package Section Field Descriptions

| Field | Description |
| ----- | ----------- |
| Package name | The name of the package - This must be a unique name within the System
| Description | An optional description of the package |
| Default transformation rules | It is possible to define a set of transformation rules that will always be applied when the Package is selected during deployment |
| Schedules | Select the schedules that form part of this package - A schedule can only belong to a single package |

When adding default transformation rules to the server, select the Edit button and the Select one or more rules dialog will appear.

To add a transformation rule, either double-click or select the rule in the upper table and then select the include arrow. To remove a transformation rule, either double-click or select the rule in the lower table and the select the remove arrow.

![Package Default Transformation Rule Selection Dialog](/img/package-default-transformation-rule.png)

To view the transformation rule definitions, perform a right-click on the definition in the list (upper or lower tables) and View Definition will appear. Then, select this to view the JSON definition.

If transformation rules exist for a package deployment, but the server settings don't allow for transformation rules, a warning message stating "The selected server does not allow transformation rules: this deployment will fail" will appear.

![Package Deployment Transformation Rules not allowed](/img/package-deployment-fail.png)

The package transformation rules will appear, but will not be selectable and the deployment cannot be completed. You may choose to go back to the previous screen, simulate a deployment, or cancel the current deployment. The Batch OpCon Deploy and OpCon Deploy buttons will be disabled.

It is possible to search for a value in the JSON by entering the required value in the search field above the definition and selecting a search direction (forward or backward arrow). Selecting the X will remove the search result from the definition and the search field.

![Viewing Transformation Rule Definitions from Package Dialog](/img/view-transformation-rule-package-definition.png)

When adding default schedules to the package, select the Edit button and the Select one or more Schedules dialog will appear.

To add a schedule, either double-click or select the schedule in the upper table and then select the include arrow. To remove a schedule, either double-click or select the schedule in the lower table and the select the remove arrow.

![Package Schedule Selection Dialog](/img/package-schedule-selection.png)

To view the Schedule definitions, perform a right-click on the definition in the list (upper or lower tables) and View Definition will appear. Then, select this to view the JSON definition.

It is possible to search for a value in the JSON by entering the required value in the search field above the definition and selecting a search direction (forward or backward arrow). Selecting the X will remove the search result from the definition and the search field.

![Viewing Schedule Definitions from Package Dialog](/img/view-schedule-package-definition.png)




