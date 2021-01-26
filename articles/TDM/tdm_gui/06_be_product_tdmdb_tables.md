# Business Entities and Products - TDM DB Tables

The TDM settings are saved in the [TDM PostgreSQL DB](/articles/TDM/tdm_architecture/02_tdm_database.md). 

The Business Entity (BE)  and Product definitions update the following TDM DB tables:

### Business_Entities

This tables contains all the [BEs](/articles/TDM/tdm_gui/04_tdm_gui_business_entity_window.md) defined in the TDM GUI. A new record is created on each BE. Each BE is created with **Active status** and gets a unique sequence: **be_id**.  The be_id is the PK of this table.

**Deleted BEs** are not physically deleted from this table, but get **Inactive status**.

Note that there is a **unique index** on the **be_name** when the status is Active to disable creating several active BEs with the same  name.

### Products

This table contains all the [Products] defined in the TDM GUI. A new record is created on each Product. Each Product is created with **Active** status and gets a unique sequence: **product_id**. The product_id is the PK of this table. 

**Deleted Products** are not physically deleted from this table, but get **Inactive status**.

Note that there is a **unique index** on the **product_name** when the status is Active to disable creating several active Products with the same name.

### Product_Logical_Units

This table holds the BE - LU - Product links. 

The following information is stored in this table:

- Maps a list of LUs to each [BE].
- Maps the relationship of LUs in a BE.
- Maps the link of the combined BE and LU to a product. Each combination of BE and LU can be attached to a [Product].

Adding an LU to a BE creates a new record in this table. Each record is marked by a unique sequence: **lu_id**, This is the PK of the table. The table contains the following information:

- **LU information** - lu_id, lu_name, lu_description, and lu_dc_name columns. 
- **BE information** - be_id column.  This is the linkage to **business_entities** table.
- **LU relationship in the BE** - lu_parent_id and lu_parent_name columns  that hold the ID and name of the [parent LU](/articles/TDM/tdm_overview/03_business_entity_overview.md#building-an-lu-hierarchy-in-a-be) if exists. 
- **Product information** - product_id and product_name columns. The product_id is the linkage to **Products** table.  The product information is updated when the LU is attached to the Product. If the LU is not attached to a Product, the product_id is populated by -1 and the product_name is NULL.

### TDM_BE_Post_Exe_Process

This table holds the list of [Post Execution Processes](/articles/TDM/tdm_gui/04_tdm_gui_business_entity_window.md#post-execution-processes-tab) attached to each BE. A separate record is created on each post execution process. Each record is marked by a unique sequence: **process_id**. This is the PK of this table.

process_id bigint NOT NULL DEFAULT nextval('post_exe_process_id_seq'::regclass),
  process_name character varying(500),
  process_description character varying(500),
  be_id

The following information is stored in this table:

- **Process Information** - process_id, process_name, process_description, and execution_order columns.
- **BE information** -  be_id column.  This is the linkage to **business_entities** table.



  [![Previous](/articles/images/Previous.png)](05_tdm_gui_product_window.md)[<img align="right" width="60" height="54" src="/articles/images/Next.png">](07_tdm_gui_environment_window.md)



