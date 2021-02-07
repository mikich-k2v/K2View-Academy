# Task Window - Reference Tab

The **General tab** of the Task window of Extract and Load enables a selection of Reference table to be process by the task. The following options are available:

- **None**, default value. Do not include Reference tables in the task.
- **Reference Only**, create a task to process Reference tables only. Do not include entities in the task.
- **Both - reference and entities**, create a process both entities and Reference tables.

When selecting the **Reference Only** or **Both - reference and entities** modes, a new tab is added to the Task window:  **Reference**.

Extract tasks extract the **Reference tables** from the source environment and stores into **Cassandra DB**.   Load tasks selects the Reference tables data from Cassandra DB and loads them to the target environment.

Unlike LUIs, the Load task does not activate an extract from the source environment. Therefore, the Reference tables must be loaded into Cassandra by the Extract task before loading them to the target.

Click for more information about [-Reference tables implementation].

## Reference Tab - Extract Task

Display the list of all Reference tables [defined in Fabric as available for the task's LU]. The Reference tab displays on each table its **Source Interface Name**, **Schema Name**, and the **LU Name**. You can **Select All**, **Unselect All**, or check a selected list of Reference tables:

------------------------------------99999999999999999999999---------------------------------------------

![reference](images/task_reference_tab.png)

The Extract task extracts the selected Reference tables and saves them into Cassandra DB. 



## Reference Tab - Load Task

### Regular Mode

Display the list of all Reference tables [extracted into Cassandra for the task's LU and source environment. Like the Extract task window, the Reference tab displays on each table its **Source Interface Name**, **Schema Name**, and the **LU Name**. You can **Select All**, **Unselect All**, or check a selected list of Reference tables.

### Data Flux Mode

Displays the list of available versions created on the reference tables, the source environment, and the load task's LU. The versions created during the last month are displayed. You can set a different period by editing the **From Date** and **To Date** settings.

. See example:

------------------------------------99999999999999999999999---------------------------------------------

![reference](images/task_reference_tab_dataflux.png)



- 



 [![Previous](/articles/images/Previous.png)](22_task_execution_timing_tab.md)[<img align="right" width="60" height="54" src="/articles/images/Next.png">](24_task_reference_tab.md)

