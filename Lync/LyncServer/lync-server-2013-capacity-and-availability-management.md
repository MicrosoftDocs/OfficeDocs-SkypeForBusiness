---
title: 'Lync Server 2013: Capacity and availability management'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Capacity and availability management
ms:assetid: 207a2997-f482-4bee-892d-d2b112294481
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn720325(v=OCS.15)
ms:contentKeyID: 63969586
ms.date: 01/27/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Capacity and availability management in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-08-18_

The purpose of capacity management and availability management is to measure and control system performance. We recommend that you implement capacity management and availability management procedures so that you can measure and control system performance. You have to know whether the system is available and if it can handle the current and the projected demands by setting baselines and monitoring the system to look for trends.

<div>

## Capacity management

Capacity management involves planning, sizing, and controlling service capacity to help guarantee that the minimum performance levels specified in your SLA are exceeded. Good capacity management helps ensure that you can provide IT services at a reasonable cost and still meet the levels of performance defined in your SLAs with the client. These criteria can include the following:

  - **System Response Time**   This is the measured time that the system takes to do typical actions. Examples include the time that is required for the audio/video server role to process audio/video traffic, the time that is required for a client to create and join a conference, or the time taken for presence to be updated in all watcher clients.

  - **Storage Capacity**   This is the capacity of a storage system, whether it is a content database, a backup device, or a local drive. Examples include the maximum amount of storage space to be provided per site and the time that backups should be stored before they are overwritten.

Adjusting capacity is frequently a case of making sure that enough physical resources are available, such as disk space and network bandwidth. The following table lists typical resolutions for capacity-related issues.

### Typical resolutions for capacity-related issues

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Issue</th>
<th>Possible resolution</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Remote users having poor audio/video performance</p></td>
<td><p>Check to see whether appropriate bandwidth is available on the WAN links and if QoS is enabled and appropriately configured. Check QoE data.</p></td>
</tr>
<tr class="even">
<td><p>Overall response of the Lync environment is slow.</p></td>
<td><p>Run tests to check that the existing front-end servers can deal with the load. Introduce a new front-end server if it is needed.Check SQL database response times and fix the causes for the delays (for example, improve disk I/O).</p></td>
</tr>
</tbody>
</table>


Troubleshooting in greater detail is covered in the Lync Server Networking Guide.

Capacity is affected by system configuration and depends on physical resources such as network bandwidth. For example, if a Lync environment is configured to perform a full backup nightly, care must be taken to help guarantee that the effect on the interactive performance experienced by end-users is minimized.

Capacity management is the process of keeping the capacity of a system within acceptable levels and addresses the following issues:

  - **Reacting to changes in requirements**   Capacity requirements have to be adjusted to account for changes in the system or the organization. For example, if your environment decides to implement Enterprise Voice, the number and placement of Mediation Servers and public switched telephone network (PSTN) gateways will be very important. If you'll be doing Session Initiation Protocol (SIP) trunking or direct SIP, the overall design will be significantly changed to provide the best Enterprise Voice performance.

  - **Predicting future requirements**   Some capacity requirements change predictably over time. By tracking trends you can plan upgrades in advance. For example, available bandwidth between various Lync sites must be monitored to create a baseline. This baseline will allow you to predict when you have to add more bandwidth to these links as user count in these remote sites increases with time.

</div>

<div>

## Availability management

Availability management is the process of making sure that any IT service consistently and cost effectively delivers the level of consistent, reliable service that is required by the customer. Availability management deals with minimizing loss of service and with making sure that appropriate action is taken if service is lost. In a Lync environment, you may be concerned about whether the Enterprise Voice service is available, whether users can join scheduled conferences, and so on. An SLA defines an acceptable frequency and length of outages and allows for certain periods when the system is unavailable for planned maintenance.

If you have to provide reports to your management about the availability of systems, or if you have financial or other penalties associated with missing availability targets, you must record availability data. Even if you do not have such formal requirements, it is a good idea to at least know how frequently a system has failed in a certain time period. For example, system availability in the last 12 months and how long it took to recover from each failure. This information will help you measure and improve your team’s effectiveness in responding to a system failure. It can also give you useful information if there is a dispute.

Measures related to availability are as follows:

  - **Availability**   This is typically expressed as the time that a system or service can be accessed compared to the time that it is down. It is typically expressed as a percentage. (You may see references to “three nines” or “five nines”. These refer to 99.9 percent or 99.999 percent availability.)

  - **Reliability**   This is a measure of the time between failures of a system and is sometimes expressed as mean (or average) time between failures (MTBF).

  - **Time to Repair**   This is the time taken to recover a service after a failure has occurred and is often expressed as mean (meaning average) time to repair (MTTR).

Availability, reliability, and time to repair are related as follows:

**Availability = (MTBF – MTTR) / MTBF**   For example, if a server fails two times over a six-month period and is unavailable for an average of 20 minutes, the MTBF is three months or 90 days and the MTTR is 20 minutes. Therefore, Availability = (90 days – 20 minutes) / 90 days = 99.985 percent.

Availability management is the process of making sure that availability is maximized and kept within the parameters that are defined in SLAs. Availability management includes the following processes:

  - **Monitoring**    Examining when and for how long services are unavailable.

  - **Reporting**   Availability figures should be regularly provided to management, users, and operations teams. These reports should highlight trends and identify areas that are doing well and areas that require attention. The report should summarize compliance with targets set in the SLAs.

  - **Improvement**   If availability does not meet targets that are defined in the SLAs or where the trend is toward reduced availability, the availability management process should plan remedial steps. This should include working with other responsible teams to highlight reasons for outages and to plan remedial actions to prevent a recurrence of the outages.

Capacity and availability measurements are repetitive tasks that are ideally suited to automated tools and scripts such as Microsoft System Center Operations Manager (formerly Microsoft Operations Manager), which is discussed later in this document.

</div>

<div>

## See Also


[Monitoring Lync Server 2013 with System Center Operations Manager](lync-server-2013-monitoring-lync-server-with-system-center-operations-manager.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

