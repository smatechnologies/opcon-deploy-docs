# Batch Diagram Processing

OpCon Deploy includes the capability to create a diagram of either a package or a schedule.

Diagrams of schedules and packages are produced using a command-line interface (CLI). The CLI only creates the diagrams that exist in the configured diagrams directory and displays the full name of the created PDF file.

Diagram.SMAOpConDeployClient supports the following arguments in the CLI:

**-ho**

* Optional argument that indicates if the package diagram should only consist of headers. Default value is complete diagram.

**-p**	

* Required argument that consists of the password of the user that is defined in the -u argument 
    * The password must be encrypted using the encryption tool provided by Enterprise Manager

**-pkg**	

* Optional argument that consists of the name of a package that the diagram must be created for
    * Either a package (-pkg) or a schedule (-sch) argument must be present

**-sch**

* Optional argument that consists of the name of a schedule that the diagram must be created for
q* Either a package (-pkg) or a schedule (-sch) argument must be present

**-u**	

* Required argument that defines the user that will perform the action 
* It must be a registered user in the repository 
* During the DEPLOY or SIMULATE actions, a check is made to determine if the user has the appropriate role to access the server defined in the -s argument

**-v**	

* Required argument that defines the version of the schedule or package to create the diagram

## Examples

```
C:\test\deploy\Diagram.SMAOpConDeployClient.exe -sch "SCH001" -u admin -v 11 -p lBsC5ohnSf2P7/Ku81FiGw==
```
 
```
C:\test\deploy\Diagram.SMAOpConDeployClient.exe -pkg "PKG001" -u admin -v 15 -p lBsC5ohnSf2P7/Ku81FiGw==
```
 
```
C:\test\deploy\Diagram.SMAOpConDeployClient.exe -pkg "PKG001" -u admin -v 15 -ho -p lBsC5ohnSf2P7/Ku81FiGw==
```
 

The above examples show how the Diagram.SMAOpConDeployClient program can be used to create diagrams:

* In the first example, a diagram of schedule .SCH001 version 11 is created
* In the second example, a complete diagram of package .PKG001 version 15 is created
* In the third example, a headers only diagram of package .PKG001 version 15 is created