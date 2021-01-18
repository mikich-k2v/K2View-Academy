# TDM LU Implementation - Generic Guidelines

The TDM task copies a selected [Business Entity](/articles/TDM/tdm_overview/03_business_entity_overview.md) from the selected source environment to the selected target environment. A Business Entity can have multiple [LUs](/articles/03_logical_units/01_LU_overview.md)) with a flat or a hierarchical structure. For example, a Customer Business Entity can consist of Customer Care, Billing, Ordering and Usage LUs. The ability to break a BE up into several LUs enables maximum flexibility and avoiding duplicate development. In addition, defining a hierarchical structure of parent-child LUs enables creating LUs based on the natural root entity of the related data sources instead of forcefully setting unified root entities on all LUs related to a given BE.

Each LU in the TDM project must have additional components to support TDM functionality.

### Step 1 - Copy the Objects from the TDM_LIBRARY LU into each LU

Import the [TDM_LIBRARY LU](/articles/TDM/tdm_implementation/04_fabric_tdm_library.md#tdm_library-lu) from the **TDM Library** to your project and copy the LU level objects in the TDM_LIBRARY to your LU.

### Step 2 - Add the TDM LU Table to the LU Schema

- Add the **FABRIC_TDM_ROOT** LU table to the LU Schema and set it as a [Root table](/articles/03_logical_units/08_define_root_table_and_instance_ID_LU_schema.md). Set the **Instance PK Column** to **k2_tdm_eid** column. Verify that the **fnCheckInsFound** enrichment function under Shared Objects is attached to this LU table. This function runs if the TDM task needs to insert the entity to the target, and therefore needs to extract its data from the data source. It validates that the entity (IID) exists in the main source LU tables. If the entity is not found in the source table, reject the entity. 
- Add the **LU_PARAMS**, **INSTANCE_TABLE_COUNT** , **TDM_LU_TYPE_RELATION_EID** and **TDM_LU_TYPE_REL_TAR_EID** to the LU Schema. Connect these tables to the **FABRIC_TDM_ROOT.IID** :

![tdm lu example](images/tdm_lu_example1.png)



- The LU_PARAMS LU table must be added to each LU Schema, even when it is not required for defining parameters on the LU. In this case, the LU_PARAM table only contains the ENTITY_ID and SOURCE_ENVIRONMENT fields.

- Edit the **trnLuParams** and **LU_PARAMS** to add selection parameters to the LU. 

  Click for more information about [Handling TDM Parameters](07_tdm_implementation_parameters_handling.md).

- Sensitive data on LU tables must be masked using a Broadway population and the [masking actor](/articles/19_Broadway/actors/07_masking_and_sequence_actors.md). 

   Click for more information about [TDM Masking].

### LU Debug

The LUI must include the source environment which must be set as the [active environment](/articles/25_environments/01_environments_overview.md) of Fabric. When debugging the TDM implementation on Fabric debug server, either:

- Populate the source environment using `_dev_`. For example, **_dev_1**.
- Create and deploy the environment to the Fabric debug server, set the source environment as an active environment and concatenate this source environment to the Entity ID (IID). For example, **UAT_1**.  

[![Previous](/articles/images/Previous.png)](04_fabric_tdm_library.md)[<img align="right" width="60" height="54" src="/articles/images/Next.png">](06_tdm_implementation_support_hierarchy.md)
