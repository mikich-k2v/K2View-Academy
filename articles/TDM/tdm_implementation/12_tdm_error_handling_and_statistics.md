# TDM Error Handling and Statistics Flows

The TDM library delivers a generic error handling and the statistics gathering mechanism which is based on the Broadway capabilities tailored per TDM business requirements. 

It includes a set of generic flows that gather the errors and the statistics during the task execution and populate them into the dedicated tables. This data is used for the creation of TDM execution reports.

### How Do I Perform Error Handling in TDM?

The TDM library includes two utility flows to handle the errors during the TDM task execution:

* PopulateTableErrorsWithFailed.flow
* PopulateTableErrorsWithReject.flow

Both utilities invoke the internal **PopulateTableErrors.flow** for gathering the error details into the **task_exe_error_detailed** table. The difference between these two utilities is that the first one sets on the session level:

~~~
ENTITY_STATUS = failed 
~~~

It also sets the error category as *Entity Failed* in the **task_exe_error_detailed** table, while the second flow sets a record as *Record Rejected*.

The error handling utility is invoked from each Load flow's **Load Data To Target** Stage. By default, the error is suppressed, sent to log file and the **PopulateTableErrorsWithFailed.flow** is invoked. If it is needed only to reject a record instead of failing the whole entity, replace the flow name with **PopulateTableErrorsWithReject.flow**. 

![image](images/12_tdm_err_stat_01.PNG)

[Click to learn how to use the ErrorHandling Actor](/actors/06_error_handling_actors.md#how-do-i-use-the-errorhandler-actor).