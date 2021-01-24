# TDM LU Implementation - Generic Guidelines

A TDM task copies a selected [Business Entity](/articles/TDM/tdm_overview/03_business_entity_overview.md) from the selected source environment to the selected target environment. A Business Entity can have multiple [LUs](/articles/03_logical_units/01_LU_overview.md) with a flat or a hierarchical structure. For example, a Customer Business Entity can consist of Customer Care, Billing, Ordering and Usage LUs. The ability to break a BE up into several LUs enables maximum flexibility and avoiding duplicate development. In addition, defining a hierarchical structure of parent-child LUs enables creating LUs based on the natural root entity of the related data sources instead of forcefully setting unified root entities on all LUs related to a given BE.

Each LU in a TDM project must have additional components to support TDM functionality.

## LU Basic Structure

Every LU in the TDM project has the following structure:

- Dummy root table: FABRIC_TDM_ROOT. 

- TDM generic LU tables linked to the root table. 

- Two main branches linked to the root table:

  - **Source branch**, LU tables that extract the entity's source data.  The source LU tables are populated when the TDM task needs to copy (insert) the entities to the target environment and therefore needs to extract the source data of these entities.

  - **Target branch**, LU tables that extract the target keys of the entity. The keys are extracted from the target environment to enable a delete of the entity from the target environment if required by the TDM task.

    [Click for more information about delete entities from the target environment].

### Step 1 - Copy the Objects from the TDM_LIBRARY LU into Each LU

Import the [TDM_LIBRARY LU](/articles/TDM/tdm_implementation/04_fabric_tdm_library.md#tdm_library-lu) from the **TDM Library** to your project and copy the LU level objects in the TDM_LIBRARY to your LU.

### Step 2 - Add the TDM Root Table to the LU Schema

1. Add the **FABRIC_TDM_ROOT** LU table to the LU Schema and set it as a [Root table](/articles/03_logical_units/08_define_root_table_and_instance_ID_LU_schema.md). 

2.  Set the **Instance PK** column** to **k2_tdm_eid** and verify that the **fnCheckInsFound** enrichment function under Shared Objects is attached to the LU table. 
    This function runs if the TDM task inserts the entity to the target, and therefore must extract its data from the data source. It validates that the entity (IID) exists in the main source LU tables. If the entity is not found in the source table, reject the entity. 
3. Add the **LU_PARAMS**, **INSTANCE_TABLE_COUNT** , **TDM_LU_TYPE_RELATION_EID** and **TDM_LU_TYPE_REL_TAR_EID** to the LU Schema and link the tables to the **FABRIC_TDM_ROOT.IID** :

![tdm lu example](images/tdm_lu_example1.png)



4. Add the LU_PARAMS LU table to each LU Schema, even if it is not required for defining parameters on the LU, in which case the LU_PARAM table only holds the ENTITY_ID and SOURCE_ENVIRONMENT fields.

5. Edit **trnLuParams** and **LU_PARAMS** and add selection parameters to the LU. 

   Click for more information about [Handling TDM Parameters](07_tdm_implementation_parameters_handling.md).

6. Mask sensitive data on LU tables using a Broadway population and the [Masking Actor](/articles/19_Broadway/actors/07_masking_and_sequence_actors.md). 

   Click for more information about [TDM Masking].

### Step 3 - Add the Source LU Tables to the LU Schema

1. Link the main source LU tables to FABRIC_TDM_ROOT table. 

2. Verify that the main source LU tables are also populated in [ROOT_TABLE_NAME Global](/articles/TDM/tdm_implementation/04_fabric_tdm_library.md#globals).

3. The source LU tables need to be populated under the following conditions. The population of the main source tables must check these conditions: 

   - The TDM task requires to [copy (insert) the entities] to the target environment.
   - The user does not ask to [avoid synchronizing] the entities from the source.  

   Note that if the user asks to avoid synchronizing the data from the source, i.e. sets the Sync Mode to Off, and the LUI does not exist in Fabric yet (first sync), an Exception must be thrown, since the LUI data is not stored in Fabric and Fabric cannot extract the data of the source. 

4. Create the population of the main source LU tables based on [Root function](/articles/07_table_population/11_1_creating_or_editing_a_root_function.md). 

5.  Edit the Root function of the main source LU tables based on [TBD- add the template when its ready] template. The updated Root function checks the conditions above.  

6. Link the remaining source LU tables to the main LU tables. This way, when the main source LU table is not populated, the remaining source LU table remain empty are well.

### Step 4 - Add the Target LU Tables to the LU Schema

1. Define the LU tables to extract the target keys to enable a deleting of the entity from target if needed.

2. Link the main target LU table to FABRIC_TDM_ROOT table.

3. Add the following decision function to the main target root table: **fnDecisionDeleteFromTarget**. Note that this decision function is located under the Shared Objects and is imported from the [TDM Library](04_fabric_tdm_library.md).

4. Link the remaining target LU tables to the main target LU table.

   Click for more information about the [delete entities] from target environment by a TDM task.

### LU Debug

The LUI must include the source environment which must be set as the [active environment](/articles/25_environments/01_environments_overview.md) in Fabric. When debugging the TDM implementation on Fabric, the debug server either:

- Populates the source environment using `_dev_`. For example, **_dev_1**.
- Creates and deploys the environment to the Fabric Debug server, set the source environment as an active environment and concatenate this source environment to the Entity ID (IID). For example, **UAT_1**.  

[![Previous](/articles/images/Previous.png)](04_fabric_tdm_library.md)[<img align="right" width="60" height="54" src="/articles/images/Next.png">](06_tdm_implementation_support_hierarchy.md)
