---
title: 'Lync Server 2013: user models'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Lync Server 2013 user models
ms:assetid: c551371c-d740-4372-bada-f0d713ec0d33
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398811(v=OCS.15)
ms:contentKeyID: 49733811
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# User models in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-10-07_

The user models described here provide the basis for the capacity planning measurements and recommendations described in [Capacity planning for Lync Server 2013 using the user models](lync-server-2013-capacity-planning-using-the-user-models.md).

<div>

## Lync Server 2013 User Models

The following table describes the user model for registration, contacts, instant messaging (IM), and presence for Lync Server 2013.

### Environment and Registration User Model

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Category</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Deployment size and distribution</p></td>
<td><p>We model a large deployment with three central sites, with one Front End pool per site.</p></td>
</tr>
<tr class="even">
<td><p>Percentage of Active Directory users</p></td>
<td><p>We assume that 70% of all Active Directory users in the organization are enabled for Lync Server. 80% of those enabled users are logged on to Lync Server each day (80% concurrency). The concurrent users are the basis for the numbers in the rest of this section.</p></td>
</tr>
<tr class="odd">
<td><p>Active Directory changes</p></td>
<td><p>We assume that 0.5% of total users are created and enabled for Lync in Active Directory each week, and that 0.5% of total users are disabled from Active Directory and from Lync each week. 5% of users have at least one Active Directory attribute changed each week.</p></td>
</tr>
<tr class="even">
<td><p>Active Directory distribution groups</p></td>
<td><p>We assume that the number of Active Directory distribution groups in the organization is equal to three times the number of all users in Active Directory. The distribution groups have the following sizes:</p>
<ul>
<li><p>64% have 2-30 users</p></li>
<li><p>13% have 31-50 users</p></li>
<li><p>10% have 51-100 users</p></li>
<li><p>13% have 101-500 users</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Voice over IP (VoIP) users</p></td>
<td><p>60% of Lync Server users are enabled for unified communications (UC) (that is, their phone numbers are owned by Lync Server).</p></td>
</tr>
<tr class="even">
<td><p>Registered client distribution</p></td>
<td><p>65% of clients run Lync 2013 software, including Lync and Lync Phone Edition.</p>
<p>30% of clients running client software from a previous version of Lync.</p>
<p>5% of clients using Lync Web App.</p>
<p>If mobility is enabled, we assume that 40% of users are using mobility concurrently with the other previously cited registered client options. In this case the client multiple point of presence (MPOP) ratio is 1:1.9. If mobility is disabled, the MPOP ratio is 1:1.5.</p></td>
</tr>
<tr class="odd">
<td><p>Remote user distribution</p></td>
<td><p>70% of users connecting internally.</p>
<p>30% of users connecting through an Edge Server and a Director.</p></td>
</tr>
<tr class="even">
<td><p>Contact distribution</p></td>
<td><p>The maximum number of contacts a user has is 1,000. Less than 1% of users have 1,000 contacts. Less than 25% of users have 100 or more contacts.</p>
<p>Average of 80 contacts for users with public cloud connectivity. Of these users:</p>
<ul>
<li><p>50% of the contacts are within the organization. 10% of those users are remote users, connecting from outside the firewall.</p></li>
<li><p>40% of the contacts are public cloud users (such as users of AOL, Yahoo!, MSN, or Google Talk).</p></li>
<li><p>10% of the contacts are from federated partners.</p>
<div>

> [!IMPORTANT]  
> <UL>
> <LI>
> <P>As of September 1st, 2012, the Microsoft Lync Public IM Connectivity User Subscription License (“PIC USL”) is no longer available for purchase for new or renewing agreements. Customers with active licenses will be able to continue to federate with Yahoo! Messenger until the service shut down date. An end of life date of June 2014 for AOL and Yahoo! has been announced. For details, see <A href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Support for public instant messenger connectivity in Lync Server 2013</A>.</P>
> <LI>
> <P>The PIC USL is a per-user per-month subscription license that is required for Lync Server or Office Communications Server to federate with Yahoo! Messenger. Microsoft’s ability to provide this service has been contingent upon support from Yahoo!, the underlying agreement for which is winding down.</P>
> <LI>
> <P>More than ever, Lync is a powerful tool for connecting across organizations and with individuals around the world. Federation with Windows Live Messenger requires no additional user/device licenses beyond the Lync Standard CAL. Skype federation will be added to this list, enabling Lync users to reach hundreds of millions of people with IM and voice.</P></LI></UL>


