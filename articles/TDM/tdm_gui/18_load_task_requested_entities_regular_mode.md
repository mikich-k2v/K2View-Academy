# TDM Load Task - Regular Mode - Requested Entities Tab

This tab defines the selection method to define the subset of entities of the task. See example below:

![requested entities](images/load_requested_entities_tab_regular.png)



The entities in the task can be selected using one of the following options:

### Entities List

This is the default selection method. Populate a list of entity IDs, separated by a comma. This method is suitable for a limited number of entities. For example, the tester checks a defect, opened on given entities, and loads this entities to the testing environment to test them.

Notes:

- It is not allowed to populate entities that exist in one of the [exclusion lists](13_environment_exclusion_lists.md) of the task's environment and BE  into the entities list. For example, if customer 1 is excluded from copy, this customer cannot be populated in the entities list of a task.
- It is not allowed to populate entities that are also populated in the task's **Exclusion List** setting.
- An entity can be populated in the task even if it does not exists in Fabric yet. The entity is extracted from the the source environment, synchronized into Fabric, and loaded from Fabric to the target environment.

### **Random selection** 

Get random list entities from the [LU PARAMS](/articles/TDM/tdm_architecture/02_tdm_database.md#lu_name_params) table, created  in the TDM DB for root LU of the task's BE.  Entities of the environment or task level exclusion lists, are excluded from the task.

A tester can select this option only if his permitted to select this method by their role on the target environment.

### Create Synthetic Entities

Create X clones of the selected entity in the target environment.  You must populate the real entity ID to be replicated when selecting this selection method. See example:

![synthetic](images/requested_entities_synthetic_mode.png)



For example, if the **Number of Entities** setting is populated by  5, and the **Entity ID** is set to 109, then the task creates five clones (replicas) of entity ID 109 in the target environment. 

The task replaces the sequences on each replica to avoid duplicated sequences in the target environment. 

A tester can select this option only if his permitted to select this method by their role on the target environment.

### Parameters 

- Select entities by a predefined list of parameters. Entities of the environment or task level exclusion lists, are excluded from the task. You can select one of several parameters. In addition, you can add the same parameter multiple times with different values.

- The parameters list must be [defined on each LU of the task BE](/articles/TDM/tdm_implementation/07_tdm_implementation_parameters_handling.md) in the Fabric project.

  #### Use Parameters with Random Selection Checkbox

  The Parameters selection has two modes: 

  - When this checkbox is checked (default value), the TDM randomly selects the entities from the list of all entities that match the selected parameters. This way, each task execution gets different list of entities that match the selected parameters. The **Selection Method** displayed in the Tasks List window is **Parameters- selection based on parameters with random selection**. 

    Example: 

    - Creating a task to load 5 customers by selected parameters. There are 800 Customers that match the selected parameters. The task execution gets a random list of 5 Customers from the list of 800 Customers that match the selected parameters.  

  - When this checkbox is unchecked, gets the first entities that match the selected parameters. This way, each task execution gets the same list of entities that match the selected parameters. The **Selection Method** displayed in the Tasks List window is **Parameters - selection based only on Parameters**. 

    Example:

    - Create a task to load 5 customers by selected parameters. There are 800 Customers that match the selected parameters. The task execution gets the first 5 Customers that match the selected parameters. 

  #### How Do I Add a Condition? 

  To add a parameter:

  -  Click the **Add Condition** button. 
  - Select the required parameter and the operator from the dropdown lists, and populate the value of the parameter.
  - Add **AND/OR** operator to connect the parameter to the previous parameters or group.

  ##### How Do I Populate the Parameter's Value?

  There are several types of parameters:

  - **Combo**: parameters with a limited number of values. The task window displays a dropdown list of the parameters values. Select a value from the dropdown list.

    Click for more information about the [setting of a parameter as a combo parameter](/articles/TDM/tdm_implementation/07_tdm_implementation_parameters_handling.md#tdm-parameters-implementation-guidelines).

  - **Number**: the TDM GUI displays the minimum and maximum values on this parameter. If the populated values exceeds the parameter's range, an error message is displayed.

  - **Date**: populate the value using the following format: **YYYYMMDD**.

  - **Text**: populate the value by a free text.

  See the example below: 

  -------------------(((((((((((((((())))))))))))))))

  #### How Do I Add a Group of Parameters?

  To add a group of parameters: 

  - Click the **Add Group** button.

  Note that you can add nested groups of parameters, i.e. define an inner group inside an outer group.

  See the example below:

  -------------------(((((((((((((((())))))))))))))))

  #### How Do I Remove A Parameter or a Parameters Group?

  - Click the ![remove parameter](images/delete_parameters_icon.png) icon located on the right side of the parameter to delete a parameter.
  - Click the **Remove Group** button to remove a parameters group.

#### Getting the Number of Matching Entities

- Click the Refresh icon next to the **Entities Matched** to calculate the number of entities that match the selected parameters.
- The Parameters selection supports the parent-child hierarchy relationship between the LUs of the selected BE. It can crosscheck the matching entities of parameters selective combination, taking into consideration parameters from different LUs on the same BE with hierarchy structure. For example, if the user selects Customers that live in New York and have scheduled visits (see the screenshot below), the TDM checks the related visits for each patient which lives in New York and checks for their status.

- When clicking the Refresh button, it brings up the number of matching entities according to the parameters’ conditions and displays the SQL query, built based on the selected parameters.

See the example below:

-------------------(((((((((((((((())))))))))))))))



Click for more information about the [TDM parameters tables and View] created by the TDM on the TDM DB to display a hierarchical view on the TDM parameters. 

### Exclusion List

This is an optional setting. Populate entity IDs, separated by a comma, to be excluded from the task's entities. These entities are excluded from the task, even if they match selected criteria. This list can be populated for every selection method.

Notes:

- You cannot populate an entity ID in both task's settings: **Entities List** and **Exclusion List**.
- [Environment level exclusion lists](13_environment_exclusion_lists.md) are also excluded from the task's entities.





 [![Previous](/articles/images/Previous.png)](17_load_task_regular_mode.md)[<img align="right" width="60" height="54" src="/articles/images/Next.png">](19_load_task_request_parameters_regular_mode.md)

