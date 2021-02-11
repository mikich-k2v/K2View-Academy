# TDM Clean-Up Process

**TDMDB_CleanUp** job is defined in **TDM LU** to clean old Inactive records from the [TDM DB](02_tdm_database.md). 

The list of TDM tables for clean-up and the Delete statement are taken from [trnTDMCleanup](/articles/TDM/tdm_implementation/04_fabric_tdm_library.md#trntdmcleanup) shared translation. The clean-up process gets all translation records whose **cleanup_ind** setting is checked and runs the Delete statement on each table. 

The following clean-up parameters  are defined in [tdm_general_parameters](02_tdm_database.md#tdm_general_parameters):

- **cleanup_active_ind**: this parameter indicates if the TDM clean-up process is enabled or disabled. By default, this parameter is set to **true**. To disable the clean-up process on the TDM DB, set the parameter to **false**. 

- **cleanup_retention_period**: the number of months of the retention period of Inactive records. The clean-up process deletes Inactive records that are older than the retention period. By default, this value is set to 2, i.e. all Inactive records updated more than two months ago, will be deleted from the TDM DB by the cleanup process. 

  Update this parameter to set a different retention period.

### How do I Run the TDM Clean-Up Process?

By default, the **TDMDB_CleanUp** job is scheduled to run automatically every two days in the TDM Job's table. You can set it to run manually or set a different time interval for the automatic execution.

Click for more information about the [Jobs table](/articles/20_jobs_and_batch_services/03_create_a_new_user_job.md#step-4). 




  [![Previous](/articles/images/Previous.png)](05_tdm_ reference_processes.md)

  