</div></li>
</ul>
<p>Average of 50 contacts for users without public cloud connectivity. Of these users:</p>
<ul>
<li><p>80% of the contacts are within the organization. 10% of those users are remote users, connecting from outside the firewall.</p></li>
<li><p>20% of the contacts are from federated partners.</p>
<p>Each user has 1 distribution group in their contact list. For performance testing, we assume that distribution groups are always expanded.</p></li>
</ul>
<p>25% of a user’s contacts use XMPP.</p></td>
</tr>
<tr class="odd">
<td><p>Session time</p></td>
<td><p>The average user logon session lasts 12 hours. All users log on within 120 minutes of the start of the session.</p></td>
</tr>
</tbody>
</table>


### IM and Presence User Model

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Category</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Peer-to-peer IM sessions</p></td>
<td><p>Each user averages six peer-to-peer IM sessions per day.</p>
<p>10 instant messages per session.</p>
<p>Each message is matched by two SIP INFO messages and 2 SIP 200 OK messages (for the status indicators such as “&lt;Name&gt; is Typing”)</p></td>
</tr>
<tr class="even">
<td><p>Presence polling</p></td>
<td><p>Overall, we assume presence polling at an average of 60 polls per user per hour. For each user, assume an average of:</p>
<ul>
<li><p>One poll per day of the presence of users in the user’s organization tab (but not Contacts list). Average number of non-contacts in the user’s organization tab is 15 users. Two contact card viewing operations per day.</p></li>
<li><p>One presence poll every time the user clicks another user to start a conversation, estimated at once per hour.</p></li>
<li><p>Six user searches per hour. Every time a search is performed, a batch poll is sent for everyone in the search result list. We assume the average size of search results is 20. If the search results stay on screen, the batch poll is refreshed every 5 minutes; we assume that there will be two such refreshes per hour.</p></li>
<li><p>When the user opens or previews an email in Outlook, a poll of the presence of users in the To: and CC: fields of the email, estimated at five emails per hour and four users per email.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Presence subscriptions</p></td>
<td><p>When one user adds another as a contact, the first user is <em>subscribing</em> to five categories of information about the second user. Updates of these categories of information are automatically sent to the first user.</p>
<p>For each client, a single batch subscription request is sent to obtain the presence state of an average of 40 contacts, with an additional 40 dialogs to obtain presence for federated contacts.</p>
<p>Presence for members of an expanded distribution group is found through persistent presence subscriptions, not polling, and is modeled as 1 expansion per user for each 2 hours.</p>
<p><em>Short subscriptions</em> happen when a user logs in, there is a batch subscription for all the user’s contacts, and then the user soon logs off. We assume 6 short subscriptions per user per hour, where each subscription lasts 10 minutes.</p></td>
</tr>
<tr class="even">
<td><p>Presence Publication</p></td>
<td><p>Presence state is published at an average of 4 publications per user per hour, with a maximum 6 per user per hour.</p></td>
</tr>
<tr class="odd">
<td><p>Presence Document Size</p></td>
<td><p>The average size of a complete presence document is assumed to be 4K, with a maximum of 25K.</p></td>
</tr>
</tbody>
</table>


The following table describes the user model for address book use.

### Address Book Usage User Model

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Address Book search mode</th>
<th>Usage</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Address Book Web Query only (all queries performed by Address Book Web Query service)</p></td>
<td><p>Four prefix queries per user per day.</p>
<p>60 exact search queries per user per day. 40% of those are batched, with an average of 20 contacts per query. The other 60% of the queries are for a single contact.</p>
<p>25 photo queries per user per day. 24 are for a single photo, the other is a batch query with an average of 20 contacts.</p>
<p>One total organization search query per user per day.</p></td>
</tr>
<tr class="even">
<td><p>Mixed mode, both address book file and web queries used. This is the default mode.</p></td>
<td><p>Only two types of queries go to the network, the photo and total organizational search queries.</p>
<p>25 photo queries per user per day. 24 are for a single photo, the other is a batch query with an average of 20 contacts.</p>
<p>One total organization search query per user per day.</p></td>
</tr>
</tbody>
</table>


