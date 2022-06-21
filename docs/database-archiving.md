# Database Archiving

OpCon Deploy includes the capability to archive records no longer required in the deploy_package, deploy_schedule, deploy_deployment, and deploy_transformation_rule tables.

* Archiving is performed using a designated value that indicates how many versions should be maintained in the main tables. The value is set using the Settings function (Number of versions to retain). The default value is 5.
* Archiving is a complex process that checks the various tables to determine if the version is still active as an active version cannot be archived.
* During the archiving process, if a deployment record is associated with the schedule or package version that is being archived, the deployment record will also be archived.

A schedule (```DEPLOY_UTILITIES.json```) containing the task definitions for the archive process is available in the templates directory of the client software. The machine name, directory, frequency, and user code that the tasks run under need to be transformed to match the target environment. The global property SMADeployPath should be set to the client installation directory so the programs can be executed.

It is recommended that the tasks are scheduled on a weekly basis.

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

A list of transformation rule versions to be archived is then extracted from the database and a check is made to determine if the transformation version is part of a server, package or deployment definition, it cannot be removed. It should be noted that if the deployment, server or package records are removed the transformation rule will no longer be linked and be available for removal.

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