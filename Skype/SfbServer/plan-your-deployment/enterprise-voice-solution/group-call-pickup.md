---
title: "Plan for Group Call Pickup in Skype for Business"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom:
ms.assetid: 3dc0eca8-c773-463c-96bb-9cd6afa2a840
description: "Planning for Group Call Pickup in Skype for Business Server Enterprise Voice, which enables users to answer calls originally intended for others."
---

# Plan for Group Call Pickup in Skype for Business
 
Planning for Group Call Pickup in Skype for Business Server Enterprise Voice, which enables users to answer calls originally intended for others.
  
Group Call Pickup enables users to answer incoming calls to their colleagues from their own phones. This increases the availability of a user's line by enabling other users to answer an incoming call by dialing a call pickup group number. When Group Call Pickup is deployed, the number of incoming calls that are routed to voice mail can be significantly reduced, which is particularly useful for calls from customers who are external to your organization.
  
The Group Call Pickup feature is designed in particular for business units in open office environments. Incoming calls are not disruptive because they ring only at the intended destination. Other users who hear the ring, however, can still pick up the call simply by dialing the group number. 
  
In environments where users are not located in an open office layout, or where users who share a common responsibility are geographically distributed, team call presents the most suitable solution. The primary difference between Group Call Pickup and team call is that, with Group Call Pickup, an incoming call rings only at the intended destination, but anyone can still choose to answer it by dialing a group number. With team call, the call rings at all the team members' phones, and any user in the team can pick up the phone to answer the call. An additional difference between Group Call Pickup and team call is that Group Call Pickup is managed by an administrator, through Skype for Business Server. With team call, end users manage the feature by using the Skype for Business client. With Group Call Pickup, therefore, this aspect of call management can be centralized.
  
Group Call Pickup is built on the Call Park application. When you deploy Group Call Pickup, you configure the call park orbit table with separate ranges of extension numbers that are designated as call pickup group numbers. Like call park orbit numbers, call pickup group numbers must be virtual extensions that have no user or phone assigned to them. Each Front End pool where you deploy Group Call Pickup can have one or more ranges of call pickup group numbers. The group number ranges must be globally unique across the Skype for Business Server deployment. 
  
> [!NOTE]
> Number ranges that are designated as Group Call Pickup numbers in the call park orbit table cannot be managed or viewed by using the Skype for Business Server Control Panel. The only way to see all the number ranges in the call park orbit table is to use Skype for Business Server Management Shell. Similarly, the only way to add, modify, or remove Group Call Pickup numbers is to use Skype for Business Server Management Shell. 
  
After you configure the call pickup group numbers, you assign users to a call pickup group. Any user who is assigned to a call pickup group can have their calls answered by other users. When a call comes in to a user who is assigned to a call pickup group, any other user who notices the call can answer it by manually dialing the call pickup group number. The user who picks up the call does not need to be a member of the group. When a call is picked up by another user, a notification is sent to the number originally called.
  
> [!NOTE]
> A user can be a member of only one call pickup group. 
  
> [!NOTE]
> Although any user in the Skype for Business Server deployment can answer a call to a call pickup group member, the person answering the call must know the correct call pickup group number to dial. 
  
If a user dials a call pickup group number to answer a call when multiple phones in the group are ringing, the user answers the call that has been ringing the longest.
  
Simultaneous ringing settings will work for users who have group call pickup. That is, a call made to a user who has Group Call Pickup will ring for all the configured destinations, and another user can answer the call. The exception to this rule is when the user configures simultaneous ringing to call all the team members.
  
Group Call Pickup cannot be used to answer the following types of calls:
  
- Calls to a private line
    
- Calls from a contact who has been assigned the Friends and Family privacy relationship
    
    > [!TIP]
    > A user who is a member of a call pickup group can prevent certain calls from being retrieved through Group Call Pickup by marking the contact as a personal contact in the Skype for Business client. To mark a contact as a personal contact, set the Privacy Relationship for the contact to Friends and Family. Any incoming call from contacts with the Privacy Relationship set to Friends and Family cannot be retrieved by using Group Call Pickup. 
  
- Video portion of audio/video calls 
    
    > [!NOTE]
    > If a user answers an audio/video call, the user receives only the audio. Either the person calling or the person answering the call can escalate the call to add video. 
  
- Simultaneous ringing calls that are routed to team call members
    
- Calls routed to a delegate
    
- Calls routed to a response group
    
The following types of users cannot participate in Group Call Pickup. That is, they should not be included in a Group Call Pickup group, and they cannot pick up calls for users who have Group Call Pickup enabled.
  
- Users who are homed online in a hybrid deployment
    
- Users who are not homed on either a Skype for Business Server 2015 pool or a Lync Server 2013 pool with Cumulative Updates for Lync Server 2013: February 2013 in an on-premises deployment
    
If no one answers a call to a member of a call pickup group, the call is routed as specified in the client settings. That is, the call goes to voicemail or is forwarded to a different destination, as specified in the client settings.
  
## Deployment and requirements

Group Call Pickup is automatically deployed when you deploy Enterprise Voice and the Call Park application. You enable Group Call Pickup by configuring the Call Park orbit table with separate ranges of numbers designated as call pickup group numbers, and then by assigning users to call pickup groups and enabling the users for Group Call Pickup.
  
## Clients supported for Group Call Pickup

Any of the following clients can be used to answer calls to Group Call Pickup members:
  
- Skype for Business
    
- Lync 2013
    
- Lync 2010
    
- Lync Phone Edition
    
> [!NOTE]
> Users can use any of these clients to answer calls to Group Call Pickup members, but the users must be homed on a Skype for Business Server pool or a Lync Server 2013 pool with Cumulative Updates for Lync Server 2013: February 2013. 
  
The following clients and devices are not supported for picking up calls to Group Call Pickup members:
  
- Lync Mobile
    
- Lync app for Windows 8 and Windows RT
    
- Lync for iPad
    
- Analog phones
    
- Phones with public switched telephone network (PSTN) numbers
    
## Capacity planning

The following table describes the Group Call Pickup user model that you can use as the basis for capacity planning requirements.
  
> [!IMPORTANT]
> Group Call Pickup is based on the Call Park application. Keep in mind that, for disaster recovery capacity planning, each pool of a paired pool should be able to handle the workloads for Call Park services, including Group Call Pickup, in both pools. 
  
**Group Call Pickup User Model**

|**Metric**|**Per Front End pool  <br/>  (with 8 Front End Servers)**|**Per Standard Edition server**|
|:-----|:-----|:-----|
|Recommended number of users per group  <br/> |50  <br/> |50  <br/> |
|Recommended number of groups  <br/> |500  <br/> |60  <br/> |
|Maximum number of users per pool enabled for Group Call Pickup  <br/> |25,000  <br/> |3,000  <br/> |
|Maximum rate of incoming calls to total users enabled for Group Call Pickup per pool per minute  <br/> |500  <br/> |60  <br/> |
|Maximum rate of calls retrieved by users with Group Call Pickup per pool per minute  <br/> |200  <br/> |25  <br/> |
   
> [!NOTE]
> For Front End pools that have fewer than eight Front End Servers, calculate the metrics linearly. For example, if your Front End pool has one Front End Server, calculate the maximum load as 1/8 of the values shown in the table. 
  
> [!NOTE]
> You can increase or decrease the recommended number of users per group and number of groups as long as you do not exceed the maximum number of users per pool. For example, your Standard Edition server can have 120 groups with 25 users per group because the number of users enabled for Group Call Pickup is still within the user model maximum (that is, 120 groups times 25 users is 3,000 users enabled for Group Call Pickup). 
  