The following table describes the conferencing model.

### Conferencing Model

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Category</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Scheduled meetings versus &quot;Meet now&quot; meetings</p></td>
<td><p>60% scheduled, 40% unscheduled.</p>
<p>Of the scheduled meetings, we assume that 80% are assigned conferences, which are occurences of recurring conferences; 10% are one-time open meetings; 8% are one-time anonymous meetings, and 2% are one-time closed meetings.</p></td>
</tr>
<tr class="even">
<td><p>Conferencing client distribution</p></td>
<td><p>For scheduled meetings:</p>
<ul>
<li><p>65% of conferencing users use Lync 2013.</p></li>
<li><p>5% of conferencing users use Microsoft Lync Web App.</p></li>
<li><p>30% of conferencing users use earlier clients, including Microsoft Lync 2010, Office Communicator 2007 R2, Office Communicator 2007, and Microsoft Office Communicator Web Access (2007 release).</p></li>
</ul>
<p>For unscheduled meetings:</p>
<ul>
<li><p>70% of conferencing users use Lync 2013.</p></li>
<li><p>30% of conferencing users use earlier clients, including Microsoft Lync 2010, Office Communicator 2007 R2, Office Communicator 2007, and Microsoft Office Communicator Web Access (2007 release).</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Meeting concurrency</p></td>
<td><p>5% of users will be in conferences during working hours. Thus, in an 80,000-user pool, as many as 4,000 users might be in conferences at any one time.</p></td>
</tr>
<tr class="even">
<td><p>Meeting audio distribution</p></td>
<td><p>40% mixed VoIP audio and dial-in conferencing, with a 3:1 ratio of VoIP users to dial-in users.</p>
<p>35% VoIP audio only.</p>
<p>15% dial-in conferencing audio only.</p>
<p>10% no audio (IM-only conferences, with an average of five messages sent per user).</p></td>
</tr>
<tr class="odd">
<td><p>Media mix for conferences</p></td>
<td><p>75% of conferences are web conferences, which include audio plus some other collaboration modalities.</p>
<p>For these conferences, the other collaboration methods are as follows:</p>
<div>

> [!NOTE]  
> These numbers add up to more than 100% because one conference can have multiple collaboration methods.


</div>
<ul>
<li><p>50% add application sharing. We assume one users sends data at a peak of 1.1 MB per second.</p></li>
<li><p>50% add instant messaging (with an average of 2 messages per user).</p></li>
<li><p>20% add data collaboration, including PowerPoint or whiteboard In these, an average of 2 PowerPoint files presented per conference, with an average PowerPoint file size of 10 MB (without embedded video) or 30 MB (with embedded video). Average of 20 annotations per whiteboard.</p></li>
<li><p>20% add video. Of these users, 70% are in conferences enabled for multiview video, where each user receives 2-3 video streams.</p></li>
<li><p>15% add shared notes.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Meeting participant distribution</p></td>
<td><p>50% internal, authenticated users.</p>
<p>25% remote access, authenticated users.</p>
<p>15% anonymous users.</p>
<p>10% federated users.</p></td>
</tr>
<tr class="odd">
<td><p>Meeting join distribution</p></td>
<td><p>Users are simulated as joining the meeting within the first 5 minutes.</p></td>
</tr>
</tbody>
</table>


In regular Front End pools, Lync Server 2013 has a maximum supported meeting size of 250 users. Each pool can host one 250-user meeting at a time. While this large meeting is occurring, the pool can also host other smaller conferences. Additionally, you can support meetings of up to 1000 users by setting up a dedicated pool to host these meetings. For details, see [Support for large meetings in Lync Server 2013](lync-server-2013-support-for-large-meetings.md).

Conferences were simulated as follows:

  - 85% of conferences had four participants.

  - 10% of conferences had six participants.

  - 5% of conferences had 11 participants.

  - One large conference of 250 users.

The following table provides details about the user model for conferences involving dial-in users.

