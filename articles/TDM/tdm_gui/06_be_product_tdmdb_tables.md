# Business Entities and Products - TDM DB Tables

TDM settings are saved in the [TDM PostgreSQL DB](/articles/TDM/tdm_architecture/02_tdm_database.md). 

Business Entity (BE) and Product definitions update the following TDM DB tables:

### Business_Entities

This tables holds all [BEs](04_tdm_gui_business_entity_window.md) defined in the TDM GUI. 

-  A new record is created for each BE. 
-  Each BE is created in **Active** status and gets a unique **be_id** sequence which is the table's PK.

- Deleted BEs have an **Inactive** status and are not physically deleted from this table.

Note that to prevent creating several active BEs with the same name, the **be_name** column has a **unique index** when the status is **Active**.

### Products

This table holds all [Products](05_tdm_gui_product_window.md) defined in the TDM GUI.
-  A new record is created for each Product.  
-  Each Product is created in **Active** status and gets a unique **product_id** sequence which is the table's PK. 
-  **Deleted Products** have an **Inactive** status and are not physically deleted from this table.

Note that to prevent creating several active Products with the same name, the **product_name** column has a **unique index** when the status is **Active**. 

### Product_Logical_Units

This table holds the BE - LU - Product links, as follows:
- Holds the links of the LUs to each [BE](04_tdm_gui_business_entity_window.md).
- Holds the parent-child relationship of the LUs in a BE.
- Holds the link of the combined BE and LU to a product. Each BE and LU combination can be attached to a [Product](05_tdm_gui_product_window.md).

Adding an LU to a BE creates a new record in this table. Each record is marked by a unique **lu_id** sequence which is the table's PK. The table contains the following information:

- **LU information** - lu_id, lu_name, lu_description, and lu_dc_name columns. 
- **BE information** - be_id column. This is the link to the **business_entities** table.
- **LU relationship in the BE** - lu_parent_id and lu_parent_name columns holding the ID and name of the [parent LU](/articles/TDM/tdm_overview/03_business_entity_overview.md#building-an-lu-hierarchy-in-a-be) if it exists. 
- **Product information** - product_id and product_name columns. The product_id links to the **Products** table.  The product_id and product_name columns set to -1 and NULL default values when the record is created. Product information is set when the LU is attached to the Product. If the LU is deleted in the Product, the product columns return to their default values.

### TDM_BE_Post_Exe_Process

This table holds a list of [Post-Execution Processes](/articles/TDM/tdm_gui/04_tdm_gui_business_entity_window.md#post-execution-processes-tab) attached to each BE. A separate record is created for each post-execution process. Each record is marked with a unique **process_id** sequence which is the table's PK.

The following information is stored in this table:

- **Process Information** -  process_id, process_name, process_description and execution_order columns.
- **BE information** -  be_id column that links to the **business_entities** table.



  [![Previous](/articles/images/Previous.png)](05_tdm_gui_product_window.md)[<img align="right" width="60" height="54" src="/articles/images/Next.png">](07_tdm_gui_environment_overview.md)



