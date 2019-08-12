---
title: 'Lync Server 2013: Internet Information Services (IIS) requirements'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Internet Information Services (IIS) requirements
ms:assetid: 4f57a605-a8a9-4c5a-9a18-05ecb3d9ab6b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398321(v=OCS.15)
ms:contentKeyID: 48184128
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Internet Information Services (IIS) requirements in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-06-19_

Several Lync Server 2013 components require Internet Information Services (IIS). This topic describes the specific IIS features required to support Lync Server. The topics in this section describe the requirements of specific components for IIS.

When the Web Server (IIS) role is enabled on Windows Server 2008, various role services are installed by default. The following table describes the additional role services that must be installed when the Web Server (IIS) role is enabled on Windows Server 2008.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Role service</th>
<th>Feature</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Common HTTP Features</p></td>
<td><p>HTTP Redirection</p></td>
</tr>
<tr class="even">
<td><p>Application Development</p></td>
<td><p>ASP.NET</p></td>
</tr>
<tr class="odd">
<td><p>Application Development</p></td>
<td><p>.NET Extensibility</p></td>
</tr>
<tr class="even">
<td><p>Application Development</p></td>
<td><p>ISAPI Extensions</p></td>
</tr>
<tr class="odd">
<td><p>Application Development</p></td>
<td><p>ISAPI Filters</p></td>
</tr>
<tr class="even">
<td><p>Health and Diagnostics</p></td>
<td><p>Logging Tools</p></td>
</tr>
<tr class="odd">
<td><p>Health and Diagnostics</p></td>
<td><p>Tracing</p></td>
</tr>
<tr class="even">
<td><p>Security</p></td>
<td><p>Basic Authentication</p></td>
</tr>
<tr class="odd">
<td><p>Security</p></td>
<td><p>Windows Authentication</p></td>
</tr>
<tr class="even">
<td><p>Management Tools</p></td>
<td><p>IIS Management Scripts and Tools</p></td>
</tr>
<tr class="odd">
<td><p>Management Tools</p></td>
<td><p>IIS 6 Management Compatibility</p></td>
</tr>
</tbody>
</table>


<div>

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398321.security(OCS.15).gif" title="security" alt="security" />Security Note:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>If you are using IIS 7.0 on a Windows Server 2008 operating system, Lync Server Setup disables kernel mode authentication in IIS.</td>
</tr>
</tbody>
</table>


</div>

<div>

## In This Section

  - [IIS requirements for Front End pools and Standard Edition servers in Lync Server 2013](lync-server-2013-iis-requirements-for-front-end-pools-and-standard-edition-servers.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

