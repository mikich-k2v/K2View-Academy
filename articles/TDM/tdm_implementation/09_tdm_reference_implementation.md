# TDM - Reference Implementation

TDM enables the user to extract Reference tables from several source environments and save them into Cassandra DB. 

In addition it enables to save different versions on given Reference table and source environment into Cassandra DB.

You can later create and execute TDM load tasks to copy the Reference tables from Cassandra DB to your target environment. 

The TDM implementation contains the following steps:

### Step 1 - Populate trnRefList Translation

The list of Reference tables available for [TDM extract tasks](/articles/TDM/tdm_gui/24_task_reference_tab.md#reference-tab---extract-task) is populated in the [trnRefList](04_fabric_tdm_library.md#trnreflist) translation object. Populate trnRefList by the list of available Reference tables for each LU. The following settings must be populated on each record:

- **lu_name** - populated by the LU name
- **ID**- populated by a sequence
- **reference_table_name** - populated by the Reference table
- **schema_name** - populated by the source DB schema name where the Reference table is stored
- **interface_name** - the Reference table's source interface
- **target_schema_name** - populated by the target DB schema name where the Reference table is stored
- **target_interface_name** - the Reference table's target interface name. 

See example:

<table width="900pxl">
<thead>
<tr>
<td colspan="2" width="169">
<p><strong>Input</strong></p>
</td>
<td colspan="5" width="436">
<p><strong>Output</strong></p>
</td>
</tr>
<tr>
<td width="127">
<p><strong>lu_name</strong></p>
</td>
<td width="42">
<p><strong>ID</strong></p>
</td>
<td width="199">
<p><strong>reference_table_name</strong></p>
</td>
<td width="125pxl">
<p><strong>schema_name</strong></p>
</td>
<td width="150pxl">
<p><strong>interface_name</strong></p>
</td>
<td width="125pxl">
<p><strong>target_schema_name</strong></p>
</td> 
<td width="150pxl">
<p><strong>target_interface_name</strong></p>
</td>
</tr>
</thead>
<tbody>
<tr>
<td width="127">
<p>Customer</p>
</td>
<td width="42">
<p>1</p>
</td>
<td width="199">CUSTOMER_TYPE</td>
<td width="124">CUST</td>
<td width="112">CRM_DB</td>
<td width="124">TAR_CUST</td>
<td width="112">CRM_DB</td>    
</tr>
<tr>
<td width="127">
<p>Customer</p>
</td>
<td width="42">
<p>2</p>
</td>
<td width="199">ADDRESS_ZIP_CODES</td>
<td width="124">CUST</td>
<td width="112">CRM_DB</td>
<td width="124">TAR_CUST</td>
<td width="112">CRM_DB</td>     
</tr>
<tr>
<td width="127">
<p>Billing</p>
</td>
<td width="42">
<p>3</p>
</td>
<td width="199">BILL_TYPE</td>
<td width="124">BILL</td>
<td width="112">BILLING_DB</td>
<td width="124">TAR_BILL</td>
<td width="112">BILLING_DB</td>    
</tr>
</tbody>
</table> 

### Step 2 - Creating Cassandra Tables for the Reference Tables

Run [fnValidateAndRebuildRefTables](/articles/TDM/tdm_architecture/05_tdm_reference_processes.md#tdm-lu---fnvalidateandrebuildreftables-job)  job to create an empty Cassandra table for each Reference table in **trnRefList**. The tables are created in  **k2view_tdm** keyspace.

### Step 3 - Create and Execute TDM Extract Tasks

TDM extract tasks store the selected Reference data in the related Cassandra DB table.

Click for more information how the [TDM stores the Reference tables in Cassandra DB](/articles/TDM/tdm_architecture/05_tdm_reference_processes.md#reference-cassandra-table).

### Step 4 - Create and Execute TDM Load Tasks

The TDM GUI enables creating [TDM load tasks](/articles/TDM/tdm_gui/24_task_reference_tab.md#reference-tab---load-task) to copy Reference tables that have been successfully extracted to Cassandra DB. The execution of the load task runs the **TDMReferenceLoader** Broadway flow to copy the task's reference tables to the target environment.

Click for more information about the [TDM generic Broadway flows](10_tdm_generic_broadway_flows).

[![Previous](/articles/images/Previous.png)](08_tdm_implement_delete_of_entities.md)[<img align="right" width="60" height="54" src="/articles/images/Next.png">](10_tdm_generic_broadway_flows.md)





