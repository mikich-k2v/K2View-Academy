# TDM Fabric Implementation - Environments Setup

During the execution of a TDM task, data is extracted from a selected source environment and loaded into the selected target environments.
An environment can be defined as a source environment, target environment or both source and target environments. 

TDM environments must be defined in the following TDM layers:

- TDM GUI, define the TDM environment types, related products (systems), roles and permissions and additional settings. These definitions are kept in the [TDM DB](/articles/TDM/tdm_architecture/02_tdm_database.md).
- Fabric, define the TDM environment source and target and connection details of each environment. 

### Defining TDM Environments in Fabric

Fabric environments are used to run TDM processes on various environments by switching between them according to specific needs. The connection details of each environment's data sources are taken from the Fabric environment's data.

**Example:**

Running a TDM task to copy selected entities from the **Production** environment to the **UAT** environment. Fabric must extract the source data from Production and load it to UAT. Each environment can have different connection details for its data sources. 

The TDM execution process sets the active environment as follows:

1. Set the active environment to Production before synchronizing the entity from the data source.
2. Set the active environment to UAT before loading the entity to the target.

To save a separate LUI for each source environment, since the [TDM concatenates the source environment to each LUI](01_tdm_set_instance_per_env_and_version.md), the TDM implementation must include the creation and deployment of all the TDM environments with their connection details to enable the execution of the TDM tasks. 

Click for more information about [Fabric environments](/articles/25_environments/02_create_new_environment.md).
