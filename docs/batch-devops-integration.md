# DevOps Integration

The Devops.SMAOpConDeployClient.exe provides integration possibilities with the DevOps environment.

The concept is to create schedules and scripts within an OpCon system, export these created definitions (schedule and script version) and store them in a DevOps repository. 
These definitions can them be deployed to OpCon systems through Release Pipelines, or directory from a branch in a repository using Deploy.

![DevOps Extraction Process](../img/devops-extraction-process.png)

The extraction part of the integration is to export the required definitions from the development OpCon system and store them in a branch of a local DevOps repository. During this process, the schedule definition is first saved as a new version in the Deploy repository. The script version is also saved as a new script version if the script is defined in the Deploy repository. If the script itself is not definied in the Deploy repsoitory, the script is inserted into the Deploy repositoty and the script versions stored.
The definitions are extracted as files which can then be included in a local DevOps repository branch which is subsequently 'pushed' up to the main repository and then via a 'pull-request' merged into the production branch.

Deploy performs the extraction process 'exporting' the schedule and script definitions from the source OpCon system. During this process the extracted information is stored in the Deploy repository creating new versions of the schedule and script. If the schedule does not exist, a new schedule definition is created. If the script does not exist a new script definition is created. Otherwise a new version of the schedule or script is created.

The schedule information is then written out into a file and the name of  the file consists of the schedule name and a .json extension. The script version is written out into a file and the name of the file consists of the script name.

These files can then be included in a new branch of a local repository, committed and pushed up to the main DevOps repository where a 'pull-request' can be created to merge the new definition into the production branch.

![DevOps Deploy Process](../img/devops-deploy-process.png)

The deployment process uses Deploy to 'push' the definitiosn to the target system. During this process, the definitions are stored in the Deploy repository as new versions of existing schedules and scripts before they are sent to the target system. If a release tag is provided, the tag will be included in the description fields of the Deploy records as well as the deployment information of the schedule and the description of the script version. This means that it will be possible to see which DevOps release version is active on the OpCon system.

The schedule and script definitions are generated as artifacts during the release build process and can then be deployed to the required target OpCon system within a release pipeline. The release pipeline includes a trigger mechanism which consists of submitting a JOB ADD request to an OpCon system. The JOB ADD request is passed to the OpCon system through the OpCOn REST-API passing parameters as instance properties. The Job ADD request executes the Devops.SMAOpConDeployClient.exe program using the arguments, which defines the target OpCon system, the filename, an object type (SCHEDULE or SCRIPT) and optionally a release tag.

It is also possible to push a schedule or a script definition from a repository branch to a target OpCon system. The Devops.SMAOpConDeployClient.exe program uses the DevOps REST-API to access the repository information (through the DevopsService), retrieves the schedule or script blob item, creates a temporary file and then completes the deployment process.

It should be noted that when deploying a script version, the script information must exist in the Deploy repository.

DevOps integration provides the following capabilities.

* Export a specific schedule from an OpCon System to a file, which can then be saved in the DevOps repository.
* Export a specific script version from an OpCon System to a file, which can then be saved in the DevOps repository.
* Deploy an artifact (schedule or script) provided as a file during a release pipeline process.
* Deploy a schedule definition from a specific DevOps repository / branch.
* Deploy a script definition from a specific DevOps repository / branch.
 
DevOps Integration is performed using a command-line interface (CLI). 

Devops.SMAOpConDeployClient supports the following arguments:

**-a**

* Required argument that indicates the action to be performed.
    * DEPLOY   deploy artifact (schedule or script) to a target OpCon system. 
    * EXPORT   export a specific schedule version or a specific script version from a source OpCon system into files. 
    * REPO     deploy a definition (schedule or script) from a repository branch to a target OpCon system. 

**-b**

* Optional argument required for REPO action. Defines the DevOps branch where the definition must be retrieved from.

**-d**
    
* Optional argument that contains a value that will be added to the comment fields within Deploy.

**-di**	

* Optional argument required for EXPORT action. Indicates the directory where the extracted information will be placed. 

**-e**
   
* Optional argument for DEPLOY action. It defines a environment transformation rule, which can be used to create a unique instance of the schedule in the target system.

**-f**	

* Optional argument required for DEPLOY action. Indicates the filename of the artifact to be deployed. 

**-ip**	

* Optional argument required for REPO action. Defines the path of the item to retrieve within the branch.

**-o**	

* Required argument that defines the OpCon system that the object must be extracted from or deployed to. The value is the name of a server definition in the Deploy database. 

**-p**	

* Required argument that consists of the password of the user that is defined in the -u argument 
    * The password must be encrypted using the encryption tool provided by Enterprise Manager

**-t**	

* Required argument that indicates the object type associated with the action 
    * SCHEDULE
    * SCRIPT
	
**-tn**	

