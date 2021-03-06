![](/academy/Training_Level_1/03_fabric_basic_LU/images/example.png)

### Example - Keyspaces & Commands

 Let's look at our project and product keyspaces:

1. Run **describe keyspaces;**.

2. Check the name of the keyspace, created for Customer LU. In pronciple Fabric concatenates **k2view_** to the LU name. When deploying the LU to Fabric debug server, Fabric also concatenates the Fabric version and the project name to the keyspace of each LU. For example: k2view_test_cust_6_2_kb_fabric_project.

3. Change the keyspace scope to the Customer's keyspace by executing **use [customer keyspace name];**.

4. Let's review the entities in **[customer keyspace name].entity** using the following statement: 
   *select * from [customer keyspace name].entity;. 
   
   Note, you can also review the results from fabric executing the following:

   ```cql select * from [customer keyspace name].entity;``` 
   The results varies a bit ,  instead of a  huge blob  you'll be able to review the microDB file sizing.

```
|id |batch_id|chunks_count|data           |key_desc_id|schema_hash|sync_version |

+---+--------+------------+---------------+-----------+-----------+-------------+

|82 |        |1           |**BYTES[4568]**|0          |1024909903 |1592227429701|

|215|        |1           |**BYTES[2634]**|0          |1024909903 |1592227437514|
```

### ![](/academy/Training_Level_1/03_fabric_basic_LU/images/Exercise.png)Exercise – Keyspaces & Commands

1. `Question: Which Instance IDs are stored in k2view_customer?` `How will you list them?`
2. `Question: How will you list the LUTs that have been deployed?`






 

------
