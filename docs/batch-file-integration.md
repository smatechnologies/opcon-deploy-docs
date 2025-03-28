# Batch File Integration

File integration provides the following capabilities.

* Export a specific schedule from an OpCon System to a file.
* Export a specific script version from an OpCon System to a file.
* Export a specific schedule version from the Deploy database to a file.
* Export a specific script version from the Deploy database to a file.
* Import a schedule definition into the Deploy database from a file.
* Import a new version of an existing script into the Deploy database from a file.
 
File Integration is performed using a command-line interface (CLI). 

File.SMAOpConDeployClient supports the following arguments in the CLI:

**-a**

* Required argument that indicates the action to be performed.
    * IMPORT   import a schedule (new or new version) or a new script version into the Deploy database from a file 
    * EXPORT   export a specific schedule version or a specific script version from the Deploy database into a file
    * OEXPORT  export a schedule or a specific script version from and OpCon system (defined in Deploy Server configuration) into a file 

**-di**	

* Required argument that indicates the directory where the extracted information will be placed for EXPORT & OEXPORT actions and where the information can be read for IMPORT actions. 

**-o**	

* Optional argument used for OEXPORT action and defines the OpCon system that the object must be extracted from. The value is the name of a server definition in the Deploy database. 

**-p**	

* Required argument that consists of the password of the user that is defined in the -u argument 
    * The password must be encrypted using the encryption tool provided by Enterprise Manager

**-t**	

* Required argument that indicates the object type associated with the action 
    * SCHEDULE
    * SCRIPT
	
**-tn**	

* Required argument that indicates the name of the schedule or script associated with the action. 
    * schedule EXPORT/OEXPORT   contains the name of the schedule to export. The value is used to create the filename along with a .json extension 
    * script EXPORT/OEXPORT     contains the name of the script to export. The value is used to create the filename
    * schedule IMPORT           contains the name of the schedule to import. The value is used to create the filename along with a .json extension
    * script IMPORT             contains the name of the script to import. The value is used to create the filename

**-u**	

* Required argument that defines the user that will perform the action 
* It must be a registered user in the repository 
* During the DEPLOY or SIMULATE actions, a check is made to determine if the user has the appropriate role to access the server defined in the -s argument

**-v**	

* Optional argument that defines the version of the schedule or script to export.
    * EXPORT action    defines the version of the schedule or script to extract from the Deploy datatabase 
    * OEXPORT action   defines the version of the script to extract from the OpCon system


## Examples

```
C:\test\deploy\File.SMAOpConDeployClient.exe -a "EXPORT" -t "SCHEDULE" -tn "SCH001" -v 5 -di "c:\test\data" -u admin -p lBsC5ohnSf2P7/Ku81FiGw==
```
 
```
C:\test\deploy\File.SMAOpConDeployClient.exe -a "OEXPORT" -t "SCHEDULE" -tn "SCH001" -o "OPCONDEV" -di "c:\test\data" -u admin -p lBsC5ohnSf2P7/Ku81FiGw==
```
 
```
C:\test\deploy\File.SMAOpConDeployClient.exe -a "EXPORT" -t "SCRIPT" -tn "scripta" -v 5 -di "c:\test\data" -u admin -p lBsC5ohnSf2P7/Ku81FiGw==
```
 
```
C:\test\deploy\File.SMAOpConDeployClient.exe -a "OEXPORT" -t "SCRIPT" -tn "scripta" -v 5 -o "OPCONDEV" -di "c:\test\data" -u admin -p lBsC5ohnSf2P7/Ku81FiGw==
``` 

```
C:\test\deploy\File.SMAOpConDeployClient.exe -a "IMPORT" -t "SCHEDULE" -tn "SCHD001" -di "c:\test\data" -u admin -p lBsC5ohnSf2P7/Ku81FiGw==
``` 

```
C:\test\deploy\File.SMAOpConDeployClient.exe -a "IMPORT" -t "SCRIPT" -tn "scripta" -di "c:\test\data" -u admin -p lBsC5ohnSf2P7/Ku81FiGw==
``` 

The above examples show how the File.SMAOpConDeployClient program can be used to export / import definitions:

* In the first example, version 5 of schedule SCH001 is extracted from the Deploy database and written into a file c:\test\data\SCH001.json
* In the second example, schedule SCH001 is extracted from OpCon system OPCONDEV written into a file c:\test\data\SCH001.json
* In the third example, version 5 of script scripta is extracted from the Deploy database and written into a file c:\test\data\scripta
* In the fourth example, version 5 of script scripta is extracted from OpCon system OPCONDEV written into a file c:\test\data\scripta
* In the fifth example, the definition contained in file c:\test\data\SCH001.json is imported into the Deploy database. If schedule SCH001 exists, a new version is created.
* In the sixth example, the definition contained in file c:\test\data\scripta is imported into the Deploy database creating a version of the script.
