# Transformation Tag Definitions

This section provides information on the following tag definitions and associated tags that are supported for each definition:

### Container_Sub_Schedule_Name

This tag is used to change the name of the subschedule that the container job references and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs with which the rule is associated. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the name of the subschedule to change in the container job definition.

* newValue	

    * (*Required*): The value to insert in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### Department_Name

This tag is used to change the name of the department in the job definition. When used with the environment and no department definition is present, the department will be set to the value defined in the newValue tag, which should be set to the same name value as the environment tag. The Department_Name tag supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs with which the rule is associated. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the name of the department to change in the job definition.

* newValue	

    * (*Required*): The value to insert in the definition if the currentValue matches the value in the definition.

* partialUpdate

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### Event

This tag is used to change the name of schedule or a job in an event definition associated with a schedule or job and supports the following tags:

* ```<job_name>```

    * (*Optional*): When present, this indicates the job or group of jobs with which the rule is associated. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

 * ```<current_value>```	

    * (*Required*): Contains the event command to change in the job or schedule definition.

* ```<new_value>```	

    * (*Required*): The value to insert in the definition if the current_value matches the value in the definition.

* ```<partial_update>```

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### Event_Related_User

This tag is used to change the related OpCon user name that is associated with the event and supports the following tags:

* ```<current_value>```

    * (*Required*): Contains the name of the user to change in the event definition. A value of * will automatically replace the value with the value in the new_value field.

 * ```<new_value>```

    * (*Required*): The value to insert in the definition if the current_value matches the value in the definition.

* ```<partial_update>```

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### File_Transfer_Destination_Machine

This tag is used to change the name of the destination machine in the file transfer job definition and supports the following tags:

* jobName

    * (*Optional*): When present, this indicates the job or group of jobs with which the rule is associated. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the name of the destination host to change in the file transfer job definition.

* newValue	

    * (*Required*): The value to be inserted in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).


### File_Transfer_Source_Machine

This tag is used to change the name of the destination machine in the file transfer job definition and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs with which the rule is associated. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the name of the destination host to change in the file transfer job definition.

* newValue	

    * (*Required*): The value to be inserted in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### Frequency_Name

This tag is used to change the name of the frequency machine in the definition. The frequency name is changed in all objects, including frequencies, dependencies and events. This tag supports the following tags:

* currentValue	

    * (*Required*): Contains the name of the frequency to change in the definitions.

* newValue	

    * (*Required*): The value to be inserted in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### Frequency_Use_Existing_Definitions

This tag is a special tag that is used when you want the definition of the frequency on the target system to be used instead of the frequency in the definition. This is typically used when importing a schedule or task on production systems and the real frequency should be used instead of the test frequency.

 An example would be if there is a frequency definition on the target system LWDOM, which is the last working day of the month. During testing, the frequency definition for LWDOM will probably be an all days definition, as you do not want to wait until the last day of the month to perform tests.

The Frequency_Use_Existing_Definitions tag supports the following tags:

* currentValue	

    * (*Not Required*): Leave empty.

* newValue	

    * (*Not Required*): Leave empty.

* partialUpdate	

    * (*Not Required*): leave default partialUpdate false.

### IBMi_Call_Information

This tag is used to change a value in the Call field of the IBM i job definition and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs with which the rule is associated. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the name of the value in the Call field to change in the job definition.

* newValue	

    * (*Required*): The value to be inserted in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### IBMi_Job_Description

This tag is used to change the values in the Job Description field of the IBM i job definition. The job description field consists of two values: Name and Library. When changing the job description field, both values must be separated by a comma (e.g., name,library). This tag supports this following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs with which the rule is associated. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the name of the value in both the Name and Library fields, separated by a comma in the job definition (e.g., *USRPRF,*LIBL).

* newValue	

    * (*Required*): The value to be inserted in the definition if the currentValue matches the value in the definition (e.g., *USRPRF,*CURLIB).

* partialUpdate	

    * This function does not support partial update, so the value must be set to false.

### IBMi_Job_Queue

This tag is used to change the values in the Job Queue field of the IBM i job definition. The job queue field consists of two values: Name and Library. When changing the job queue field, both values must be separated by a comma (e.g., name,library). This tag supports this following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs with which the rule is associated. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the name of the value in both the Name and Library fields, separated by a comma in the job definition (e.g., *JOBD,*LIBL).

* newValue	

    * (*Required*): The value to be inserted in the definition if the currentValue matches the value in the definition (e.g., *JOBD,*CURLIB).

