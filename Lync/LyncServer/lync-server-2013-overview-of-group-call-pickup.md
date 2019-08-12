---
title: 'Lync Server 2013: Overview of Group Call Pickup'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Overview of Group Call Pickup
ms:assetid: 3dc0eca8-c773-463c-96bb-9cd6afa2a840
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ945623(v=OCS.15)
ms:contentKeyID: 51541466
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Overview of Group Call Pickup in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-12_

Group Call Pickup, a new feature in Cumulative Updates for Lync Server 2013: February 2013, lets users answer incoming calls to their colleagues from their own phones. This new feature increases the availability of a user's line by enabling other users to answer an incoming call by dialing a call pickup group number. When Group Call Pickup is deployed, the number of incoming calls that are routed to voice mail can be significantly reduced, which is particularly useful for calls from customers who are external to your organization.

The Group Call Pickup feature is designed in particular for business units in open office environments. Incoming calls are not disruptive because they ring only at the intended destination. Other users who hear the ring, however, can still pick up the call simply by dialing the group number.

In environments where users are not located in an open office layout, or where users who share a common responsibility are geographically distributed, team call presents the most suitable solution. The primary difference between Group Call Pickup and team call is that, with Group Call Pickup, an incoming call rings only at the intended destination, but anyone can still choose to answer it by dialing a group number. With team call, the call rings at all the team members' phones, and any user in the team can pick up the phone to answer the call. An additional difference between Group Call Pickup and team call is that Group Call Pickup is managed by an administrator, through Lync Server. With team call, end users manage the feature by using the Lync client. With Group Call Pickup, therefore, this aspect of call management can be centralized.

Group Call Pickup is built on the Call Park application. When you deploy Group Call Pickup, you configure the call park orbit table with separate ranges of extension numbers that are designated as call pickup group numbers. Like call park orbit numbers, call pickup group numbers must be virtual extensions that have no user or phone assigned to them. Each Front End pool where you deploy Group Call Pickup can have one or more ranges of call pickup group numbers. The group number ranges must be globally unique across the Lync Server deployment.

<div>


> [!NOTE]  
> Number ranges that are designated as Group Call Pickup numbers in the call park orbit table cannot be managed or viewed by using the Lync Server Control Panel. The only way to see all the number ranges in the call park orbit table is to use Lync Server Management Shell. Similarly, the only way to add, modify, or remove Group Call Pickup numbers is to use Lync Server Management Shell.



</div>

After you configure the call pickup group numbers, you assign users to a call pickup group. Any user who is assigned to a call pickup group can have their calls answered by other users. When a call comes in to a user who is assigned to a call pickup group, any other user who notices the call can answer it by manually dialing the call pickup group number. The user who picks up the call does not need to be a member of the group. When a call is picked up by another user, a notification is sent to the number originally called.

<div>


> [!NOTE]  
> A user can be a member of only one call pickup group.



</div>

<div>


> [!NOTE]  
> Although any user in the Lync Server deployment can answer a call to a call pickup group member, the person answering the call must know the correct call pickup group number to dial.



</div>

If a user dials a call pickup group number to answer a call when multiple phones in the group are ringing, the user answers the call that has been ringing the longest.

Simultaneous ringing settings will work for users who have group call pickup. That is, a call made to a user who has Group Call Pickup will ring for all the configured destinations, and another user can answer the call. The exception to this rule is when the user configures simultaneous ringing to call all the team members.

Group Call Pickup cannot be used to answer the following types of calls:

  - Calls to a private line

  - Calls from a contact who has been assigned the Friends and Family privacy relationship
    
    <div>
    

    > [!TIP]  
    > A user who is a member of a call pickup group can prevent certain calls from being retrieved through Group Call Pickup by marking the contact as a personal contact in the Lync client. To mark a contact as a personal contact, set the Privacy Relationship for the contact to Friends and Family. Any incoming call from contacts with the Privacy Relationship set to Friends and Family cannot be retrieved by using Group Call Pickup.

    
    </div>

  - Video portion of audio/video calls
    
    <div>
    

    > [!NOTE]  
    > If a user answers an audio/video call, the user receives only the audio. Either the person calling or the person answering the call can escalate the call to add video.

    
    </div>

  - Simultaneous ringing calls that are routed to team call members

  - Calls routed to a delegate

  - Calls routed to a response group

The following types of users cannot participate in Group Call Pickup. That is, they should not be included in a Group Call Pickup group, and they cannot pick up calls for users who have Group Call Pickup enabled.

  - Users who are homed online in a hybrid deployment

  - Users who are not homed on a Lync Server 2013 pool with Cumulative Updates for Lync Server 2013: February 2013 in an on-premises deployment

If no one answers a call to a member of a call pickup group, the call is routed as specified in the client settings. That is, the call goes to voicemail or is forwarded to a different destination, as specified in the client settings.

</div>

<span> </span>

</div>

</div>

</div>

