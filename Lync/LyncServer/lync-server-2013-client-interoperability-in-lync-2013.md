---
title: 'Lync Server 2013: Client interoperability in Lync 2013'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Client interoperability in Lync 2013
ms:assetid: 0f126571-91a2-45d5-855c-1e4ddb45fc04
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204672(v=OCS.15)
ms:contentKeyID: 48183417
ms.date: 03/04/2016
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Client interoperability in Lync 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2016-03-04_

This topic discusses the ability of Microsoft Lync Server 2013 clients to coexist and interact with clients from earlier versions of Lync Server and Office Communications Server.

<div>

## Server and Client Compatibility

The following table shows the supported combinations of client versions and server versions. This table indicates whether sign-in is supported when the client attempts to connect to the server indicated. Lync Server 2013 supports the previous client version. Also, unlike previous releases, Lync Server 2010 supports the new Lync 2013 clients. This allows organizations who are upgrading from Lync Server 2010 to roll out new clients independent of Lync Server upgrades.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Client</th>
<th>Lync Server 2013</th>
<th>Lync Server 2010</th>
<th>Office Communications Server 2007 R2</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 2013</p></td>
<td><p>Supported</p></td>
<td><p>Supported5</p></td>
<td><p>Not Supported</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 Basic</p></td>
<td><p>Supported</p></td>
<td><p>Supported</p></td>
<td><p>Not Supported</p></td>
</tr>
<tr class="odd">
<td><p>Lync Web App 2013</p></td>
<td><p>Supported</p></td>
<td><p>Not Supported</p></td>
<td><p>Not Supported</p></td>
</tr>
<tr class="even">
<td><p>Lync 2010</p></td>
<td><p>Supported</p></td>
<td><p>Supported</p></td>
<td><p>Not Supported</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2010 Attendant</p></td>
<td><p>Supported</p></td>
<td><p>Supported</p></td>
<td><p>Not Supported</p></td>
</tr>
<tr class="even">
<td><p>Lync 2010 Group Chat</p></td>
<td><p>Supported1</p></td>
<td><p>Supported2</p></td>
<td><p>Not Applicable</p></td>
</tr>
<tr class="odd">
<td><p>Lync Web App 2010</p></td>
<td><p>Not Supported</p></td>
<td><p>Supported</p></td>
<td><p>Not Supported</p></td>
</tr>
<tr class="even">
<td><p>Lync 2010 Attendee</p></td>
<td><p>Not Supported3</p></td>
<td><p>Supported</p></td>
<td><p>Not Supported</p></td>
</tr>
<tr class="odd">
<td><p>Office Communicator 2007 R2</p></td>
<td><p>Interoperable4</p></td>
<td><p>Supported</p></td>
<td><p>Supported</p></td>
</tr>
<tr class="even">
<td><p>Microsoft Office Communications Server 2007 R2 Attendant</p></td>
<td><p>Not Supported</p></td>
<td><p>Supported</p></td>
<td><p>Supported</p></td>
</tr>
<tr class="odd">
<td><p>Office Communicator 2007</p></td>
<td><p>Not Supported</p></td>
<td><p>Supported</p></td>
<td><p>Supported</p></td>
</tr>
<tr class="even">
<td><p>Office Live Meeting 2007</p></td>
<td><p>Not Supported</p></td>
<td><p>Supported</p></td>
<td><p>Supported</p></td>
</tr>
<tr class="odd">
<td><p>Lync Windows Store app</p></td>
<td><p>Supported</p></td>
<td><p>Supported</p></td>
<td><p>Not Supported</p></td>
</tr>
</tbody>
</table>


1For details, see [Migration from Lync Server 2010, Group Chat or Office Communications Server 2007 R2 Group Chat to Lync Server 2013, Persistent Chat Server](migration-from-lync-server-2010-group-chat-or-office-communications-server-2007-r2-group-chat-to-lync-server-2013-persistent-chat-server.md).

2In Microsoft Lync Server 2010, group chat functionality was available with Group Chat Server, a third-party trusted application for Lync Server 2010. Lync 2013 clients are not compatible with Lync Server 2010, Group Chat.

3Lync Web App 2013 now provides a full in-meeting experience, including computer audio and video, and is considered the replacement for Lync 2010 Attendee. Lync 2010 Attendee will connect to Lync Server 2013 only when you are using an unsupported browser (Internet Explorer 6 or Internet Explorer 7) and Windows XP.

4The presence and IM features in Office Communicator 2007 R2 are compatible with Lync Server 2013, but conferencing features are not. During migration from Office Communications Server 2007 R2, Office Communicator 2007 R2 is suitable for presence and IM interoperability, but users should use Lync Web App 2013 to join Lync Server 2013 meetings.

5 For limitations, see "Conferencing Feature Support for Lync 2013 Clients in Lync Server 2010 Meetings" later in this topic.

</div>

<div>

## Interoperability among Clients

