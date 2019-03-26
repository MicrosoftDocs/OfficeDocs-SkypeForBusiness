---
title: 'Lync Server 2013: Migration considerations for meetings'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Migration considerations for meetings
ms:assetid: a9807d58-99a3-4cff-b4c6-74950d106a2b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412800(v=OCS.15)
ms:contentKeyID: 61097556
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Migration considerations for meetings in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-02-10_

The following topics are discussed in this section:

  - Changes to meetings in Microsoft Lync Server 2013

  - Migrating users based on their conferencing needs

  - Migrating existing meetings and meeting content

  - User experience during Lync Server 2010 migration

  - User Experience during Office Communications Server 2007 R2 migration

  - Microsoft Lync 2013 compatibility with meetings on earlier server versions

<div>

## Changes to Meetings in Lync Server 2013

**Lync Server 2013 features.**   Lync Server 2013 provides new conferencing features that become available to users after their accounts are moved to Lync Server 2013 and they sign in with the Lync 2013 client. New features are outlined in [New conferencing features in Lync Server 2013](lync-server-2013-new-conferencing-features.md) and [What's new for clients in Lync Server 2013](lync-server-2013-what-s-new-for-clients.md).

**Meeting URL.**   As in Lync Server 2010, all newly scheduled meetings in Lync Server 2013 have a URL prefix of https:// and existing meetings migrate along with user accounts. However, Lync Server 2013 does not support the Office Communications Server 2007 R2 conference call (conf:// URL prefix) or web conference (meet:// URL prefix). See “Migrating Meetings from Office Communications Server 2007 R2” later in this topic for more information.

**Client support.**   Unlike Lync Server 2010, Lync Server 2013 does not support Office Communicator clients for conferencing. You cannot use the following clients to join meetings scheduled through the Online Meeting Add-in for Lync 2013:

  - Office Communicator 2007 R2

  - Microsoft Office Communications Server 2007 R2 Attendant

  - Office Communicator 2007

  - Office Live Meeting 2007

During migration, Office Communicator 2007 R2 users should use Lync Web App 2013 to join Lync Server 2013 meetings until their clients are upgraded. Note that Office Communicator 2007 R2 users can continue to use their existing client against Lync Server 2013 for presence and IM features, but conferencing features are not supported.

<div>


</div>

</div>

<div>

## Migrating Users Based on Their Conferencing Needs

**Frequent meeting organizers.**   Consider migrating frequent meeting organizers early in the process so that they can take advantage of the new Lync Server 2013 and Lync 2013 features outlined in [New conferencing features in Lync Server 2013](lync-server-2013-new-conferencing-features.md) and [What's new for clients in Lync Server 2013](lync-server-2013-what-s-new-for-clients.md).

**Live Meeting users.**   If you are migrating from Office Communications Server 2007 R2 and you have users who need web conferencing features specific to Live Meeting—particularly support for large meetings and break-out rooms—you have the following options:

  - Advise organizers to use the Live Meeting service, if available in your organization.

  - Leave the organizers homed on the earlier version of Office Communications Server, so they can continue to schedule server-based Live Meeting web conferences.

</div>

<div>

## Migrating Existing Meetings and Meeting Content

<div>

## Migrating Meetings from Lync Server 2010

When you move a user from Lync Server 2010 to Lync Server 2013, the following information moves with the user’s account:

  - Meetings already scheduled by the user. This includes conferencing directories and conferencing data.

  - The user’s personal identification number (PIN). The user’s current PIN continues to work until it expires or the user requests a new PIN.

However, the following user account information does not move to the new server:

  - Meeting content, for example PowerPoint presentations, whiteboard content, and poll data

To move the content that has been shared in meetings, use the MoveMeetingContent parameter of the Move-CsUser cmdlet. For details about using this cmdlet, see [Move-CsUser](https://docs.microsoft.com/powershell/module/skype/Move-CsUser) in the Lync Server 2013 cmdlets documentation.

</div>

<div>

## Migrating Meetings from Office Communications Server 2007 R2

Office Communications Server 2007 R2 meetings are either conference calls (conf:// URL prefix) or web conferences (meet:// URL prefix). Lync Server 2013 does not support these earlier conf:// and meet:// conferences, and they are not migrated along with the user account. After migration, you should instruct users to update the links for any online meetings they have scheduled. They can do this after installing the Lync 2013 client by opening a scheduled meeting invitation—which updates the meeting URL—and resending the invitation to participants.

</div>

</div>

<div>

## User Experience during Lync Server 2010 Migration

This section provides a summary of users’ conferencing experience when migrating from Lync 2010. For more details about how Lync Server 2013 clients can coexist and interact with previous client and server versions, see [Client interoperability in Lync 2013](lync-server-2013-client-interoperability-in-lync-2013.md).

<div>

## Joining Lync Server 2010 Meetings with a Lync 2013 Client

During migration from Lync Server 2010, there may be a period of coexistence when users join Lync Server 2010 meetings with a Lync 2013 client. These users have access to Lync 2013 client features with the following exceptions:

  - In the **Participants** management options, which are accessible by pointing to the people icon in the meeting window, the **No Meeting IM** option does not function.

  - Gallery View does not function in video conferences. The user sees only the active speaker instead of all speakers. In the list of **Pick a Layout** options, **Gallery View** is unavailable

  - The participant list displays by default in video conferences.

  - When right-clicking a user in the participants list, the **Lock the Video Spotlight** and **Pin to Gallery** participant management options are unavailable.

</div>

</div>

<div>

## User Experience during Office Communications Server 2007 R2 Migration

This section provides a summary of users’ conferencing experience when migrating from Office Communications Server 2007 R2, both before and after Lync 2013 is installed. For more details about how Lync Server 2013 clients can coexist and interact with previous client and server versions, see [Client interoperability in Lync 2013](lync-server-2013-client-interoperability-in-lync-2013.md).

<div>

## After User Account is Migrated, Before Lync 2013 Is Installed

After a user is migrated to the Lync Server 2013 server, but before new clients are installed, Office Communicator 2007 R2 users can continue to use their existing client against Lync Server 2013 for presence and IM features, but conferencing features are not supported.

</div>

<div>

## After User Account is Migrated, After Lync 2013 Is Installed

When a migrated user installs Lync 2013, the Online Meeting Add-in for Lync 2013 is installed too. This has the following effects:

  - All subsequently scheduled meetings use the new meeting format, which uses an https:// address instead of the legacy meet:// Live Meeting address.

  - In an IT-managed deployment of Lync 2013, the administrator has the option of uninstalling the Conferencing Add-in for Microsoft Office Outlook, which is used to schedule Live Meeting server and service-based meetings. However, you may have users who need to continue to schedule Live Meeting service meetings. In this case, you can allow both add-ins to coexist.

</div>

<div>

## Meetings with Federated Organizations that Use Previous Clients

Users in federated organizations who are using Microsoft Office Communicator 2007 cannot join Lync Server 2013 meetings in your organization if those meetings are locked by the organizer. You have to reschedule these meetings in Lync Server 2013 so when federated participants join the meeting by using the new https:// meeting URL, they can use Lync Web App.

</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

