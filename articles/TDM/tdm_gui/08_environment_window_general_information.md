# Environment Window - General Information

The General Information section of the Environment Window holds the following information:  

Note that after editing the General Information section, click  **Save Changes**.

### Environment Name

Mandatory settings.

Populate the following settings:

- **TDM Environment Name**, environment name. When creating a TDM task, select the name of the source and target environments. It is recommended to set the same name in the  **TDM Environment Name** and **Fabric Environment Name** settings. 
- **Fabric Environment Name**, select the environments deployed to Fabric from the dropdown list. 

### Environment Additional Information

Optional settings:

- Description.
- Contact person settings.

### Environment Type

Mandatory setting. 

Set the environment type to one of the following:

- **Source** this can only be defined as a source environment in a TDM task. For example, in a Production environment a TDM task can extract entities but cannot insert entities.

- **Target**, this environment can only be used as a target environment in a TDM task.

- **Both**, this environment can be used as both a source and target environment in the TDM task. This mode is useful for [Data Flux tasks]. 

  Example: 

  - A tester backs up data in a testing environment before functional tests by creating and executing an [Extract Data Flux task] on the testing environment. The testing environment is set as a source environment. During theExtract task the data is saved in the TDM Fabric repository.
  - During functional tests the data in the testing environment becomes corrupted and the tester needs to replace it using the last backed up version created in the testing environment. The tester creates a [Load Data Flux task] and sets the testing environment to be both source and target. 

### Override Sync Mode

Optional setting. 

Override mode can be set if the **Environment Type** is **Source or Both**. This setting overrides the default Fabric [Sync mode](/articles/14_sync_LU_instance/02_sync_modes.md)  when extracting the selected entities from the source environment and sets another Sync mode which can be overridden on both the environment and [task] levels. 

The following values can be set in Override Sync Mode settings:

#### Do not Sync 

Do not sync the entities from the source when running a TDM task with the environment as a source, instead get the entities from Fabric. Note that if the entities do not exist in Fabric, the task's execution will return an error. This mode is needed when access to the source environment is limited by the organization.

**Example**:

- The Production team allocates a predefined window to extract a subset of entities from Production. Access to Production is restricted apart from a predefined window.
- An [Extract task] needs to be created and run to extract a large subset of entities from Production and to migrate them into Fabric. The **Override Sync Mode** in the **Production** TDM environment must be set to **Do not Sync** to avoid additional access to Production. Other TDM tasks in the Production source environment get the data entities from Fabric. 

#### Always Sync  

Always sync the entities from the source when running a TDM task with the environment as a source.  

Click for more information on [how overriding the sync mode impacts the task execution] process.

### Environment Owners

- Admin users can add or remove one or several environment owner users to/from the environment.  An environment owner user can be added to several environments.
- An environment owner user can be attached to an environment with tester permissions. For example, a user is attached to ENV1 as the environment owner and attached to ENV2 as a tester.
- The environment owner can edit the environment except for adding or removing environment owner users. Only Admin users can add or remove environment owners.
- The environment owner can create and execute TDM tasks on their environment without limitations, unlike test users who can define a task on the environment based on their permissions.

Click for more information about [environment roles and permissions].

#### Who can be an Environment Owner?  

Environment owner users are usually testing team leaders and must be defined under a dedicated group in the **LDAP** system.

The group name must be also defined in the **TDM GUI configuration file**: [config.js] in the **ownersGroupName** attribute.  This way the TDM GUI can enable adding only permitted users as environment owners.

Note that the TDM GUI installation includes an internal LDAP for development. The environment owners group name in the internal LDAP is **k2venvownerg**. Therefore the default value of the **ownersGroupName** attribute in the config.js file is **k2venvownerg**.

#### How Do I Add or Remove Environment Owners to an Environment? 

- Click the Environment Owners setting. A list of permitted users is displayed. Select one of the users in the list. 

- Click again the Environment Owners setting  and select one of the users from the list to set an additional environment owner.

- Click the X on the environment owner user name to remove this environment owner from the environment:

  ![env owner](images/environment_owners.png)





  [![Previous](/articles/images/Previous.png)](07_tdm_gui_environment_overview.md)[<img align="right" width="60" height="54" src="/articles/images/Next.png">](09_environment_window_summary_section.md)

