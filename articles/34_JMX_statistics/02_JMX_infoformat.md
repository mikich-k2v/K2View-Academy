## JMX Fabric Built-In Statistics

JMX statistics are displayed in a web page that presents information extracted from Fabric systems during runtime.



### Access JMX Statistics


1. Click the **Globe** icon in the top left corner of the **Fabric Studio** to access the Admin panel.

   <img src="/articles/34_JMX_statistics/images/JMX-pic2.png">

2.  Enter the **Admin credentials** and then click **Statistics** in the left panel.

   <img src="/articles/34_JMX_statistics/images/JMX-pic1.PNG">

The following statistics are displayed.
#### Processes

This section displays statistics about the **Loading phase** of each component running in the current session:
 
``` Fabric Launch Sequence ```
    

    since		56:38:23.041					Time in miliseconds since the event last occured
    timestamp	2020-12-10 12:34:39.733 UTC		The time, in miliseconds since 1970-1-1 00:00 UTC, this event last occured
    

```Loading Common Area```

    
    since		56:38:23.730					Time in miliseconds since the event last occured
    timestamp	2020-12-10 12:34:39.045 UTC		The time, in miliseconds since 1970-1-1 00:00 UTC, this event last occured



#### Actions

This section displays statistical information like project deployment or Fabric commands:

```Deployment count for a specific LU```


    count		1								The number of times this event has occured
    total		0:00:00.330						The accumulated total of this event value
    average		0:00:00.330						The average of this event value since the process was launched
    timestamp	2020-12-12 21:12:32.131 UTC		The time, in miliseconds since 1970-1-1 00:00 UTC, this event last occured 
    since		0:00:30.648 					Time in miliseconds since the event last occured
    



```Count of Fabric Commands Executed```

    
    count		22								The number of times this event has occured
    timestamp	2020-12-12 21:13:02.638 UTC		The time, in miliseconds since 1970-1-1 00:00 UTC, this event last occured
    since		0:00:00.141						Time in miliseconds since the event last occured
    



```GET```

    count		1								The number of times this event has occured
    timestamp	2020-12-12 21:12:54.676 UTC		The time, in miliseconds since 1970-1-1 00:00 UTC
    since		0:00:08.104						Time in miliseconds since the event last occured
    



#### Transactions

This section displays statistics about Fabric jobs, **get** performances, Web Services, LUI queries and LU population syncs:

``` GET Duration```

    last			0:00:00.408					The last value for this event
    average			0:00:00.408					The average of this event value since the process was launched
    count			1							The number of times this event has occured
    timestamp		2020-12-12 21:12:55.092 UTC	The time, in miliseconds since 1970-1-1 00:00 UTC
    since			0:00:07.689					Time in miliseconds since the event last occured
    total			0:00:00.408					The accumulated total of this event value

```Web Services Calls```

Statistics on executions and authentications are also provided.

    count				10							The number of times this event has occured
    total				0:00:04.684					The accumulated total of this event value
    average				0:00:00.468					The average of this event value since the process was launched
    timestamp			2020-12-12 21:13:02.642 UTC	The time, in miliseconds since 1970-1-1 00:00 UTC
    since				0:00:00.141					Time in miliseconds since the event last occured



#### Resources 

This section displays statistics about general information on system resources:

``` Number of LU in the systems```
 
    last			3								The last value for this event
    timestamp		2020-12-12 21:12:32.131 UTC		The time, in miliseconds since 1970-1-1 00:00 UTC
    since			0:26:17.201						Time in miliseconds since the event last occured
    



```Number of Active Cassandra Sessions```

    total			1								The accumulated total of this event value
    count			1								The number of times this event has occured
    timestamp		2020-12-10 12:34:35.294 UTC		The time, in miliseconds since 1970-1-1 00:00 UTC
    since			57:04:14.038					Time in miliseconds since the event last occured



#### MicroDBs

This section displays very useful information like the number of LUIs synced, fetch times and sizes:

```mdb Cache Count```

    last			3								The last value for this event
    timestamp		2020-12-12 21:38:39.802 UTC		The time, in miliseconds since 1970-1-1 00:00 UTC
    since			0:00:09.533						Time in miliseconds since the event last occured

```mdb Fetch Bytes```

    count			3								The number of times this event has occured
    average			53248 B							The average of this event value since the process was launched
    total			156 KB							The accumulated total of this event value
    timestamp		2020-12-12 21:38:39.794 UTC		The time, in miliseconds since 1970-1-1 00:00 UTC
    since			0:00:09.544						Time in miliseconds since the event last occured
   



[![Previous](/articles/images/Previous.png)](/articles/34_JMX_statistics/01_JMX_overview.md)[<img align="right" width="60" height="54" src="/articles/images/Next.png">](/articles/34_JMX_statistics/03_JMX_custom.md)
