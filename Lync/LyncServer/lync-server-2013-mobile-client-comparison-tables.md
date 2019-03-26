---
title: 'Lync Server 2013: Mobile client comparison tables'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Mobile client comparison tables
ms:assetid: f3ba3379-afe4-4bc8-a038-9dff9dfd3bff
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Hh691004(v=OCS.15)
ms:contentKeyID: 51541531
ms.date: 09/21/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Mobile client comparison tables for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2015-09-21_

The following tables compare the features and capabilities among Lync 2013 mobile clients and the Lync 2013 desktop client in the following categories:

  - Sign-in, push notifications, and general features

  - Enhanced presence

  - Contacts and contact groups

  - Instant messaging (IM)

  - Lync-to-Lync audio and video

  - Conferencing

  - Telephony

  - External users

  - Archiving and compliance

These tables indicate the features that are available to Lync users in an on-premises deployment of Lync Server 2013. The same features are also available to Skype for Business Online and Microsoft Office 365 users, unless otherwise indicated in the table footnotes.

<div>


> [!NOTE]  
> <UL>
> <LI>
> <P>Looking for the mobile client comparison tables for Skype for Business? See <A href="https://technet.microsoft.com/en-us/library/dn951412.aspx">Mobile client comparison tables for Skype for Business</A>.</P>
> <LI>
> <P>For online help and resources for end users, see <A href="http://go.microsoft.com/fwlink/?linkid=286237">Microsoft Lync 2013 for Mobile Clients</A>.</P>
> <LI>
> <P>To compare the features available in other Lync 2013 clients, see <A href="lync-server-2013-desktop-client-comparison-tables.md">Client comparison tables for Lync Server 2013</A>.</P>
> <LI>
> <P>Lync Server 2013 also supports Lync 2010 mobile apps. For details, see <A href="http://go.microsoft.com/fwlink/p/?linkid=234777">Mobile Client Comparison Tables</A> in the Lync Server 2010 documentation.</P></LI></UL>



</div>

<div>

## Sign-in, Push Notifications, and General Features


<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Feature/Capability</th>
<th>Lync 2013 desktop client</th>
<th>Windows Phone</th>
<th>iPhone</th>
<th>iPad</th>
<th>Android</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync session remains signed in</p></td>
<td><p>●</p></td>
<td><p>●1</p></td>
<td><p>●1</p></td>
<td><p>●1</p></td>
<td><p>●1</p></td>
</tr>
<tr class="even">
<td><p>Support for push notifications</p></td>
<td></td>
<td><p>●</p></td>
<td><p>4Not required</p></td>
<td><p>4Not required</p></td>
<td><p>4Not required</p></td>
</tr>
<tr class="odd">
<td><p>Country code populates based on region settings</p></td>
<td></td>
<td></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Account information for multiple users can be cached on the same device</p></td>
<td><p>●</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Screen reader/voice over</p></td>
<td><p>●</p></td>
<td><p>●2<br />
English only</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●<br />
English only</p></td>
</tr>
<tr class="even">
<td><p>Use an external keyboard with Lync</p></td>
<td></td>
<td></td>
<td><p>●3</p></td>
<td><p>●3</p></td>
<td><p>●</p></td>
</tr>
<tr class="odd">
<td><p>Certificate and passive authentication support for mobile clients (Lync Server only)</p></td>
<td></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
</tr>
<tr class="even">
<td><p>Microsoft Customer Experience Improvement Program support </p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td></td>
</tr>
</tbody>
</table>


1 On Windows Phone, Lync signs out automatically if the user has not used the application for a period of time, as follows:

  - If the user has enabled push notifications, Lync signs out after 10 days of inactivity.

  - If the user has not enabled push notifications, Lync signs out after 1 hour.

On iPhone and iPad, Lync signs out automatically if the user has not used the application for a period of time, as follows:

  - If the mobile client has not contacted the server for 10 days due to loss of network connectivity or other issues.

2 In app only.

3 Must be in VoiceOver mode.

4iPhone, iPad, and Android don't require push notifications for receiving messages when an app is running in the background.

</div>

<div>

## Enhanced Presence Support in Lync Mobile Clients


<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Feature/Capability</th>
<th>Lync 2013 desktop client</th>
<th>Windows Phone</th>
<th>iPhone</th>
<th>iPad</th>
<th>Android</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Publish and view status</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
</tr>
<tr class="even">
<td><p>View status based on calendar free/busy information</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
</tr>
<tr class="odd">
<td><p>View status notes and Out of Office messages</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
</tr>
<tr class="even">
<td><p>Add a custom location</p></td>
<td><p>●</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Add a custom note</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
</tr>
<tr class="even">
<td><p>Publish status based on calendar free/busy information</p></td>
<td><p>●1</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Set manual presence state (such as Busy, Do Not Disturb, and so on)</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
</tr>
</tbody>
</table>


