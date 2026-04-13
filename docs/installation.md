---
title: Installation
description: "Install and configure the OpCon Deploy client, database, and server components on Windows systems that participate in the OpCon Deploy environment."
tags:
  - Procedural
  - System Administrator
  - Installation
---

# Installation

**Theme:** Configure  
**Who Is It For?** System Administrator

## What is it?

OpCon Deploy is installed across three components: the client software, the database, and the server software. Each participates in the OpCon Deploy environment with a distinct role.

* Install when setting up OpCon Deploy for the first time across multiple OpCon systems
* Install the client on any Windows machine where deployments need to be performed
* Install the server component on each OpCon system that participates in the deployment environment
* Install the database once on a SQL Server instance shared across all participating systems
* Upgrade any component independently when a new version is released

## Requirements

* Operating System: Support for Windows Server 2012, 2012 R2, 2016, and 2019
* Java: Embedded OpenJDK 11
* Microsoft SQL Server version 2012 SP3 or higher
* OpCon Server version 18.3 minimum
* OpCon RestAPI must be active for each OpCon system participating in OpCon Deploy
* To use the Diagram feature, the open source software Graphviz (version 2.38), is required. This can be downloaded from [www.graphviz.org](http://www.graphviz.org)
* To implement Windows Authentication for the OpCon Deploy Client requires manual configuration after the installation is complete
* To implement Windows Authentication for the OpCon Impex Server requires OpCon versions 21.0.10, 20.0.15 or greater and manual configuration after the installation is complete
* Version 22.2 requires matching SMA OpCon ImpEx2 versions (OpCon 22.1 or greater, OpCon 22.0.2 or greater, OpCon 21.0.14 or greater and OpCon 20.0.20 or greater)

## Deploy installation

The OpCon Deploy installation process consists of three basic steps: the installation of the client software, the installation of the database, and the installation of the server software.

The client software may be installed as many times as required on any Windows system. 

The database should only be installed once on a SQL Server environment. It can be installed on an existing SQL Server implementation used by OpCon or on a separate installation. There are no dependencies between an SMA OpCon database and an SMA OpCon Deploy database.

The server software must be installed on each OpCon system that participates in the OpCon Deploy environment. Each participating OpCon system must have a valid OpCon Deploy license and the OpCon RestAPI must be active on each system as OpCon Deploy uses the OpCon RestAPI to perform the license check.

One OpCon server in the OpCon Deploy environment should be designated the BatchScheduleServer which will be used to schedule Batch Deployments, archive jobs, and database backups. This server does not require an OpCon Deploy license, but must have the OpCon RestAPI active so requests can be passed for processing. The client software should be installed on the server and the SMADeployPath global property should be set to the installation directory.

A single software installer provides the installation for the three options:
* The installation of the client software
* The installation of the database
* The installation of the server software

## Deploy new or upgrade installation

To install or upgrade all OpCon Deploy components, complete the following steps:

1. Log in to the Windows machine as a local Administrator.
2.  Download the files from the [https://smatechnologies.files.com/](https://smatechnologies.files.com/) site.
3. In the **Username** field, enter your username.
4. In the **Password** field, enter your password.
5. Select the **Login** button.
6. Go to the ```/OpCon Releases/Deploy``` folder.
7. Download the software.
8. Select the **SMA OpCon Deploy.exe** installer to open it. The Select Language screen appears.
9. In the **Language** list, select the desired installation language.
10. Select **OK**. The Welcome screen is displayed.
11. Select the **Next** button.
12. Select one of the following options:
   - To change the default installation directory: Select the **Change** button, enter a new directory, and select the **Next** button.
   - To use the default installation directory: Select the **Next** button.
   The Custom Setup screen is displayed.
13. By default, all items will be installed.
14. Select the **Next** button.
15. Enter the OpCon Deploy database connection information for the client:
   * OpCon Deploy database server name (If a MS SQL instance is being used, enter ```<servername>\<instancename>)```
   * SQL Server login ID
   * SQL Server login ID password
   * Database name (default: SMAOpConDeploy)
16. Select the **Next** button.
17. Enter the definitions for the ImpEx2 Server:
   * OpCon database server name (If a MS SQL instance is being used, enter ```<servername>\<instancename>)```
   * OpCon database name
   * OpCon database login ID
   * OpCon database login ID password
   * The port number to be used for the ImpEx2 server (default 9001 for non-TLS, 9011 for TLS)
   * Select if the connection uses TLS
18. Select the **Next** button.
19. Select the **Done** button.

## Deploy client new installation

To install the OpCon Deploy client, complete the following steps:

1. Log in to the Windows machine as a local Administrator.
2. Download the files from the [https://smatechnologies.files.com/](https://smatechnologies.files.com/) site.
3. In the **Username** field, enter your username.
4. In the **Password** field, enter your password.
5. Select the **Login** button.
6. Go to the ```/OpCon Releases/Deploy``` folder.
7. Download the software.
8. Select the **SMA OpCon Deploy.exe** installer to open it. The Select Language screen appears.
9. In the **Language** list, select the desired installation language.
10. Select **OK**. The Welcome screen is displayed.
11. Select the **Next** button.
12. Select one of the following options:
   - To change the default installation directory: Select the **Change** button, enter a new directory, and select the **Next** button.
   - To use the default installation directory: Select the **Next** button.
   The Custom Setup screen is displayed.
13. By default, all items will be installed. For this installation, only the SMA OpCon Deploy Client should be installed. Follow these steps to deselect the other items from the list so that they are not installed:
   * Select the button to the left of the SMA OpCon Deploy Database item
   * Select the X (This feature will not be available.) option from the list
   * Select the button to the left of the SMA OpCon Deploy Server item
   * Select the X (This feature will not be available.) option from the list
14. Select the **Next** button.
15. Enter the OpCon database connection information for the client:
   * OpCon Deploy database server name (If a MS SQL instance is being used, enter ```<servername>\<instancename>```)
   * SQL Server login ID
   * SQL Server login ID password
   * Database name (default: SMAOpConDeploy)
16. Select the **Next** button.
17. Select the **Done** button.

## Deploy database new installation

To install the OpCon Deploy database, complete the following steps:

1. Log in to the Windows machine as a local Administrator.
2. Download the files from the [https://smatechnologies.files.com/](https://smatechnologies.files.com/) site.
3. In the **Username** field, enter your username.
4. In the **Password** field, enter your password.
5. Select the **Login** button.
6. Go to the ```/OpCon Releases/Deploy``` folder.
7. Download the software.
8. Select the **SMA OpCon Deploy.exe** installer to open it. The Select Language screen appears.
9. In the **Language** list, select the desired installation language.
10. Select **OK**. The Welcome screen is displayed.
11. Select the **Next** button.
12. Select one of the following options:
   - To change the default installation directory: Select the **Change** button, enter a new directory, and select the **Next** button.
   - To use the default installation directory: Select the **Next** button.
   The Custom Setup screen is displayed.
13. By default, all items will be installed. For this installation, only the SMA OpCon Deploy Database should be installed. Follow these steps to deselect the other items from the list so that they are not installed:
   * Select the button to the left of the SMA OpCon Deploy Client item
   * Select the X (This feature will not be available.) option from the list
   * Select the button to the left of the SMA OpCon Deploy Server item
   * Select the X (This feature will not be available.) option from the list
14. Select the **Next** button.
15. Enter the OpCon Deploy database connection information for the client:
   * OpCon Deploy database server name (If a named MS SQL instance is being used, enter ```<servername>\<instancename>```)
   * In the "Connect using:" section of the screen, you may elect to use either Windows authentication or SQL Server authentication by selecting the corresponding option
   * If you select SQL Server authentication, then you must enter:
      * SQL Server login ID
      * SQL Server login ID password
   * Database name (default: SMAOpConDeploy)
16. Select the **Next** button.
17. Select the **Done** button.

## Deploy server new installation

To install the OpCon Deploy server, complete the following steps:

1. Log in to the Windows machine as a local Administrator.
2. Download the files from the [https://smatechnologies.files.com/](https://smatechnologies.files.com/) site.
3. In the **Username** field, enter your username.
4. In the **Password** field, enter your password.
5. Select the **Login** button.
6. Go to the ```/OpCon Releases/Deploy``` folder.
7. Download the software.
8. Select the **SMA OpCon Deploy.exe** installer to open it. The Select Language screen appears.
9. In the **Language** list, select the desired installation language.
10. Select **OK**. The Welcome screen is displayed.
11. Select the **Next** button.
12. Select one of the following options:
   - To change the default installation directory: Select the **Change** button, enter a new directory, and select the **Next** button.
   - To use the default installation directory: Select the **Next** button.
   The Custom Setup screen is displayed.
13. By default, all items will be installed. For this installation, only the SMA OpCon Deploy Server should be installed. Follow these steps to deselect the other items from the list so that they are not installed:
   * Select the button to the left of the SMA OpCon Deploy Client item
   * Select the X (This feature will not be available.) option from the list
   * Select the button to the left of the SMA OpCon Deploy Database item
   * Select the X (This feature will not be available.) option from the list
14. Select the **Next** button.
15. Enter the definitions for the ImpEx2 Server:
   * OpCon database server name (If a MS SQL instance is being used, enter ```<servername>\<instancename>```, if TLS for database connection, add ***;TrustServerCertificate=True*** name)
   * OpCon database name
   * OpCon database login ID
   * OpCon database login ID password
   * The port number to be used for the ImpEx2 server (default 9001 for non-TLS, 9011 for TLS)
   * Select if the connection uses TLS
16. Select the **Next** button.
17. Select the **Done** button.

## Deploy client configuration

The config.ini file contains the configuration statements that provide the connection to the OpCon Deploy database. After installation, the config.ini file can be found in the c:\ProgramData\OpConxps\Deploy\client directory.

Users may establish a connection to the OpCon Deploy database using Windows Authentication. The databaseUser should be left blank and the password of the Windows Domain user should be encrypted and placed in the config file (see databaseUser / databaseUserPassword).

Users may establish a TLS connection to the OpCon Deploy database if required by adding ***;ssl=require*** to the database URL (see databaseURL).

### debug

Set to true or false. Should only be set to true at SMA Technologies' request.

### ebeanServerName

The name of the Ebean Server.
   * For MS SQL: ```mssql```

### databaseDriver

The database driver software class name.
   * For MS SQL: ```net.sourceforge.jtds.jdbc.Driver```

### databaseURL

The database URL. If a specific database instance is to be used for MS SQL, the instance name is appended after the database name.
   * For MS SQL: ```jdbc:jtds:sqlserver: //<server>/SMAOpConDeploy jdbc:jtds:sqlserver://<server>/SMAOpConDeploy;instance=INST001```

The database URL. If TLS is required append the **;ssl=require** to the URL.
   * For MS SQL: ```jdbc:jtds:sqlserver: //<server>/SMAOpConDeploy jdbc:jtds:sqlserver://<server>/SMAOpConDeploy;ssl=require```

### databaseUser

The name of the database user who has the required privileges to all tables in the OpCon Deploy database.
For Windows Authentication, the field should be left blank.

### databaseUserPassword

The password of the database user, encrypted using the Enterprise Manager encryption tool.
For Windows Authentication, the field should contain the encrypted password of the Windows User.

### minConnections

Use the default value of 1.

### maxConnections

Use the default value of 25.

### graphvizDirectory

Used with diagram feature and defines the location of the GraphViz dot exe program.

### diagramDirectory

Used with diagram feature and defines the location of the created .dot and .pdf files.

### devOpsOrganization

Used with DevOps integration and consists of the Organization name.

### devOpsToken

Used with DevOps integration and consists of the PAT (Personal Access Token) of the user that is allowed to access the data in the DevOps repository.

## Sample Deploy client configuration file

```

# SMA OpCon Deploy Configuration File

#

###########################

#  General Settings Area  #

###########################


debug=false

ebeanServerName=mssql

databaseDriver=net.sourceforge.jtds.jdbc.Driver

databaseUrl=jdbc:jtds:sqlserver://VM-REPOS-SQL/SMAOpconDeploy

# example for connecting to a specific instance
# databaseUrl=jdbc:jtds:sqlserver://VM-REPOS-SQL/SMAOpConDeploy;instance=INST001       

# example for connection using SSL
# databaseUrl=jdbc:jtds:sqlserver://VM-REPOS-SQL/SMAOpConDeploy;ssl=require

# example for connecting to a specific instance using SSL
# databaseUrl=jdbc:jtds:sqlserver://VM-REPOS-SQL/SMAOpConDeploy;instance=INST001;ssl=require

databaseUser=ormadmin

databaseUserPassword=sYnk3bzpZybGPbSOrhsr4g==

minConnections=1

maxConnections=25

graphvizDirectory=F:\\GraphViz_238\\bin\\dot.exe

diagramDirectory=C:\\test\\relmgmt\\diagrams

devOpsOrganization=SMATechnologies

devOpsToken=xxxxxxxxxxxxxxxxxxxxxxxx

```

## Sample Deploy client configuration file using Windows Authentication

```

# SMA OpCon Deploy Configuration File

#

###########################

#  General Settings Area  #

###########################


debug=false

ebeanServerName=mssql

databaseDriver=net.sourceforge.jtds.jdbc.Driver

databaseUrl=jdbc:jtds:sqlserver://VM-REPOS-SQL/SMAOpconDeploy

# example for connecting to a specific instance
# databaseUrl=jdbc:jtds:sqlserver://VM-REPOS-SQL/SMAOpConDeploy;instance=INST001

# example for connection using SSL
# databaseUrl=jdbc:jtds:sqlserver://VM-REPOS-SQL/SMAOpConDeploy;ssl=require

# example for connecting to a specific instance using SSL
# databaseUrl=jdbc:jtds:sqlserver://VM-REPOS-SQL/SMAOpConDeploy;instance=INST001;ssl=require

databaseUser=

databaseUserPassword=sYnk3bzpZybGPbSOrhsr4g==

minConnections=1

maxConnections=25

graphvizDirectory=F:\\GraphViz_238\\bin\\dot.exe

diagramDirectory=C:\\test\\relmgmt\\diagrams

devOpsOrganization=SMATechnologies

devOpsToken=xxxxxxxxxxxxxxxxxxxxxxxx

```

## OpCon Deploy server configuration

The config.ini file contains the configuration statements that provide the connection to the local OpCon system. After installation, the config.ini file can be found in the ```c:\ProgramData\OpConxps\Deploy\Server``` directory.

### Configuring Windows Authentication

When using Windows Authentication, **the SMA OpCon Impex2 RestAPI** service must run using a Windows Domain user.

To configure Windows Authentication, complete the following steps:

1. Stop the **SMA OpCon Impex2 RestAPI** service.
2. Set the `opcon.db.using.winauth` property to `true`.
3. Change the service to run under a specific account (**Properties** > **Log On**, not **Local System Account**).
4. Ensure the chosen account is registered with SQL Server.
5. Restart the **SMA OpCon Impex2 RestAPI** service.

The db user and password entered during installation are not used for Windows Authentication, but they should not be removed from the config.ini file.

### Deploy server configuration statement descriptions

| Tag Name | Description |
| -------- | ----------- |
| opcon.server.name | The name of the OpCon server to which the OpCon Deploy RESTFul Server will connect |
| opcon.db.name | The name of the OpCon database to which the OpCon Deploy RESTFul Server will connect (e.g., OPCONXPS)|
| opcon.db.user | The name of a valid user who has privileges on the database named in the opcon.db.name definition (e.g., opconsam) |
| opcon.db.password | The password of the user named in the opcon.db.user definition |
| opcon.db.using.winauth | Indicates if the connection to the OpCon Database should use Windows Authentication (values true or false) |
| opcon.db.connection.max | The maximum number of simultaneous database connections allowed to the OpCon database |
| web.port | The port number used by the OpCon Deploy RESTFul server (default 9001) |
| system.debug | Set to true or false - Should only be set to true at SMA Technologies' request |

### Sample Deploy server configuration file

```
#
# OpCon server connection information
#
opcon.server.name=EC2AMAZ-2QV0RKO
opcon.db.name=OPCONXPS
opcon.db.user=opconsam
opcon.db.password=sYnk3bzpZybGPbSOrhsr4g==
opcon.db.using.winauth=false
opcon.db.connection.max=10
#
# REST server configuration
#
web.port=9001
#
# Logger configuration
#
system.debug=false

```

### Sample Deploy server configuration file using Windows Authentication

```
#
# OpCon server connection information
#
opcon.server.name=EC2AMAZ-2QV0RKO
opcon.db.name=OPCONXPS
opcon.db.user=opconsam
opcon.db.password=sYnk3bzpZybGPbSOrhsr4g==
opcon.db.using.winauth=true
opcon.db.connection.max=10
#
# REST server configuration
#
web.port=9001
#
# Logger configuration
#
system.debug=false

```
### Sample Deploy server configuration file using TLS SQL Server connection

```
#
# OpCon server connection information
#
opcon.server.name=EC2AMAZ-2QV0RKO
opcon.db.name=OPCONXPS;TrustServerCertificate=True
opcon.db.user=opconsam
opcon.db.password=sYnk3bzpZybGPbSOrhsr4g==
opcon.db.using.winauth=true
opcon.db.connection.max=10
#
# REST server configuration
#
web.port=9001
#
# Logger configuration
#
system.debug=false

```
## Deploy database backup scripts

When implementing a production environment, it is necessary to take regular backups of the OpCon Deploy database.

The scripts in ```<program data>/SMAOpConDeploy\Utilities\Database``` directory can be used to implement database and transaction log backups.

A schedule (DEPLOY_UTILITIES.json) containing the job definitions for the backup process is available in the templates directory of the client software. The machine name, directory, frequency, and user code that the jobs run under need to be transformed to match the target environment. The global property SMADeployDataPath should be set to the client program data directory so the programs can be run.

## Key terms

**OpCon Deploy Client** — the Windows application used to perform deployments, imports, and administration tasks.

**OpCon Deploy Database** — the central SQL Server database that stores all schedule definitions, transformation rules, deployment records, and configuration.

**OpCon Deploy Server (ImpEx2)** — the service installed on each participating OpCon system that provides the API used to import and deploy schedule definitions.

**BatchScheduleServer** — a designated OpCon system used to schedule batch deployments, archive jobs, and perform database backups.

**config.ini** — the configuration file used by the OpCon Deploy Client to establish a connection to the OpCon Deploy database.

## FAQs

**Can the OpCon Deploy client software be installed on more than one machine?**

Yes. The client software may be installed as many times as required on any Windows system. Each client installation connects to the same central OpCon Deploy database, so all clients share the same repository of schedule definitions, transformation rules, and deployment records.

**What is the BatchScheduleServer and does it need an OpCon Deploy license?**

The BatchScheduleServer is a designated OpCon system used to schedule batch deployments, archive jobs, and perform database backups. Unlike other participating OpCon systems, it does not require an OpCon Deploy license. However, the OpCon RestAPI must be active on it so that requests can be passed for processing, and the OpCon Deploy client software should be installed on it.

**What is the SMADeployPath global property used for?**

The `SMADeployPath` global property should be set to the installation directory on the BatchScheduleServer. This allows the batch deployment jobs and utility scripts — such as the database backup schedule (DEPLOY_UTILITIES.json) provided in the templates directory — to locate the programs they need to run. A related property, `SMADeployDataPath`, should be set to the client program data directory for the backup scripts.

**Related topics:**

- [Getting started](getting-started)
- [Servers](administration/servers)
- [Users](administration/users)