* partialUpdate	

    * This function does not support partial update, so the value must be set to false.

### IBMi_Job_Queue_Priority

This tag is used to change a value in the JobQ Priority field of the IBM i job definition and supports the following tags:

* jobName	

    * (*Optional*): When present indicates the job or group of jobs that the rule is associated with. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue

    * (*Required*): Contains the name of the value in the JobQ Priority field to change in the job definition.

* newValue	

    * (*Required*): The value to be inserted in the definition if the currentValue matches the value in the definition (e.g., *JOBD,*CURLIB).

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### IBMi_Library_Current

This tag is used to change a value in the Library Current field of the IBM i job definition and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs with which the rule is associated. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the name of the value in the Library Current field to change in the job definition.

* newValue	

    * (*Required*): The value to be inserted in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### IBMi_Library_Init_List

This tag is used to change a value in the Library Current field of the IBM i job definition and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs with which the rule is associated. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the name of the value in the Library Init Lib List field to change in the job definition.

* newValue	

    * (*Required*): The value to be inserted in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### IBMi_Message_Logging_Level

This tag is used to change a value in the Message Logging Level field of the IBM i job definition and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs with which the rule is associated. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the name of the value in the Message Logging Level field to change in the job definition.

* newValue	

    * (*Required*): The value to be inserted in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### IBMi_Message_Logging_Severity

This tag is used to change a value in the Message Logging Severity field of the IBM i job definition and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs with which the rule is associated. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the name of the value in the Message Logging Severity field to change in the job definition.

* newValue	

    * (*Required*): The value to be inserted in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### IBMi_Message_Logging_Text

This tag is used to change a value in the Message Logging Text field of the IBM i job definition and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs with which the rule is associated. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the name of the value in the Message Logging Text field to change in the job definition.

* newValue	

    * (*Required*): The value to be inserted in the definition if the currentValue matches the value in the definition.

 * partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### IBMi_Output_Queue

* This tag is used to change the values in the Output Queue field of the IBM i job definition. The output queue field consists of two values: Name and Library. When changing the output queue field, both values must be present separated by a comma (e.g., name,library). This tag supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs with which the rule is associated. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the name of the value in both the Name and Library fields separated by a comma in the job definition (e.g., *JOBD,*LIBL).

* newValue	

    * (*Required*): The value to insert in the definition if the currentValue matches the value in the definition (e.g., *DEV,*CURLIB).

* partialUpdate	

    * This function does not support partial update, so the value must be set to false.

### IBMi_User_ID

This tag is used to change a value in the User ID text field of the IBM i job definition and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs with which the rule is associated. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the name of the value in the User ID text field to change in the job definition.

* newValue	

    * (*Required*): The value to be inserted in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### Job_Instance_Property

This tag is used to change the job instance property name value of the job instance property definition as well as the contents of the property. The job instance property name is also changed in the Windows command line, Windows working directory, UNIX start image and UNIX fields. This tag supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs with which the rule is associated. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the value of the job instance property in the definition if the contents of the property should be changed.

* currentValueContents	
 
    * (*Optional*): Contains the value of the job instance property in the definition if the contents of the property should be changed.
 
* newValue	

    * (*Required*): The value to be inserted in the definition if the currentValue matches the value in the definition.

* newValueContents	

    * (*Optional*): The value to insert in the definition if the currentValueContents matches the value in the definition or if the newValue matches the currentValue.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### Job_Machine_Group_Name

This tag is used to change the machine group value of the job definition and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs with which the rule is associated. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

 * currentValue	

    * (*Required*): Contains the name of the value of the machine group in the job definition.

 * newValue	

    * (*Required*): The value to be inserted in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### Job_Machine_Group_Name_to_Machine_Name

This tag is used to change the machine group value of the job definition and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs with which the rule is associated. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

 * currentValue	

    * (*Required*): Contains the name of the value of the machine group in the job definition.

 * newValue	

    * (*Required*): The value to be inserted in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### Job_Machine_Name

This tag is used to change the Primary, Alternate Machine 1, Alternate Machine 2, Alternate Machine 3, File Transfer Source, and Destination Host values of the job definition. The Job_Machine_Name tag supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs with which the rule is associated. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the name of the machine in the job definition.

* newValue	

    * (*Required*): The value to be inserted in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### Job_Machine_Name_to_Machine_Group_Name

This tag is used to change the Primary Machine name to a Machine Group name. The Job_Machine_Name_to_Machine_Group_Name tag supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs with which the rule is associated. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the name of the machine in the job definition.

