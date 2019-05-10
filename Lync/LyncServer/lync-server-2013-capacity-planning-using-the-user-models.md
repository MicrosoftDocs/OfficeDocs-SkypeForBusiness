---
title: Lync Server 2013 capacity planning using the user models
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Capacity planning using the user models
ms:assetid: 902ab23e-94d6-482a-9d6e-c0b28dc3e03d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg615015(v=OCS.15)
ms:contentKeyID: 49733733
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Capacity planning for Lync Server 2013 using the user models

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-01-14_

This section provides guidance on how many servers you need at a site for the number of users at that site, according to the usage described in [User models in Lync Server 2013](lync-server-2013-user-models.md).

<div>

## Tested Hardware Platform

All the performance results and deployment recommendations in this section are based on performance testing on servers running the hardware described in the following table. We recommend that you use similar hardware. If you use less powerful hardware, you may experience functionality problems or poor performance. Note that these hardware recommendations are higher than those of previous versions of Lync Server.

### Hardware Used in Performance Testing

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Hardware component</th>
<th>Recommended</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CPU</p></td>
<td><p>64-bit dual processor, hex-core, 2.26 gigahertz (GHz) or higher</p>
<p>Intel Itanium processors are not supported for Lync Server server roles.</p></td>
</tr>
<tr class="even">
<td><p>Memory</p></td>
<td><p>32 gigabytes (GB)</p></td>
</tr>
<tr class="odd">
<td><p>Disk</p></td>
<td><ul>
<li><p>8 or more 10,000-RPM hard disk drives with at least 72 GB free disk space.</p>
<p>Two of the disks should use RAID 1, and six should use RAID 10.</p>
<p>- OR -</p></li>
<li><p>Solid state drives (SSDs) which provide performance similar to 8 10,000-RPM mechanical disk drives.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Network</p></td>
<td><ul>
<li><p>1 dual-port network adapter, 1 Gbps or higher (2 recommended, which requires teaming with a single MAC address and single IP address)</p></li>
</ul></td>
</tr>
</tbody>
</table>


</div>

<div>

## Summary of Results

The following table summarizes these recommendations.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Server role</th>
<th>Maximum number of users supported</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Front End pool with twelve Front End Servers and one Back End Server or a mirrored pair of Back End Servers.</p></td>
<td><p>80,000 unique users simultaneously logged in, plus 50% multiple points of presence (MPOP) representing non-mobile instances, plus 40% of users enabled for Mobility for a total of 152,000 endpoints.</p></td>
</tr>
<tr class="even">
<td><p>A/V Conferencing</p></td>
<td><p>The A/V Conferencing service provided by a Front End pool supports the pool’s conferences assuming a maximum conference size of 250 users, and only one such large conference running at a time.</p>
<div>

> [!NOTE]  
> Additionally, you can support large conferences of between 250 and 1000 users by deploying a separate Front End pool with two Front End Servers to host the large conferences. For details, see <A href="lync-server-2013-supporting-large-meetings.md">Supporting large meetings using Lync Server 2013</A>.


</div></td>
</tr>
<tr class="odd">
<td><p>One Edge Server</p></td>
<td><p>12,000 concurrent remote users</p></td>
</tr>
<tr class="even">
<td><p>One Director</p></td>
<td><p>12,000 concurrent remote users</p></td>
</tr>
<tr class="odd">
<td><p>Monitoring and Archiving</p></td>
<td><p>In Lync Server 2013, the Monitoring and Archiving front end services now run on each Front End Server, instead of on separate server roles.</p>
<p>Monitoring and Archiving each still require their own database stores. If you also run Exchange 2013, you can keep your Archiving data in Exchange, rather than in a dedicated SQL database.</p></td>
</tr>
<tr class="even">
<td><p>One Mediation Server</p></td>
<td><p>Mediation Server collocated with Front End Server runs on every Front End Server in a pool, and should provide enough capacity for the users in the pool. For stand-alone Mediation Server, see the “Mediation Server” section later in this topic.</p></td>
</tr>
<tr class="odd">
<td><p>One Standard Edition server</p></td>
<td><p>We strongly recommend that if you use Standard Edition servers to host users, you always use two servers, paired using the recommendations in <a href="lync-server-2013-planning-for-high-availability-and-disaster-recovery.md">Planning for high availability and disaster recovery in Lync Server 2013</a>. Each server in the pair can host up to 2,500 users, and if one server fails the remaining server can support 5,000 users in a failover scenario.</p>
<p>If your deployment includes a significant amount of audio or video traffic, server performance may suffer with more than 2,500 users per server. In this case, you should consider adding more Standard Edition servers or moving to Lync Server Enterprise Edition.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Front End Server

<div>


