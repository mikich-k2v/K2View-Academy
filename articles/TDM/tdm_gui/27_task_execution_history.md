# Task Execution History

The TDM GUI has several windows to display the execution history on a given task:

- [Task Execution Summary] :  displays the list of the executions of the task.
- [Logical Units Execution Summary] : displays the list of related LUs and post execution processes of a given task execution.
- [Task Execution]- Detailed Statistics] : displays the hierarchical structure of the copied and failed entities of a given task execution.



## Task Executions Summary 

Display of the a task's executions list. Note that an editing a task creates a new version on the task. Each version has its own record in the Tasks Lists window and has its own task execution summary. 

Open the [Tasks List window](14_task_overview.md#tdm-tasks-list-window) and click the ![task icon](images/task_execution_history_icon.png)icon next to the selected task to open the Task Execution Summary window for the task and display the full list of the task's executions:

![task execution summary](images/task_execution_summary.png)

Click **Show/Hide Columns** to open a popup window displaying the list of available fields for each task. Fields in green are displayed by default.  Click a field to remove it from the display.

The following information is displayed on each task execution:

- Task_execution_id
- Source and target environments
- Task Executed By:  the username who has executed the task
- BE name
- Summary statistics about the processed entities, Reference tables, and post execution processes.
- Execution status: will be set to completed if all the related task's processed have been completed successfully.

### Generating Task Execution Summary Report

Click ![task execution summary report](images/task_execution_summary_report_icon.png) icon next to each task execution to generate and download a summary execution report.

Example of Summary Execution Report:

[summary execution report example](ExtractDataFlux_Summary_Execution_Report_EXECID_12.xlsx)

## Logical Units Execution Summary

Display of a task execution LUs and post execution processes. Click the **Task Execution Id** setting of a given task in **Task Execution Summary** window. 

The following window is opened:



