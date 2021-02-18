# TDM Error Handling and Statistics Flows

The TDM library has a generic error handling and statistics gathering mechanism based on Broadway capabilities that are tailored for TDM business requirements. 

The mechanism includes a set of generic flows that gather errors and statistics during task execution and populates them into dedicated tables. This data is used for monitoring  TDM tasks and creating TDM execution reports.

### How Do I Perform Error Handling in TDM?

The TDM library includes two utility flows that handle errors during the execution of TDM tasks:

* PopulateTableErrorsWithFailed.flow
* PopulateTableErrorsWithReject.flow

Both utilities invoke the internal **PopulateTableErrors.flow** to populate error details into the **task_exe_error_detailed** table. The difference between these two utilities is that the PopulateTableErrorsWithFailed.flow is set on a session level:

~~~
ENTITY_STATUS = failed 
~~~

PopulateTableErrorsWithFailed.flow also sets the error category as *Entity Failed* in the **task_exe_error_detailed** table, while PopulateTableErrorsWithReject.flow sets a record as *Record Rejected*.

The error handling utility is invoked from each Load flow's **Load Data To Target** Stage. The error is suppressed in order not to stop the task execution in the middle and to get to the statistics gathering step.

By default, the **PopulateTableErrorsWithFailed.flow** is invoked. If the record rejection is needed instead of failing the entire entity, replace the Inner flow name with **PopulateTableErrorsWithReject.flow**. 

![image](images/12_tdm_err_stat_01.PNG)

[Click to learn how to use the ErrorHandling Actor](/articles/19_Broadway/actors/06_error_handling_actors.md#how-do-i-use-the-errorhandler-actor).

### How Do I Gather Statistics in TDM?

The TDM library includes the PopulateTableStats.flow that gather statistics during a TDM task execution:

PopulateTableStats.flow populates statistics data into the **task_exe_stats_detailed** table, including the number of records in the source and the target tables. 

PopulateTableStats.flow is invoked from each Load flow's **Get Statistics** Stage to gather the statistics and then **Report Statistics** Stages to be loaded into TDM DB tables. 

![image](images/12_tdm_err_stat_02.PNG)



[![Previous](/articles/images/Previous.png)](11_tdm_implementation_using_generic_flows.md)[<img align="right" width="60" height="54" src="/articles/images/Next.png">]()