> [!NOTE]  
> Stretched pools are not supported for this server role.



</div>

In a Front End pool, you should have one Front End Server for every 6,660 users homed in the pool, assuming that hyper-threading is enabled on all servers in the pool, and that the server hardware meets the recommendations in [Server hardware platforms for Lync Server 2013](lync-server-2013-server-hardware-platforms.md). The maximum number of users in one Front End pool is 80,000, assuming that hyper-threading is enabled on all the servers in the pool. If you have more than 80,000 users at a site, you can deploy more than one Front End pool.

When you account for the number of users in a Front End pool, include the users homed on Survivable Branch Appliances and Survivable Branch Servers at branch offices that are associated with this Front End pool.

When an active server is unavailable, its connections are transferred automatically to the other servers in the pool. For example, if you have 30,000 users and five Front End Servers, then if one server is unavailable, the connections of 6000 users need to be transferred to the other four servers. The remaining four servers will each have 7500 users, which is a larger number than recommended.

If instead you had started with six Front End Servers for your 30,000 users and subsequently one became unavailable, a total of 5000 users will be moved to the remaining five servers. These five servers will each host 6000 users, which is in the recommended range.

The maximum number of users in a Front End pool is 80,000. The maximum number of Front End Servers in a pool is 12.

For a Front End pool with 80,000 users, twelve Front End Servers is sufficient for performance, in typical deployments that follow the [User models in Lync Server 2013](lync-server-2013-user-models.md). Deployments designed to support disaster recovery failover assume that a maximum of 40,000 users can be hosted in each of two paired Front End pools, in which each pool has enough Front End Servers to accommodate the users in both pools should one pool need to be failed over to the other.

The number of users supported with good performance by a particular Front End pool may differ from these numbers for the following reasons:

  - The hardware for your Front End Servers does not meet the recommendations in [Server hardware platforms for Lync Server 2013](lync-server-2013-server-hardware-platforms.md).

  - Your organization’s usage differs significantly from the user models, such as significantly more conferencing traffic.

<div>


> [!IMPORTANT]  
> In Lync Server 2013, the presence databases are now hosted on Front End Servers, unlike in Lync Server 2010 where they were hosted on the Back End Server. This means that the disk performance and capacity of your Front End Servers should not be compromised from the recommendations listed earlier in this section and in <A href="lync-server-2013-server-hardware-platforms.md">Server hardware platforms for Lync Server 2013</A>, regardless of the number of users hosted by your Front End Servers.



</div>

The following table shows the average bandwidth for IM and presence, given the user model, as defined in [User models in Lync Server 2013](lync-server-2013-user-models.md).


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Average bandwidth per user</th>
<th>Bandwidth requirements per Front End Server with 6,660 users</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1.3 Kpbs</p></td>
<td><p>13 Mbps</p></td>
</tr>
</tbody>
</table>


<div>


> [!NOTE]  
> To improve the media performance of the co-located A/V Conferencing and Mediation Server functionality on your Front End Servers, you should enable receive-side scaling (RSS) on the network adapters on your Front End Servers. RSS enables incoming packets to be handled in parallel by multiple processors on the server. For details, see "Receive-Side Scaling Enhancements in Windows Server 2008" at <A href="http://go.microsoft.com/fwlink/p/?linkid=268731">http://go.microsoft.com/fwlink/p/?linkId=268731</A>. For details about how to enable RSS, see your network adapter documentation.



</div>

</div>

<div>

## Conferencing Maximums

Given the user model that 5% of users in a pool may be in a conference at any one time, a pool of 80,000 users could have about 4,000 users in conferences at one time. These conferences are expected to be a mix of media (some IM-only, some IM with audio, some audio/video, for example) and number of participants. There is no hard limit for the actual number of conferences allowed, and actual usage determines the actual performance. For example, if your organization has many more mixed-mode conferences than are assumed in the user model, you might need to deploy more Front End Servers or A/V Conferencing Servers than the recommendations in this document. For details about the assumptions in the user model, see [User models in Lync Server 2013](lync-server-2013-user-models.md).

The maximum supported conference size hosted by a regular Lync Server 2013 Front End pool which also hosts users is 250 participants. While a 250-user conference is happening, the pool still supports other conferences as well, such that a total of 5% of pool users are in concurrent conferences. For example, in a pool of twelve Front End Servers and 80,000 users, while the 250-user conference is happening, Lync Server supports 3,750 other users participating in smaller conferences.

Regardless of the number of users homed on the Front End pool or Standard Edition server, Lync Server supports a minimum of 125 other users participating in smaller conferences on the same pool or server which is hosting a 250-user conference.

To enable conferences with between 250 and 1000 users, you can set up a separate Front End pool just to host those conferences. This Front End pool will not host any users. For details, see [Supporting large meetings using Lync Server 2013](lync-server-2013-supporting-large-meetings.md).