* newValue	

    * (*Required*): The value to be inserted in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### Job_Name

This tag is used to change the Job Name value of the job definition and is changed in events and dependencies. The Job_Name tag supports the following tags:

* currentValue	

    * (*Required*): Contains the name of the job in the job definition.

* newValue	

    * (*Required*): The value to be inserted in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### Job_Name_Mask

This tag is used to change the Job Name value of the job definition using a mask that supports wild card characters (? and *). When using the mask ? characters indicates which character in the name should not be changed, while the * characters indicates all following characters should not be changed. 
To change the first character of the name the currentValue should be T* and newValue should be P*. To change the first and last characters of the name, the currentValue should be T?????A and the newValue should be P????B. The Job_Name_Mask tag supports the following tags:

* currentValue	

    * (*Required*): Contains the value to check .

* newValue	

    * (*Required*): Contains the new value to be applied.

* partialUpdate	

    * Not used.

### Job_Tag

This tag is used to change the value of a tag on the job or insert a tag value on a job and supports following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs with which the rule is associated. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the name of the job tag in the definition or the name of a tag to add to the job.

* newValue	

    * (*Required*): The value to be inserted in the definition if the currentValue matches the value in the definition. When inserting a tag, the value must match the currentValue. The newValue will then be added to the job.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### MCP_Arguments

This tag is used to change the value of MCP arguments associated with the job and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs with which the rule is associated. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the value in the definition to change.

* newValue	

    * (*Required*): The value to replace in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### MCP_File_Title

This tag is used to change the value of an MCP file title associated with the job and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs with which the rule is associated. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the value in the definition to change.

* newValue	

    * (*Required*): The value to replace in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### MCP_Prerun_Arguments

This tag is used to change the value of MCP prerun arguments associated with the job and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs with which the rule is associated. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the value in the definition to change.

* newValue	

    * (*Required*): The value to replace in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### MCP_Prerun_File_Title

This tag is used to change the value of MCP prerun file title associated with the job and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs with which the rule is associated. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the value in the definition to change.

* newValue	

    * (*Required*): The value to replace in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### MCP_User_Code

This tag is used to change the value of an MCP user associated with the job and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs with which the rule is associated. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the value in the definition to change.

* newValue	

    * (*Required*): The value to replace in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### Move_Schedule_Package

This definition is used by customers that are doing software migration projects, and has been implemented to assist with moving schedules through the migration cycle from unit test to production (see Special Definitions section for more information).

### OS2200_Account

This tag is used to change the value of an OS2200 account associated with the job and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs with which the rule is associated. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the value in the definition to change.

* newValue	

    * (*Required*): The value to replace in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### OS2200_Elementname

This tag is used to change the value of an OS2200 element associated with the job and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs with which the rule is associated. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the value in the definition to change.

* newValue	

    * (*Required*): The value to replace in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### OS2200_Elementname_Mask

This tag is used to change the OS2200 Element Name value of the job definition using a mask that supports wild card characters (? and *). When using the mask ? characters indicates which character in the name should not be changed, while the * characters indicates all following characters should not be changed. 
To change the first character of the name the currentValue should be T* and newValue should be P*. To change the first and last characters of the name, the currentValue should be T?????A and the newValue should be P????B. The Job_Name_Mask tag supports the following tags:

* currentValue	

    * (*Required*): Contains the value to check .

* newValue	

    * (*Required*): Contains the new value to be applied.

* partialUpdate	

    * Not used.

### OS2200_Filename

This tag is used to change the value of OS2200 file name associated with the job and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs with which the rule is associated. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the value in the definition to change.

* newValue	

    * (*Required*): The value to replace in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### OS2200_Project

This tag is used to change the value of an OS2200 account associated with the job and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs with which the rule is associated. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the value in the definition to change.

* newValue	

    * (*Required*): The value to replace in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### OS2200_Qualifier

This tag is used to change the value of OS2200 qualifier associated with the job and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs with which the rule is associated. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the value in the definition to change.

* newValue	

    * (*Required*): The value to replace in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### OS2200_Runid

This tag is used to change the value of an OS2200 Runid associated with the job and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs with which the rule is associated. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the value in the definition to change.

* newValue	

    * (*Required*): The value to replace in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### OS2200_Runid_Mask

