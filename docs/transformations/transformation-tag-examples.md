# Transformation Tag Examples

* This first figure is an example of transformation definitions used as default transformation rules to remap machine names when deploying schedules to an OpCon system.

![Sample Machine_Name Transformation Image](../static/img/sample-machine-name-transformation.png)

* This second figure shows how job name matching can be used. In the first rule, the rule will only be applied if the job name is equal to WJOB001 and in the second rule, the rule will be applied to all job names starting with the value JOB01.

![Sample Transformation using Job Name Matching](../static/img/sample-transformation-job-name.png)

* This third figure shows how schedule instance properties can be transformed. In the first part, the schedule instance property value STORAGE of schedule SCHEDULE001 is transformed from STORAGE to SYR-DEV-STORAGE. In the second part, the name of the schedule instance property CLIENT will be transformed to CLIENTB and the contents of schedule instance property 55 of schedule SCHEDULE001 is transformed from 55 to 155.

![Sample Transformation Schedule Instance Properties](../static/img/sample-transformation-schedule-instance.png)

* This fourth figure shows how job instance properties can be transformed. In the first part, the job instance property name PROP1 of job WJOB001 is transformed from PROP1 to TEST1. In the second part, the contents of job instance property PROP2 of job WJOB055 is transformed from TEST to PROD.

![Sample Transformation Job Instance Properties](../static/img/sample-transformation-job-instance.png)

