# TDM Parameters Handling

The TDM enables the user to select entities based on [predefined parameters] when creating a [load task]. The list of available parameters is displayed on the task's BE (Business Entity). A BE can have flat or hierarchical structure and each LU can have its own parameters list and its own [LU PARAMS table]. 

The entities selection on a TDM task selects a subset of **root entities**, but the parameters for selection  can be based on the child LU's parameters as well. Therefore, it is highly important to have the **linkage between the root entity and the children entities** when selecting entities based on parameters.

Clicking the ![parameters matched icon](/articles/TDM/tdm_gui/images/parameters_refresh_icon.png) in the [task window] invokes **wsGetNumberOfMatchingEntities** Fabric Web-Service (imported from the TDM Library) to for the number of root entities that match the selected parameters. The Web-Service generates a **MATERIALIZED VIEW** in the [TDM DB] on each combination of **BE and source environment**: 

 `lu_relations_<BE name>_<Source Environment Name>`

Each root entity ID is populated in one single record that contains all the related parameters and values of all the LUs. The select of matching entities runs on the **MATERIALIZED VIEW**.

This VIEW is refreshed by the [checkMigrateAndUpdateTDMDB](03_task_execution_processes.md#checkmigrateandupdatetdmdb-job) job refreshes the view to get the newly synched entities when updating extract tasks status to **completed**.

**Example:**

- Customer BE has four LUs:
  - Two **root LUs**: **Customer** and **Collection**.
  - **Customer** LU has two children LUs:
    - **Billing**
    - **Order**

- Even LU of the BE has its own LU_PARAMS table in the TDM DB.

- Customer #65 has the following children IDs:

  - **Billing LU**: #169, #170, #171, #172, and #173.
  - **Order LU**: #279, #280, #281, #282, #283, #284, and #285.

- Synching Customer ID #1 inserts the following record into **CUSTOMER_PARAMS** TDM DB table:

  <table width="950pxl">
  <tbody>
  <tr>
  <td width="100pxl"><strong>entity_id</strong></td>
  <td width="120pxl"><strong>source_environment</strong></td>
  <td width="120px"><strong>CUSTOMER.FIRST_NAME</strong></td>
  <td width="120px"><strong>CUSTOMER.LAST_NAME</strong></td>
  <td width="120px"><strong>CUSTOMER.LINE_NUMBER</strong></td>
  <td width="120px"><strong>CUSTOMER.NO_OF_OPEN_CASES</strong></td>
  <td width="120px"><strong>CUSTOMER.OPEN_CASE_DATE</strong></td>
  <td width="120px"><strong>CUSTOMER.NO_OF_SUBSCRIBERS</strong></td>
  </tr>
  <tr>
  <td width="100pxl">65</td>
  <td width="120px">SRC</td>
  <td width="120px">{"Maisie"}</td>
  <td width="120px">{"Berger"}</td>
  <td width="120px">{"719 764 1363","404 376 5891","(248) 143-7235","342-203-6253","+1 (929) 454-2178"}</td>
  <td width="120px">{"3"}</td>
  <td width="120px">{"2015-09-16 06:14:40","2016-01-13 04:27:36","2017-02-10 20:44:54"}</td>
  <td width="120px">{"5"}</td>
  </tr>
  </tbody>
  </table>

  

- Synching Collection ID #1 inserts the following records into **COLLECTION_PARAMS** TDM DB table:

  <table width="900pxl">
  <tbody>
  <tr>
  <td width="150pxl"><strong>entity_id</strong></td>
  <td width="150pxl"><strong>source_environment</strong></td>
  <td width="600pxl"><strong>COLLECTION.COLLECTION_STATUS</strong></td>
  </tr>
  <tr>
  <td width="150pxl">65</td>
  <td width="150pxl">SRC</td>
  <td width="600pxl">{"5","4","3","1","2"}</td>
  </tr>
  </tbody>
  </table>

  

- Synching Billing IDs #169, #170, #171, #172, and #173 inserts the following records into **BILLING_PARAMS** TDM DB table:

  <table width="950pxl">
  <tbody>
  <tr>
  <td width="100pxl"><strong>entity_id</strong></td>
  <td width="100pxl"><strong>source_environment</strong></td>
  <td width="200pxl"><strong>BILLING.BALANCE_AMOUNT</strong></td>
      <td width="125pxl"><strong>BILLING.NO_OF_OPEN_INVOICES</strong></td>
      <td width="125pxl"><strong>BILLING.VIP_STATUS</strong></td>
      <td width="125pxl"><strong>BILLING.TOTAL_PAYMENT_AMOUNT</strong></td>
      <td width="125pxl"><strong>BILLING.SUBSCRIBER_TYPE</strong></td>
  </tr>
  <tr>
  <td width="100pxl">169</td>
  <td width="100pxl">SRC</td>
  <td width="200pxl">{"214.0","16.0","351.0",
      "387.0","333.0","178.0",
   	"276.0","197.0","144.0",
      "308.0","30.0","154.0",
      "303.0","417.0","497.0",
      "257.0","61.0","317.0",
      "56.0","177.0"}</td>
  <td width="125pxl">{"2"}</td>
  <td width="125pxl">{"Gold"}</td>
  <td width="125pxl">{"3789"}</td>
  <td width="125pxl">{"2"}</td>
  </tr>
  <tr>
  <td width="100pxl">170</td>
  <td width="100pxl">SRC</td>
  <td width="200pxl">{"480.0","492.0","202.0",
      "499.0","207.0",
      "144.0","364.0"}</td>
  <td width="125pxl">{"2"}</td>
  <td width="125pxl">{"Silver"}</td>
  <td width="125pxl">{"824"}</td>
  <td width="125pxl">{"1"}</td>
  </tr>
  <tr>
  <td width="100pxl">171</td>
  <td width="100pxl">SRC</td>
  <td width="200pxl">{"304.0","475.0","68.0",
      "70.0","263.0","395.0",
      "216.0","406.0","301.0"}</td>
  <td width="125pxl">{"0"}</td>
  <td width="125pxl">{"Gold"}</td>
  <td width="125pxl">&nbsp;</td>
  <td width="125pxl">{"4"}</td>
  </tr>
  <tr>
  <td width="100pxl">172</td>
  <td width="100pxl">SRC</td>
  <td width="200pxl">{"378.0","108.0","329.0",
      "52.0","274.0","157.0",
      "93.0","488.0","497.0",
      "11.0","422.0","146.0",
      "240.0","268.0","42.0",
      "440.0","333.0","91.0",
      "377.0","204.0"}</td>
  <td width="125pxl">{"0"}</td>
  <td width="125pxl">{"Gold"}</td>
  <td width="125pxl">&nbsp;</td>
  <td width="125pxl">{"3"}</td>
  </tr>
  <tr>
  <td width="100pxl">173</td>
  <td width="100pxl">SRC</td>
  <td width="200pxl">{"50.0","467.0","188.0",
      "208.0","411.0","27.0",
      "168.0","393.0",
      "490.0","43.0"}</td>
  <td width="125pxl">{"1"}</td>
  <td width="125pxl">{"Platinum"}</td>
  <td width="125pxl">{"1898"}</td>
  <td width="125pxl">{"4"}</td>
  </tr>
  </tbody>
  </table>

- Synching Billing IDs #169, #170, #171, #172, and #173 inserts the following records into **ORDER_PARAMS** TDM DB table:

  <table width="900pxl">
  <tr>
  <td width="225pxl"><strong>entity_id</strong></td>
  <td width="225pxl"><strong>source_environment</strong></td>
  <td width="225pxl"><strong>ORDERS.ORDER_TYPE</strong></td>
  <td width="225pxl"><strong>ORDERS.ORDER_STATUS</strong></td>
  </tr>
  <tr>
  <td width="225pxl">279</td>
  <td width="225pxl">SRC</td>
  <td width="225pxl">{"Device"}</td>
  <td width="225pxl">{"New"}</td>
  </tr>
  <tr>
  <td width="225pxl">280</td>
  <td width="225pxl">SRC</td>
  <td width="225pxl">{"Network"}</td>
  <td width="225pxl">{"Closed"}</td>
  </tr>
  <tr>
  <td width="225pxl">281</td>
  <td width="225pxl">SRC</td>
  <td width="225pxl">{"Billing"}</td>
  <td width="225pxl">{"Closed"}</td>
  </tr>
  <tr>
  <td width="225pxl">282</td>
  <td width="225pxl">SRC</td>
  <td width="225pxl">{"Billing"}</td>
  <td width="225pxl">{"New"}</td>
  </tr>
  <tr>
  <td width="225pxl">283</td>
  <td width="225pxl">SRC</td>
  <td width="225pxl">{"Network"}</td>
  <td width="225pxl">{"Closed"}</td>
  </tr>
  <tr>
  <td width="225pxl">284</td>
  <td width="225pxl">SRC</td>
  <td width="225pxl">{"Billing"}</td>
  <td width="225pxl">{"In Progress"}</td>
  </tr>
  <tr>
  <td width="225pxl">285</td>
  <td width="225pxl">SRC</td>
  <td width="225pxl">{"Billing"}</td>
  <td width="225pxl">{"Closed"}</td>
  </tr>
  </table>

- The tester selects entities based on the following parameters:

  - NO_OF_OPEN_CASES > 0  AND VIP_STATUS = "Gold" AND ORDER_TYPE = "New"

- **wsGetNumberOfMatchingEntities** Fabric Web-Service generates a new **MATERIALIZED VIEW** in the TDM DB named **lu_relations_Customer_SRC**:

  <table width="2076">
  <tbody>
  <tr>
  <td width="173"><strong>customer_root_id</strong></td>
  <td width="173"><strong>BILLING.BALANCE_AMOUNT</strong></td>
  <td width="173"><strong>BILLING.NO_OF_OPEN_INVOICES</strong></td>
  <td width="173"><strong>BILLING.SUBSCRIBER_TYPE</strong></td>
      <td width="173"><strong>BILLING.TOTAL_PAYMENT_AMOUNT</strong></td>
      <td width="173"><strong>BILLING.VIP_STATUS</strong></td>
      <td width="173"><strong>CUSTOMER.FIRST_NAME</strong></td>
      <td width="173"><strong>CUSTOMER.LAST_NAME</strong></td>
      <td width="173"><strong>CUSTOMER.LINE_NUMBER</strong></td>
      <td width="173"><strong>CUSTOMER.NO_OF_OPEN_CASES</strong></td>
      <td width="173"><strong>CUSTOMER.NO_OF_SUBSCRIBERS</strong></td>
      <td width="173"><strong>CUSTOMER.OPEN_CASE_DATE</strong></td>
  </tr>
  <tr>
  <td>65</td>
  <td width="173">{214.0,16.0,351.0, <br />&nbsp;387.0,333.0,178.0,<br />&nbsp;276.0,197.0,144.0, <br />&nbsp;308.0,30.0,154.0,<br />&nbsp;303.0,417.0,497.0,<br />&nbsp;257.0,61.0,317.0, <br />&nbsp;56.0,177.0,480.0,<br />&nbsp;492.0,202.0,499.0,<br />&nbsp;207.0, 144.0,364.0, <br />&nbsp;304.0,475.0,68.0, <br />&nbsp;70.0,263.0,395.0, <br />&nbsp;216.0,406.0,301.0, <br />&nbsp;378.0,108.0,329.0, <br />&nbsp;52.0,274.0,157.0, <br />&nbsp;93.0,488.0,497.0, <br />&nbsp;11.0,422.0,146.0, <br />&nbsp;240.0,268.0,42.0, <br />&nbsp;440.0,333.0,91.0,<br />&nbsp;377.0,204.0,50.0,<br />&nbsp;467.0,188.0,208.0,<br />&nbsp;411.0,27.0, 168.0,<br />&nbsp;393.0, 490.0,43.0}</td>
  <td>{2,0,1}</td>
  <td>{2,1,4,3,4}</td>
  <td>{3789,824,1898}</td>
  <td>{Gold,Silver,Platinum}</strong></td>
  <td>{Maisie}</td>
  <td>{Berger}</td>
  <td>{719 764 1363,404 376 5891,(248) 143-7235,342-203-6253,+1 (929) 454-2178}</td>
  <td>{3}</td>
  <td>{5}</td>
  <td>{2015-09-16 06:14:40,2016-01-13 04:27:36,2017-02-10 20:44:54}</td>
  </tr>
  </tbody>
  </table>

   

  

  [![Previous](/articles/images/Previous.png)](06_tdmdb_cleanup_process.md)[<img align="right" width="60" height="54" src="/articles/images/Next.png">]()

  

    

  

  

  