This tag is used to change the OS2200 Runid value of the job definition using a mask that supports wild card characters (? and *). When using the mask ? characters indicates which character in the name should not be changed, while the * characters indicates all following characters should not be changed. 
To change the first character of the name the currentValue should be T* and newValue should be P*. To change the first and last characters of the name, the currentValue should be T?????A and the newValue should be P????B. The Job_Name_Mask tag supports the following tags:

* currentValue	

    * (*Required*): Contains the value to check .

* newValue	

    * (*Required*): Contains the new value to be applied.

* partialUpdate	

    * Not used.

### OS2200_Userid

This tag is used to change the value of an OS2200 userid associated with the job and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs with which the rule is associated. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the value in the definition to change.

* newValue	

    * (*Required*): The value to replace in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### Property_Name

* This tag is used to change the Property Name value of the property definition as well as the contents of the property. The property name will also be changed in the Events, Expression Dependencies, Job Instance Properties, Complex Expressions, Windows Command Line, Windows Working Directory, Windows Prerun Command Line, Windows Prerun Working Directory, UNIX Start Image, UNIX Parameter, and UNIX Prerun Command fields.

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs with which the rule is associated. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the name of the property in the definition.

* currentValueContents	

    * (*Optional*): Contains the value of the property in the definition if the contents of the property should be changed.

* newValue	

    * (*Required*): The value to insert in the definition if the currentValue matches the value in the definition. If only the content of the property is to be changed, then the newValue matches the currentValue.

* newValueContents	

    * (*Required*): The value to insert in the definition if the currentValueContents matches the value in the definition or if the newValue matches the currentValue.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### Resource_Name

* This tag is used to change the Resource Name value of the resource definition. The resource name is changed in events and dependencies as well.

* currentValue	

    * (*Required*): Contains the name of the resource in the definition.

* newValue	

    * (*Required*): The value to insert in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### Role_Add

* This tag is used to add a Role Name to the list of role definitions. 

* currentValue	

    * (*Required*): Contains the name of the role to add to the list of roles.

* newValue	

    * (*Required*): Use the same name as the currentValue.

* partialUpdate	

    * not used.

### Role_Name

* This tag is used to change the Role Name value of the role definition. The role name is changed in schedule role list as well.

* currentValue	

    * (*Required*): Contains the name of the role in the definition.

* newValue	

    * (*Required*): The value to insert in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### Schedule_Auto_Build_Time

This tag is used to change the Schedule auto build time for schedules that have the auto build option enabled.

* scheduleName	

    * (*Optional*): When present, this indicates the schedule or group of schedules with which the rule is associated. A group of schedules is defined by using a wild card character in the schedule name.

* currentValue	

    * (*Required*): Schedule auto build time in the format HH:MM.

* newValue	

    * (*Required*): New value for schedule auto build time in the format HH:MM.

### Schedule_Build_For_All_Machines_In_Group

This tag is used to change the name of the Machine Group in a schedule definition if the schedule is a multi-instance schedule. This tag also supports the following tags:

* scheduleName	

    * (*Optional*): When present, this indicates the schedule or group of schedules with which the rule is associated. A group of schedules is defined by using a wild card character in the schedule name (e.g., SCHED0100 or SCHED01* for all schedules starting with the characters SCHED01).

* currentValue	

    * (*Required*): Contains the name of the machine group in the definition.

* ```<newValue>```	

    * (*Required*): The value to be inserted into the definition if the current_value matches the value in the definition.

* ```<partialUpdate>```	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### Schedule_Instance_Property

This tag is used to change the Schedule Instance Property name value of the schedule instance property definition and the contents of the property. The schedule instance property name will also be changed in the Schedule Events, Job Instance Properties, Events, Windows Command Line, Windows Working Directory, UNIX Start Image, and UNIX fields of the jobs associated with the schedule . This tag also supports the following tags:

* scheduleName	

    * (*Optional*): When present, this indicates the schedule or group of schedules with which the rule is associated. A group of schedules is defined by using a wild card character in the schedule name (e.g., SCHED0100 or SCHED01* for all schedules starting with the characters SCHED01).

* currentValue	

    * (*Required*): Contains the name of the schedule instance property in the definition.

* currentValueContents	

    * (*Optional*): Contains the value of the Schedule Instance Property in the definition if the contents of the property are changed.

* newValue	

    * (*Required*): The value to insert in the definition if the currentValue matches the value in the definition. But, if only the contents of the Schedule Instance Property are changed, then the newValue must match the value in the currentValue.

 * newValueContents	

    * (*Optional*): The value to insert in the definition if the currentValueContents matches the value in the definition or if the newValue matches the currentValue.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### Schedule_Name

