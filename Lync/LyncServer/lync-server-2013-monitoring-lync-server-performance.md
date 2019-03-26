---
title: 'Lync Server 2013: Monitoring Lync Server performance'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Monitoring Lync Server 2013 performance
ms:assetid: 2acfd720-6120-4816-a2d4-30476bd5cd0e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn720910(v=OCS.15)
ms:contentKeyID: 63969592
ms.date: 01/27/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Monitoring Lync Server 2013 performance

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-05-15_

Lync Server 2013 performance is affected by various factors such as user profiles, system architecture, software, hardware components, third-party integration points such as gateways and telephony equipment, network connectivity and performance, Windows Active Directory service configuration and performance in addition to the Windows operating system functionality.

At the core of a Lync Server 2013 deployments’ performance is the server software and hardware it is implemented on. As an example, a front-end server must have sufficient hardware resources to cope with the expected (short-term) user load. If a respective front-end server is required to provide services to 10 thousand users, then an adequately configured server must meet the expected load requirements to ultimately help ensure the best possible end-user experience.

Monitoring server performance is therefore extremely important to gauge whether the implemented server infrastructure have suitable hardware resources for the day-to-day peak-load requirements. Monitoring server performance helps identify system bottlenecks allowing administrators to apply corrective action before the end-user experience is affected. The performance data should be used for long-term capacity planning.

While detailed information on all performance objects and counters to be observed is linked to in [Monitoring Lync Server 2013 with System Center Operations Manager](lync-server-2013-monitoring-lync-server-with-system-center-operations-manager.md), some performance counters that you should follow can provide administrators a quick view of the system performance:

  - To track overall system health of the front-end server, a good starting point is to check Processor\\% Processor Time. The value should always be below 80 percent.

  - To track the performance of the back end SQL Server database software instance used by the Front End pool, monitor the following performance counters:
    
    LC:USrv – 00 – DBStore\\Usrv – 002 – Queue Latency (msec)
    
    LC:USrv – 00 – DBStore\\Usrv – 0 04– Sproc Latency (msec)
    
    The healthy server at steady state should show \<100 ms latency values. The throttling mechanism will engage when latency reaches 12 seconds, which means the front-end server starts throttling requests to the back end. This causes clients to start to receive a 503 Server too busy error message.

  - To track the processing time at the front-end server, monitor the following counter:
    
    LC:SIP - 07 - Load Management\\SIP - 000 - Average Holding Time For Incoming Messages
    
    This is another throttling mechanism on the front-end servers, this time starting when the processing time on the front end is high. If average processing time is more than six seconds, the server goes into throttling mode and only allows one outstanding transaction per client connection.

  - To track memory issues at SQL Back End Server, monitor the following counter:
    
    SQL Server Buffer Manager\\Page life expectancy
    
    A low value, below 3600 seconds (together with high latency writes/sec and checkpoint pages/sec) indicates memory pressure.

<div>

## Additional Counters to View

There are several key counters that are good indicators of overall health from the front end server. This is not a comprehensive list and is not meant to identify root cause. These counters will let you perform a quick check on your server health. We recommend verifying these counters on each of the servers in the pool. It is important to understand what these counter values are when your server is healthy. A baseline is required to understand what changed when the user experience is degraded.

The front-end server can indicate issues that may be caused by bottlenecks elsewhere in the system. This means that it is the best place to start when looking at overall system health.

Two additional counters to review first are as follows:

LC:USrv-00-DBStore\\Usrv-002-Queue Latency (msec)

LC:USrv-00-DBStore\\Usrv-004-Sproc Latency (msec)

The queue latency counter represents the time that a request spent in the queue to the back end and the Sproc latency represents the time that it took for the back end to process the request. If, for any reason, disk, memory, network, and processor on the back end are in trouble, the queue latency counter will be high.

It can also be high if there is high network latency between the front end and the back end. So what is acceptable queue latency?