If your organization has many more mixed-mode conferences than are assumed in the user model, you might need to deploy more Front End Servers than the recommendations in this document (up to a limit of 12 FEs). For details about the assumptions in the user model, see [User models in Lync Server 2013](lync-server-2013-user-models.md).

</div>

<div>

## Edge Server

<div>


> [!NOTE]  
> Stretched pools are not supported for this server role.



</div>

You should deploy one Edge Server for every 12,000 remote users who will access a site concurrently. At a minimum we recommend two Edge Servers for high availability. These recommendations assume that the hardware for your Edge Servers meets the recommendations in [Server hardware platforms for Lync Server 2013](lync-server-2013-server-hardware-platforms.md).

When you account for the number of users for the Edge Servers, include the users homed on Survivable Branch Appliances and Survivable Branch Servers at branch offices that are associated with a Front End pool at this site.

<div>


> [!NOTE]  
> To improve the performance of the A/V Conferencing Edge service on your Edge Servers, you should enable receive-side scaling (RSS) on the network adapters on your Edge Servers. RSS enables incoming packets to be handled in parallel by multiple processors on the server. For details, see "Receive-Side Scaling Enhancements in Windows Server 2008" at <A href="http://go.microsoft.com/fwlink/p/?linkid=268731">http://go.microsoft.com/fwlink/p/?linkId=268731</A>. For details about how to enable RSS, see your network adapter documentation.



</div>

</div>

<div>

## Director

<div>


> [!NOTE]  
> Stretched pools are not supported for this server role.



</div>

If you deploy the Director server role we recommend that you deploy one Director for every 12,000 remote users who will access a site concurrently. At a minimum we recommend two Directors for high availability. These recommendations assume that the hardware for your Edge Servers meets the recommendations in [Server hardware platforms for Lync Server 2013](lync-server-2013-server-hardware-platforms.md).

When you account for the number of users for the Directors, include the users homed on Survivable Branch Appliances and Survivable Branch Servers at branch offices that are associated with a Front End pool at this site.

</div>

<div>

## Mediation Server

<div>


> [!NOTE]  
> Stretched pools are not supported for this server role.



</div>

If you collocate Mediation Server with Front End Server, Mediation Server runs on every Front End Server in the pool, and should provide enough capacity for the users in the pool.

If you deploy a stand-alone Mediation Server pool, then how many Mediation Servers to deploy depends on many factors, including the hardware used for Mediation Server, the number of VoIP users you have, the number of gateway peers that each Mediation Server pool controls, the busy hour traffic through those gateways, and the percentage of calls with media that bypasses the Mediation Server.

The following tables provide a guideline for how many concurrent calls a Mediation Server can handle, assuming that the hardware for the Mediation Servers meets the requirements in [Server hardware platforms for Lync Server 2013](lync-server-2013-server-hardware-platforms.md) and that hyper-threading is enabled. For details about Mediation Server scalability, see [Estimating voice usage and traffic for Lync Server 2013](lync-server-2013-estimating-voice-usage-and-traffic.md) and [Deployment guidelines for Mediation Server in Lync Server 2013](lync-server-2013-deployment-guidelines-for-mediation-server.md).

All the following tables assume usage as summarized in [User models in Lync Server 2013](lync-server-2013-user-models.md).

### Stand-alone Mediation Server Capacity: 70% Internal Users, 30% External users with non-bypass call capacity (media transcoding performed by Mediation Server)

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Server hardware</th>
<th>Maximum number of calls</th>
<th>Maximum number of T1 lines</th>
<th>Maximum number of E1 lines</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Dual processor, hex core, 2.26 GHz hyper-threaded CPU <strong>with hyper-threading disabled</strong>, with 32 GB memory and one dual-port network adapter card.</p></td>
<td><p>1100</p></td>
<td><p>46</p></td>
<td><p>35</p></td>
</tr>
<tr class="even">
<td><p>Dual processor, hex core, 2.26 GHz hyper-threaded CPU, with 32 GB memory and one dual-port network adapter card.</p></td>
<td><p>1500</p></td>
<td><p>63</p></td>
<td><p>47</p></td>
</tr>
</tbody>
</table>


<div>


> [!NOTE]  
> Although servers with 32 GB of memory were used for performance testing, servers with 16 GB of memory are supported for stand-alone Mediation Server, and are sufficient to provide the performance shown in this table.



</div>

### Mediation Server Capacity (Mediation Server Collocated with Front End Server) 70% Internal Users, 30% External Users, Non-Bypass Call Capacity (Media Processing Performed by Mediation Server)

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Server hardware</th>
<th>Maximum number of calls</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Dual processor, hex core, 2.26 GHz hyper-threaded CPU, with 32 GB memory and 2 1GB network adapter cards.</p></td>
<td><p>150</p></td>
</tr>
</tbody>
</table>


