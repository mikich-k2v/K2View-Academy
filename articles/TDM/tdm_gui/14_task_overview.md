# TDM Task Overview

Data provisioning is implemented by creating and executing TDM tasks. 

A TDM task is created in the TDM interface. It holds a list of instructions and settings that define the type and subset of processed entities, the source and target environments and additional information. For example, create a task to copy 5 customers with small and medium business plans from Production into the UAT1 target environment.

The actual data provisioning is performed by the task execution where each task can be executed multiple times.

The following task types are supported by TDM:

- Extract task, extracts the selected entities or Reference tables from the selected source environment and saves this data in Fabric for later use.

- Load task, extracts the selected entities or Reference tables from the selected source environment and copies them to the selected target environment.

A task type can have either of the following task modes:

- [Data Flux], whereby users can backup versions of data and reload it to the testing environment. To do so, check **Entity Versioning** to create a Data Flux task. 
- Regular, the default mode.


## Who Can Create a Task?
-  Admin users.
-  Environment owners who can create a TDM task for their environment.
-  Testers who can create a TDM task for the environments they are attached to by a [role](/articles/TDM/tdm_gui/10_environment_roles_tab.md):
   - Source environment, testers must be attached to the source environment by a role with [Read](/articles/TDM/tdm_gui/10_environment_roles_tab.md#read-and-write-and-number-of-entities) access.
   - Target environment, testers must be attached to the target environment by a role with [Write](/articles/TDM/tdm_gui/10_environment_roles_tab.md#read-and-write-and-number-of-entities) access.



## TDM Tasks List Window

The TDM Task List displays the following:

- Task Title, task name.

- Task Type, Load / Extract.

- [Entity Versioning], true / false.

- BE name.

- Source and Target environments. 

- Selection criteria for entities.

- Number of processed entities.

- General parameters like created by user and update date. 

The following screenshot shows an example of the TDM Task List. 

  ![tasks list](images/tdm_task_list_window.png)

  

1.  Click **Show/Hide Columns** to open a popup window displaying the list of available fields for each task. Fields in green are displayed by default. 
2.  To display additional fields, click the fields.
3.  To remove a field from the display, click the field:

![show hide columms](images/task_list_show_hide_columns.png)

4. To find a field, click **Search** and filter the displayed tasks using the filters.

The TDM interface displays a list of icons next to each task record:

- ![task icon](images/execute_task_icon.png)[Execute Task]. 
- ![task icon](images/hold_task_icon.png) [Hold Task], set the task on-hold temporarily.
- ![task icon](images/save_as_icon.png)[Save As], copy the task into a new task.
- ![task icon](images/task_execution_history_icon.png)[Task Execution History], display the execution history of the selected task.



### How Do I Create or Edit a Task?

1. Click **New Task** in the right corner of the Tasks List window.
2. To open a selected task, click the **Task Title** (task name) of the task.

 [![Previous](/articles/images/Previous.png)](13_environment_exclusion_lists.md)[<img align="right" width="60" height="54" src="/articles/images/Next.png">](15_data_flux_task.md)

