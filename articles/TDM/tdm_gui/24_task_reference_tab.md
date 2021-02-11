# Task Window - Reference Tab

The **General tab** in the Extract and Load Task window displays Reference tables that are processed by the task. The following options are available:

- **None**, default value. Do not include Reference tables in the task.
- **Reference Only**, create a task to process Reference tables only. Do not include entities in the task.
- **Both - reference and entities**, create and process both entities and Reference tables.

When selecting **Reference Only** or **Both - reference and entities** modes the **Reference** tab is added to the Task window.   

Extract tasks extract **Reference tables** from a source environment and store them in **Cassandra DB**.  Load tasks select data in Reference tables from the Cassandra DB and load them to the target environment.

Unlike LUIs, a Load task does not activate an extraction from the source environment. Therefore, Reference tables must be loaded into Cassandra by the Extract task before loading them to the target.

Click for more information about [-Reference tables implementation].

## Reference Tab - Extract Task

Display a list of all Reference tables [defined in Fabric as available for the task's LU]. The Reference tab displays its **Source Interface Name**, **Schema Name** on each table and **LU Name**. You can **Select All**, **Unselect All**, or check a selected list of Reference tables:

------------------------------------99999999999999999999999---------------------------------------------

![reference](images/task_reference_tab.png)

The Extract task extracts the selected Reference tables and saves them into the Cassandra DB. 



## Reference Tab - Load Task

### Regular Mode

Display a list of all Reference tables [extracted into Cassandra for the task's LU and source environment. Similar to the Extract Task window, a Reference tab displays the **Source Interface Name**, **Schema Name**, and the **LU Name** on each table. You can **Select All**, **Unselect All**, or check a selected list of Reference tables.

### Data Flux Mode

Displays the list of available versions created on reference tables and a source environment, and a load task's LU. The versions created during the last month are displayed. To select another period, edit the **From Date** and **To Date** settings.

For example:

------------------------------------99999999999999999999999---------------------------------------------

![reference](images/task_reference_tab_dataflux.png)





 [![Previous](/articles/images/Previous.png)](22_task_execution_timing_tab.md)[<img align="right" width="60" height="54" src="/articles/images/Next.png">](24_task_reference_tab.md)
