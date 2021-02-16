# Broadway Flows Implementation

The TDM library provides a set of generic flows that enable the creation of a TDM standard implementation just in a couple of minutes.  Do the below steps in order to create a TDM standard implementation using the generic flows.

Note that after the below steps are executed and the standard implementation is created, all the flows can be edited and tailored per your project's specific requirements.

## How Do I Create TDM Broadway Flows?

### Step 1 - Define Tables to Filter Out

A preparation step that must be performed prior to starting the TDM implementation process is to define the tables to be filtered out from the TDM load to target process. The library includes a definition of the following auxiliary tables that must be filtered:

![image](images/11_tdm_impl_actor_1.PNG)

This definition is done using the **TDMFilterOutTargetTables** Actor. If you need more tables to be filtered out from the TDM load, edit the Actor's definition. 

To do so, open the **TDMFilterOutTargetTables** Actor and edit its table input argument. The **lu_name** column should be populated as follows:

* ALL_LUS - when a table is relevant for all TDM's Logical Units.
* [LU name] - when a table belongs to a specific LU.

![image](images/11_tdm_impl_actor_2.PNG)



### Step 2 - Create Load and Delete Flows

Now you are ready to create your TDM implementation using the library flows. Do it by running the generic **createFlowsFromTemplates.flow** from the Shared Objects Broadway folder. The flow is comprised of the following inner flows:

1. #### Create a LOAD flow per table

Performed by the **createLoadTableFlows.flow** that receives the Logical Unit name, target interface and target schema and retrieves the list of tables from the LU's Schema. Then for each one of the tables, it creates a Broadway flow to load the data into this table in the target DB. The name of each of the newly creates flows is **load_[Table Name].flow**, for example load_Customer.flow. The tables defined in Step 2 are filtered out and the flow is not created for them. 

2. #### Create the main LOAD flow

Performed by the **createLoadAllTablesFlow.flow** that receives the Logical Unit name and creates an envelope **LoadTables.flow** Broadway flow. The purpose of this flow is to invoke all the LOAD flows based on the LU's Schema execution order.

3. #### Create a DELETE flow per table

Performed by the **createDeleteTableFlows.flow** that receives the Logical Unit name, target interface and target schema and retrieves the list of tables from the LU's Schema. Then for each one of the tables, it creates a Broadway flow to delete the data from this table in the target DB. The name of each of the newly creates flows is **delete_[Table Name].flow**, for example delete_CUSTOMER.flow. The tables defined in Step 2 are filtered out and the flow is not created for them. 

The following two updates must be performed manually:

* Populate the **sql** input argument of **Get Table Data** Actor with the SELECT query that retrieves they keys of the data to be deleted. For example, in the delete_ADDRESS.flow you can write the following query because CUSTOMER_ID is the key of ADDRESS table.

  ~~~sql
  SELECT CUSTOMER_ID FROM TAR_CUSTOMER;
  ~~~

  ![images](images/11_tdm_impl_delete1.PNG)

* Populate the **keys** input argument of the **DbDelete** Actor. These should correlate with the table's key.

  ![images](images/11_tdm_impl_delete2.PNG)



4. #### Create the main DELETE flow

Performed by the **createDeleteAllTablesFlow.flow** that receives the Logical Unit name and creates an envelope **DeleteAllTables.flow** Broadway flow. The purpose of this flow is to invoke all the DELETE flows in the order opposite to the population order, considering the target DB's foreign keys. 


### Step 3 - Create the TDMOrchestrator.flow from Template

Once all LOAD and DELETE flows are ready, you need to create an orchestrator. The purpose of the **TDMOrchestrator.flow** is to encapsulate all Broadway flows of the TDM task. It includes the invocation of all steps such as:

* Initiate of the TDM load.
* Delete the target data, if required by the task's [operation mode](/articles/TDM/tdm_gui/19_load_task_request_parameters_regular_mode.md#operation-mode) or the [Data Flux load task](/articles/TDM/tdm_gui/20_load_task_dataflux_mode.md[).
* Load the new data into the target, if required by the task's [operation mode](/articles/TDM/tdm_gui/19_load_task_request_parameters_regular_mode.md#operation-mode) or the [Data Flux load task](/articles/TDM/tdm_gui/20_load_task_dataflux_mode.md). 
* Manage the TDM process as one transaction.
* Perform the [error handling and the statistics gathering](12_tdm_error_handling_and_statistics.md). 

The **TDMOrchestrator.flow** should be created from the Logical Unit's Broadway folder using a template as follows:

![image](images/11_tdm_impl_02.PNG)

### Step 4 - Create the Sequence Creation Flows

The sequences are required when populating the target DB, thus the sequences definition and initiation is a mandatory part of the TDM implementation creation. These flows need to be defined in the Shared Objects of your project since they need to be available across various Logical Units. 

The examples of sequence initiation flow can be found in the TDM demo project. 

Each sequence initiation flow must include the steps of getting the task execution ID and the original IID from the Fabric, retrieving the next sequence value and populating the TDM_SEQ_MAPPING table. You need to create a flow per each table in your LU's schema. 

[Click for the Sequence Implementation Guidelines](/articles/19_Broadway/actors/08_sequence_implementation_guide.md). 

To create a sequence initiation flow, do the following:

1. Create a flow per each table in your LU's Schema, using the following pattern:

   * Get task execution ID, original IID and LU Type from the session.

   * Get the sequence value using the **MaskingSequence** Actor and setting its input arguments per the project requirements.

     [Click to learn how to set the input arguments of the MaskingSequence Actor](/articles/19_Broadway/actors/07_masking_and_sequence_actors.md#how-do-i-set-masking-input-arguments).

   * Populate the TDM_SEQ_MAPPING table for reporting purpose.

   ![image](images/11_tdm_impl_03.PNG)

2. Save the flow. Then save it as Actor, in order to be able to invoke the flow as [Inner Flow](/articles/19_Broadway/22_broadway_flow_inner_flows.md#save-as-actor).

3. Edit the Load flow of the related table. For example, create a sequence initiation flow for the Payment table. Then edit the **load_PAYMENT.flow** by adding the sequence flow to the **Transformation** Stage and connecting its input and output arguments to the relevant columns.

   ![image](images/11_tdm_impl_04.PNG)



### Step 5 - Mask the Sensitive Data

TDM systems often handle sensitive data. To be compliant with Data Privacy laws, Fabric provides an ability to mask sensitive fields like SSN, credit card numbers and email addresses before they are loaded either to the Fabric or into the target DB.

* To mask a sensitive field prior to loading it into Fabric, create a Broadway population flow for the table that includes this field and use one of the **Masking** Actors. 

  ![image](images/11_tdm_impl_05.PNG)

* To mask a sensitive field as part of the load to the target DB, add a Masking Actor to the relevant **load_[Table Name].flow**. However the TDM infrastructure controls enabling or disabling of the masking based on the settings of the global variables. There are three possible scenarios of masking handling:

  * When the TDM task is for the synthetic data creation, the masking is always enabled.
  * When The TDM task is for Data Flux, the masking is always disabled.
  * In all other cases the masking behavior depends on the setting of the MASK_FLAG.

[Click to learn how to use the Masking Actors](/articles/19_Broadway/actors/07_masking_and_sequence_actors.md#).



[![Previous](/articles/images/Previous.png)](10_tdm_generic_broadway_flows.md)[<img align="right" width="60" height="54" src="/articles/images/Next.png">](12_tdm_error_handling_and_statistics.md)



