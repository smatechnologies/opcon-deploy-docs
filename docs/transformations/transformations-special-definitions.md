# Transformations - Special Definitions

## Special Definitions

This section contains information about some special tags that can be used during transformation.

### environment  

Within OpCon, a schedule name must be unique within an OpCon instance. There may be requirements to create additional versions of the same schedule in a single OpCon instance for various testing scenarios. The environment tag can be used to create additional copies of an existing schedule by defining a value that will be used to prefix information in the schedule definitions (e.g., using environment value of TST results in all schedules in the definition being prefixed with the value TST resulting in schedule names TST_SCHED001, TST_SCHED002). At the same time, all global properties, resources, and thresholds in the definition will be prefixed with the same value (e.g., property PROP1 becomes TST_PROP1, resource RES001 becomes TST_RES001, and threshold THR001 becomes TST_THR001). The values are updated throughout the definition, providing an isolated test instance.
 
* It is also possible to include the Department_Name tag, setting the value to value of the environment definition resulting in the jobs in the schedule being associated with the department defined in the Department_Name definition.

* This definition supports the following tags:

**environment**	

(*Required*): This tag is defined in the Transformations object and consists of a value that will be prefixed to schedule, property, resource, and threshold definitions.

![Environment Sample](/img/environment-sample.png)

### Frequency_Use_Existing_Definitions 

* This definition is used by customers that are doing software migration projects, and has been implemented to assist with moving schedules through the migration cycle from unit test to production which allows a frequency definition to have a temporary definition.
 
* This tag is a special tag that is used when you want the frequency definition of the frequency on the target system to be used instead of the frequency in the definition. This is typically used when importing a schedule or task on production systems and the real frequency definition should be used instead of the test frequency definition.

* One example would be if there is a frequency definition on the target system LWDOM (the last working day of the month). During testing, the frequency definition for LWDOM will probably be an All Days definition, as you do not want to wait until the last day of the month to perform tests.

![Frequency_Use_Existing_Definitions Sample](/img/frequency-use-existing-definitions.png)

### Move_Schedule_Package

* This definition is used by customers that are doing software migration projects, and has been implemented to assist with moving schedules through the migration cycle from unit test to production. The unique aspect of this implementation is that frequencies are also prefixed with the value. This approach allows frequencies to have different definitions through the development phase than the production phase. When used with the Frequency_Use_Existing_Definitions tag, the frequencies will get the correct definitions.
 
* Within OpCon, a schedule name must be unique within an OpCon instance. There may be requirements to create additional versions of the same schedule in a single OpCon instance for various testing scenarios. The Move_Schedule_Package tag can be used to move schedules through existing systems including to the final production destination. The implementation prefixes the schedule name, global property names, frequency names, resource names, and threshold names, thereby creating a unique test instance. Events are scanned for schedule names, property, and frequency names and UNIX start image and parameters are scanned for property names.

* The Move_Schedule_Package can initially create the schedule from a standard definition by prefixing the values with the specified value. Once a package has been created, it can be moved to the next test scenario by replacing the existing prefix with a new prefix. During the final move to production, the prefixes are removed and the frequencies implement the real frequency definitions.

This definition supports the following tags:

**currentValue**	

* (*Optional*): When creating an initial schedule, it must be empty while newValue contains the prefix to add to the schedule name, frequencies, global properties, resources, and thresholds.

When moving the schedule to a new test scenario, it contains the existing prefix which must be replaced with the value in the newValue which is the new prefix.

When moving the schedule to production, it contains the existing prefix which must be removed while the newValue must be empty.

**newValue**

* (*Optional*): When creating an initial schedule, it must be set to the prefix that will be added to the schedule, frequency, resource, threshold, and global property names while the currentValue must be empty.

When moving the schedule to a new test scenario, it contains the new prefix which must be replaced when the currentValue matches.

When moving the schedule to production, it must be empty while the currentValue matches the prefix being removed.

**partialUpdate**	

* Indicates if the match to be performed is the complete definition or a partial definition (this is set to true by the software).

## Examples

* This first example shows how the schedule can be created. In this case, the value DEV will be prefixed to the schedule name, frequency names, resource, thresholds, and global properties.

![Move_Schedule_Package Create Initial Package Example](/img/create-initial-package.png)

* This second example shows how the schedule package can be moved between the test scenarios. In this case, the value DEV will be replaced on the schedule name, frequency names, resource, thresholds, and global properties with TST.

![Move_Schedule_Package Between Test Scenarios Example](/img/move-between-test-scenarios.png)

* This third example displays how the schedule package can be moved to production. In this case, the value TST will be removed from the schedule name, frequency names, resource, thresholds, and global properties and the frequencies will take on the values defined in the target OpCon system and not the value in the definition.

![Move_Schedule_Package to Production Example](/img/move-to-production.png)