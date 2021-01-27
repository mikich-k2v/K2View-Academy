# Environment Window - General Information

The General Information of the environment can be edited. Click the **Save Changes** button to save the changes. The General Information section of the Environment Window holds the following information:

### Environment Name

Populate the following mandatory settings:

- **TDM Environment Name** - environment name. When creating a TDM task, you need to select source and target environments by their name. It is recommended to set the same name in both settings:  **TDM Environment Name** and **Fabric Environment Name**.
- **Fabric Environment Name** - select from the dropdown list of the the environments deployed to Fabric. 

### Environment Additional Information

Optional settings of the environments: 

- Description.
- Contact person settings.

### Environment Type

A mandatory setting. Set the environment type to one of the following:

- **Source** - environment that can only be used as a source environment in TDM task. For example, Production. It is possible to extract entities from Production, but the system must not allow to copy entities into the Production by the TDM.

- **Target** - environment that can only be used as a target environment in TDM task.

- **Both** - environment that can be used as both - source and target environment - in the TDM task. This mode is useful on [Data Flux tasks].

  Example: 

  - The tester backs up the testing environment data before starting the functional tests by creating and executing an [Extract Data Flux task] on the testing environment. The testing environment is set as a source environment on the Extract task and the data is being saved in the TDM Fabric repository.
  - The testing environment data gets corrupted during the functional tests and the tester needs to replace it by the latest version (backup), created on the testing environment. The user creates a [Load Data Flux task] and sets the testing environment to be both - source and target. 

### Override Sync Mode

An optional setting. Can be set if the **Environment Type** is **Source or Both**. This setting overrides the default [Sync mode](/articles/14_sync_LU_instance/02_sync_modes.md) of Fabric when extracting the selected entities from the source environment and set a different Sync mode. The Sync mode can be overridden on both levels: environment and [task]. 

The following values can be set in the Override Sync Mode setting:

#### Do not Sync 

Do not sync the entities from the source when running a TDM task with the environment as a source, but get the entities from Fabric. Note that if the entities do not exist in Fabric, the task execution will return an error. This mode is needed when the access to the source environment is limited by the organization.

**Example**:

- The Production team allocates a predefined window to extract a subset of entities from Production. The access to Production is restricted except the predefined window.
- It is needed to create and execute an [Extract task] to extract a large subset of entities from Production and migrate them into Fabric. Then the **Override Sync Mode** of the **Production** TDM environment must be set to **Do not Sync** to avoid an additional access to Production. Any additional TDM tasks with the Production source environment will get the entities data from Fabric. 

#### Always Sync  

Always sync the entities from the source when running a TDM task with the environment as a source.  

Click for more information how the [overriding of the sync mode impacts the task execution] process.

### Environment Owners

- Admin user can add or remove one or several environment owner users to the environment.  An environment owner user can be added to several environments.
- An environment owner user can still be attached to an environment with tester permissions. For example, a user is attached to ENV1 as environment owner and attached to ENV2 as a tester.
- The environment owner can edit the environment except adding or removing environment owners users. Only Admin users can add or remove environment owners.
- The environment owner can create and execute TDM tasks on their environment without limitations, unlike the test users that can define the task on the environment based on their permissions.

Click for more information about [environment roles and permissions].

#### Who is Entitled to be an Environment Owner?  

The environment owner users are usually the testing team leaders. These users must be defined under a dedicated group in the **LDAP** system.

The group name must be also defined in the **TDM GUI configuration file**: [config.js] in the **ownersGroupName** attribute.  This way the TDM GUI can enable adding only permitted users as environment owners.

Note that the TDM GUI installation includes an internal LDAP for development. The environment owners group name in the internal LDAP is **k2venvownerg**. Therefore the default value of the **ownersGroupName** attribute in the config.js file is **k2venvownerg**.

#### How Do I Add or Remove Environment Owners to an Environment? 

- Click the Environment Owners setting. A list of permitted users is displayed. Select one of the users in the list. 

- Click again the Environment Owners setting  and select one of the users from the list to set an additional environment owner.

- Click the X on the environment owner user name to remove this environment owner from the environment:

  ![env owner](images/environment_owners.png)





  [![Previous](/articles/images/Previous.png)](07_tdm_gui_environment_overview.md)[<img align="right" width="60" height="54" src="/articles/images/Next.png">](09_environment_window_summary_section.md)

