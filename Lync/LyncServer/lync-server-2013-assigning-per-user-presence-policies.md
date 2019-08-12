---
title: 'Lync Server 2013: Assigning per-user presence policies'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Assigning per-user presence policies
ms:assetid: fd1097b7-248d-4b78-8c43-456b03257c18
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg182614(v=OCS.15)
ms:contentKeyID: 48185955
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Assigning per-user presence policies in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-11_

A presence policy is a set of limits and restrictions that affect presence. The following table describes the presence policy settings available in Lync Server 2013.

### Presence Policy Settings

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>XML name</th>
<th>Display name</th>
<th>Description</th>
<th>Type</th>
<th>Value</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CategorySubscriptions</p></td>
<td><p>Maximum Number of Subscriber Category Subscriptions</p></td>
<td><p>Limits the number of subscriber category subscriptions. For example, when Communicator subscribes to a user’s presence, it obtains a category subscription for each of the contact card, calendar data, notes, services, and state categories.</p>
<p>A setting of 0 means that the user or contact object cannot be subscribed to by others.</p>
<div>

> [!NOTE]  
> This setting can have a significant impact on performance if it is set to a high number, and the average user has a large number of users subscribing to his or her presence.


</div></td>
<td><p>Integer</p></td>
<td><p>0-3000</p></td>
</tr>
<tr class="even">
<td><p>PromptedSubscribers</p></td>
<td><p>Maximum Number of Queued Presence Subscription Alerts</p></td>
<td><p>Limits the number of entries in the prompted subscribers table. This setting determines the maximum number of prompts that can be queued for a given user. For example, when user A subscribes to user B’s presence, user B receives a prompt that user A is now subscribed to user B, and an acknowledgement prompt is created in user B’s prompted subscribers table. After user B accepts, or acknowledges, the subscription, the acknowledgement prompt is removed from user B’s prompted subscribers table.</p>
<p>A setting of 0 means that the user is not prompted when someone subscribes to his or her presence.</p></td>
<td><p>Integer or Token</p></td>
<td><p>0-500</p></td>
</tr>
</tbody>
</table>


By default, the **Default Policy** and **Service: Medium** presence policies are installed when you deploy Lync Server. The following table describes the specific settings of the two presence policies.

### Presence Policies

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Policy name</th>
<th>Description</th>
<th>CategorySubscriptions</th>
<th>PromptedSubscribers</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Default Policy</p></td>
<td><p>Policy for typical users. This is the default presence policy.</p></td>
<td><p>1000</p></td>
<td><p>200</p></td>
</tr>
<tr class="even">
<td><p>Service: Medium</p></td>
<td><p>Policy for applications that require more users to subscribe to the object’s presence.</p></td>
<td><p>1000</p></td>
<td><p>0</p></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

