---
title: 'Lync Server 2013: Lync 2013 compatibility'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Lync 2013 compatibility
ms:assetid: ac3a1046-b438-4e21-9d4f-3b0057dd685d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412817(v=OCS.15)
ms:contentKeyID: 51541502
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Lync 2013 compatibility

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-10-07_

This section describes the compatibility of Lync 2013 with various versions of Microsoft Office suites, Microsoft Exchange Server, Windows operating systems, and selected public instant messaging (IM) clients.

<div>

## Office and Lync 2013

The following table describes the Lync 2013 features that are supported by various versions of Office.

### Lync 2013 and Microsoft Office Compatibility

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
<th>Feature</th>
<th>Microsoft Office 2003 with Service Pack 3 (SP3) (required) or the latest service pack (recommended)</th>
<th>Microsoft Office 2007</th>
<th>Microsoft Office 2010</th>
<th>Microsoft Office 2013</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Customize Outlook meeting invitations (add logo, help URL, disclaimer, footer text)</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>Yes</p></td>
</tr>
<tr class="even">
<td><p>In Outlook, configure meeting option to mute attendee audio and video by default</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>Yes</p></td>
</tr>
<tr class="odd">
<td><p>Unified Contact Store for managing Contacts lists across Office and Lync</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>Yes (requires Exchange 2013)1</p></td>
</tr>
<tr class="even">
<td><p>High-resolution pictures</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>Yes (requires Exchange 2013)1</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 setup integrated into the Office setup program</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>Yes</p></td>
</tr>
<tr class="even">
<td><p>OneNote shared notes</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>Yes</p></td>
</tr>
<tr class="odd">
<td><p>PowerPoint presentation content</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
</tr>
<tr class="even">
<td><p>Presence status in the Microsoft Outlook To and Cc fields</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
</tr>
<tr class="odd">
<td><p>Reply with conference call from the availability menu</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>Yes (from the contact card)</p></td>
<td><p>Yes (from the contact card)</p></td>
</tr>
<tr class="even">
<td><p>Presence status in a meeting request on the Scheduling Assistant tab</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
</tr>
<tr class="odd">
<td><p>Reply with IM, or call from the toolbar or ribbon in a received email message</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
</tr>
<tr class="even">
<td><p>Presence status in the Outlook From field</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
</tr>
<tr class="odd">
<td><p>Reply with IM or voice from availability menu</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>Yes (from the contact card)</p></td>
<td><p>Yes (from the contact card)</p></td>
</tr>
<tr class="even">
<td><p>IM and presence in Microsoft Word and Microsoft Excel files (smart tags enabled)</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>Microsoft Word only</p></td>
<td><p>Microsoft Word only</p></td>
</tr>
<tr class="odd">
<td><p>IM and presence in Microsoft SharePoint sites (Outlook must be installed)</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
</tr>
</tbody>
</table>


1 For more information, see [Integrating Microsoft Lync Server 2013 and Microsoft Exchange Server 2013](lync-server-2013-integrating-with-microsoft-exchange-server-2013.md) in the Planning documentation.

The following features are available only with Office 2010 or Office 2013:

  - Contact card with expanded options, such as video call and desktop sharing

  - Quick search from the Find a Contact field in Outlook

  - Reply with an IM or call from the Outlook Home ribbon in the Mail, Calendar, Contacts, and Tasks folders

  - Lync Contacts list in Outlook To-Do Bar

  - Office Backstage (File tab) presence status, program sharing, and file transfer

  - Presence menu in Microsoft Office SharePoint Workspace 2010 (formerly Microsoft Office Groove 2007)

  - Presence menu extensibility

</div>

<div>

## Exchange Server and Lync 2013

The following table describes Lync 2013 support for various versions of Exchange Server. Outlook must be installed on the client computer to handle Extended MAPI calls, and some features require the use of Exchange Web Services (EWS).

### Lync 2013 and Exchange Server Compatibility

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Exchange Server version</th>
<th>Lync 2013 support</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Exchange Server 2013</p></td>
<td><p>Same as Exchange Server 2010 support, with the addition of Unified Contact Store, high-resolution pictures, and archiving integration.</p>
<div>

> [!NOTE]  
> For details, see <A href="lync-server-2013-integrating-with-microsoft-exchange-server-2013.md">Integrating Microsoft Lync Server 2013 and Microsoft Exchange Server 2013</A>.