This tag is used to change the Schedule Name value of the schedule definition and is changed in both events and dependencies. This tag also supports the following tags:

* currentValue	

    * (*Required*): Contains the name of the schedule in the schedule definition.

* newValue	

    * (*Required*): The value to insert in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### Schedule_Named_Instance

This tag is used to change the schedule name value of the schedule definition. The schedule name is changed in events as well as dependencies and supports the following tags:

* currentValue	

    * (*Required*): Contains the name of the schedule named instance in the schedule definition.

* newValue	

    * (*Required*): The value to insert in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### Schedule_Start_Time

This tag is used to change the schedule start time.

* scheduleName	

    * (*Optional*): When present, this indicates the schedule or group of schedules with which the rule is associated. A group of schedules is defined by using a wild card character in the schedule name.

* currentValue	

    * (*Required*). Schedule auto build time in the format HH:MM.

* newValue	

    * (*Required*). New value for schedule auto build time in the format HH:MM.

### Script_Name

This tag is used to change the script name value of the script definition. The script name is changed in embedded script job definitions as well:

* currentValue	

    * (*Required*): Contains the name of the script in the script definition.

* newValue	

    * (*Required*): The value to insert in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### SQL_DTExec_Server

This tag is used to change the server name of the job MS SQL DTEXec job action definition and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs that is associated with the rule. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the name of the Server in the MS SQL DTEXec job definition.

* newValue	

    * (*Required*): The value to insert in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### SQL_DTExec_Package_Path

This tag is used to change the package value of the job MS SQL DTEXec job action definition and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs that is associated with the rule. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the name of the package in the MS SQL DTEXec job definition.

* newValue	

    * (*Required*): The value to insert in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### SQL_DTExec_User

This tag is used to change the user name of the job MS SQL DTEXec job action definition and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs that is associated with the rule. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the name of the user in the MS SQL DTEXec job definition.

* newValue	

    * (*Required*): The value to insert in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### SQL_Job_Server

This tag is used to change the server name of the job MS SQL JOB job action definition and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs that is associated with the rule. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the name of the server in the  MS SQL JOB job definition.

* newValue	

    * (*Required*): The value to insert in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### SQL_Job_Jobname

This tag is used to change the job name of the MS SQL JOB job action definition and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs that is associated with the rule. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the name of the MS SQL job in the  MS SQL JOB job definition.

* newValue	

    * (*Required*): The value to insert in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### SQL_Job_User

This tag is used to change the user name of the MS SQL JOB job action definition and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs that is associated with the rule. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the name of the MS SQL user in the  MS SQL JOB job definition.

* newValue	

    * (*Required*): The value to insert in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### SQL_Script_Server

This tag is used to change the server name of the MS SQL Script job action definition and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs that is associated with the rule. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the server name in the MS SQL Script job definition.

* newValue	

    * (*Required*): The value to insert in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).
 
### SQL_Script_Database

This tag is used to change the database name of the MS SQL Script job action definition and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs that is associated with the rule. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the database name in the MS SQL Script job definition.

* newValue	

    * (*Required*): The value to insert in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### SQL_Script_User

This tag is used to change the user name of the MS SQL Script job action definition and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs that is associated with the rule. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains theuser name in the MS SQL Script job definition.

* newValue	

    * (*Required*): The value to insert in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### SQL_Script_Filename

This tag is used to change the file name of the MS SQL Script job action definition and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs that is associated with the rule. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the file name in the MS SQL Script job definition.

* newValue	

    * (*Required*): The value to insert in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### Threshold_Name

This tag is used to change the threshold name value of the threshold definition. The threshold name is changed in events as well as dependencies and supports the following tags:

* currentValue	

    * (*Required*): Contains the name of the threshold in the definition.

* newValue	

    * (*Required*): The value to insert in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### Unix_Group_Id

This tag is used to change the UNIX Group ID of the job definition and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs that is associated with the rule. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the name of the UNIX Group ID in the job definition.

* newValue	

    * (*Required*): The value to insert in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### Unix_GroupId_UserId

This tag is used to change the Group ID and User ID of the UNIX job definition. The field consists of two values: GroupId and UserId. When changing the field, both values must be present and separated by a comma (e.g., groupid,userid). This tag supports this following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs that is associated with the rule. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the name of the value of both fields, separated by a comma in the job definition (e.g., test, user1).

* newValue	

    * (*Required*): The value to insert in the definition if the currentValue matches the value in the definition (e.g., prod, user1).

