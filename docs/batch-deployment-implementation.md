# Batch Deployment Implementation

Batch Deployment is used to deploy a schedule or package at a future date and time. It requires an OpCon system that is used to schedule the deployment at the requested date and time.

The Batch Deploy consists of selecting the schedule or package for deployment, the target OpCon server, and, if required, transformation rules. Once this selection is complete, the Batch Deploy button can be selected, which will then request the date and time of the deployment. The user must also enter their OpCon Deploy password.

![Batch Deployment Process Overview](/img/batch-deployment-process-overview.png)

OpCon Deploy then injects either a ```DEPLOY_SCHEDULE``` or ```DEPLOY_PACKAGE``` task into the ```BATCH_DEPLOY``` schedule using the OpCon RestAPI. If the task is injected correctly into the ```BATCH_DEPLOY``` schedule, a successful completion message is displayed to the user and a record is inserted into the Deployment table, indicating that the schedule or package has been scheduled for future deployment.

![Deployment Record Showing Scheduled Deployment](/img/deployment-record-showing-deployment.png)

The following message will be displayed if OpCon Deploy is unable to schedule the task for future deployment:

![Deployment Scheduling Error Message](/img/deployment-scheduling-error.png)

The following items are required when implementing the Batch Deploy capability:

* An OpCon system must be identified to schedule the deployment tasks.
* Solution Manager must be installed on the identified OpCon system.
* OpCon RestAPI must be installed on the identified OpCon system using TLS with an internal certificate.
* The Schedule definition ```BATCH_DEPLOY``` must be installed on the system. The schedule is available in the templates (```BATCH_DEPLOY.json```) directory of the client software. The machine name, directory, and the user code that the tasks run under need to be transformed to match the target environment.
* The ```BATCH_DEPLOY``` schedule must be available in the daily so the tasks can be added to the schedule (set auto build values as required).
* The OpCon Deploy Client software must be installed on a Windows system that has an associated Windows LSAM (the installation directory must be transformed to match the environment).
* The jobs ```DEPLOY_SCHEDULE``` and ```DEPLOY_PACKAGE``` definitions should be adjusted to match the Windows system and directories where the OpCon Deploy Client has been installed.
* The BatchScheduleServer definition must be updated for the environment.
* The config.ini file must be updated to point to the OpCon Deploy database.

The database contains a BatchScheduleServer definition that must be modified to point to the OpCon system that will be used to perform the batch scheduling. 

The Server Address field defines the connection to the OpCon RestAPI using TLS (you will be required to enter a port number in the Server Port field – enter 9011). 

The definition requires OpCon API Port number (9010) and Using TLS must be selected.

![Sample BatchScheduleServer Definition](/img/sample-batchscheduleserver-definition.png)