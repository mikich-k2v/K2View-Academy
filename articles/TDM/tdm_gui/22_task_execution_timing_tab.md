# Task Execution Timing Tab 

This is the last tab in the Task window and enables setting the execution timing options. Select one of the following options:

- **Execution by Request**, click ![execution](images/execute_task_icon.png) to execute the task.
- **Scheduled Execution**, sets the automatic execution of a task via a [TDM Scheduler process] on predefined intervals.  For example, execute the task every Monday at 2:15 AM.

![execution timing example1](images/task_scheduling_parameters_example1.png)

Notes:

- Testers can select Scheduled Execution only when their [role](10_environment_roles_tab.md#role-permissions) has permissions to select this method for the target environment. 
- To execute a scheduled task, click ![execution](images/execute_task_icon.png).

### Scheduled Execution Parameters

- The Execution Time Interval is saved in TDM as a **crontab** value. Scheduling parameters can be populated by either:
  - Checking the **Advanced** setting and populating the **crontab** value manually. Set a **Quartz crontab expression**. 
  - Clearing the **Advanced** setting (default option) and setting the scheduling parameters using the TDM Wizard. The following options are available:

<table width="900pxl">
<tbody>
<tr>
<td width="200pxl">
<p><strong>Every setting</strong></p>
</td>
<td width="350pxl">
<p><strong>At setting</strong></p>
</td>
<td width="350pxl">
<p><strong>On setting</strong></p>
</td>
</tr>
<tr>
<td width="200pxl">
<p>Minute</p>
</td>
<td width="350pxl">
<p>N/A</p>
</td>
<td width="350pxl">
<p>N/A</p>
</td>
</tr>
<tr>
<td width="200pxl">
<p>Hour</p>
</td>
<td width="350pxl">
<p>Select the number of minutes past the hour in gaps of 5 minutes: 0, 5, 10&hellip;</p>
</td>
<td width="350pxl">
<p>N/A</p>
</td>
</tr>
<tr>
<td width="200pxl">
<p>Day</p>
</td>
<td width="350pxl">
<p>Select hour and minutes</p>
</td>
<td width="350pxl">
<p>N/A</p>
</td>
</tr>
<tr>
<td width="200pxl">
<p>Week</p>
</td>
<td width="350pxl">
<p>Select an hour and minutes</p>
</td>
<td width="350pxl">
<p>Select a day of the week: Sunday, Monday&hellip;</p>
</td>
</tr>
<tr>
<td width="200pxl">
<p>Month</p>
</td>
<td width="350pxl">
<p>Select hour and minutes</p>
</td>
<td width="350pxl">
<p>Select a day in the month: 1<sup>st</sup>, 2<sup>nd</sup> &hellip;</p>
</td>
</tr>
<tr>
<td width="200pxl">
<p>Year</p>
</td>
<td width="350pxl">
<p>Select hour and minutes</p>
</td>
<td width="350pxl">
<p>Select a month and a day in the month. For example, 1<sup>st</sup> of February.</p>
</td>
</tr>
</tbody>
</table>

- The **End By** setting can be set to run a task by the scheduler until a predefined date. For example, run the task every week till the end of February.

  

   [![Previous](/articles/images/Previous.png)](21_load_task_requested_entities_dataflux_mode.md)[<img align="right" width="60" height="54" src="/articles/images/Next.png">](23_task_globals_tab)

  