### Dial-In Conferencing User Model

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Category</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Authenticated/anonymous</p></td>
<td><p>70% of callers join as anonymous and are prompted for a recorded name. 30% join as authenticated users.</p></td>
</tr>
<tr class="even">
<td><p>Call duration and music on hold</p></td>
<td><p>Average call duration without music on hold: 50 seconds.</p>
<p>50% of call-in users hear music on hold, for an average of 5 minutes.</p></td>
</tr>
<tr class="odd">
<td><p>Dual-tone multifrequency (DTMF)</p></td>
<td><p>15% of conferences that are dial-in only have phone leaders. 10% of mixed conferences that include dial-in users also have phone leaders.</p>
<p>20% of phone leaders use 2 DTMF commands per conference.</p></td>
</tr>
<tr class="even">
<td><p>Announcement languages</p></td>
<td><p>Simulations use English as the announcement language.</p></td>
</tr>
</tbody>
</table>


The following table provides details about the user model for conference lobbies.

### Conference Lobby User Model

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Category</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Number of users in lobby</p></td>
<td><p>5% of dial-in users go through the lobby, and 25% of other users go through the lobby</p></td>
</tr>
<tr class="even">
<td><p>Admitting from lobby</p></td>
<td><p>In simulations, all users were admitted by the presenter before client timeout.</p></td>
</tr>
</tbody>
</table>


The following table describes the user model for other peer-to-peer sessions.

### Peer-to-Peer Sessions User Model

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Category</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Application sharing</p></td>
<td><p>Each user participates in 5 peer-to-peer application sharing sessions per month, for an average of 0.25 sessions per day.</p></td>
</tr>
<tr class="even">
<td><p>File transfer</p></td>
<td><p>Each user participates in 1 peer-to-peer file transfer session per month (as part of an IM session), for an average of 0.05 sessions per day. The average session file size transferred is 1 MB.</p></td>
</tr>
</tbody>
</table>


The following table describes the user model for policies.

### Policies User Model

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Category</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Conferencing, Presence, and Archiving Policies</p></td>
<td><p>We assume that there is one global policy, 10 tag conferencing policies, 4 Archiving policies, and 10 tag presence policies.</p></td>
</tr>
<tr class="even">
<td><p>Voice Policy</p></td>
<td><p>We assume that there is one global policy and 2 tag policies per site. 100% of sites have a site policy, and 30% of users have a per-user policy assigned. We assume one dial plan per site and two routes per site.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Busy Hour

For peer-to-peer sessions, peak load is calculated using busy hour call attempts (BHCA). This voice industry term assumes that 50% of all calls for the day will be completed in 20% of the time. It is calculated using the following formula:

`BHCA=(total calls * 0.5) / 1.6`

Performance testing simulated busy hour by running VoIP and other peer-to-peer sessions at a busy hour load for at least 1.6 hours per day.

Conferencing peak load assumes that 75% of all conferences for an eight-hour day happen in 4 peak time hours. Those peak hours have 1.5 times the average conferencing load.

</div>

<div>

## Enterprise Voice to PSTN Calls

The following assumptions apply to Enterprise Voice calls:

  - 50% of users are enabled for Enterprise Voice, and 60% of these users are enabled for PSTN calling.

  - Each of these users enabled for PSTN calling makes 4 PSTN calls during the busy hour. Each call duration is 3 minutes.

  - 65% of these PSTN voice calls use media bypass.

</div>

<div>

## Mobility

40% of registered users are assumed to be enabled for Mobility. For each user that has mobility enabled, we assume that the activity of the mobile client is additive to that of the other MPOP instances for that user, with the exception of conferencing interactions, for which the mobility client is just another client type that can be used to participate in conferences.

</div>

<div>

## Persistent Chat

We assume that 25% of registered users will be involved in Persistent chat sessions, with the following characteristics:

  - An average of 1.5 chat rooms per user

  - Each chat room results in 12 polling requests per hour, targeting an average of 10 users each

</div>

<div>

## Response Group and Call Park

We assume that 0.15% of registered users belong to response groups. We assume that 0.02% of registered users have parked calls at any given point of time.

</div>

</div>

<span> </span>

</div>

</div>

</div>