1 Lync mobile clients do not update a user’s presence based on the user’s free/busy calendar information. If a mobile client user is also signed in to the Lync desktop client, the desktop client updates the user’s presence based on the user’s free/busy calendar information. If the user is signed in to a mobile client only, the user’s presence does not update based on free/busy calendar information.

</div>

<div>

## Contacts and Contact Groups Support in Lync Mobile Clients


<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Feature/capability</th>
<th>Lync 2013 desktop client</th>
<th>Windows Phone</th>
<th>iPhone</th>
<th>iPad</th>
<th>Android</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>View Contacts list</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
</tr>
<tr class="even">
<td><p>View contact groups</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
</tr>
<tr class="odd">
<td><p>View Frequent Contacts group</p></td>
<td><p>●</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Modify Contacts list</p></td>
<td><p>●</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Tag contacts for status change alerts</p></td>
<td><p>●</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Control privacy relationships</p></td>
<td><p>●</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Search the corporate address book</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
</tr>
<tr class="even">
<td><p>Search Contacts list</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
</tr>
<tr class="odd">
<td><p>Manage contact groups</p></td>
<td><p>●</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Expand distribution groups</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
</tr>
<tr class="odd">
<td><p>Search for Response Groups</p></td>
<td><p>●1</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
</tr>
<tr class="even">
<td><p>Display or hide contact photos</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
</tr>
<tr class="odd">
<td><p>Pin a contact to your home screen</p></td>
<td></td>
<td><p>●</p></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>


1 Not available to Skype for Business Online and/or Office 365 users.

</div>

<div>

## Instant Messaging Support in Lync Mobile Clients


<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Feature/capability</th>
<th>Lync 2013 desktop client</th>
<th>Windows Phone</th>
<th>iPhone</th>
<th>iPad</th>
<th>Android</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Initiate instant messaging (IM) with a contact</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
</tr>
<tr class="even">
<td><p>Participate in multiparty IM</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
</tr>
<tr class="odd">
<td><p>Invite others from within the conversation window</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Display current conversations</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
</tr>
<tr class="odd">
<td><p>Navigate among multiple IM conversations</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
</tr>
<tr class="even">
<td><p>Automatically log IM conversations in Exchange</p></td>
<td><p>●</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Send an IM conversation as an email message</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
</tr>
<tr class="even">
<td><p>Initiate an email to a contact</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
</tr>
<tr class="odd">
<td><p>View missed IM invitations</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
</tr>
<tr class="even">
<td><p>Vibrate with incoming IM</p></td>
<td></td>
<td><p>●1</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
</tr>
</tbody>
</table>


1 This device vibrates every time an IM is received even if the current message in the IM conversation is displayed

</div>

<div>

## Lync-to-Lync Audio and Video


<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Feature/Capability</th>
<th>Lync 2013 desktop client</th>
<th>Windows Phone</th>
<th>iPhone</th>
<th>iPad</th>
<th>Android</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync-to-Lync voice</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
</tr>
<tr class="even">
<td><p>Lync-to-Lync video</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Conferencing Support in Lync Mobile Clients


<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Feature/Capability</th>
<th>Lync 2013 desktop client</th>
<th>Windows Phone</th>
<th>iPhone</th>
<th>iPad</th>
<th>Android</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Click a link in the meeting reminder to join a meeting (public switched telephone network (PSTN))</p></td>
<td><p>●</p></td>
<td><p>●1</p></td>
<td><p>●1</p></td>
<td><p>●1</p></td>
<td><p>●1</p></td>
</tr>
<tr class="even">
<td><p>Click a link in the meeting reminder to join a video or VoIP meeting</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
</tr>
<tr class="odd">
<td><p>Participate in multiparty IM</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
</tr>
<tr class="even">
<td><p>Use dial-out conferencing (server calls the mobile device)</p></td>
<td><p>●</p></td>
<td><p>●2</p></td>
<td><p>●2</p></td>
<td><p>●2</p></td>
<td><p>●2</p></td>
</tr>
<tr class="odd">
<td><p>Use dial-in audio conferencing</p></td>
<td><p>●3</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>View meeting video</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
</tr>
<tr class="odd">
<td><p>View multiparty video (gallery view)</p></td>
<td><p>●</p></td>
<td></td>
<td></td>
<td><p>●</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Wait in meeting lobby</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
</tr>
<tr class="odd">
<td><p>Use in-meeting presenter controls</p></td>
<td><p>●</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Access detailed meeting roster for audio conferences</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
</tr>
<tr class="odd">
<td><p>Access detailed meeting roster for IM conferences</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
</tr>
<tr class="even">
<td><p>Share desktop or program</p></td>
<td><p>●</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>View shared desktop or program</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>View shared PowerPoint</p></td>
<td><p>●</p></td>
<td><p>●4</p></td>
<td><p>●4</p></td>
<td><p>●4</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Use meeting tools (present Microsoft PowerPoint files, use whiteboard, conduct polls, share files)</p></td>
<td><p>●</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Navigate a list of your meetings</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
</tr>
<tr class="odd">
<td><p>Join a meeting even if you don’t have a Lync account</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>View more information about meeting participants</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Start an unscheduled group conversation with multiple participants directly from your client or device</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td></td>
</tr>
</tbody>
</table>


