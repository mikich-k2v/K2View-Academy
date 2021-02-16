# Fabric TDM Library

The TDM Library contains all the utilities required to implement a TDM project and to run TDM execution processes.  It holds the following:

- [Shared Objects](#tdm-library---shared-objects).
- [TDM LU](#tdm-lu).
- [TDM_LIBRARY LU](#tdm_library-lu).

Note that the TDM Library must be imported to the Fabric project created for TDM.

## TDM Library - Shared Objects

### TDM Web Services

Import and deploy the Web Services to Fabric and then define the **tdm-WS** token in Fabric for the WS.

Note that it is recommended to add the project's Web Services to a separate category to simplify upgrading the TDM version since the TDM category contains the product's Web Services.

### Generic TDM Interfaces

Import and deploy the following [interfaces](/articles/05_DB_interfaces/01_interfaces_overview.md) into the project's **Shared Objects**:
-  **DB_CASSANDRA**, the connection to the Cassandra DB.  This interface is used by TDM utilities. Edit the IP address according to the environment.
-  **TDM**, the connection to the [TDM PosgreSQL DB](/articles/TDM/tdm_architecture/02_tdm_database.md). Edit the IP address according to the environment.
-  **FabricRedis**, the [Redis interface](/articles/24_non_DB_interfaces/09_redis_interface.md) that connects to the environment's **Redis** storage. Edit the IP address and populate it with the IP address of the TDM server. 

### Shared Globals

Import the list of shared [global variables](/articles/08_globals/01_globals_overview.md) required to execute TDM on your project.

### Shared Functions

TDM shared functions are saved in the **TDM** [Logic file](/articles/04_fabric_studio/09_logic_files_and_categories.md). 

Import the TDM shared functions to your project. Note that it is recommended to add the project's shared functions to a separate category (Logic file) to simplify upgrading the TDM version since the TDM category contains the product's functions.

### Shared Translations

<table width="900pxl">
<tbody>
<tr>
<td valign="top" width="200pxl">
<p><strong>Item&nbsp;</strong></p>
</td>
<td valign="top" width="300pxl">
<p><strong>Description&nbsp;</strong></p>
</td>
<td valign="top" width="400pxl">
<p><strong>Instructions&nbsp;</strong></p>
</td>
</tr>
<td valign="top" width="200pxl">
<p><h4>trnMigrateList</p>
</td>
<td valign="top" width="300pxl">
<p>Define the query and interface name to run the <strong>extract task</strong> on all entities of each LU. One record per LU.</p>
</td>
<td valign="top" width="400pxl">
<p>Populate this translation for each Logical Unit. A separate record must be created for each Logical Unit in the Fabric project apart from TDM, TDM_LIBRARY and the dummy LU of the post-execution processes. &nbsp;</p>
<p>If there is a need to define a query per source environment, populate the source environment name and create a separate record for each Logical Unit and source_env_name combination. Otherwise, leave the source environment empty.</p>
  <p><strong>Example 1:</strong></p>
  <ul><li>LU_NAME= ORDER</li>
    <li>SOURCE_ENV_NAME = ENV1</li>
    <li>INTERFACE_NAME = TDM</li>
<li>IG_SQL = Select lu_type2_eid from tdm_lu_type_relation_eid where lu_type_2 = &lsquo;ORDER&rsquo; and source_env = 'ENV1';</li></ul>
  <p><strong>Example 2:</strong></p>
  <ul><li>LU_NAME= CUSTOMER</li>
    <li>SOURCE_ENV_NAME is empty</li>
    <li>INTERFACE_NAME = CRM_DB</li>
    <li>IG_SQL = Select customer_id from customer limit 1000;</li></ul>
</td>
</tr>
<tr>
<td valign="top" width="200pxl">
<p><h4>trnMigrateListQueryFormats</p>
</td>
<td valign="top" width="300pxl">
<p>Supports special syntax for <strong>extract tasks </strong>when creating the LU instance query based on the trnMigrateList translation. Each LUI consists of a concatenation of source environment, IID, version name and version datetime.</p>
<p>Click to read more about <a href="01_tdm_set_instance_per_env_and_version.md">LUI structure for TDM implementation</a>.</p>
<p>This translation is required for DBs that do not support the standard &lsquo;||&rsquo; syntax for concatenated strings. For example, sqlServer.</p>
</td>
<td valign="top" width="400pxl">
<p>Populate two records for each DB, one record with version_ind&nbsp;&lsquo;true&rsquo; and another with&nbsp;version_ind&nbsp;&lsquo;false&rsquo;.&nbsp;</p>
  <p><strong>Example 1:</strong> </p>
<ul> <li>interface_type = sqlserver </li>
<li>version_ind = true </li>
<li>query_format = CONCAT(&lt;source_env_name&gt;,'_',&lt;entity_id&gt;,'_',&lt;task_name&gt;,'_',&lt;timestamp&gt;)</li>
</ul>
<p><strong> Example 2:</strong></p>
<ul><li>interface_type = sqlserver </li>
<li>version_ind = false </li>
<li>query_format = CONCAT(&lt;source_env_name&gt;,'_',&lt;entity_id&gt;)</li>
  </ul>
</td>
</tr>
<tr>
<td valign="top" width="200pxl">
<p><h4>trnRefList</p>
</td>
<td valign="top" width="300pxl">
<p>Define the list of available reference tables for <strong>extract tasks</strong>.</p>
</td>
<td valign="top" width="400pxl">
<p>Populate this translation for each reference table. A separate record must be created for each reference table. Set the LU name on each record.</p>
</td>
</tr>
<tr>
<td valign="top" width="200pxl">
<p><h4>trnPostProcessList</p>
</td>
<td valign="top" width="300pxl">
<p>Define the list of post-processes to run at the end of the task's execution. For example, a process that sends a mail to notify the user when the task's execution ends.</p>
<p>Each process is implemented as a Broadway flow.</p>
</td>
<td valign="top" width="400pxl">
<p>Populate the list of Broadway flows and the LU of the Broadway flow. The LU can be empty if the post processes are defined under the Shared Objects. In this case the TDM task execution process will set the LU name parameter to TDM when running the BATCH commands to execute the post execution processes. </p>
</td>
</tr>
<tr>
<td valign="top" width="200pxl">
<p><h4>trnTDMCleanUp</p>
</td>
<td valign="top" width="300pxl">
<p>Define the list of the TDM DB tables that need to be cleaned by the <a href= "articles/TDM/tdm_architecture/06_tdmdb_cleanup_process.md">TDM clean-up process</a>. The translation defines the Delete statement on each table and a clean-up indicator to indicate if the table needs to be cleaned by the TDM clean-up process.</p>
</td>
<td valign="top" width="400pxl">
  <p>Clear the <strong>cleanup_ind</strong> to remove a table from the clean-up process. It is also possible to add TDM tables or edit the Delete statements on the tables if needed. </p>
</td>
</tr>
</tbody>
</table>


### Broadway Generic Flows and Templates

The Fabric TDM library includes a set of built-in generic Broadway flows defined for easy adaptation of the TDM generic implementation per the specific data model. 

Click for more information about the [TDM Generic Broadway Flows](10_tdm_generic_broadway_flows.md).

## TDM LU

The TDM Logical Unit must be deployed to the Fabric project. It has the following tasks:

- Saves information about executed TDM tasks. The TDM GUI provides execution statistics and reports based on the data in the TDM LU. The LUI of the TDM LU is a unique task_Execution_id generated by the TDM GUI for each executed task. 
- Task execution utilities are defined and run under the TDM LU.
- The TDM cleanup job that cleans the TDM DB and is defined under the TDM LU. 


## TDM_LIBRARY LU

The TDM_LIBRARY LU holds utilities that must be copied to the project's LUs, as follows:

### Globals

- LU level [Globals](/articles/08_globals/01_globals_overview.md). Populate the **ROOT_TABLE_NAME**  Global using the main source table or tables. Several source tables can be populated when separated by a comma. For example: CUSTOMER, ACCOUNT.
- The **fnCheckInsFound** [enrichment function](/articles/10_enrichment_function/01_enrichment_function_overview.md) (attached to the root LU table) validates the source data and verifies that the entity (IID) exists in the main source tables. If the entity is not found in the main source tables, this function throws an Exception and the entity is rejected.

### LU Tables

- **FABRIC_TDM_ROOT**, the Root table of each LU. This table contains the following columns:

  - K2_TDM_EID, populated by the LU instance ID. 
  - IID, populated by the entity ID without the concatenation of the source environment, version name and version datetime.
  - SOURCE_ENV, populated by the source environment name of the TDM task.
  - TASK_NAME, version name. Populated by a [DataFlux](/articles/TDM/tdm_overview/02_tdm_glossary.md#data-flux) task by the task name.
  - TIMESTAMP, version datetime. Populated by a [DataFlux](/articles/TDM/tdm_overview/02_tdm_glossary.md#data-flux) task. 

  **Example:** 

  <table width="900pxl">
  <tbody>
  <tr>
  <td valign="top" width="200pxl">
  <p><strong>K2_TDM_EID</strong></p>
  </td>
  <td valign="top" width="100pxl">
  <p><strong>IID</strong></p>
  </td>
  <td valign="top" width="200pxl">
  <p><strong>SOURCE_ENV</strong></p>
  </td>
  <td valign="top" width="200pxl">
  <p><strong>TASK_NAME</strong></p>
  </td>
  <td width="200pxl" valign="top">
  <p><strong>TIMESTAMP</strong></p>
  </td>
  </tr>
  <tr>
  <td valign="top" width="200pxl">
  <p>PROD_1</p>
  </td>
  <td valign="top" width="100pxl">
  <p>1</p>
  </td>
  <td valign="top" width="200pxl">
  <p>PROD</p>
  </td>
  <td valign="top" width="200pxl">
  <p>&nbsp;</p>
  </td>
  <td width="200pxl" valign="top">
  <p>&nbsp;</p>
  </td>
  </tr>
  <tr>
  <td valign="top" width="200pxl">
  <p>PROD_1_copyCust_20201105090000</p>
  </td>
  <td valign="top" width="100pxl">
  <p>1</p>
  </td>
  <td valign="top" width="200pxl">
  <p>PROD</p>
  </td>
  <td valign="top" width="200pxl">
  <p>copyCust</p>
  </td>
  <td width="200pxl" valign="top">
  <p>20201105090000</p>
  </td>
  </tr>
  </table>

- **LU_PARAMS**, parameters table.  Must be added to each LU schema even when it is not required for defining parameters on the LU whereby the LU_PARAM table only holds the ENTITY_ID and SOURCE_ENVIRONMENT fields.

  Click for more information about [TDM parameters handling](/articles/TDM/tdm_implementation/07_tdm_implementation_parameters_handling.md).

- **TDM_LU_TYPE_RELATION_EID** and **TDM_LU_TYPE_REL_TAR_EID**, TDM relationship tables that map the parent to child IDs. Note that these tables are also created in the TDM DB.

  Click for more information about [TDM Hierarchy implementation](/articles/TDM/tdm_implementation/06_tdm_implementation_support_hierarchy.md).

- **INSTANCE_TABLE_COUNT**, this table holds the number of records populated on each LU table and is used to populate the [TDM execution Report](). 

### LU Level Translations

<table width="900pxl">
<tbody>
<tr>
<td valign="top" width="200pxl">
<p><strong>Item</strong></p>
</td>
<td valign="top" width="300pxl">
<p><strong>Description&nbsp;</strong></p>
</td>
<td valign="top" width="400pxl">
<p><strong>Instructions&nbsp;</strong></p>
</td>
</tr>
<tr>
<td valign="top" width="200pxl">
<p><h4>trnChildLink</p>
</td>
<td valign="top" width="300pxl">
<p>Translation for mapping parent and child IDs.&nbsp;</p>
<p>Click for more information about <a href="/articles/TDM/tdm_overview/03_business_entity_overview.md">TDM business entities</a> and how to <a href="/articles/TDM/tdm_implementation/06_tdm_implementation_support_hierarchy.md">support a hierarchy</a> when implementing the LUs.</p>
</td>
<td valign="top" width="400pxl">
<p>This translation must be added and populated on each <strong>parent LU</strong> and is used to populate TDM relationship tables. The child_lu field must be populated by the name of the child LU.</p>
<p>Both SQLs populated in child_lu_eid_sql and child_lu_tar_eid_Sql fields must run on the parent LU and get the source and target child IDs for each parent ID.</p>
<p><strong>Example:</strong><u><br /></u>Customer LU is the parent of the Orders LU. <br />trnChildLink of the Customer LU must be populated as follows:</p>
<ul>
<li><strong>Child_lu = </strong>Orders</li>
<li><strong>Child_lu_eid_sql = </strong>select order_id from subscriber</li>
<li><strong>Child_lu_tar_eid_sql = </strong>select order_id from tar_subscriber</li>    
</ul>
</td>
</tr>
<tr>
<td valign="top" width="200pxl">
<p><h4>trnLuParams</p>
</td>
<td valign="top" width="300pxl">
<p>Translation for the population of the LU_PARAMS table.&nbsp;</p>
</td>
<td valign="top" width="400pxl">
<p>The COLUMN_NAME is populated by the name of the parameter and the SQL is populated by the SQL query that gets the values for the defined parameter.</p>
<p>Click for more information about <a href="/articles/TDM/tdm_implementation/07_tdm_implementation_parameters_handling.md">handling parameters</a>. </p>
</td>
</tr>
<tr>
<td valign="top" width="200pxl">
<p><h4>trnParsList</p>
</td>
<td valign="top" width="300pxl">
<p>Translation for splitting large files.&nbsp;</p>
</td>
<td valign="top" width="400pxl">
<p>Copy the translation to the LU if needed and populate it with the list of large parsers.&nbsp;</p>
</td>
</tr>
</tbody>
</table>



### Split Large Files

**parExecuteJob**, the main parser that runs other parsers and splits them to run in parallel. The **trnParsList** translation object holds the large parser names to be split. Copy this parser to the LU if needed. 



[![Previous](/articles/images/Previous.png)](03_tdm_fabric_implementation_flow.md)[<img align="right" width="60" height="54" src="/articles/images/Next.png">](05_tdm_lu_implementation_general.md)
