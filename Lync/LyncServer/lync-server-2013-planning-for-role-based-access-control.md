---
title: 'Lync Server 2013: Planning for role-based access control'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Planning for role-based access control (RBAC)
ms:assetid: 41204ba3-ce5b-41a8-a6c3-b444468fa328
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425917(v=OCS.15)
ms:contentKeyID: 48183962
ms.date: 01/28/2015
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Planning for role-based access control in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2015-01-27_

To enable you to delegate administrative tasks while maintaining high standards for security, Lync Server 2013 offers role-based access control (RBAC). With RBAC, administrative privilege is granted by assigning users to administrative roles. Lync Server 2013 includes a rich set of built-in administrative roles, and also enables you to create new roles and specify a custom list of cmdlets for each new role. You can also add scripts of cmdlets to the allowed tasks of both predefined and custom RBAC roles.

<div>

## Better Server Security and Centralization

With RBAC, access and authorization is based precisely on a user’s Lync Server role. This enables use of the security practice of "least privilege," granting administrators and users only the rights that are necessary for their job.

<div>


> [!IMPORTANT]  
> RBAC restrictions work only on administrators working remotely, using either the Lync Server Control Panel or Lync Server Management Shell. A user sitting at a server running Lync Server is not restricted by RBAC. Therefore, physical security of your Lync Server is important to preserve RBAC restrictions.



</div>

</div>

<div>

## Roles and Scope

In RBAC, a *role* is enabled to use a list of cmdlets, designed to be useful for a certain type of administrator or technician. A *scope* is the set of objects which the cmdlets defined in a role can operate on. The objects that scope affects can be either user accounts (grouped by organizational unit) or servers (grouped by site).

The following table lists the predefined roles in Lync Server, and gives a general overview of the types of tasks each can do. The fourth column shows the similar Microsoft Exchange Server role for each Lync Server role, if there is one.

### Predefined Administrative Roles

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Role</th>
<th>Tasks allowed</th>
<th>Underlying Active Directory group</th>
<th>Exchange equivalent</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CsAdministrator</p></td>
<td><p>Can perform all administrative tasks and modify all settings, including creating roles and assigning users to roles. Can expand a deployment by adding new sites, pools, and services.</p></td>
<td><p>CSAdministrator</p></td>
<td><p>Organization Management</p></td>
</tr>
<tr class="even">
<td><p>CsUserAdministrator</p></td>
<td><p>Can enable and disable users for Lync Server, move users and assign existing policies to users. Cannot modify policies.</p></td>
<td><p>CSUserAdministrator</p></td>
<td><p>Mail Recipients</p></td>
</tr>
<tr class="odd">
<td><p>CsVoiceAdministrator</p></td>
<td><p>Can create, configure, and manage voice-related settings and policies.</p></td>
<td><p>CSVoiceAdministrator</p></td>
<td><p>Not applicable</p></td>
</tr>
<tr class="even">
<td><p>CsServerAdministrator</p></td>
<td><p>Can manage, monitor, and troubleshoot servers and services. Can prevent new connections to servers, stop and start services, and apply software updates. Cannot make changes with global configuration impact.</p></td>
<td><p>CSServerAdministrator</p></td>
<td><p>Server Management</p></td>
</tr>
<tr class="odd">
<td><p>CsViewOnlyAdministrator</p></td>
<td><p>Can view the deployment, including user and server information, in order to monitor deployment health.</p></td>
<td><p>CSViewOnlyAdministrator</p></td>
<td><p>View-Only Organization Management</p></td>
</tr>
<tr class="even">
<td><p>CsHelpDesk</p></td>
<td><p>Can view the deployment, including user's properties and policies. Can run specific troubleshooting tasks. Cannot change user properties or policies, server configuration, or services.</p></td>
<td><p>CSHelpDesk</p></td>
<td><p>HelpDesk</p></td>
</tr>
<tr class="odd">
<td><p>CsArchivingAdministrator</p></td>
<td><p>Can modify archiving configuration and policies.</p></td>
<td><p>CSArchivingAdministrator</p></td>
<td><p>Retention Management, Legal Hold</p></td>
</tr>
<tr class="even">
<td><p>CsResponseGroupAdministrator</p></td>
<td><p>Can manage the configuration of the Response Group application within a site.</p></td>
<td><p>CSResponseGroupAdministrator</p></td>
<td><p>Not applicable</p></td>
</tr>
<tr class="odd">
<td><p>CsLocationAdministrator</p></td>
<td><p>Lowest level of rights for Enhanced 9-1-1 (E9-1-1) management, including creating E9-1-1 locations and network identifiers, and associating these with each other. This role is always assigned with a global scope.</p></td>
<td><p>CSLocationAdministrator</p></td>
<td><p>Not applicable</p></td>
</tr>
<tr class="even">
<td><p>CsResponseGroupManager</p></td>
<td><p>Can manage specific response groups.</p></td>
<td><p>CSResponseGroupManager</p></td>
<td><p>Not applicable</p></td>
</tr>
<tr class="odd">
<td><p>CsPersistentChatAdministrator</p></td>
<td><p>Can manage the Persistent Chat feature and specific Persistent Chat rooms.</p></td>
<td><p>CSPersistentChatAdministrator</p></td>
<td><p>Not applicable</p></td>
</tr>
</tbody>
</table>