1 For Office 365 users, this feature is available for audio conferencing provider (ACP)-enabled meetings only.

2 Not available to Office 365 users.

3 For Skype for Business Online and/or Office 365 users, this feature is available from third-party audio conferencing providers.

4A PowerPoint presentation shared by Lync Web App cannot be viewed from Lync Mobile 2013. Annotations made on Lync 2013 Desktop clients are not viewable on mobile devices.

</div>

<div>

## Telephony Support in Lync Mobile Clients


<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Feature/Capability</th>
<th>Lync 2013 desktop client</th>
<th>Windows Phone</th>
<th>iPhone</th>
<th>iPad</th>
<th>Android</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>In Lync, tap the call icon to call a contact</p></td>
<td><p>●1</p></td>
<td><p>●2</p></td>
<td><p>●2</p></td>
<td><p>●2</p></td>
<td><p>●2</p></td>
</tr>
<tr class="even">
<td><p>Transfer a call</p></td>
<td><p>●1</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Manage call forwarding</p></td>
<td><p>●3</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
</tr>
<tr class="even">
<td><p>Manage team call settings</p></td>
<td><p>●3</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Manage delegates</p></td>
<td><p>●3</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Initiate a call to a Response Group</p></td>
<td><p>●3</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Support emergency services</p></td>
<td><p>●4</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Make calls on behalf of another contact (manager/delegate scenario)</p></td>
<td><p>●3</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Handle another contact’s calls, if configured as a delegate</p></td>
<td><p>●3</p></td>
<td><p>●3</p></td>
<td><p>●3</p></td>
<td><p>●3</p></td>
<td><p>●3</p></td>
</tr>
<tr class="even">
<td><p>Use Call via Work (Lync Server 2013 places your outgoing calls so that the receiver’s caller ID displays your work number instead of your mobile number)</p></td>
<td></td>
<td><p>●3</p></td>
<td><p>●3</p></td>
<td><p>●3</p></td>
<td><p>●3</p></td>
</tr>
<tr class="odd">
<td><p>Access voice mail</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
</tr>
<tr class="even">
<td><p>Use the keypad in Lync</p></td>
<td><p>●</p></td>
<td><p>●3</p></td>
<td><p>●3</p></td>
<td><p>●3</p></td>
<td><p>●3</p></td>
</tr>
</tbody>
</table>


1 Lync Server 2013, Skype for Business Online, and Office 365 users may call other Lync users and Skype users by tapping the icon. Lync Server 2013 users may also place PSTN calls by tapping the icon.

2 For on-premises Lync Server 2013 users, on Windows Phone, iPhone, and iPad devices, the user taps the call icon in the contact card and accepts the callback from Lync Server 2013. For Office 365 users, on Windows Phone, iPhone, and iPad devices, when the user taps the call button, a dialog box opens asking the user to confirm that he or she wants to call the number.

3 Not available to Skype for Business Online and/or Office 365 users.

4 For Skype for Business Online and/or Office 365 users, this feature is supported by Microsoft partners.

</div>

<div>

## External User Support in Lync Mobile Clients


<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Feature/Capability</th>
<th>Lync 2013 desktop client</th>
<th>Windows Phone</th>
<th>iPhone</th>
<th>iPad</th>
<th>Android</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Initiate IM with a public contact</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
</tr>
<tr class="even">
<td><p>Initiate IM with a federated contact</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
<td><p>●</p></td>
</tr>
<tr class="odd">
<td><p>Conduct two-party calls with external users</p></td>
<td><p>●</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Conduct multiparty calls with external users</p></td>
<td><p>●</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Use Call via Work to reach a federated contact on their mobile phone by calling their published work number1</p></td>
<td></td>
<td><p>●2</p></td>
<td><p>●2</p></td>
<td><p>●2</p></td>
<td><p>●2</p></td>
</tr>
</tbody>
</table>


1 By default, federated users are assigned the External Contacts privacy relationship. To be able to reach a federated contact on their mobile phone by calling their published work number, the federated contact must manually assign you the Colleagues privacy relationship.

2 Not available to Office 365 users.

</div>

<div>

## Address Book Integration


<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Feature/Capability</th>
<th>Lync 2013 desktop client</th>
<th>Windows Phone</th>
<th>iPhone</th>
<th>iPad</th>
<th>Android</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Call address book contacts</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td><p>●</p></td>
</tr>
<tr class="even">
<td><p>Make Lync calls to contacts directly from address book</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td><p>●</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Archiving and Compliance Support in Lync Mobile Clients


<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Feature/Capability</th>
<th>Lync 2013 desktop client</th>
<th>Windows Phone</th>
<th>iPhone</th>
<th>iPad</th>
<th>Android</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Provide client-side archiving</p></td>
<td><p>●</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Provide client-side recording</p></td>
<td><p>●</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

