---
title: 'Lync Server 2013: Capacity planning for Group Call Pickup'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Capacity planning for Group Call Pickup
ms:assetid: 0d654a19-6cf0-4118-903d-ec2c4e519253
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ984297(v=OCS.15)
ms:contentKeyID: 51476680
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Capacity planning for Group Call Pickup in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-12_

<div id="sectionSection0" class="section">

The following table describes the Group Call Pickup user model that you can use as the basis for capacity planning requirements.

<div>


> [!IMPORTANT]  
> Group Call Pickup is based on the Call Park application. Keep in mind that, for disaster recovery capacity planning, each pool of a paired pool should be able to handle the workloads for Call Park services, including Group Call Pickup, in both pools.



</div>

### Group Call Pickup User Model

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Metric</th>
<th>Per Front End pool (with 8 Front End Servers)</th>
<th>Per Standard Edition server</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Recommended number of users per group</p></td>
<td><p>50</p></td>
<td><p>50</p></td>
</tr>
<tr class="even">
<td><p>Recommended number of groups</p></td>
<td><p>500</p></td>
<td><p>60</p></td>
</tr>
<tr class="odd">
<td><p>Maximum number of users per pool enabled for Group Call Pickup</p></td>
<td><p>25,000</p></td>
<td><p>3,000</p></td>
</tr>
<tr class="even">
<td><p>Maximum rate of incoming calls to total users enabled for Group Call Pickup per pool per minute</p></td>
<td><p>500</p></td>
<td><p>60</p></td>
</tr>
<tr class="odd">
<td><p>Maximum rate of calls retrieved by users with Group Call Pickup per pool per minute</p></td>
<td><p>200</p></td>
<td><p>25</p></td>
</tr>
</tbody>
</table>


<div>


> [!NOTE]  
> <UL>
> <LI>
> <P>For Front End pools that have fewer than eight Front End Servers, calculate the metrics linearly. For example, if your Front End pool has one Front End Server, calculate the maximum load as 1/8 of the values shown in the table.</P>
> <LI>
> <P>You can increase or decrease the recommended number of users per group and number of groups as long as you do not exceed the maximum number of users per pool. For example, your Standard Edition server can have 120 groups with 25 users per group because the number of users enabled for Group Call Pickup is still within the user model maximum (that is, 120 groups times 25 users is 3,000 users enabled for Group Call Pickup).</P></LI></UL>



</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

