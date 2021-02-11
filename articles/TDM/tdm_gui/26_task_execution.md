# Task Execution

A task can be executed multiple times either by clicking ![task execution icon](images/execute_task_icon.png) or by a TDM scheduling process if the task's [Execution Timing](22_task_execution_timing_tab.md) is **Scheduled Execution**.

The TDM Scheduling process checks the **End Date** of the task's scheduling parameters. If the End Date is earlier than the current date, the process cleans the task's  **Scheduled Execution parameters** and skips the task execution. 

## Task Execution Order

A TDM task can include multiple LUs with a flat or hierarchical structure and post execution processes.

The execution of the related task components runs in the following order:

1. LUs: run the LUs from parent to child.  

   Click for more information about the [execution order of hierarchical LUs](03_business_entity_overview.md#task-execution-of-hierarchical-business-entities).

2. Post Execution Processes: run the post execution processes after the execution of the LUs ends. The post execution processes are executed according to their [execution order](04_tdm_gui_business_entity_window.md#post-execution-processes-tab) as defined in the task's BE. 

## Holding Task Execution

Occasionally you may need to temporarily set a task on-hold. For example, if the testing environment is temporarily down, to hold all task executions on an environment until the testing environment is up again and to then reactivate the tasks for this environment.

Hold or Activate task activities are enabled only for Active tasks. When a task is deleted (set to Inactive), its task execution status cannot be modified.

Tasks with an **on-Hold** task execution status cannot be executed.  

Hold and Activate task buttons are displayed on the Tasks screen of each task:

- To set the task to on-hold (pause), click ![hold task](images/hold_task_icon.png).
- To activate a task execution status, click ![activate task icon](images/activate_onhold_task_icon.png).

### Who Can Hold or Activate a Task?

- Admin user, can hold or activate all active tasks.
- Environment owner user, can hold or activate all active tasks in their environment.
- Testers, can hold or activate their active tasks.



**Notes:**

- To execute a scheduled task on demand, click ![task execution icon](images/execute_task_icon.png). 

- Both the TDM GUI or TDM Scheduling processes initiate an execution request in the TDM DB. The TDM task execution process gets pending execution requests and executes the tasks.

  Click for more information about the [TDM task execution process].

- A task cannot be executed several times in parallel. An additional execution can be initiated only if the previous execution has ended.

- The TDM Scheduling process skips running tasks.

- The TDM Scheduling process skips on-hold tasks.



  [![Previous](/articles/images/Previous.png)](25_task_tdmdb_tables.md)[<img align="right" width="60" height="54" src="/articles/images/Next.png">]()