All predefined roles shipped in Lync Server have a global scope. To follow least privilege practices, you should not assign users to roles with global scope if they are going to administer only a limited set of servers or users. To accomplish this, you can create roles which are based on an existing role, but with a more limited scope.

<div>

## Creating a Scoped Role

When you create a role with limited scope (a scoped role), you specify the scope, along with the existing role it is based on and the Active Directory group to be assigned the role. The Active Directory group you specify must already be created. The following cmdlet is an example of a creating a role which has the privileges of one of the pre-defined administrative roles, but with limited scope. It creates a new role called `Site01 Server Administrators`. The role has the abilities of the predefined CsServerAdministrator role, but only for the servers located in the Site01 site. For this cmdlet to work, the Site01 site must already be defined, and a universal security group named `Site01 Server Administrators` must already exist.

    New-CsAdminRole -Identity "Site01 Server Administrators" -Template CsServerAdministrator -ConfigScopes "site:Site01"

After this cmdlet runs, all users who are members of the `Site01 Server Administrators` group will have server administrator privileges for the servers in Site01. Additionally, any users who are later added to this universal security group also gain the privileges of this role. Note that both the role itself, and the universal security group it is assigned to are called `Site01 Server Administrators`.

The following example limits user scope instead of server scope. It creates a `Sales Users Administrator` role to administer the user accounts in the Sales organizational unit. The SalesUsersAdministrator universal security group must already be created for this cmdlet to work.

    New-CsAdminRole -Identity "Sales Users Administrator " -Template CsUserAdministrator -UserScopes "OU:OU=Sales, OU=Lync Tenants, DC=Domain, DC=com"

</div>

<div>

## Creating a New Role

To create a role that has access to a set of cmdlets not in one of the predefined roles, or to a set of scripts or modules, you again start by using one of the predefined roles as a template. Note that scripts and modules that roles are to be able to run must be stored in the following locations:

  - The Lync module path, which is by default C:\\Program Files\\Common Files\\Microsoft Lync Server 2013\\Modules\\Lync

  - The user script path, which is by default C:\\Program Files\\Common Files\\Microsoft Lync Server 2013\\AdminScripts

To make a new role, you use the **New-CsAdminRole** cmdlet. Before running **New-CsAdminRole**, you must first create the underlying universal security group that will be associated with this role.

The following cmdlets serve as an example of a creating a new role. They create a new role type called `MyHelpDeskScriptRole`. The new role has the abilities of the predefined CsHelpDesk role, and can additionally run the functions in a script named “testscript”.

    New-CsAdminRole -Identity "MyHelpDeskScriptRole" -Template CsHelpDesk -ScriptModules @{Add="testScript.ps1"}

For this cmdlet to work, you must have first created the universal security group MyHelpDeskScriptRole.

After this cmdlet runs, you can assign users directly to this role (in which case they have global scope), or create a scoped role based on this role, as explained in Creating a Scoped Role, previously in this document.

</div>

<div>

## Assigning Roles to Users

Each Lync Server role is associated with an underlying Active Directory universal security group. Any users who you add to the underlying group gain the abilities of that role.

The examples in the preceding sections both created a new role and assigned an existing universal security group to the new role. To assign an existing role to one or more users, add those users to the group associated with the role. You can add both individual users and universal security groups to these groups.

For example, the **CsAdministrator** role is automatically granted to the **CS Administrators** universal security group in Active Directory. This universal security group is created in Active Directory when you deploy Lync Server. To grant a user or group this privilege, you can simply add them to the **CS Administrators** group.

A user can be given multiple RBAC roles by being added to the underlying Active Directory groups that correspond to each role.

Note that when you create a role, users who are later added to the underlying Active Directory group gain the abilities of that role.

</div>

<div>

## Modifying the Abilities of a Role

You can modify the list of cmdlets and scripts that a role can run. You can modify both the cmdlets and scripts that custom roles can run, but you can modify only the scripts for predefined roles. Each cmdlet you type can add, remove, or replace cmdlets or scripts.

To modify a role, use the **Set-CsAdminRole** cmdlet. The following cmdlet removes one script from the role.

    Set-CsAdminRole -Identity "MyHelpDeskScriptRole" -ScriptModules @{Remove="testScript.ps1"}

</div>

</div>

<div>

## Planning for RBAC

For each person who is to be given any kind of administrative rights for your Lync Server deployment, consider exactly which tasks they need to perform, then assign them to roles with the least privilege and scope necessary for their job. If necessary, you can use the **Set-CsAdminRole** cmdlet to create a new role with only the cmdlets necessary for this person’s tasks.

Users who have the CsAdministrator role can create all types of roles, including roles based on CsAdministrator, and assign users to them. The best practice is to assign the CsAdministrator role to a very small set of trusted users.

</div>

</div>

<span> </span>

</div>

</div>

</div>

