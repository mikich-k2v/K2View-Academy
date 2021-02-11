# Task Execution Processes

The task execution process has several steps:

1. Creating task execution request.
2. Initiating a Batch process on each task's LU and post execution process in a-synchronic mode.
3. Updating the status of the completed processes.

The [first step](/articles/TDM/tdm_gui/26_task_execution.md) can be initiated either by the TDM GUI or the TDM Scheduling process.

This article focuses on the 2nd and 3rd steps.

The task can include the following:

- Entities
- Reference tables
- Post Execution processes. For example, sending a mail to the user after the execution ends. 

The following diagram displays the task execution flow:

![task execution process](images/tdm_task_execution_processes.png)



## Main TDM Task Execution Process: tdmExecuteTask Job

This job runs every ten seconds and scans [task_execution_list](02_tdm_database.md#task_execution_list) TDM DB table and gets pending task execution requests.

Every task execution gets a unique identifier: **task_execution_id**. A task execution may include several LUs and post execution processes and each one has a separate record in task_execution_list. However, all the related records that belong to a given task execution, have the same **task_execution_id**. 

The task execution order of the related task's components is set as follows:

1. LUs: run the LUs from parent to child.  Process all the related entities on each LU before moving to its child LU.

   Click for more information about the [execution order of hierarchical LUs](/articles/TDM/tdm_overview/03_business_entity_overview.md#task-execution-of-hierarchical-business-entities).

2. Post Execution Processes: run the post execution processes after the execution of the LUs ends. The post execution processes are executed by their [execution order](/articles/TDM/tdm_gui/04_tdm_gui_business_entity_window.md#post-execution-processes-tab) as defined in the task's BE. 

The following diagram describe the TDM Task execution process flow:

![task execution job](images/tdmExcuteTask_job_flow.png)

The execution is done on asynchrony mode: the **tdmExecuteTask** job starts the execution on each LU or post execution process and a separate job - **checkMigrateAndUpdateTDMDB** - checks and updates the execution status of each process.

Both jobs must work in parallel. 

**Example:**

1. Execute a task with **Customer and Billing LUs** and with a post execution process which sends a mail when the task execution ends. Customer is the parent LU of Billing. 
2. Three records are created in task_execution_list on this task. All of them have the same task_execution_id.
3. **tdmExecuteTask** job executes the Batch process on **Customer LU**. 
4. **checkMigrateAndUpdateTDMDB** job updates the status of **Customer LU** when the execution is completed.
5. **tdmExecuteTask** job starts the execution of **Billing LU**, since its parent LU - Customer - is marked as completed.
6.  **checkMigrateAndUpdateTDMDB** job updates the status of **Billing LU** when the execution is completed.
7. **tdmExecuteTask** job can start the execution of the **post execution process** after the execution of all task's LU ends.



### Building Entities List on the Tasks LUs

#### Root LUs

##### Extract Tasks

The entity list depends on the task:

- The [Select All Entities](/articles/TDM/tdm_gui/16_extract_task.md#select-all-entities) setting is checked: run the SQL query defined in [trnMigrateList](/articles/TDM/tdm_implementation/04_fabric_tdm_library.md#trnmigratelist) translation object for the LU.
- The **Selected All Entities** setting is unchecked: build the entity list based on the entities in the task's  [Requested Entities](/articles/TDM/tdm_gui/16_extract_task.md#requested-entities) tab.

##### Load Tasks - Regular Mode

The entity list depends on the task's selection method in the [Requested Entities](/articles/TDM/tdm_gui/18_load_task_requested_entities_regular_mode.md) tab: 

- **Entities List** - build the entity list based on the entities in the task's Requested Entities tab.

- **Random Selection** - randomly select the entities from the  [`<LU Name>_<params>`](/articles/TDM/tdm_implementation/07_tdm_implementation_parameters_handling.md#tdm-parameter-tables) table.

- **Create Synthetic Entities** - duplicate the entity ID, set in the task. Attach a different clone_id on each clone. 

  Example: 

  Select Customer #1 from ENV1 source environment and clone it four times. The following LUIs will be generated: 

  - ENV1_1#params#{"clone_id"=1}

  - ENV1_1#params#{"clone_id"=2}

  - ENV1_1#params#{"clone_id"=3}

  - ENV1_1#params#{"clone_id"=4}

    

- **Parameters** - select the entities based on the task's parameters from a [DB view], created in TDM DB on each combination of BE and source environment.  

##### Load Tasks - Data Flux Mode

-  [Select All Entities](/articles/TDM/tdm_gui/20_load_task_dataflux_mode.md#select-all-entities) is checked  -  copy the full list of the LUIs successfully synced into Fabric by the selected version. The full list it taken from Cassandra table:

  - Get the **batch_id** of the extract task that created the selected version from task_execution_list TDM DB table.

  - Get the full list of completed entities by the selected batch id: 

    ```sql
    SELECT entityID FROM k2batchprocess.batchprocess_entities_info WHERE bid = <selected batch id> and status =  'COMPLETED' ALLOW FILTERING;
    ```

- **Select All Entities** in unchecked - get the entities list from the task.

#### Children LUs

The entity list of a child LU must include all the IDs related to the parent IDs, successfully processed by the task execution.

Click for example of an [execution of hierarchical BE](/articles/TDM/tdm_overview/03_business_entity_overview.md#task-execution-of-hierarchical-business-entities).

The generation of the entity list is based on a JOIN of [task_execution_entities](02_tdm_database.md#task_execution_entities) and the [TDM relationship tables](/articles/TDM/tdm_implementation/06_tdm_implementation_support_hierarchy.md#tdm-relationship-tables):

##### Insert without Load Task

Select the children IDs from task_execution_list and [tdm_lu_type_relation_eid](/articles/TDM/tdm_implementation/06_tdm_implementation_support_hierarchy.md#tdm_lu_type_relation_eid) tables:

```sql
SELECT rel. rel.lu_type2_eid as child_entity_id
From FROM task_execution_entities t, tdm_lu_type_relation_eid rel 
where t.task_execution_id= <task execution id> 
and t.execution_status = 'completed' 
and t.lu_name = <parent lu name> 
and t.source_env  = rel.source_env 
and t.lu_name = rel.lu_type_1 
and t.iid = rel. lu_type1_eid 
and rel.lu_type_2= <child lu name> 
and rel.version_name = <empty string on a regular task and the selected version name on a Data Flux task>;
```



##### Delete before Load Task

Select the children IDs from task_execution_list and both TDM relationship tables: [tdm_lu_type_relation_eid](/articles/TDM/tdm_implementation/06_tdm_implementation_support_hierarchy.md#tdm_lu_type_relation_eid) and [tdm_lu_type_rel_tar_eid](/articles/TDM/tdm_implementation/06_tdm_implementation_support_hierarchy.md#tdm_lu_type_rel_tar_eid) to get the children IDs from source and target environments: 

```sql
SELECT rel. rel.lu_type2_eid as child_entity_id
From FROM task_execution_entities t, tdm_lu_type_relation_eid rel 
where t.task_execution_id= <task execution id> 
and t.execution_status = 'completed' 
and t.lu_name = <parent lu name> 
and t.source_env  = rel.source_env 
and t.lu_name = rel.lu_type_1 
and t.iid = rel. lu_type1_eid 
and rel.lu_type_2= <child lu name> 
and rel.version_name = <empty string on a regular task and the selected version name on a Data Flux task>
UNION
SELECT rel. rel.lu_type2_eid as child_entity_id
From FROM task_execution_entities t, tdm_lu_type_rel_tar_eid rel 
where t.task_execution_id= <task execution id> 
and t.execution_status = 'completed' 
and t.lu_name = <parent lu name> 
and rel.target_env = <target environment name> 
and t.lu_name = rel.lu_type_1 
and t.iid = rel. lu_type1_eid 
and rel.lu_type_2= <child lu name>; 
```



##### Delete Entity without Load Task

Select the children IDs from task_execution_list and [tdm_lu_type_rel_tar_eid](/articles/TDM/tdm_implementation/06_tdm_implementation_support_hierarchy.md#tdm_lu_type_rel_tar_eid) to get the target children IDs: 

```sql
SELECT rel. rel.lu_type2_eid as child_entity_id
From FROM task_execution_entities t, tdm_lu_type_rel_tar_eid rel 
where t.task_execution_id= <task execution id> 
and t.execution_status = 'completed' 
and t.lu_name = <parent lu name> 
and rel.target_env = <target environment name> 
and t.lu_name = rel.lu_type_1 
and t.iid = rel. lu_type1_eid 
and rel.lu_type_2= <child lu name>; 
```



## checkMigrateAndUpdateTDMDB Job

This job runs every ten seconds and check the execution status of running process. It select records from **task_execution_list** TDM DB table where execution_status is **running**.

The execution status is checked  as follows:

- Reference tables: check the execution status or all related Reference tables in [task_exe_ref_stats](02_tdm_database.md#task_ref_exe_stats) TDM DB table.
- Processed entities of each LU: check the batch status based on the **batch_id**, populated in **task_execution_list.fabric_execution_id** column by the tdmExecuteTask job. 

When the process is completed, update the following TDM DB tables:

- **task_execution_list**: update the execution_status and additional data.
- [task_execution_entities](02_tdm_database.md#task_execution_entities): populate each entity or Reference table and its status. Set the **id_type** to **ENTITY** or **REFERENCE** according the data type: entity or Reference table.
- [task_exe_error_detailed](02_tdm_database.md#task_exe_error_detailed): populate the execution errors on Extract tasks. Note that the execution errors of Load tasks are reported to this table by the **PopulateTableErrors** Actor.

### Handling Completed Task Executions

A task execution is completed when it does not have pending or running executions.  The **checkMigrateAndUpdateTDMDB** Job handles completed task executions as follows:

1. Updates the execution summary TDM DB tables.
2. Synchronizes the task execution details to Fabric. 

#### Updating Execution Summary TDM Tables

Updates the following TDM DB tables:

- [task_execution_summary](02_tdm_database.md#task_execution_summary)
- [task_exe_error_summary](02_tdm_database.md#task_exe_error_summary)

#### Sync the Task Execution ID to TDM LU

The TDM LU holds the execution details of each task execution. The TDM's **instance ID** is the **task_execution_id** generated by the TDM GUI for each task execution.

A completed task execution is synchronized into the TDM LU.  The execution information and the TDM execution reports are extracted from the TDM LUI data.



[![Previous](/articles/images/Previous.png)](02_tdm_database.md)[<img align="right" width="60" height="54" src="/articles/images/Next.png">](04_task_execution_overridden_parameters.md)





