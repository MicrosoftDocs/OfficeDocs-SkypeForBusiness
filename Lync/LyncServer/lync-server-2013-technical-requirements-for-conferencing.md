---
title: Lync Server 2013 technical requirements for conferencing
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Technical requirements for conferencing
ms:assetid: 3c0d89e1-53e6-46d7-bf8c-491260b292ea
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425889(v=OCS.15)
ms:contentKeyID: 48183923
ms.date: 06/26/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Technical requirements for conferencing in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-06-25_

For Lync Server 2013, dial-in conferencing, A/V conferencing, instant messaging (IM) conferencing and web conferencing capabilities always run on Front End Servers.

This section details the hardware and software requirements for these servers, along with the supported collocation.

Dial-in conferencing is a feature that includes a variety of components. Some of the components are specific to dial-in conferencing and some are Enterprise Voice components. This section describes the requirements for the components that are specific to dial-in conferencing. For details about Mediation Server and public switched telephone network (PSTN) gateway requirements, see [Mediation Server component in Lync Server 2013](lync-server-2013-mediation-server-component.md) and [Components and topologies for Mediation Server in Lync Server 2013](lync-server-2013-components-and-topologies-for-mediation-server.md) in the Planning documentation.

<div>

## Hardware Requirements

Because web conferencing and A/V conferencing are collocated with the Front End Server, the server hardware requirements are the same as for the Front End Servers. For details about hardware requirements, see [Server hardware platforms for Lync Server 2013](lync-server-2013-server-hardware-platforms.md) in the Supportability documentation. The following components required for dial-in conferencing also have the same hardware requirements as Front End Servers:

  - Application service

  - Conferencing Attendant application

  - Conferencing Announcement application

The hardware requirements for Front End Server are the same as for many other server roles in Lync Server 2013 are outlined in the following table.

</div>

<div>

## Software Requirements

Because web conferencing and A/V conferencing are collocated with the Front End Server, the server software requirements are the same as for the Front End Servers. For details about software requirements, see [Server and tools operating system support in Lync Server 2013](lync-server-2013-server-and-tools-operating-system-support.md) in the Supportability documentation.

For web conferencing, Lync Server 2013 also requires Office Web Apps and the Office Web Apps Server (formerly known as WAC Server) to handle PowerPoint presentations. For details, see [Configuring integration with Office Web Apps Server and Lync Server 2013](lync-server-2013-enabling-office-web-apps-server-and-lync-server-2013.md).

For dial-in conferencing, Application service, Conferencing Attendant application, and Conferencing Announcement application have the same operating system requirements as Front End Servers. For details about software requirements, see [Server and tools operating system support in Lync Server 2013](lync-server-2013-server-and-tools-operating-system-support.md) in the Supportability documentation.

Conferencing Attendant application and Conferencing Announcement application require that Windows Media Format Runtime is installed on Front End Servers. The Windows Media Format Runtime is required to play Windows Media audio (WMA) files that are used for music on hold, recorded names, and prompts. Except for Windows Server 2012 and Windows Server 2012 R2, the Windows Media Format Runtime is installed automatically as part of the Windows Desktop Experience when you run Setup, but you might need to restart the computer. Therefore, we recommend that you install as part of the Windows Desktop Experience, which includes Windows Media Format Runtime before you run Setup. Windows Server 2012 and Windows Server 2012 R2 requires Microsoft Media Foundation.

</div>

<div>

## Port Requirements for dial-in conferencing

The following table describes the ports that are used by dial-in conferencing. If you use a load balancer, ensure that the load balancer is configured for the ports used by any applications that will run in the pool.

These ports are default settings that you can change by using the **Set-CsApplicationServer** cmdlet. For details about this cmdlet, see the Lync Server Management Shell documentation.

<div>


> [!NOTE]  
> All instances of the same application in a pool use the same SIP listening port.



</div>

### Ports used by dial-in conferencing

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Port number</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>5072</p></td>
<td><p>Used by Conferencing Attendant application for SIP listening requests</p></td>
</tr>
<tr class="even">
<td><p>5073</p></td>
<td><p>Used by Conferencing Announcement application for SIP listening requests</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Supported Clients for Dial-In Conferencing

You can use the following client to schedule on-premises conferences that support dial-in access:

  - Online Meeting Add-in for Lync 2013 (installed automatically when you install Lync 2013 or Attendee)

</div>

<div>

## Dial-in Conferencing Settings page Requirements

The Dial-in Conferencing Settings page supports the combinations of operating systems and web browsers described in the following table.

<div>


> [!NOTE]  
> 32-bit and 64-bit versions of the operating systems are supported.



</div>

### Supported Operating Systems and Web Browsers

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Operating system</th>
<th>Web browser</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Windows 7</p></td>
<td><p>Internet Explorer 9</p>
<p>Internet Explorer 8</p>
<p>Firefox</p></td>
</tr>
<tr class="even">
<td> </td>
<td> </td>
</tr>
<tr class="odd">
<td> </td>
<td> </td>
</tr>
<tr class="even">
<td><p>Windows Server 2008 R2</p></td>
<td><p>Internet Explorer 9</p>
<p>Internet Explorer 8</p>
<p>Internet Explorer 7</p></td>
</tr>
<tr class="odd">
<td><p>Mac OS</p></td>
<td><p>Firefox</p>
<p>Safari</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Audio File Requirements for dial-in conferencing

Lync Server 2013 does not support customization of voice prompts and music for dial-in conferencing. However, if you have a strong business need that requires you to change the default audio files, see Microsoft Knowledge Base article 961177, [How to customize voice prompts or music files for dial-in audio conferencing in Microsoft Office Communications Server 2007 R2](http://go.microsoft.com/fwlink/p/?linkid=3052%26kbid=961177).

You can also use the [Microsoft Lync Server Conferencing Attendant Custom Voice Prompts](http://go.microsoft.com/fwlink/p/?linkid=396880) management utility, which enables administrators to replace the default voice prompts used when a phone caller joins a Lync meeting with custom prompts to provide a different meeting entry experience. The custom voice prompts can be installed on a server that is running Lync Server 2010 or Lync Server 2013, either Enterprise or Standard Edition.

Conferencing Attendant application and Conferencing Announcement application have the following requirements for music on hold, recorded name, and audio prompt files:

  - Windows Media Audio (WMA) file format

  - 16-bit mono

  - 48 kbps 2-pass CBR (constant bit rate)

  - Speech level at -24DB

</div>

<div>

## User Requirements for Dial-In Conferencing

Dial-in conferencing users must have a unique phone number or extension assigned to their account. This requirement supports authentication during dial-in conferencing. Enterprise users (that is, users who have Active Directory Domain Services credentials and Lync Server accounts within your organization) enter their phone number (or extension) and a personal identification number (PIN) to dial in to conferences as an authenticated user.

</div>

</div>

<span> </span>

</div>

</div>

</div>