At 12 seconds, the Front End Servers start throttling requests to the Back End Servers. This means the servers start returning Server too busy – 503 errors to the clients. A healthy server should have less than 100 msec DBStore queue latencies at steady state, but during times where the server has just come online and users are all logging in at the same time, that counter can be very high and you may even see it hit multiple seconds.

You may have a load-balanced configuration, where you have a pool deployed with multiple front-end servers and a load balancer that is configured for "least number of connections." In this case, if one front-end server is restarted, then all users who attempt to reconnect will be pointed to the restarted server, because that server will have fewer connections compared to the other pool members. During this time, the respective front-end server may be overloaded while the other pool members are not.

We recommend that you perform maintenance during off-hours to reduce the performance affect as users will not all be competing to connect to the server at the same time.

If the previous two performance counters are high, the most likely bottleneck is the SQL Back End Server. The next components to confirm are as follows:

  - Is the SQL Server CPU too high? For example, is it greater than 80 percent?

  - Is the disk latency high?

In an ideal world, you have enough RAM to have both the RTC and RTCDYN databases in memory. Then, the only reason the server would be accessing the disk, is to write to the log files and flush to the databases. Tests have shown that 12 GB of RAM is sufficient for 100 thousand user deployments. This assumes that the RTC and RTCDYN databases size totals less than 12 GB. If your databases are larger than that, then you may need additional memory.

You can determine whether your SQL Server requires additional RAM by reviewing the SQL Server Buffer Manager page life expectancy performance counter. A value less than 3,600 indicates memory pressure. You should also see little to no reads on your database drive if you have sufficient memory because SQL Server should only be writing to the database.

There is an additional throttling mechanism in a Lync Server 2013 Front End Server that starts if the server processing time is high. The DBStore latency throttling is only enabled if the latency to the SQL Server is high. One example in which such throttling is enabled is if the front-end server is CPU-bound.

If the average processing time **(LC:SIP-07-Load Management\\SIP-000-Average Holding Time For Incoming Messages)** on the server exceeds six seconds, then the server goes into throttling mode and only gives users one outstanding transaction per client connection. Once the processing time drops to three seconds, then the server drops out of throttling mode and gives users up to 20 outstanding transactions per client connection. Whenever the number of transactions on a specific connection exceeds the threshold above, the connection is marked as flow controlled. The result is the server does not post any receives on it, and the **LC:SIP-01-Peers\\Flow Controlled Connections** counter is incremented. If a connection stays in a flow-controlled state for more than one minute, then the server closes it. It does so lazily. When it has an opportunity to check the connection, it determines whether it was throttled for too long and closes it if it has more than one minute.

These are the two throttling mechanisms and there is one performance counter that summarizes what, if any, throttling the server is performing.

**LC:SIP-04-Responses\\SIP-053-Local 503 Responses/sec**

  - The term "Local" in the previous counter refers to locally generated responses.

  - The 503 code corresponds to server unavailable—where you should not see any 503 codes on a healthy server. During the period after a server is just brought online, you may see some 503 codes. When all of the users sign back in and the server returns to a stable state, there should no additional 503 codes.

**LC:SIP-04-Responses\\SIP-074-Local 504 Responses/sec**

This performance counter indicates connectivity issues with other servers and it can indicate failures to connect or delays in connecting. If you are seeing 504 errors then the following performance counter should be checked.

**LC:SIP-01-Peers\\SIP-017-Sends Outstanding**

This counter indicates the number of outgoing queued requests and responses. If this counter is high then the issue is most likely not on the local server. Note that this counter can be high if there are network latency issues. It could also indicate issues with the local network adapter, but is more likely caused by an issue on a remote server. This counter would most likely be high on a Director server when the pool it is trying to communicate with is overloaded. The key with this counter is to look at the instances, not just the total.

</div>

</div>

<span> </span>

</div>

</div>

</div>

