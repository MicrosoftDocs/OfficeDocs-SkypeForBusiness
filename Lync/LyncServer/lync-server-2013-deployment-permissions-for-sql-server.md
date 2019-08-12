---
title: 'Lync Server 2013: Deployment permissions for SQL Server'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Deployment permissions for SQL Server
ms:assetid: 56ea0c02-bcf5-4d45-aa13-570531c29074
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398375(v=OCS.15)
ms:contentKeyID: 48184197
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Deployment permissions for SQL Server in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-01_

Microsoft SQL Server 2012 has specific requirements when installing and deploying Lync Server 2013. Because Windows and SQL Server define their security differently, logging in as an administrator in the Active Directory domain does not implicitly grant permissions for SQL Server. You must also be a member of the sysadmin entity on the SQL Server-based server you are configuring.

<div>

## Permissions Required for Database and Lync Server Installation

The following options detail three permissions and group membership associations for installation of Lync Server 2013 files and SQL Server databases. Choose the scenario that best meets the requirements of your organization.

### Permissions and Group Membership Associations

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>SQL Server or Lync Server 2013 role</th>
<th>Role-Typical SQL Server permissions and group membership</th>
<th>Role-typical Lync Server 2013 permissions and group membership</th>
<th>Permissions outcome</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync Server 2013 administrator</p></td>
<td><p>Must be granted membership of sysadmins SQL Server security group and member of the SQL Server local Administrators group</p></td>
<td><p>Must be a member of the RTCUniversalServerAdmins group</p></td>
<td><p>Lync Server 2013 administrator has the proper permissions to install both Lync Server 2013 and SQL Server databases.</p></td>
</tr>
<tr class="even">
<td><p>SQL Server administrator</p></td>
<td><p>SQL Server sysadmin group member (or equivalent) and member of the SQL Server local Administrators group</p></td>
<td><p>Must be a member of the RTCUniversalServerReadOnly group</p></td>
<td><p>SQL Server administrator has the proper permissions to install both Lync Server 2013 and SQL Server databases.</p></td>
</tr>
<tr class="odd">
<td><p>Both administrators sharing installation duties</p></td>
<td><p>SQL Server administrator is member of sysadmins group (or equivalent) and member of the SQL Server local Administrators group</p></td>
<td><p>Lync Server 2013 administrator is member of RTCUniversalServerAdmins</p></td>
<td><p>The Lync Server 2013 administrator can install Lync Server 2013, but cannot install the databases. The SQL Server administrator uses the Lync Server Management Shell and Windows PowerShell cmdlets provided by the Lync Server 2013 administrator to install the databases. The Lync Server 2013 Management Shell used by the SQL Server administrator is installed on the Front End Server. This eliminates the need to install the Lync Server 2013 administrative tools on the SQL Server-based server.</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

