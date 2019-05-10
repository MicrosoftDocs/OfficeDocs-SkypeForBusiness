---
title: Lync Server 2013 user experience during pool failure
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: User experience during pool failure
ms:assetid: b224b0d0-87e3-4cac-ae87-f45f54fabb49
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205184(v=OCS.15)
ms:contentKeyID: 48185166
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# User experience during pool failure in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-03_

If a pool is failed over, all users of the affected pool are forced to sign out and then sign into the backup pool. For a brief period users who sign into the backup pool may be in resiliency mode. In Resiliency mode, users are unable to perform tasks that would cause a persistent change on Lync Server, such as adding a contact. After the failover is complete, all users can get all services from the backup pool.

Any sessions a user has when the pool fails are disrupted, and the user must re-establish those sessions after failover to continue.

Users are not rehomed during failover or failback. Users who are homed on a pool that fails will be temporarily serviced by the backup pool. When the home pool is restored, the administrator can fail back these users to be serviced by their original home pool.

Note in Lync 2013, the Location Information Server database is not replicated to the backup pool. For best practice, the administrator should regularly back up the LIS database and use the latest backup copy to restore the LIS database in the backup pool after the failover.

<div>

## User Experience During Failover

When a user is in a pool that fails, the user is logged out. Any peer-to-peer session the user was participating in is terminated, as are conferences organized by that user. The user cannot log back in until either the registrar resiliency timer expires or the administrator initiates failover procedures, whichever comes first. When the user logs back in, they will log in to the backup pool. If they log in before the failover has completed, they will be in Resiliency mode until failover is complete. Only then the user is able to establish new sessions or re-establish previous sessions.

</div>

<div>

## User Experience During Failback

Pool failback can happen while an affected user is logged on to the backup pool, and the user remains logged on and working during the failback. Note that the failback process takes several minute to complete.  For reference, it is expected to take up to 60 minutes for a pool of 20,000 users.

The following tables show more details about how a user with a Lync 2013 client or a Microsoft Lync 2010 client is affected during and after failback, and also how users in other pools see and interact with a user in a pool who is being failed back. Users with Microsoft Office Communicator 2007 R2 clients cannot sign in until the Front End pool is completely failed back.)

The term *affected user* refers to any user who was failed over from the home pool and is being serviced by the backup pool. By definition, any user originally homed on the backup pool is not an affected user.

### User Experience for an Affected User in a Pool in Failback

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>User state or task</th>
<th>During failback</th>
<th>After failback completion</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>User state of user already logged in</p></td>
<td><p>User stays signed in and connected to backup pool. At some point user will be signed out and sign back in to the original home pool, in Resiliency mode.</p></td>
<td><p>User remains signed in and goes into regular mode.</p></td>
</tr>
<tr class="even">
<td><p>New user logging in</p></td>
<td><p>User can sign in to the home pool in Resiliency mode.</p></td>
<td><p>User can sign in to the original home pool in regular mode.</p></td>
</tr>
<tr class="odd">
<td><p>Ongoing conferences organized by affected user</p></td>
<td><p>All modalities of conference are terminated. Rejoin button will appear, but no users can rejoin while the affected user is in Resiliency mode.</p></td>
<td><p>All modalities now work. Every participant needs to click to rejoin the conference.</p></td>
</tr>
<tr class="even">
<td><p>Ongoing conferences organized by unaffected user</p></td>
<td><p>Conference continues and affected user can stay in the conference. Affected user is restricted to what he/she can do in Resiliency mode.</p></td>
<td><p>Conference continues, and affected user can stay in the conference and all modalities work after user exits Resiliency mode.</p></td>
</tr>
<tr class="odd">
<td><p>Scheduling or modifying scheduled meetings, creating ad-hoc conferences</p></td>
<td><p>Not possible while user is in Resiliency mode.</p></td>
<td><p>Available for all modalities.</p></td>
</tr>
<tr class="even">
<td><p>Presence as seen by other users in the same pool</p></td>
<td><p>Presence unknown while user is signed into backup pool during Resiliency mode.</p></td>
<td><p>Shows the last presence state set by the user, and presence changes will now be reflected.</p></td>
</tr>
<tr class="odd">
<td><p>Contacts list and Address Book Service availability</p></td>
<td><p>Not available</p></td>
<td><p>Available</p></td>
</tr>
<tr class="even">
<td><p>All peer-to-peer sessions and modalities</p></td>
<td><p>Available</p></td>
<td><p>Available</p></td>
</tr>
</tbody>
</table>


### User Experience for a User Homed in an Unaffected Pool During Failback of Another Pool

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>User task</th>
<th>During failback</th>
<th>After failback completion</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Viewing presence of affected user</p></td>
<td><p>Shows the last presence state set by the affected user.</p></td>
<td><p>Working. Unaffected users see updates made by affected users.</p></td>
</tr>
<tr class="even">
<td><p>Ongoing conferences organized by affected user</p></td>
<td><p>All modalities of conference are terminated.</p></td>
<td><p>All modalities now work. Every participant needs to click to rejoin the conference.</p></td>
</tr>
<tr class="odd">
<td><p>Ongoing conferences organized by unaffected user</p></td>
<td><p>Conference continues, and affected user can stay in the conference and all modalities work.</p></td>
<td><p>Conference continues, and affected user can stay in the conference and all modalities work.</p></td>
</tr>
<tr class="even">
<td><p>All peer-to-peer sessions and modalities</p></td>
<td><p>Available</p></td>
<td><p>Available</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

