---
title: 'Lync Server 2013: List of Persistent Chat Server tables'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: List of Persistent Chat Server tables
ms:assetid: 26c9e271-3516-4d90-b930-70fec4e359ea
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg558628(v=OCS.15)
ms:contentKeyID: 48183659
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# List of Persistent Chat Server tables in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-06_

The Persistent Chat database schema consists of the following tables.

<div>

## Active Directory Sync


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Table</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-tbladcookie.md">tblADCookie in Lync Server 2013</a></p></td>
<td><p>Contains the current Lightweight Directory Access Protocol (LDAP) Sync cookies. Each row corresponds to an Active Directory Domain Services domain that Persistent Chat Server is actively monitoring for changes. (Only the Active Directory domains that are relevant for Persistent Chat Server are represented in this table.)</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tblprincipalmemberdifference.md">tblPrincipalMemberDifference in Lync Server 2013</a></p></td>
<td><p>Contains group membership changes (both added and removed members) that have not yet been processed by the later Active Directory Sync steps and is one of the temporary tables (along with tblADUpdates table) that is used in the first step of Active Directory Sync.</p>
<p>Membership changes are stored, processed, or both, only for groups that are listed in the tblPrincipal table or that already have members listed there.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-tbladupdates.md">tblADUpdates in Lync Server 2013</a></p></td>
<td><p>Contains changes to Active Directory Domain Services that have not yet been processed by the later Active Directory Sync steps and is one of the temporary tables (along with the tblPrincipalMemberDifference table) that is used in the first step of Active Directory Sync.</p>
<p>Changes to Active Directory are stored, processed, or both only for principals that are already listed in the tblPrincipal table.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tblprincipalmembers.md">tblPrincipalMembers in Lync Server 2013</a></p></td>
<td><p>Contains principal memberships.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-tblprincipalmeta.md">tblPrincipalMeta in Lync Server 2013</a></p></td>
<td><p>Contains the principals that have to be refreshed from Active Directory.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tblskippedaffiliations.md">tblSkippedAffiliations in Lync Server 2013</a></p></td>
<td><p>Contains affiliations that could not be refreshed for some reason, usually due to Active Directory access errors.</p>
<p>This table is for informational purposes only. Its content is not used.</p>
<p>The principals with affiliations that could not be refreshed properly are kept in the tblPrincipalMeta table and are given another chance to be refreshed.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Principals, Affiliations, Nodes, Scopes, and Roles


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Table</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-tblprincipaltype.md">tblPrincipalType in Lync Server 2013</a></p></td>
<td><p>Contains principal types to categorize what is in the tblPrincipal table. This table is static. It is set up during database creation and does not change.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tblprincipal.md">tblPrincipal in Lync Server 2013</a></p></td>
<td><p>Contains all principals (users, folders, groups, and so on). Persistent Chat Server handles this as a flat heterogeneous list. Various columns are based on the type of each principal.</p>
<p>Most of these principals are cached copies of objects stored in Active Directory. Creating the cached copy in the Principal table of these Active Directory objects is referred as <em>provisioning</em>.</p>
<p>Some principals are created more aggressively than others, and some Active Directory objects are ignored altogether.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-tblprincipalaffiliations.md">tblPrincipalAffiliations in Lync Server 2013</a></p></td>
<td><p>Contains principal affiliations that describe memberships in Active Directory security groups, Active Directory containers, and so on.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tblnode.md">tblNode in Lync Server 2013</a></p></td>
<td><p>Contains the category node, as managed in Lync Server Control Panel.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-tblroletype.md">tblRoleType in Lync Server 2013</a></p></td>
<td><p>Contains role types and their associated permission sets. This lookup table is static.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tblscopeprincipal.md">tblScopePrincipal in Lync Server 2013</a></p></td>
<td><p>Contains scopes assigned to nodes.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-tblprincipalrole.md">tblPrincipalRole in Lync Server 2013</a></p></td>
<td><p>Contains roles assigned to nodes.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tblsiopwhitelist.md">tblSiopWhiteList in Lync Server 2013</a></p></td>
<td><p>Contains the registered Add-ins that can be associated with nodes.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-tblenumattribute.md">tblEnumAttribute in Lync Server 2013</a></p></td>
<td><p>Contains only the hardcoded &quot;Visibility&quot; and &quot;Behavior&quot; attributes that are used in the tblNode table.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tblenumvalue.md">tblEnumValue in Lync Server 2013</a></p></td>
<td><p>Contains the values of the hardcoded &quot;Visibility” and “Behavior&quot; attributes that are used in the tblNode table.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Invites, Chats, and Other Client Support


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Table</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-tblprincipalinvites.md">tblPrincipalInvites in Lync Server 2013</a></p></td>
<td><p>Contains invites for all provisioned users in the system for all nodes with Auto Invite enabled.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tblchat.md">tblChat in Lync Server 2013</a></p></td>
<td><p>Contains all chat messages.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-tbllastinviteid.md">tblLastInviteId in Lync Server 2013</a></p></td>
<td><p>Contains the last invite ID that was generated (and used in the tblPrincipalInvites table) for each user.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tbllastchatid.md">tblLastChatId in Lync Server 2013</a></p></td>
<td><p>Contains the last chat ID that was generated (and used in the tblChat table) for each user.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-tblpreference.md">tblPreference in Lync Server 2013</a></p></td>
<td><p>Contains user client preferences (used by legacy clients only).</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tblfiletoken.md">tblFileToken in Lync Server 2013</a></p></td>
<td><p>Contains temporary tokens for file transfer purposes. Each time a file is uploaded or downloaded, the Persistent Chat service generates a token that the client uses to access the Web service file store.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Server Support


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Table</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-tblserveridentity.md">tblServerIdentity in Lync Server 2013</a></p></td>
<td><p>Contains the active servers in the Persistent Chat Server pool.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tbladminlock.md">tblAdminLock in Lync Server 2013</a></p></td>
<td><p>Contains the administrator lock to run some administrator commands. The system revision entry in the tblSystemRevision table is incremented after each release of the lock.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-tblsystemrevision.md">tblSystemRevision in Lync Server 2013</a></p></td>
<td><p>Contains the revision number entry used (along with the tblAdminLock table) for achieving consistency across multiple servers.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tblactivepeers.md">tblActivePeers in Lync Server 2013</a></p></td>
<td><p>Contains current peer-to-peer connections between Persistent Chat services.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-tblconfig.md">tblConfig in Lync Server 2013</a></p></td>
<td><p>Contains the Persistent Chat Server unsupported configuration.</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