* Required argument that indicates the name of the schedule or script associated with the action. 
    * schedule EXPORT      contains the name of the schedule to export. The value is used to create the filename along with a .json extension 
    * script EXPORT        contains the name of the script to export. The value is used to create the filename
    * schedule DEPLOY/REPO contains the name of the schedule to deploy. For REPO is the full name of the item in the branch.
    * script DEPLOY/REPO   contains the name of the script to deploy. For REPO is the full name of the item in the branch.

**-u**	

* Required argument that defines the user that will perform the action 
* It must be a registered user in the repository 
* During the DEPLOY or SIMULATE actions, a check is made to determine if the user has the appropriate role to access the server defined in the -s argument

**-v**	

* Optional argument that defines the version of the schedule or script to export.
   
    * EXPORT action    defines the version of the script to extract from the OpCon system


## Examples

```
C:\test\deploy\Devops.SMAOpConDeployClient.exe -a "EXPORT" -t "SCHEDULE" -tn "SCH001" -di "c:\test\data" -u admin -p lBsC5ohnSf2P7/Ku81FiGw== -o "OPCONDEV"
```
In the above example, schedule SCH001 is extracted from OpCon system OPCONDEV, inserted into the Deploy repository and written into a file c:\test\data\SCH001.json. For schedule definitions, the .json extension is added to the schedule name.

```
C:\test\deploy\Devops.SMAOpConDeployClient.exe -a "EXPORT" -t "SCRIPT" -tn "scripta" -v 5 -o "OPCONDEV" -di "c:\test\data" -u admin -p lBsC5ohnSf2P7/Ku81FiGw==
``` 
In the above example, version 5 of script scripta is extracted from OpCon system OPCONDEV, inserted into the Deploy repository (if script record not found, a script record is created) and written into a file c:\test\data\scripta. Before creating the 

```
C:\test\deploy\Devops.SMAOpConDeployClient.exe -a "DEPLOY" -t "SCHEDULE" -tn "SCH001" -o "OPCONTST" -f "c:\test\data\SCHED001.json" -u admin -p lBsC5ohnSf2P7/Ku81FiGw== -d "REL 22.0.1"
```
In the above example, the schedule definition in the file c:\test\data\SCHED001.json is deployed to the OpCon System OPCONTST. Before deploying the schedule to the opCon system, OPCONTST,
the schedule definition is first saved in the deploy repository and the description "REL 22.0.1" is inserted as a comment. When deploying the schedule definition, the comment "REL 22.0.1" is
attached to the Deployment record as well as the Deployment Information of the schedule.

```
C:\test\deploy\Devops.SMAOpConDeployClient.exe -a "DEPLOY" -t "SCRIPT" -tn "scripta" -o "OPCONTST" -f "c:\test\data\scripta" -u admin -p lBsC5ohnSf2P7/Ku81FiGw== -d "REL 22.0.1"
```
In the above example, the script definition in the file c:\test\data\scripta is deployed to the OpCon System OPCONTST as a new version of script scripta. This means that a script definition for scripta must exist in the Deploy environment.
Before deploying the script version to the opCon system, OPCONTST, the script version is first saved in the deploy repository and the description "REL 22.0.1" is inserted as a comment.  

```
C:\test\deploy\Devops.SMAOpConDeployClient.exe -a "REPO" -t "SCHEDULE" -tn "SCHD001.json" -pj "TSG" -r "SCHEDULE_DEF" -b "develop" -ip "src/schedules" -u admin -p lBsC5ohnSf2P7/Ku81FiGw== -d "DEVTEST 1.0" -o OPCONTST
``` 
In the above example, the schedule definition in the /src/schedules location of the develop branch of the SCHEDULE_DEF repository is deployed to the OpCon System OPCONTST. Before deploying the schedule to the opCon system, OPCONTST,
the schedule definition is first saved in the deploy repository and the description "DEVTEST 1.0" is inserted as a comment. When deploying the schedule definition, the comment "DEVTEST 1.0" is attached to the Deployment record as well as the Deployment Information of the schedule. This function requires additional configuration information in the config.ini file. 

```
C:\test\deploy\Devops.SMAOpConDeployClient.exe -a "REPO" -t "SCRIPT" - tn "scripta" -pj "TSG" -r "SCHEDULE_DEF" -b "develop" -ip "src/scripts" -u admin -p lBsC5ohnSf2P7/Ku81FiGw== -d "DEVTEST 1.0" -o OPCONTST
``` 
In the above example, the script definition in the /src/scripts location of the develop branch of the SCHEDULE_DEF repository is deployed to the OpCon System OPCONTST as new script version for scripta. Before deploying the script version to the opCon system, OPCONTST, the definition is first saved in the deploy repository as a new script version for the script scripta. The description "DEVTEST 1.0" is inserted as a comment. This function requires additional configuration information in the config.ini file. 
