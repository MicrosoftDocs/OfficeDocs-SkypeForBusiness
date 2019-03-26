---
title: 'Lync Server 2013: Supported clients from previous deployments'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Supported clients from previous deployments
ms:assetid: 69d427f8-57a5-4244-b2ed-f2eb7600285e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398499(v=OCS.15)
ms:contentKeyID: 48184390
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Supported clients from previous deployments in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-12-14_

In a coexistence scenario, Lync Server 2013 clients can interact with clients from earlier versions of Lync Server and Office Communications Server. Unlike previous releases, Lync Server 2010 supports the new Lync 2013 clients. This allows organizations who are upgrading from Lync Server 2010 to roll out new clients independent of Lync Server upgrades.

<div>

## Supported Server and Client Combinations

The following table shows the supported combinations of client versions and server versions. Lync Server 2013 supports two previous client versions, and Lync Server 2010 supports the new Lync 2013 client.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Client</th>
<th>Lync Server 2013</th>
<th>Lync Server 2010</th>
<th>Office Communications Server 2007 R2</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 2013</p></td>
<td><p>Supported</p></td>
<td><p>Supported</p></td>
<td><p>Not Supported</p></td>
</tr>
<tr class="even">
<td><p>Lync Web App 2013</p></td>
<td><p>Supported</p></td>
<td><p>Not Supported</p></td>
<td><p>Not Supported</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2010</p></td>
<td><p>Supported</p></td>
<td><p>Supported</p></td>
<td><p>Not Supported</p></td>
</tr>
<tr class="even">
<td><p>Lync 2010 Attendant</p></td>
<td><p>Supported</p></td>
<td><p>Supported</p></td>
<td><p>Not Supported</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2010 Group Chat</p></td>
<td><p>Not Applicable</p></td>
<td><p>Supported1</p></td>
<td><p>Not Applicable</p></td>
</tr>
<tr class="even">
<td><p>Lync Web App 2010</p></td>
<td><p>Not Supported</p></td>
<td><p>Supported</p></td>
<td><p>Not Supported</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2010 Attendee</p></td>
<td><p>Not Supported2</p></td>
<td><p>Supported</p></td>
<td><p>Not Supported</p></td>
</tr>
<tr class="even">
<td><p>Office Communicator 2007 R2</p></td>
<td><p>Interoperable3</p></td>
<td><p>Supported</p></td>
<td><p>Supported</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft Office Communications Server 2007 R2 Attendant</p></td>
<td><p>Not Supported</p></td>
<td><p>Supported</p></td>
<td><p>Supported</p></td>
</tr>
<tr class="even">
<td><p>Office Communicator 2007</p></td>
<td><p>Not Supported</p></td>
<td><p>Supported</p></td>
<td><p>Supported</p></td>
</tr>
<tr class="odd">
<td><p>Office Live Meeting 2007</p></td>
<td><p>Not Supported</p></td>
<td><p>Supported</p></td>
<td><p>Supported</p></td>
</tr>
</tbody>
</table>


1In Microsoft Lync Server 2010, group chat functionality was available with Group Chat Server, a third-party trusted application for Lync Server 2010. Lync 2013 clients are not compatible with Lync Server 2010, Group Chat.

2Lync Web App 2013 now provides a full in-meeting experience, including computer audio and video, and is considered the replacement for Lync 2010 Attendee.

3The presence and IM features in Office Communicator 2007 R2 are compatible with Lync Server 2013, but conferencing features are not. During migration from Office Communications Server 2007 R2, Office Communicator 2007 R2 is suitable for presence and IM interoperability, but users should use Lync Web App 2013 to join Lync Server 2013 meetings.

<div>


> [!NOTE]  
> For details about the ability of Lync Server 2013 clients to coexist and interact with clients from earlier versions of Lync Server and Office Communications Server, see <A href="lync-server-2013-client-interoperability-in-lync-2013.md">Client interoperability in Lync 2013</A> in the Planning documentation.



</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

