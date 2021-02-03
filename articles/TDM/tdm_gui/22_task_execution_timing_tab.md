# Task Execution Timing Tab

This is the last tab of the task window and set the execution timing options. Select one of the following options:

- **Execution by Request**: the task is only executed when the user clicks the![execution](images/execute_task_icon.png)icon.
- **Scheduled Execution**: defines an automatic task execution by the [TDM scheduler process] on predefined intervals.  For example, execute the task every Monday at 2:15 AM:

![execution timing example1](images/task_scheduling_parameters_example1.png)

Notes:

- A tester can select the Scheduled Execution option only if is permitted to select this method by their [role](10_environment_roles_tab.md#role-permissions) on the target environment. 
- A scheduled task can still be executed by request clicking the![execution](images/execute_task_icon.png)icon.

### Scheduled Execution Parameters

- The execution time interval is kept in the TDM as a **crontab** value. You can populate the scheduling parameters either by:
  - Check the **Advanced** setting and populate the crontab value manually.
  - Clear the **Advanced** setting (default option) and set the scheduling parameters using the TDM wizard. The following options are available:

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
<p>select the number of minutes past the hour in gaps of 5 minutes: 0, 5, 10&hellip;</p>
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

- You can set the **End By** setting to run the task by a scheduler till a predefined date. For example, run the task every week till the end of Feb.

  

   [![Previous](/articles/images/Previous.png)](21_load_task_requested_entities_dataflux_mode.md)[<img align="right" width="60" height="54" src="/articles/images/Next.png">](23_task_globals_tab)

  



