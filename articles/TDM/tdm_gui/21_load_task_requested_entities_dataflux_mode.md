# TDM Load Task - Data Flux Mode - Requested Entities Tab

This tab displays the list of the available versions that can be selected and re-loaded to the target environment. By default, the TDM GUI displays the list of the versions, created during the last month. You can set a different period by editing the **From Date** and **To Date** settings.

The Requested Entities tab setting depends on the [Select All Entities] setting of the General tab:

### Select All Entities is Checked

Display all available versions, created on the source environment and the load task's LUs. See example:

![requested entities- All entities](images/load_task_requested_entities_dataflux.png)

Select one version and click the **Next** button.

### Select All Entities is Unchecked

Populate the list of entities, separated by a comma in the **Entities List** setting.

The TDM displays all available versions, created on the source environment, the load task's LUs, and the selected entities. See example:

------------------99999999999999900----------------------



The available versions are selected based on the following criteria:

- All versions, created for All Entities.
- All versions, created for entities list, where the list of the version contains the selected entities of the load task.

Each update of the entities list may change the list of available versions for the task. 

Select the required version and click on the Next button. When clicking the Next button, the TDM re-validates the entities list and checks for each entity if it has been successfully migrated into Fabric by the extract task of the selected version. 

#### Notes:

- Only one version cab be selected on the load task.
- The version name is the **Task title** of the extract task, created the version.
- The date time is the execution date of the task. One extract task can be executed multiple times. Each execution creates a separate version and has its own date time.
- The  **Version Type** setting indicates if the extract task has been created for all entities, or for a selected list of entities.
- You can sort or filter the table of the available versions.
- You can get the updated list of available versions clicking on the refresh icon.





 [![Previous](/articles/images/Previous.png)](20_load_task_dataflux_mode.md)[<img align="right" width="60" height="54" src="/articles/images/Next.png">](21_task_globals_tab.md)

