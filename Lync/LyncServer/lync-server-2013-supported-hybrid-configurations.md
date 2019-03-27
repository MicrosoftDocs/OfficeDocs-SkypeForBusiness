---
title: 'Lync Server 2013: Supported hybrid configurations'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Supported hybrid configurations
ms:assetid: 5d456d6c-ad71-420c-b6d8-4d9cd0324f86
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ945633(v=OCS.15)
ms:contentKeyID: 51541482
ms.date: 05/10/2016
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Supported Lync Server 2013 hybrid configurations

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2016-05-10_

You can configure Lync Server 2013 deployments for integration with both Microsoft Exchange Server 2010 and Microsoft Exchange Server 2013 and SharePoint Server, both on-premises and online. The features listed in the following table are supported with all clients unless otherwise specified. For more information about client support, see [Client comparison tables for Lync Server 2013](lync-server-2013-desktop-client-comparison-tables.md) and Skype for Business Online client comparison tables at [Clients for Skype for Business Online](http://go.microsoft.com/fwlink/p/?linkid=281902).

<div>

## Integration with Exchange Server

The following table lists the features supported in a hybrid deployment when integrated with Microsoft Exchange Server.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>Exchange on-premises</th>
<th>Exchange Online</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Lync Server 2013 on-premises</strong></p></td>
<td><ul>
<li><p>IM/Presence in Outlook</p>
<p>For more information, see <a href="lync-server-2013-im-and-presence.md">IM and presence in Lync Server 2013</a></p></li>
<li><p>Schedule and join online meetings through Outlook</p>
<p>For more information, see <a href="lync-server-2013-integrating-with-microsoft-exchange-server-2013.md">Integrating Microsoft Lync Server 2013 and Microsoft Exchange Server 2013</a></p></li>
<li><p>IM/Presence in Outlook Web App</p>
<p>For more information, see <a href="lync-server-2013-configuring-lync-server-in-a-cross-premises-environment.md">Configuring Microsoft Lync Server 2013 in a cross-premises environment</a></p></li>
<li><p>Schedule and join online meetings through Outlook Web App</p></li>
<li><p>IM/Presence in Mobile Clients</p></li>
<li><p>Join online meetings in Mobile clients</p>
<p>For more information, see <a href="lync-server-2013-deploying-mobility.md">Deploying mobility in Lync Server 2013</a></p></li>
<li><p>Publish status based on Outlook calendar free/busy information</p></li>
<li><p>Contact List (via Unified Contact Store)</p>
<p>For more information, see <a href="lync-server-2013-configuring-lync-server-to-use-the-unified-contact-store.md">Configuring Microsoft Lync Server 2013 to use the unified contact store</a></p>
<div>

> [!NOTE]  
> Requires Exchange 2013.<BR>A Lync 2013 desktop client is required.


</div></li>
<li><p>High-resolution Contact Photo in Lync 2013 client and Lync Web App.</p>
<p>For more information, see <a href="lync-server-2013-configuring-the-use-of-high-resolution-photos.md">Configuring the use of high-resolution photos in Microsoft Lync Server 2013</a></p>
<div>

> [!NOTE]  
> Requires Exchange 2013.


</div></li>
<li><p>Meeting delegation</p>
<p>Supported only when both users are homed online in the same forest, or both are homed on-premises.</p></li>
<li><p>Missed Conversations history and Call Logs are written to user’s exchange mailbox</p></li>
<li><p>Archiving Content (IM and Meeting) in Exchange</p>
<p>For more information, see <a href="lync-server-2013-deployment-checklist-for-archiving.md">Deployment checklist for Archiving in Lync Server 2013</a></p>
<div>

> [!NOTE]  
> Requires Exchange 2013.


</div></li>
<li><p>Search archived content</p>
<div>

> [!NOTE]  
> Requires Exchange 2013.


</div></li>
<li><p>Voice mail</p>
<p>For more information, see <a href="lync-server-2013-deploying-on-premises-exchange-um-to-provide-lync-server-2013-voice-mail.md">Deploying on-premises Exchange UM to provide Lync Server 2013 voice mail</a></p></li>
</ul></td>
<td><ul>
<li><p>IM/Presence in Outlook</p>
<p>For more information, see <a href="lync-server-2013-configuring-on-premises-lync-server-integration-with-exchange-online.md">Configuring on-premises Lync Server 2013 integration with Exchange Online</a></p></li>
<li><p>Schedule and join online meeting through Outlook</p></li>
<li><p>IM/Presence in OWA</p>
<p>For more information, see <a href="lync-server-2013-configuring-on-premises-lync-server-integration-with-exchange-online.md">Configuring on-premises Lync Server 2013 integration with Exchange Online</a></p></li>
<li><p>Schedule and join online meeting from Outlook Web App</p>
<p>For more information, see <a href="lync-server-2013-configuring-on-premises-lync-server-integration-with-exchange-online.md">Configuring on-premises Lync Server 2013 integration with Exchange Online</a></p></li>
<li><p>IM/Presence in Mobile Clients</p></li>
<li><p>Join online meeting in Mobile clients</p></li>
<li><p>Publish status based on Outlook calendar free/busy information</p></li>
<li><p>Contact List (via Unified Contact Store). For more information, see <a href="lync-server-2013-configuring-lync-server-to-use-the-unified-contact-store.md">Configuring Microsoft Lync Server 2013 to use the unified contact store</a></p>
<div>

> [!NOTE]  
> Lync Server 2013 only. A Lync 2013 desktop client is required.


</div></li>
<li><p>High-resolution Contact Photo in Lync 2013 client and Lync Web App.</p>
<p>For more information, see <a href="lync-server-2013-configuring-the-use-of-high-resolution-photos.md">Configuring the use of high-resolution photos in Microsoft Lync Server 2013</a>.</p></li>
<li><p>Meeting delegation</p>
<p>Supported only when both users are homed online in the same forest, or both are homed on-premises.</p></li>
<li><p>Missed Conversations history and Call Logs are written to user’s exchange mailbox</p></li>
<li><p>Archiving Content (IM and Meeting) in Exchange.</p>
<p>For more information, see <a href="lync-server-2013-deployment-checklist-for-archiving.md">Deployment checklist for Archiving in Lync Server 2013</a></p></li>
<li><p>Search archived content. For more information, see at <a href="http://go.microsoft.com/fwlink/p/?linkid=285448">Configure Exchange for SharePoint eDiscovery Center</a></p></li>
<li><p>Voice mail. For more information, see <a href="lync-server-2013-providing-lync-server-users-voice-mail-on-hosted-exchange-um.md">Providing Lync Server 2013 users voice mail on hosted Exchange UM</a></p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Lync Online</strong></p></td>
<td><ul>
<li><p>IM and Presence in Outlook</p></li>
<li><p>Schedule and join online meetings through Outlook</p></li>
<li><p>IM/Presence in Mobile clients</p></li>
<li><p>Missed Conversations history and Call Logs are written to user’s exchange mailbox</p></li>
<li><p>High-resolution Contact Photo in Lync 2013 client.</p>
<div>

> [!NOTE]  
> Requires Microsoft Exchange Server 2013. This is not supported in Lync Web App when users are homed on Skype for Business Online.


</div></li>
<li><p>Join online meeting in Mobile clients</p></li>
<li><p>Publish status based on Outlook calendar free/busy information</p></li>
<li><p>Meeting delegation</p>
<p>Supported only when both users are homed online in the same forest, or both are homed on-premises.</p></li>
</ul></td>
<td><ul>
<li><p>IM/Presence in Outlook</p></li>
<li><p>Schedule and join online meetings through Outlook</p></li>
<li><p>IM/Presence in Outlook Web App</p></li>
<li><p>Schedule and join online meeting from Outlook Web App</p></li>
<li><p>IM/Presence in Mobile Clients</p></li>
<li><p>Join online meeting in Mobile clients</p></li>
<li><p>Publish status based on Outlook calendar free/busy information</p></li>
<li><p>Missed Conversations history and Call Logs are written to user’s exchange mailbox</p></li>
<li><p>Contact List (via Unified Contact Store)</p>
<div>

> [!NOTE]  
> Lync Server 2013 client Required


</div></li>
<li><p>High-resolution Contact Photo in Lync 2013 client and Lync Web App</p></li>
<li><p>Meeting delegation</p>
<p>Supported only when both users are homed online in the same forest, or both are homed on-premises.</p></li>
<li><p>Archiving Content (IM and Meeting) in Exchange</p></li>
<li><p>Search archived content</p></li>
<li><p>Voicemail</p></li>
</ul></td>
</tr>
</tbody>
</table>


</div>

<div>

## Integration with SharePoint

The following table lists the features supported in a Lync Server 2013 hybrid deployment when integrated with SharePoint.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>SharePoint on-premises</th>
<th>SharePoint Online</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Lync Server 2013 on-premises</strong></p></td>
<td><ul>
<li><p>Skills search</p></li>
<li><p>Presence in SharePoint</p></li>
</ul></td>
<td><ul>
<li><p>Presence in SharePoint</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Lync Online</strong></p></td>
<td><ul>
<li><p>Presence in SharePoint</p></li>
</ul></td>
<td><ul>
<li><p>Presence in SharePoint</p></li>
</ul></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

