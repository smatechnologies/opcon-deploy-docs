# Working with SAP Jobs

The OpCon environment supports the scheduling of SAP Jobs defined within the SAP environment.

The latest release includes the capabilities to extract the associated SAP job definition from the SAP system and then insert the definitions into the SAP system associated with the target OpCon system. To enable this capability, the Refresh SAP Job Definitions and Import SAP Job Definitions options must be selected during the Import or OpCon Deploy functions.

The SAP Job Definitions are saved in the OpCon JMASTER_AUX table using field codes 13100 for the Query details and field code 13101 for the Step details. There will be one field code 13101 record for each defined Step starting at sequence no 1 to the number of steps defined in the Query details information. This data is not visible from Enterprise Manager as the field codes do not exist in the OpCon implementation. The addition of these field codes associated with the OpCon SAP R3/CRM job has no impact on the job execution and are removed when the OpCon SAP job is deleted.

It should be understood that, while it is possible to import and OpCon Deploy SAP job definitions, it is not possible to import and deploy the ABAP program and, therefore, the program must be available on the target SAP system.

When importing an OpCon SAP job definition and Refresh SAP Job Definitions has been selected, the SAP job definition associated with the OpCon SAP job will be extracted from the SAP system, saved in the OpCon database using field codes 13100 and 13101, and included in the schedule definition. If the Refresh SAP Job Definitions option is not selected, field codes 13100 and 13101 will be checked for SAP job definitions and will be included in the schedule definition if found.

When deploying an OpCon SAP Job definition and Insert SAP Job Definitions has been selected, the SAP Job Definition associated with the OpCon SAP Job will be used to create a new job in the SAP system. Before creating the job, a check is made to see if the job already exists in the SAP system. If the job already exists, the SAP job definition is then linked with the OpCon SAP job definition. Otherwise, the SAP job is created and the new SAP job definition is linked with the OpCon SAP job definition. The SAP Job definitions will be saved in the target OpCon database using field codes 13100 and 13101.