<div>


> [!NOTE]  
> This number is much smaller than the numbers for the stand-alone Mediation Server because the Front End Server has to handle other features and functions for the 6600 users homed on it, in addition to the transcoding needed for voice calls.



</div>

<div>


> [!NOTE]  
> To improve the performance of the Mediation Server, you should enable receive-side scaling (RSS) on the network adapters on your Mediation Servers. RSS enables incoming packets to be handled in parallel by multiple processors on the server. For details, see "Receive-Side Scaling Enhancements in Windows Server 2008" at <A href="http://go.microsoft.com/fwlink/p/?linkid=268731">http://go.microsoft.com/fwlink/p/?linkId=268731</A>. For details about how to enable RSS, see your network adapter documentation.



</div>

</div>

<div>

## Back End Server

In Lync Server 2013, the presence databases are located on the Front End Servers instead of the Back End Server. This has resulted in a much simpler requirement for each Back End Server in Lync Server 2013, equivalent to the hardware requirement for the Front End Server. Contrast this to Lync Server 2010, where the Back End Server was required to be a much higher grade server with 25 disks. However, the workload of Back End Servers is still such that you should not fail to meet the hardware recommendations listed earlier in this section and in [Server hardware platforms for Lync Server 2013](lync-server-2013-server-hardware-platforms.md).

To provide high availability of your Back End Server, we recommend deploying server mirroring. For more information, see [Back End Server high availability in Lync Server 2013](lync-server-2013-back-end-server-high-availability.md).

</div>

<div>

## Monitoring and Archiving

In Lync Server 2013, if you deploy Monitoring or Archiving, the front end functionality of these services runs on the Front End Servers, instead of on separate server roles. Monitoring and Archiving each still use their own database store, separate from the Back End store. Alternatively, if you have Exchange 2013 deployed, you can store instant message Archiving data in Exchange instead of in a dedicated SQL store.

The following table indicates approximately how much database storage is required per user per day for Monitoring and Archiving data.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<tbody>
<tr class="odd">
<td></td>
<td><p><strong>CDR (Monitoring)</strong></p></td>
<td><p><strong>QoE (Monitoring)</strong></p></td>
<td><p><strong>Archiving</strong></p></td>
</tr>
<tr class="even">
<td><p>Disk space required per user per day</p></td>
<td><p>49 KB</p></td>
<td><p>28 KB</p></td>
<td><p>57 KB</p></td>
</tr>
</tbody>
</table>


Microsoft used the hardware in the following table for the database server for Monitoring and Archiving during its performance testing. The testing collected the data of two Front End pools, each of which contained 80,000 users.

### Hardware Used in Monitoring and Archiving Performance Testing

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Hardware component</th>
<th>Recommended</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CPU</p></td>
<td><p>64-bit dual processor, hex-core, 2.26 gigahertz (GHz) or higher</p></td>
</tr>
<tr class="even">
<td><p>Memory</p></td>
<td><p>48 gigabytes (GB)</p></td>
</tr>
<tr class="odd">
<td><p>Disk</p></td>
<td><p>25 10,000-RPM hard disk drives with 300 GB on each disk, with the following configuration</p>
<h3 id="section-3"> </h3>
<div>
<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Drive</strong></p></td>
<td><p><strong>RAID Configuration</strong></p></td>
<td><p><strong>Number of disks</strong></p></td>
</tr>
<tr class="even">
<td><p>CDR, QoE, and Archiving database data files, on a single drive</p></td>
<td><p>1+0</p></td>
<td><p>16</p></td>
</tr>
<tr class="odd">
<td><p>CDR database log file</p></td>
<td><p>1</p></td>
<td><p>2</p></td>
</tr>
<tr class="even">
<td><p>QoE database log file</p></td>
<td><p>1</p></td>
<td><p>2</p></td>
</tr>
<tr class="odd">
<td><p>Archiving database log file</p></td>
<td><p>1</p></td>
<td><p>2</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
<tr class="even">
<td><p>Network</p></td>
<td><ul>
<li><p>1 dual-port network adapter, 1 Gbps or higher (2 recommended, which requires teaming with a single MAC address and single IP address)</p></li>
</ul></td>
</tr>
</tbody>
</table>


</div>

<div>

## In This Section

  - [Estimating voice usage and traffic for Lync Server 2013](lync-server-2013-estimating-voice-usage-and-traffic.md)

  - [Deployment guidelines for Mediation Server in Lync Server 2013](lync-server-2013-deployment-guidelines-for-mediation-server.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

