---
title: 'Lync Server 2013: Planning for remote call control'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Planning for remote call control
ms:assetid: 688a0328-1aa7-449f-b5f7-98c876112ed2
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg558658(v=OCS.15)
ms:contentKeyID: 48184371
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Planning for remote call control in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-05_

In Lync Server 2013, support for remote call control scenarios enables users to control their private branch exchange (PBX) phones by using Lync 2013 on their desktop computers. This section describes remote call control features and requirements for deploying remote call control.

Integration between a PBX and Lync Server 2013 makes it possible for users enabled for remote call control to use the Lync 2013 user interface (UI) to control calls on their PBX phones in the following ways:

<div>


> [!NOTE]  
> Ultimately, the capabilities of the PBX that hosts a user’s PBX phone determine the remote call control features that will be available to that user.



</div>

  - Make an outgoing call

  - Answer an incoming call

  - Answer an incoming call with an instant message
    
    <div>
    

    > [!NOTE]  
    > That is, when the caller’s phone number can be associated with an instant message address in your organization’s global address list (GAL), in the callee’s Lync Contacts list, or in a federated partner’s organization.

    
    </div>

  - Transfer a call

  - Forward an incoming call

  - Place calls on hold

  - Alternate between multiple concurrent calls

  - Answer a second call while already in a call (that is, call waiting)

  - Dial dual-tone multifrequency (DTMF) digits

  - In the Conversation window, type notes in Microsoft Office OneNote note-taking program

Additionally, when a user is enabled for remote call control, Lync 2013 provides the user with the following call information:

  - Identification of a caller by name when the caller’s phone number exists in the Contacts list of a remote call control-enabled user’s Microsoft Office Outlook messaging and collaboration client, Lync Contacts list, or your organization’s GAL.

  - Past incoming and outgoing calls, which are saved in the Conversation History folder in Outlook.

  - Missed call notifications, which are sent to the user’s Outlook Inbox folder, but are generated only if Lync is running when the incoming call is received.

<div>

## Remote Call Control and Enterprise Voice

Although remote call control features are separate from Enterprise Voice features and users cannot be enabled for both, Enterprise Voice provides a subset of features that are also available to users who are enabled for remote call control. If Enterprise Voice is deployed, users who are enabled for remote call control can use Lync to access the following Enterprise Voice features:

  - Make and receive audio calls to another Lync client

  - Join the audio portion of a conference created by a user who is enabled for Enterprise Voice

</div>

<div>

## In This Section

  - [Deployment tasks for remote call control in Lync Server 2013](lync-server-2013-deployment-tasks-for-remote-call-control.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

