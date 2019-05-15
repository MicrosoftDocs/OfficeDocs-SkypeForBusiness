---
title: 'Lync Server 2013: Lync client software support'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Lync client software support
ms:assetid: a6851e38-ba9a-4f19-9aa7-d8accf4d62b3
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412781(v=OCS.15)
ms:contentKeyID: 48184994
ms.date: 02/25/2016
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Lync client software support in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2016-02-25_

This section summarizes software support for Lync 2013 and the Online Meeting Add-in for Lync 2013.

<div>


> [!NOTE]  
> The Online Meeting Add-in for Lync 2013, which supports meeting management from within the Outlook messaging and collaboration client, installs automatically with Lync 2013.



</div>

### Software Requirements for Lync 2013 and the Online Meeting Add-in for Lync 2013

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>System component</th>
<th>Minimum requirement</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Windows Operating system</p></td>
<td><p>Windows 10</p>
<p>Windows 8.1</p>
<p>Windows 8</p>
<p>Windows 7 operating system</p>
<p>Windows Server 2008 R2 with latest service pack</p>
<div>

> [!NOTE]  
> Lync 2013 and the Online Meeting Add-in for Lync 2013 are not supported on Windows Vista or Windows XP (any version).


</div></td>
</tr>
<tr class="even">
<td><p>Installation and updates</p></td>
<td><p>Administrator rights and permissions</p></td>
</tr>
<tr class="odd">
<td><p>Browser</p></td>
<td><p>Internet Explorer 11 Internet browser</p>
<p>Internet Explorer 10 Internet browser</p>
<p>Internet Explorer 9 Internet browser</p>
<p>Internet Explorer 8 Internet browser</p>
<p>Internet Explorer 7 Internet browser</p>
<p>Mozilla Firefox web browser</p>
<div>

> [!NOTE]  
> If you are using Lync with Microsoft Exchange Online and your organization has deployed an authenticating HTTP proxy, Internet Explorer 9 or Internet Explorer 8 is required.


</div></td>
</tr>
<tr class="even">
<td><p>Microsoft Office Integration</p></td>
<td><p>For the full set of integration features:</p>
<ul>
<li><p>Outlook 2013 messaging and collaboration client</p></li>
<li><p>Outlook 2010 messaging and collaboration client</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Microsoft Exchange Integration</p></td>
<td><p>For the full set of integration features:</p>
<ul>
<li><p>Microsoft Exchange Server 2013</p></li>
<li><p>Microsoft Exchange Server 2010</p></li>
</ul></td>
</tr>
</tbody>
</table>


<div>

## Macintosh Operating Systems

Lync 2013 is available only for Windows. However, Lync Server 2013 supports the following clients on computers that are running Mac OS 10.5.8 or latest service pack or release (Intel-based) operating systems (Mac OS 10.9 operating system is not currently supported). For details about supported features, see [Client comparison tables for Lync Server 2013](lync-server-2013-desktop-client-comparison-tables.md).

  - Microsoft Lync for Mac 2011 (see “Lync for Mac 2011 Deployment Guide” at [http://go.microsoft.com/fwlink/p/?LinkId=268786](http://go.microsoft.com/fwlink/p/?linkid=268786))

  - Microsoft Communicator for Mac 2011 (see “Communicator for Mac 2011 Deployment Guide” at [http://go.microsoft.com/fwlink/p/?LinkId=268787](http://go.microsoft.com/fwlink/p/?linkid=268787))

</div>

<div>

## Lync Web App Browsers

Lync Web App supports specific combinations of operating systems and browsers. For details, see [Lync Web App supported platforms for Lync Server 2013](lync-server-2013-lync-web-app-supported-platforms.md) in the Planning documentation.

</div>

<div>

## Microsoft Office Supportability

Lync Server 2013 clients support integration with various versions of Microsoft Office, as summarized in this section.

  - Lync 2013 integration features are supported on Outlook 2013 and Microsoft Outlook 2010.

  - Lync 2013 integration features are supported on Microsoft Exchange Server 2013 and Microsoft Exchange Server 2010.

  - The Online Meeting Add-in for Lync 2013 is supported with Office 2013 and Microsoft Office 2010.

</div>

<div>

## Using Mandatory Profiles

If users are planning to use Lync 2013 conferencing features, they should not use Active Directory Domain Services mandatory profiles to sign in to the Lync 2013 client. Because mandatory profiles are read-only user profiles, the public key infrastructure (PKI) keys that are required for Lync 2013 conferencing cannot be saved to the profile. For details, see Microsoft Knowledge Base article 2552221, “Lync 2010 conferencing feature fails when the user is signed in using a mandatory user profile,” at [http://go.microsoft.com/fwlink/p/?linkid=3052\&kbid=2552221](http://go.microsoft.com/fwlink/p/?linkid=3052%26kbid=2552221).

</div>

<div>

## See Also


[Lync client hardware support in Lync Server 2013](lync-server-2013-lync-client-hardware-support.md)  
[Lync client video requirements for Lync Server 2013](lync-server-2013-lync-client-video-requirements.md)  
[Supported clients from previous deployments in Lync Server 2013](lync-server-2013-supported-clients-from-previous-deployments.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

