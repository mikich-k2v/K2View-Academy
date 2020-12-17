## JMX Fabric Custom Statistics

Fabric has two Java methods for adding customized JMX probes to an implementation and to expose its values as JMX counters. 

### Fabric Statistics APIs

#### statsCount

This method can be invoked to count statistics like events, bytes and counts. 

```java
public static void statsCount(String entry, String key, long value)
```

```entry```, designates the primary key to implement the statistics.

`key`, designates the sub-key for the statistics.

`value`, the measured value of the statistics.

In this method, the value is used to calculate total, last and average values for this measurement. In addition, this function also counts the number of times the function has been called and provides a timestamp for the last call.

#### statsDuration

```java
public static AutoCloseable statsDuration(String entry, String key)
```

The purpose of this method is to measure the duration of the function's call between its invocation and the invocation of the ```.close()``` function on the return object.

`entry`, designates the primary key for the statistics.

`key`, designates the sub-key for the  statistics.

This method is returned by calling ```.close()``` on this object to indicate the end of the measurement's duration. 


### Code Example 

```java 
  public static String fnCustomStats() throws Exception { String status= "success";

	Db ci = db("fabric");
	
	String sql = "SELECT COUNT(*) NO_OF_INVOICES, STATUS FROM INVOICE group by status";
	
	Db.Rows rows = ci.fetch(sql);
	
	for (Db.Row row:rows){
	
		String invStatus = row.cell(1).toString();
		Long noOfInv=  Long.valueOf(row.cell(0).toString()).longValue();
	
	
		UserCode.statsCount("NoOfInvoices", invStatus, noOfInv);
	
		//Alternative syntax
		//CustomStats.count("NoOfInvoices", invStatus, noOfInv);
	
		AutoCloseable sw = statsDuration("tali", "test");
		sleep(10);
		sw.close();
	
                     //Alternative syntax
		//Stopwatch sw2 = CustomStats.duration("tali", "test");
		//sleep(10);
		//sw2.close();
	}
	
	return status;
}
```

[![Previous](/articles/images/Previous.png)](/articles/34_JMX_statistics/02_JMX_infoformat.md)