</div></td>
</tr>
<tr class="even">
<td><p>Exchange Server 2010</p></td>
<td><p>Same as Exchange Server 2007 support, with the addition of Exchange contact sync.</p></td>
</tr>
<tr class="odd">
<td><p>Exchange Server 2007 with Service Pack 1 (SP1) (required) or the latest service pack (recommended)</p></td>
<td><p>The following features are available only through EWS:</p>
<ul>
<li><p>Read or delete items in the Conversation History folder</p></li>
<li><p>Read or delete voice mail items</p></li>
<li><p>Display extended free/busy information and meeting subject and location</p></li>
</ul>
<p>Public folders are optional in Exchange Server 2007 with Service Pack 1 (SP1) (required) or the latest service pack or release (recommended).</p></td>
</tr>
<tr class="even">
<td><p>Exchange Server 2003</p></td>
<td><p>Outlook MAPI only. EWS-only features are not available (see the previous row).</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Windows and Lync 2013

For information about Lync 2013 and Windows supportability, see [Lync client software support in Lync Server 2013](lync-server-2013-lync-client-software-support.md) in the Planning documentation.

</div>

<div>

## Macintosh and Lync 2013

Lync Server 2013 supports certain clients on computers that are running Macintosh operating systems. For details, see [Lync client software support in Lync Server 2013](lync-server-2013-lync-client-software-support.md) in the Planning documentation.

</div>

<div>

## Public Instant Messaging Clients and Lync 2013

If you have configured your server for public IM connectivity, Lync supports the following capabilities with public IM networks. Presence status is filtered to those presence states supported by the public IM client. For details, see [Planning for public instant messaging connectivity in Lync Server 2013](lync-server-2013-planning-for-public-instant-messaging-connectivity.md) in the Planning documentation and [Manage external access policy in Lync Server 2013](lync-server-2013-manage-external-access-policy-for-your-organization.md) in the Operations documentation.

In addition, the XMPP integration feature of Lync Server 2013 lets users exchange instant messages and presence information with users of public IM providers that use Extensible Messaging and Presence Protocol, such as Google Talk. For details, see [Planning for extensible messaging and presence protocol (XMPP) federation in Lync Server 2013](lync-server-2013-planning-for-extensible-messaging-and-presence-protocol-xmpp-federation.md) in the Planning documentation.

### Lync 2013 and Public IM Clients Compatibility

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Client</th>
<th>Supported Capabilities</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Windows Live Messenger</p></td>
<td><p>IM, basic presence, audio/video (A/V)*</p></td>
</tr>
<tr class="even">
<td><p>Skype</p></td>
<td><p>IM, basic presence, audio</p></td>
</tr>
<tr class="odd">
<td><p>AOL</p></td>
<td><p>IM and basic presence</p></td>
</tr>
<tr class="even">
<td><p>Yahoo!</p></td>
<td><p>IM and basic presence</p></td>
</tr>
<tr class="odd">
<td><p>Google Talk</p></td>
<td><p>IM and basic presence</p></td>
</tr>
</tbody>
</table>


\*A/V is supported with the latest version of Windows Live Messenger. If you are implementing audio/video (A/V) federation with Windows Live Messenger, you must also modify the server encryption level. By default, the encryption level is Required. You must change this setting to Supported by using the Lync Server Management Shell.

<div>


> [!IMPORTANT]  
> <UL>
> <LI>
> <P>As of September 1st, 2012, the Microsoft Lync Public IM Connectivity User Subscription License (“PIC USL”) is no longer available for purchase for new or renewing agreements. Customers with active licenses will be able to continue to federate with Yahoo! Messenger until the service shut down date. An end of life date of June 2014 for AOL and Yahoo! has been announced. For details, see <A href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Support for public instant messenger connectivity in Lync Server 2013</A>.</P>
> <LI>
> <P>The PIC USL is a per-user per-month subscription license that is required for Lync Server or Office Communications Server to federate with Yahoo! Messenger. Microsoft’s ability to provide this service has been contingent upon support from Yahoo!, the underlying agreement for which is winding down.</P>
> <LI>
> <P>More than ever, Lync is a powerful tool for connecting across organizations and with individuals around the world. Federation with Windows Live Messenger requires no additional user/device licenses beyond the Lync Standard CAL.</P></LI></UL>



</div>

</div>

<div>

## See Also


[Client interoperability in Lync 2013](lync-server-2013-client-interoperability-in-lync-2013.md)  
[Lync client software support in Lync Server 2013](lync-server-2013-lync-client-software-support.md)  
[Lync Web App supported platforms for Lync Server 2013](lync-server-2013-lync-web-app-supported-platforms.md)  
[Lync Windows Store app requirements for Lync Server 2013](lync-server-2013-lync-windows-store-app-requirements.md)  


[Client system requirements for Lync Server 2013](lync-server-2013-client-system-requirements.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

