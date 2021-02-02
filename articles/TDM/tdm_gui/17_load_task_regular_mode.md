# TDM Load Task - Regular Mode

A Load task extracts the selected entities or Reference tables from the selected source environment and loads them to the selected target environment. A load task can also delete the selected entities from the target environments.

A Load task contains the following tabs:

- [General](#general)
- [Requested Entities](18_load_task_requested_entities_regular_mode.md)
- [Request Parameters](19_load_task_request_parameters_regular_mode.md)
- [Execution Timing]():   this is the last tab of the Task window and is available for all task types and modes. The following options are available  for the task execution:

  - **Execution by Request**: the default option.
  - **Scheduled execution**: set scheduling parameters to automatically execute the task based on the scheduling parameters. Note that a tester can select this option only is its role has a scheduling permission.


When checking the **Set Global Variables** setting, a new tab is opened: [Task Globals].

When setting the **Reference** setting to **Reference Only** or **Both - reference and entities**, a new tab is opened: [Reference].

## General

This is the first tab of the TDM task and holds a general information of the task. See example below:

![general tab](images/load_general_tab_regular.png)

### Task Title

- A task name. A mandatory setting. Note that only one active task can have a specific Task Title. An error is displayed when an attempt is made to create several tasks with the same task title.

### Task Type

- Load or Extract. Set the task type to **Load**.

### Entity Versioning

- Check to set the task mode to [Data Flux](15_data_flux_task.md). 
- Leave the Entity Versioning unchecked to create a regular mode task.

### Set Global Variables 

- Check to [override Globals on a task level].

### Reference 

[Reference handling]. Select a value from the dropdown list:

- **None**: default value. Do not include Reference tables in the task.
- **Reference Only**: create a task to extract Reference tables only into Fabric. Do not include entities in the task.
- **Both - reference and entities**: create a task to extract both - entities and Reference tables - into Fabric.

### Number of Entities 

- This setting is displayed only on a regular mode task, i.e. the Entity Versioning setting is unchecked. 

- Populate the Number of Entities by the number of entities processed by the task:

  - Admin and Environment owner users are set any number.

  - Testers can set the number of entities that does not exceed are limited to the minimum number, set in their roles on the selected source and target environments. For example, if a tester can read up to 100 entities from the source environment and write up to 5 entities into the target environment, then the maximal number of entities that can be set by the tester, is 5. 

  - The validation on the Number of Entities, set by the testers, is made when clicking the **Next** button to move to the next tab. If the tester exceeds their permission, an error message is displayed. For example:

     

    ![validation error](images/task_number_of_entities_validation.png)

  

### Environment Names

- Select a **source environment** from the dropdown list of the active TDM environments with [environment type](08_environment_window_general_information.md#environment-type) **Source** or **Both**. 
- Select a **target environment** from the dropdown list of the active TDM environments with [environment type](08_environment_window_general_information.md#environment-type) **Target** or **Both**. 
- Note that tester users can only select source environment they are attached to by a Read [role](10_environment_roles_tab.md) and target environment they are attached to by a Write [role](10_environment_roles_tab.md). 

### Business Entity

The [BE](04_tdm_gui_business_entity_window.md) of the task. Select a BE from the dropdown list of the [BEs](05_tdm_gui_product_window.md#be-and-lu-product-relationship) included in the [environment’s products](11_environment_products_tab.md). 

### Logical Units

Select all, partial, or one LU of the selected BE. 

The following validations are set on the selected LUs:

The selected LUs must include at least one [root LU](/articles/TDM/tdm_overview/03_business_entity_overview.md#root-lu) of the selected BE. 

You cannot select an LU without its parent LU. 

**Example:**

- Customer BE has two level in its hierarchy: the  root LU is the Customer Data, the Billing LU is a child of the Customer Data, and the Collection LU is the child of the Billing LU. You cannot select a the Collection LU without the Billing LU when creating a task on Customer BE.

Click for additional [examples of BE's hierarchies](/articles/TDM/tdm_overview/03_business_entity_overview.md).

### Post Execution Processes

Select all, partial, or one [post execution process](04_tdm_gui_business_entity_window.md#post-execution-processes-tab) of the selected BE.



 [![Previous](/articles/images/Previous.png)](16_extract_task.md)[<img align="right" width="60" height="54" src="/articles/images/Next.png">](18_load_task_requested_entities_regular_mode.md)

