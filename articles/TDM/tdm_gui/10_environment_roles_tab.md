# Environment Roles Tab

The role is defined on the environment level and defines the list of permissions related to the TDM task creation on the environment. In addition, the role is used to attach testers to the environment. Testers user can create and execute a TDM task on a given environment only if they are attached to an environment's role.

A role is an **optional setting** of an environment and can be created, edited or deleted by an Admin user or the [Environment Owner](08_environment_window_general_information.md#environment-owners) **of the environment.  An Environment without a role, or without testers attached to a role, can be used only by Admin users or by its Environment Owners.

The environment roles are displayed in the **Roles tab** of the Environment window:

- To create a new Role, click the **New Role** button, populate the role's setting and click the **Add** button.
- To open a selected Role, click the **Name** setting of the Role.  Click the **Save Changes** to save the updates. 
- To delete a Role, click the [![be_Example](https://github.com/k2view-academy/K2View-Academy/raw/Academy_6.4_TDM/articles/TDM/tdm_gui/images/delete_icon.png)](https://github.com/k2view-academy/K2View-Academy/blob/Academy_6.4_TDM/articles/TDM/tdm_gui/images/delete_icon.png) icon in the right corner of the Role window.

## Role Window 

The Role window defines the role's permissions and the list of testers, attached to the role.

See example below:

![role window](images/env_role_window.png)

The Role window consists of the following settings:

### Name

The role name. The Name setting is mandatory. Note that only one active Role can have a specific Name. An error is displayed when an attempt is made to create several Roles with the same name. 

### **Description**

The Role description , an optional setting. 

### Read and Write and Number of Entities

- A Read access can be granted on a source environment, i.e. the [environment type](08_environment_window_general_information.md#environment-type) is **Source** or **Both**. 

- A Write access can be granted on a target environment, i.e. the environment type is **Source** or **Both**.

- Environment that can be used in both modes - source and target (environment type is Both) - can have both types of access: Read and Write. A role of such environment can have both types of access, or only one of the access types.

  **Example:**

  - ENV1 can be a source or target environment. The environment has two roles: 
    - role1: enables only a Read access. The testers of this role can only select this environment as a source environment on the TDM task.
    - role2: enables only a Write access. The testers of this role can only select this environment as a target environment on the TDM task.
    - role3: enables both - Read and Write - access types. The testers of this role can select this environment as a source and/or target environment on the TDM task.

- The **Number of Entities** must be set together with each access type. This is the maximum number of entities to be processed by a task.  The Number of Entities is set on both access types: **Read** and **Write**.  It is possible to set a different number of entities on each access type. 

  **Example:**
  - Read's Number of Entities is 1000. Write's Number of Entities is 10. 
  - The user attached to this role can run the following tasks on this environment:
    - Select the environment as a source environment and create a task on up to 1000 entities.
    - Select the environment as a target environment and create a task on up to 10 entities.

  Click for more information about [setting the number of entities on a TDM task]. 

  ### Testers

- Attach testers to the environment's role.  The connection of a tester to a testing environment is established by connecting the tester to the environment's role.  

- A role can be attached to a selected list of testers or to all TDM users.

- Note that although a Role without testers is not usable, the **Testers** setting is optional to enable creating a roles and add them testers in a later stage.

  #### Adding all TDM Users to the Role

- You can make the role available for all TDM users by assigning the **ALL** option to the role.

- Click the **Testers** setting and select the **ALL** option.

  #### Adding all TDM Users to the Role

- Click the **Testers** setting and select one of the user in the list.

- Click again the **Testers** setting and select an additional user if needed.

**Notes:**

- A tester can be attached to one role only per environment. A tester cannot be attached to different roles in a given environment.
- If a tester is attached specifically to a role, this role overrides the **ALL** role for this tester.

### Role Permissions

A list of permissions that can be grant to the role if checked. You can check of one, several, or all permissions. Each role has the following permissions list:

##### **Ignore Test Connection**  

- the TDM tests the connections of the source and target environments in the beginning of the task execution.  If the connection's test  fails, the user is asked whether to ignore the failure and continue the execution or stopping the execution.  When this permission is unchecked, the task execution stops with failure when the connection's test fails without giving an option to ignore the failure and continue the execution.

##### **Delete Entity from Target** 

-  [Delete an entity] from the target testing environment by a [TDM Load task].  
- This permission relevant only when the role has a **Write** access.

##### Create Synthetic Data 

- [Create replicas] of a real entity into a testing environment by a [TDM Load task].  
- This permission relevant only when the role has a **Write** access.

##### Random Entity Selection

- [Randomly select entities] by a [TDM Load task].
- This permission relevant only when the role has a **Write** access.

##### Request up to Date Entities

- Ask to [sync the entities] from the source when executing the task. 

##### Refresh Reference Data

- Create TDM tasks to extract or load [Reference tables].

#####  Task scheduling 

- Add [scheduling settings] on the TDM task to automatically execute it based on the scheduling parameters.

##### Replace Sequences

- [Replacing the sequences] of the entities when loading them to the target environment.
- This permission relevant only when the role has a **Write** access.

##### Entity Versioning 

- Creating [Data Flux](/articles/TDM/tdm_overview/02_tdm_glossary.md#data-flux) tasks.



  [![Previous](/articles/images/Previous.png)](09_environment_window_summary_section.md)[<img align="right" width="60" height="54" src="/articles/images/Next.png">](11_environment_products_tab.md)