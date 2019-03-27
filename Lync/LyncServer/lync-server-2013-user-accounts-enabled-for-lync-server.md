---
title: 'Lync Server 2013: User accounts enabled for Lync Server'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: User accounts enabled for Lync Server 2013
ms:assetid: 8021087e-5084-4a39-9fef-ab9376c6d371
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg182543(v=OCS.15)
ms:contentKeyID: 48184651
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# User accounts enabled for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-04-18_

Topics in this section provide step-by-step procedures for configuring user settings that you can perform using the Lync Server 2013 Control Panel.

<div>


> [!IMPORTANT]  
> You cannot use Lync Server Control Panel to manage users who are members of the Active Directory Domain Admins group. For Domain Admins users, you can use Lync Server Control Panel only to perform read-only search operations. To perform write operations on Domain Admins users (for example, enable or disable for Lync Server Control Panel, change pool or policy assignments, telephony settings, SIP address), you must use Windows PowerShell cmdlets while logged on as a Domain Admins user. For details about using Windows PowerShell cmdlets to manage users, see <A href="lync-server-2013-lync-server-management-shell.md">Lync Server 2013 Management Shell</A>.



</div>

When you perform any Lync Server 2013 administrative task that involves searching for a user or filtering user search results, there are some user properties that exist as attributes in Active Directory Domain Services but are not replicated to the global catalog until Microsoft Exchange Server is deployed. Microsoft Exchange, not Lync Server, marks the following attributes for replication to the global catalog when it is installed:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>User Information</th>
<th>Address and Phone</th>
<th>Organization</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Initials</p></td>
<td><p>Street address</p>
<p>Country/region</p>
<p>Pager</p>
<p>Fax</p>
<p>Mobile</p></td>
<td><p>Title</p>
<p>Company</p>
<p>Department</p>
<p>Office</p></td>
</tr>
</tbody>
</table>


<div>

## In This Section

  - [Viewing information about user accounts enabled for Lync Server 2013](lync-server-2013-viewing-information-about-user-accounts-enabled-for-lync-server.md)

  - [Enabling and disabling users for Lync Server 2013](lync-server-2013-enabling-and-disabling-users-for-lync-server.md)

  - [Managing Enterprise Voice for users in Lync Server 2013](lync-server-2013-managing-enterprise-voice-for-users.md)

  - [Modifying user account properties in Lync Server 2013](lync-server-2013-modifying-user-account-properties.md)

  - [Manage external access policy in Lync Server 2013](lync-server-2013-manage-external-access-policy-for-your-organization.md)

  - [Assigning per-user policies in Lync Server 2013](lync-server-2013-assigning-per-user-policies.md)

</div>

<div>

## See Also


[User management cmdlets in Lync Server 2013](lync-server-2013-user-management-cmdlets.md)  


[Managing users in Lync Server 2013](lync-server-2013-managing-users-in-lync-server.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