* partialUpdate	

    * This function does not support partial update, so the value must be set to false.

### Unix_Parameter

This tag is used to change a value in the UNIX Parameter field of the UNIX job definition and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs that is associated with the rule. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the name of the value in the parameter field to change in the job definition.

* newValue	

    * (*Required*): The value to insert in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### Unix_Script_Arguments

This tag is used to change a value in the UNIX Script Argument field of the UNIX job definition and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs that is associated with the rule. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the name of the value in the "Script Argument" field to change in the job definition.

* newValue	

    * (*Required*): The value to insert in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### Unix_Start_Image

This tag is used to change a value in the UNIX Start Image field of the UNIX job definition and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs that is associated with the rule. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the name of the value in the "Start Image" field to change in the job definition.

* newValue	

    * (*Required*): The value to insert in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### Unix_User_Id

This tag is used to change a value in the UNIX User Id field of the UNIX job definition and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs that is associated with the rule. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the name of the Unix User Id in the job definition.

* newValue	

    * (*Required*): The value to insert in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### Windows_Command_Line

This tag is used to change a value in the Windows Command Line field of the Windows job definition and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs that is associated with the rule. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the name of the value in the command line field to be changed in the job definition.

* newValue	

    * (*Required*): The value to insert in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### Windows_Script_Arguments

This tag is used to change a value in the Windows Script Arguments field of the Windows embedded job definition and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs that is associated with the rule. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the name of the value in the command line field to change in the job definition.

* newValue	

    * (*Required*): The value to insert in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### Windows_User

This tag is used to change the Windows User in the job definition and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs that is associated with the rule. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the name of the Windows User in the job definition.

* newValue	

    * (*Required*): The value to insert in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### Windows_Working_Directory

This tag is used to change a value in the Windows Working Directory field of the Windows job definition and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs that is associated with the rule. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the name of the value to be changed.

* newValue	

    * (*Required*): The value to insert in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### ZOS_Batch_User

This tag is used to change a value of a z/OS batch user associated with the job and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs that is associated with the rule. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the value that is to be changed in the definition.

* newValue	

    * (*Required*): The value to insert in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### ZOS_DDName

This tag is used to change the value of the z/OS ddname associated with the job and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs that is associated with the rule. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the name of the definition to change.

* newValue	

    * (*Required*): The value to insert in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### ZOS_Event_User

This tag is used to change the value of an z/OS event user associated with the job and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs that is associated with the rule. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the value in the definition to be changed.

* newValue	

    * (*Required*): The value to be placed in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### ZOS_Member_Name

This tag is used to change the value of a z/OS member name associated with the job and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs that is associated with the rule. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the value in the definition to be changed.

* newValue	

    * (*Required*): The value to be placed in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### ZOS_Prerun_File_Dataset_Name

This tag is used to change the value of a z/OS prerun file dataset name associated with the job and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs that is associated with the rule. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the value in the definition to be changed.

* newValue	

    * (*Required*): The value to be placed in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### ZOS_Prerun_Job_Task_Name

This tag is used to change the value of an z/OS prerun job task name associated with the job and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs that is associated with the rule. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the value in the definition to be changed.

* newValue	

    * (*Required*): The value to be placed in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### ZOS_Prerun_System

This tag is used to change the value of a z/OS prerun system associated with the job and supports the following tags:

* jobName	

    * (*Optional*): When present, this indicates the job or group of jobs with which the rule is associated. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the value in the definition to be changed.

* newValue	

    * (*Required*): The value to be placed in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false; default is false).

### ZOS_Prerun_REXX_Name

* jobName	

* (*Optional*): When present, indicates the job or group of jobs that is associated with the rule. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the value in the definition to be changed.

* newValue	

    * (*Required*): The value to be placed in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false, default is false).

### ZOS_Prerun_REXX_DDName

This tag is used to change the value of a z/OS prerun REXX ddname associated with the job and supports the following tags:

 * jobName	

    * (*Optional*): When present, indicates the job or group of jobs that is associated with the rule. A group of jobs is defined by using a wild card character in the job name (e.g., JOB0100 or JOB01* for all jobs starting with the characters JOB01).

* currentValue	

    * (*Required*): Contains the value in the definition to be changed.

* newValue	

    * (*Required*): The value to be placed in the definition if the currentValue matches the value in the definition.

* partialUpdate	

    * Indicates if the match to be performed is the complete definition or a partial definition (value is true or false, default is false).



