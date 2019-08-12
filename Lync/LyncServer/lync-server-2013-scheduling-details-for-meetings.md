---
title: 'Lync Server 2013: Scheduling details for meetings'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Scheduling details
ms:assetid: 39ca6fff-2c15-4347-9f1f-6c8687a39a49
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204823(v=OCS.15)
ms:contentKeyID: 48183910
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Scheduling details for meetings in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-04_

After checking to ensure that no other meeting is scheduled at the requested time, the large meeting support staff that handles the request schedules the meeting on the large-meeting pool. Use the Online Meeting Add-in for Lync that is installed with the Lync Server 2013 client to perform this task, using the credentials of a user enabled for Lync Server in the dedicated large-meeting pool.

To ensure the best user experience, it is important to schedule the large meeting with the right access levels and meeting settings that are appropriate to the meeting organizer’s needs. We recommend the following scheduling settings configured in Lync Meeting options:

  - Use a new meeting space for each large meeting instead of reusing the dedicated meeting space.

  - Specify the meeting access level as follows:
    
      - If at least one invitee is external to the organization, set the meeting access type to **Anyone (no restrictions**. This enables you to avoid having to manage a potentially large lobby when the meeting is in progress.
    
      - If the meeting is an internal-only meeting, set the meeting access type to **Anyone from my organization**.
        
        <div>
        

        > [!NOTE]  
        > Avoid setting the meeting access type to <STRONG>People I invite from my company</STRONG> because when you use this setting, organizers must add all user email addresses to the invitee list and you cannot invite a distribution group.<BR>Avoid setting the meeting access type to <STRONG>Only me, the meeting organizer</STRONG> because this setting requires that every meeting participant, including presenters, must be put in the lobby at meeting run time. The person responsible for running the large meeting must then constantly monitor the lobby roster and admit new users who are in the lobby.

        
        </div>

  - Allow users who dial-in from phones to enter the meeting automatically by checking the **Callers get in directly** setting.

  - Explicitly invite the following users:
    
      - Meeting organizer and delegate (requester)
    
      - The list of presenters provided by a meeting requester
    
    <div>
    

    > [!NOTE]  
    > If the meeting access type is set to <STRONG>People I choose</STRONG>, you need to explicitly add each participant of a large meeting as an invitee of the meeting.

    
    </div>

  - Explicitly manage presenters, instead of setting the presenter option to one of the auto-promote values. Be sure to add the following users as presenters:
    
      - Meeting organizer and delegate (requester)
    
      - The list of presenters provided by large meeting requesters
    
    <div>
    

    > [!NOTE]  
    > By explicitly managing presenters, you can control the number of presenters, so that you can limit presenters to a small enough number to make it possible to have an effective large meeting. If the majority of meeting participants have the attendee role, it helps reduce the chance of people accidentally taking control of the presentation, deleting a PowerPoint presentation, muting/unmuting presenters, and other disruptions to the meeting.

    
    </div>

  - Check the **Mute all attendees** setting to make sure that only presenters can broadcast audio into the meeting.

  - Check the **Block attendees’ video** setting to make sure only presenters can broadcast video into the meeting.

The following figure shows the recommended settings for the Online Meeting Add-in for Lync.

![54e4e70d-06b0-45cd-8d94-bab649cd5dc0](images/JJ204823.54e4e70d-06b0-45cd-8d94-bab649cd5dc0(OCS.15).jpg "54e4e70d-06b0-45cd-8d94-bab649cd5dc0")

</div>

<span> </span>

</div>

</div>

</div>