With the Lync Server 2013 release, various client versions can interact seamlessly in both peer-to-peer and conferencing scenarios. This section discusses feature availability when users interact with other users who are using different versions of clients and servers.

<div>

## Peer-to-Peer Feature Support

Peer-to-peer features are supported for users who are homed on different versions of the server and who are using different client versions. The end-user experience and available features are consistent with the capabilities of the user’s client and the version of the server the user is signed in to. In other words:

  - If a user is signed in to Lync Server 2013 with an older client, the user will have the same experience he or she is used to. None of the new features introduced in Lync Server 2013 will be available until the user’s client is upgraded. Examples include video gallery view, HD video, updated PowerPoint sharing, and the option to mute all attendee audio and video upon meeting entry. The new features are outlined in [New conferencing features in Lync Server 2013](lync-server-2013-new-conferencing-features.md) and [What's new for clients in Lync Server 2013](lync-server-2013-what-s-new-for-clients.md).

  - If a user is signed in to Lync Server 2010 with a Lync 2013 client, any new features not supported by Lync Server 2010 will be unavailable until the user is moved to Lync Server 2013.

The following table compares feature availability in peer-to-peer sessions where the client is signed in to either Lync Server 2013 or Lync Server 2010.

<div>


> [!NOTE]  
> Lync Web App and Lync 2010 Attendee are meeting-only clients and aren’t included in this table.



</div>


<table style="width:100%;">
<colgroup>
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
</colgroup>
<thead>
<tr class="header">
<th>Client</th>
<th>Instant Messaging</th>
<th>Presence</th>
<th>Voice</th>
<th>Video</th>
<th>Application Sharing</th>
<th>File Transfer</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 2013</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 Basic</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2010</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
</tr>
<tr class="even">
<td><p>Lync 2010 Attendant</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Lync 2010 Mobile</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Lync Phone Edition</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Office Communicator 2007 R2</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes1</p></td>
<td><p>Yes</p></td>
</tr>
<tr class="even">
<td><p>Public IM (AOL, Yahoo!)</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Public IM (MSN, Windows Live Messenger)</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>


<div>


> [!IMPORTANT]  
> <UL>
> <LI>
> <P>As of September 1st, 2012, the Microsoft Lync Public IM Connectivity User Subscription License (PIC USL) is no longer available for the purchase for new or renewing agreements. Customers with active licenses will be able to continue to federate with Yahoo! Messenger until the service shutdown date. An end of life date of June 2014 for AOL and Yahoo! has been announced. For details, see <A href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Support for public instant messenger connectivity in Lync Server 2013</A>..</P>
> <LI>
> <P>The PIC USL is a per-user, per-month subscription license that is required for Lync Server or Office Communications Server to federate with Yahoo! Messenger. Microsoft’s ability to provide this service has been contingent upon support from Yahoo!, the underlying agreement for which will not be renewed.</P>
> <LI>
> <P>More than ever, Lync is a powerful tool for connecting across organizations and with individuals around the world. Federation with Windows Live Messenger requires no additional user/device licenses beyond the Lync Standard CAL. Skype federation will be added to this list, enabling Lync users to reach hundreds of millions of people through IM and voice.</P></LI></UL>



</div>

1 In Office Communicator 2007 R2, only desktop sharing (and not program sharing) is available.

<div>


> [!NOTE]  
> Desktop sharing between Office Communicator 2007 R2 and Skype for Business 2015 cannot be initiated from the newer client when the Skype for Business 2015 client user interface is enforced.



</div>

</div>

<div>

## Conferencing Feature Support for Lync 2013 Clients in Lync Server 2010 Meetings

When users join Lync Server 2010 meetings with a Lync 2013 client, they have access to Lync 2013 client features with the following exceptions:

  - In the **Participants** management options, which are accessible by pointing to the people icon in the meeting window, the **No Meeting IM** option does not function.

  - Gallery View does not function in video conferences. The user sees only the active speaker instead of all speakers. In the list of **Pick a Layout** options, **Gallery View** is unavailable

  - The participant list displays by default in video conferences.

  - When right-clicking a user in the participants list, the **Lock the Video Spotlight** and **Pin to Gallery** participant management options are unavailable.

</div>

<div>

## Conferencing Feature Support in Lync Server 2013 Meetings

Lync Server 2013 provides new conferencing features that become available to users after their accounts are moved to Lync Server 2013 and they sign in with the Lync 2013 client. Examples include video gallery view, HD video, PowerPoint sharing, and the option to mute all attendee audio and video upon meeting entry. The new features are outlined in [New conferencing features in Lync Server 2013](lync-server-2013-new-conferencing-features.md) and [What's new for clients in Lync Server 2013](lync-server-2013-what-s-new-for-clients.md).

In Lync Server 2013 meetings, certain conferencing features are supported for users who are homed on different versions of the server and who are using different clients and client versions. When clients join a Lync Server 2013 meeting, users have access to the features and capabilities shown in this table.


<table style="width:100%;">
<colgroup>
<col style="width: 11%" />
<col style="width: 11%" />
<col style="width: 11%" />
<col style="width: 11%" />
<col style="width: 11%" />
<col style="width: 11%" />
<col style="width: 11%" />
<col style="width: 11%" />
<col style="width: 11%" />
</colgroup>
<thead>
<tr class="header">
<th>Client</th>
<th>Peer-to-peer IM</th>
<th>Voice</th>
<th>Video</th>
<th>Application Sharing</th>
<th>PowerPoint</th>
<th>File Transfer</th>
<th>Whiteboard</th>
<th>Polling</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 2013</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 Basic</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
</tr>
<tr class="odd">
<td><p>Lync Web App</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes2</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
</tr>
<tr class="even">
<td><p>Lync 2010</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes3</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
</tr>
<tr class="odd">
<td><p>Office Communicator 2007 R2 4</p></td>
<td><p>Yes</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>


1 In Office Communicator 2007 R2, only desktop sharing (and not program sharing) is available.

2 Lync Server 2013 uses an updated mechanism for uploading PowerPoint files. Lync Web App users who join a meeting that was originally scheduled on Lync Server 2010 can view and navigate PowerPoint presentations, but cannot upload PowerPoint files.

3 If the meeting was scheduled on Lync Server 2013 and PowerPoint slides were uploaded by a Lync 2013 client, Lync 2010 users have view-only access to the slides. Conversely, if the PowerPoint slides were uploaded by a Lync 2010 user, Lync Server 2013 users will be able to view and slides and, if Office Web Apps Server is configured, access new capabilities such as higher resolution display, animations, slide transitions, and embedded video. For more information, see [Configuring integration with Office Web Apps Server and Lync Server 2013](lync-server-2013-enabling-office-web-apps-server-and-lync-server-2013.md).

4The presence and IM features in Office Communicator 2007 R2 are compatible with Lync Server 2013, but conferencing features are not. During migration from Office Communications Server 2007 R2, Office Communicator 2007 R2 is suitable for presence and IM interoperability, but users should use Lync Web App 2013 to join Lync Server 2013 meetings.

</div>

</div>

<div>

## Scheduling Add-in Support

Server support for the various scheduling add-ins is consistent with server and client version compatibility. In general, the following scheduling add-ins are supported on Lync Server 2013. However, previous versions of add-ins do not provide new Lync 2013 add-in features, such as the option to mute all attendee audio and video upon meeting entry.

  - **Online Meeting Add-in for Lync 2013**   Provides the same features as the Online Meeting Add-in for Lync 2010, with the addition of attendee mute controls, which allow meeting organizers to schedule conferences that have attendee audio and video muted by default. Administrators can also customize the organization’s meeting invitations by adding a custom logo, a support URL, a legal disclaimer URL, or custom footer text.

  - **Online Meeting Add-in for Lync 2010**   Provides scheduling for Lync meetings and removes the capability to schedule Office Live Meeting conferences.

  - **Office Communicator 2007 R2 Conferencing Add-in**   Provides scheduling for both Office Live Meeting conferences and Office Communicator 2007 R2 conferences. 

<div>


> [!NOTE]  
> Live Meeting conferences cannot be scheduled on Lync Server 2013.



</div>


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Scheduling Client</th>
<th>Lync Server 2013</th>
<th>Lync Server 2010</th>
<th>Office Communications Server 2007 R2</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Online Meeting Add-in for Lync 2013 (can be used with Office 2013, Outlook 2010, and Outlook 2007)</p></td>
<td><p>Supported</p></td>
<td><p>Supported (new add-in features not available)</p></td>
<td><p>Not Supported</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 Web Scheduler</p></td>
<td><p>Supported</p></td>
<td><p>Not Supported</p></td>
<td><p>Not Supported</p></td>
</tr>
<tr class="odd">
<td><p>Online Meeting Add-in for Lync 2010</p></td>
<td><p>Supported</p></td>
<td><p>Supported</p></td>
<td><p>Not Supported</p></td>
</tr>
<tr class="even">
<td><p>Office Communicator 2007 R2 Conferencing Add-in</p></td>
<td><p>Not Supported</p></td>
<td><p>Supported</p></td>
<td><p>Supported</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Support for Joining Meetings

All of the clients that Lync Server 2013 supports are allowed to join Lync 2013 meetings. Because Lync Web App is a web component of the server, in cases where Lync Web App is used to join a Lync Server 2013 meeting, the newer version of Lync Web App is always used.

Lync 2013 clients can join meetings hosted on Lync 2010 and Office Communications Server 2007 R2 with scaled-down functionality. In-meeting features are limited by the version of the server on which the meeting is hosted.

</div>

<div>

## See Also


[Lync Windows Store app requirements for Lync Server 2013](lync-server-2013-lync-windows-store-app-requirements.md)  
[New conferencing features in Lync Server 2013](lync-server-2013-new-conferencing-features.md)  
[What's new for clients in Lync Server 2013](lync-server-2013-what-s-new-for-clients.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

