# TDM DB - General Parameters

The [tdm_general_parameters](/articles/TDM/tdm_architecture/02_tdm_database.md#tdm_general_parameters) TDM DB table holds the following parameters:

- [TDM Clean-up](/articles/TDM/tdm_architecture/06_tdmdb_cleanup_process.md) parameters. These parameters are automatically created in **tdm_general_parameters** by the TDMDB creation scripts.

- [LUI separator](/articles/TDM/tdm_implementation/01_tdm_set_instance_per_env_and_version.md#tdm-separator) parameters:

  - By default, the LUI separator is set to underscore. However, a different separator must be set on the LUIs if the source entity ID can contain underscore. 
  - For example, if the source Customer ID is 123_4, then the separator of the LUI must be different than underscore to enable the TDM process to parse the LUI correctly and get the correct Customer ID.
  - The **param_name** of the LUI separator is **iid_separator**.  The **param_value** needs to be populated by the String set as a separator.  
  - Note that the iid_separator setting impacts on all the project's LUs.

  

  **Example**:

  - Insert the following record to tdm_general_parameters to set the separator to @ : 

    ```sql
    insert into tdm_general_parameters (param_name, param_value) values ('iid_separator', '@');
    ```

  - The LUI of Customer 123_4 and environment ENV1 is **ENV1@123_4**.



[![Previous](/articles/images/Previous.png)](01_tdm_gui_configuration.md)[<img align="right" width="60" height="54" src="/articles/images/Next.png">](03_tdm_fabric_credentials.md)