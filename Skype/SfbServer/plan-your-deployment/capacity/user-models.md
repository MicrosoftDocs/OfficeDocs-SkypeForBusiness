---
title: "User models in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: c551371c-d740-4372-bada-f0d713ec0d33
description: "The user models described here provide the basis for the capacity planning measurements and recommendations described in Capacity planning user model usage for Skype for Business Server."
---

# User models in Skype for Business Server
 
The user models described here provide the basis for the capacity planning measurements and recommendations described in [Capacity planning user model usage for Skype for Business Server](user-model.md).
  
## Skype for Business Server User Models

The following table describes the user model for registration, contacts, instant messaging (IM), and presence for Skype for Business Server.
  
**Environment and Registration User Model**

|**Category**|**Description**|
|:-----|:-----|
|Deployment size and distribution  <br/> |We model a large deployment with three central sites, with one Front End pool per site.  <br/> |
|Percentage of Active Directory users  <br/> |We assume that 70% of all Active Directory users in the organization are enabled for Skype for Business Server. 80% of those enabled users are logged on to Skype for Business Server each day (80% concurrency). The concurrent users are the basis for the numbers in the rest of this section.  <br/> |
|Active Directory changes  <br/> |We assume that 0.5% of total users are created and enabled for Skype for Business in Active Directory each week, and that 0.5% of total users are disabled from Active Directory and from Skype for Business each week. 5% of users have at least one Active Directory attribute changed each week.  <br/> |
|Active Directory distribution groups  <br/> |We assume that the number of Active Directory distribution groups in the organization is equal to three times the number of all users in Active Directory. The distribution groups have the following sizes:  <br/> • 64% have 2-30 users  <br/> • 13% have 31-50 users  <br/> • 10% have 51-100 users  <br/> • 13% have 101-500 users  <br/> |
|Voice over IP (VoIP) users  <br/> |60% of Skype for Business Server users are enabled for unified communications (UC) (that is, their phone numbers are owned by Skype for Business Server).  <br/> |
|Registered client distribution  <br/> |65% of clients run Skype for Business software, including Skype for Business and Lync Phone Edition.  <br/> 30% of clients running client software from a previous version of Lync.  <br/> 5% of clients using Skype for Business Web App.  <br/> If mobility is enabled, we assume that 40% of users are using mobility concurrently with the other previously cited registered client options. In this case the client multiple point of presence (MPOP) ratio is 1:1.9. If mobility is disabled, the MPOP ratio is 1:1.5.  <br/> |
|Remote user distribution  <br/> |70% of users connecting internally.  <br/> 30% of users connecting through an Edge Server (you may also optionally have a Director here, but it's not required).  <br/> |
|Contact distribution  <br/> |The maximum number of contacts a user has is 1,000. Less than 1% of users have 1,000 contacts. Less than 25% of users have 100 or more contacts.  <br/> Average of 80 contacts for users with public cloud connectivity. Of these users:  <br/> • 50% of the contacts are within the organization. 10% of those users are remote users, connecting from outside the firewall.  <br/> • 40% of the contacts are Skype users.  <br/> • 10% of the contacts are from federated partners.  <br/> Average of 50 contacts for users without public cloud connectivity. Of these users:  <br/> • 80% of the contacts are within the organization. 10% of those users are remote users, connecting from outside the firewall.  <br/> • 20% of the contacts are from federated partners.  <br/> Each user has 1 distribution group in their contact list. For performance testing, we assume that distribution groups are always expanded.  <br/> |
|Session time  <br/> |The average user logon session lasts 12 hours. All users log on within 120 minutes of the start of the session.  <br/> |
   
**IM and Presence User Model**

|**Category**|**Description**|
|:-----|:-----|
|Peer-to-peer IM sessions  <br/> |Each user averages six peer-to-peer IM sessions per day.  <br/> 10 instant messages per session.  <br/> Each message is matched by two SIP INFO messages and 2 SIP 200 OK messages (for the status indicators such as "\<Name\> is Typing")  <br/> |
|Group IM sessions  <br/> |Average number of messages sent in a group IM-only session is 5 per user.  <br/> Average number of messages sent in the IM portion of an AV conference is 2 per user.  <br/> |
|Presence polling  <br/> |Overall, we assume presence polling at an average of 60 polls per user per hour. For each user, assume an average of:  <br/> • One poll per day of the presence of users in the user's organization tab (but not Contacts list). Average number of non-contacts in the user's organization tab is 15 users. Two contact card viewing operations per day.  <br/> • One presence poll every time the user clicks another user to start a conversation, estimated at once per hour.  <br/> • Six user searches per hour. Every time a search is performed, a batch poll is sent for everyone in the search result list. We assume the average size of search results is 20. If the search results stay on screen, the batch poll is refreshed every 5 minutes; we assume that there will be two such refreshes per hour.  <br/> • When the user opens or previews an email in Outlook, a poll of the presence of users in the To: and CC: fields of the email, estimated at five emails per hour and four users per email.  <br/> |
|Presence subscriptions  <br/> |When one user adds another as a contact, the first user is subscribing to five categories of information about the second user. Updates of these categories of information are automatically sent to the first user. <br/> For each client, a single batch subscription request is sent to obtain the presence state of an average of 40 contacts, with an additional 40 dialogs to obtain presence for federated contacts.  <br/> Presence for members of an expanded distribution group is found through persistent presence subscriptions, not polling, and is modeled as 1 expansion per user for each 2 hours.  <br/> Short subscriptions happen when a user logs in, there is a batch subscription for all the user's contacts, and then the user soon logs off. We assume 6 short subscriptions per user per hour, where each subscription lasts 10 minutes. <br/> |
|Presence Publication  <br/> |Presence state is published at an average of 4 publications per user per hour, with a maximum 6 per user per hour.  <br/> |
|Presence Document Size  <br/> |The average size of a complete presence document is assumed to be 4K, with a maximum of 25K.  <br/> |
   
The following table describes the user model for address book use.
  
**Address Book Usage User Model**

|**Address Book search mode**|**Usage**|
|:-----|:-----|
|Address Book Web Query only (all queries performed by Address Book Web Query service)  <br/> |Four prefix queries per user per day.  <br/> 60 exact search queries per user per day. 40% of those are batched, with an average of 20 contacts per query. The other 60% of the queries are for a single contact.  <br/> 25 photo queries per user per day. 24 are for a single photo, the other is a batch query with an average of 20 contacts.  <br/> One total organization search query per user per day.  <br/> |
|Mixed mode, both address book file and web queries used. This is the default mode.  <br/> |Only two types of queries go to the network, the photo and total organizational search queries.  <br/> 25 photo queries per user per day. 24 are for a single photo, the other is a batch query with an average of 20 contacts.  <br/> One total organization search query per user per day.  <br/> |
   
The following table describes the conferencing model.
  
**Conferencing Model**

|**Category**|**Description**|
|:-----|:-----|
|Scheduled meetings versus "Meet now" meetings  <br/> |60% scheduled, 40% unscheduled.  <br/> Of the scheduled meetings, we assume that 80% are assigned conferences, which are occurrences of recurring conferences; 10% are one-time open meetings; 8% are one-time anonymous meetings, and 2% are one-time closed meetings.  <br/> |
|Conferencing client distribution  <br/> |For scheduled meetings:  <br/> • 65% of conferencing users use Skype for Business 2016.  <br/> • 5% of conferencing users use Skype for Business Web App.  <br/> • 30% of conferencing users use earlier clients, including Lync 2013 and Microsoft Lync 2010.  <br/> For unscheduled meetings:  <br/> • 70% of conferencing users use Skype for Business.  <br/> • 30% of conferencing users use earlier clients, including Lync 2013 and Microsoft Lync 2010.  <br/> |
|Meeting concurrency  <br/> |5% of users will be in conferences during working hours. Thus, in an 80,000-user pool, as many as 4,000 users might be in conferences at any one time.  <br/> |
|Meeting audio distribution  <br/> |40% mixed VoIP audio and dial-in conferencing, with a 3:1 ratio of VoIP users to dial-in users.  <br/> 35% VoIP audio only.  <br/> 15% dial-in conferencing audio only.  <br/> 10% no audio (IM-only conferences, with an average of five messages sent per user).  <br/> |
|Media mix for conferences  <br/> |75% of conferences are web conferences, which include audio plus some other collaboration modalities.  <br/> For these conferences, the other collaboration methods are as follows:  <br/> **Note:** These numbers add up to more than 100% because one conference can have multiple collaboration methods. <br/> • 50% add application sharing. We assume one users sends data at a peak of 1.1 MB per second.  <br/> • 50% add instant messaging (with an average of 2 messages per user).  <br/> • 20% add data collaboration, including PowerPoint or whiteboard In these, an average of 2 PowerPoint files presented per conference, with an average PowerPoint file size of 10 MB (without embedded video) or 30 MB (with embedded video). Average of 20 annotations per whiteboard.  <br/> • 20% add video. Of these users, 70% are in conferences enabled for multiview video, where each user receives 2-3 video streams.  <br/> • 15% add shared notes.  <br/> |
|Meeting participant distribution  <br/> |50% internal, authenticated users.  <br/> 25% remote access, authenticated users.  <br/> 15% anonymous users.  <br/> 10% federated users.  <br/> |
|Meeting join distribution  <br/> |Users are simulated as joining the meeting within the first 5 minutes.  <br/> |
   
In regular Front End pools, Skype for Business Server has a maximum supported meeting size of 250 users. Each pool can host one 250-user meeting at a time. While this large meeting is occurring, the pool can also host other smaller conferences. Additionally, you can support meetings of up to 1000 users by setting up a dedicated pool to host these meetings. For details, see [Plan for large meetings in Skype for Business Server](../../plan-your-deployment/conferencing/large-meetings.md).
  
Conferences were simulated as follows:
  
- 85% of conferences had four participants.
    
- 10% of conferences had six participants.
    
- 5% of conferences had 11 participants.
    
- One large conference of 250 users.
    
The following table provides details about the user model for conferences involving dial-in users.
  
**Dial-In Conferencing User Model**

|**Category**|**Description**|
|:-----|:-----|
|Authenticated/anonymous  <br/> |70% of callers join as anonymous and are prompted for a recorded name. 30% join as authenticated users.  <br/> |
|Call duration and music on hold  <br/> |Average call duration without music on hold: 50 seconds.  <br/> 50% of call-in users hear music on hold, for an average of 5 minutes.  <br/> |
|Dual-tone multifrequency (DTMF)  <br/> |15% of conferences that are dial-in only have phone leaders. 10% of mixed conferences that include dial-in users also have phone leaders.  <br/> 20% of phone leaders use 2 DTMF commands per conference.  <br/> |
|Announcement languages  <br/> |Simulations use English as the announcement language.  <br/> |
   
The following table provides details about the user model for conference lobbies.
  
**Conference Lobby User Model**

|**Category**|**Description**|
|:-----|:-----|
|Number of users in lobby  <br/> |5% of dial-in users go through the lobby, and 25% of other users go through the lobby  <br/> |
|Admitting from lobby  <br/> |In simulations, all users were admitted by the presenter before client timeout.  <br/> |
   
The following table describes the user model for other peer-to-peer sessions.
  
**Peer-to-Peer Sessions User Model**

|**Category**|**Description**|
|:-----|:-----|
|Application sharing  <br/> |Each user participates in 5 peer-to-peer application sharing sessions per month, for an average of 0.25 sessions per day.  <br/> |
|File transfer  <br/> |Each user participates in 1 peer-to-peer file transfer session per month (as part of an IM session), for an average of 0.05 sessions per day. The average session file size transferred is 1 MB.  <br/> |
   
The following table describes the user model for policies.
  
**Policies User Model**

|**Category**|**Description**|
|:-----|:-----|
|Conferencing, Presence, and Archiving Policies  <br/> |We assume that there is one global policy, 10 tag conferencing policies, 4 Archiving policies, and 10 tag presence policies.  <br/> |
|Voice Policy  <br/> |We assume that there is one global policy and 2 tag policies per site. 100% of sites have a site policy, and 30% of users have a per-user policy assigned. We assume one dial plan per site and two routes per site.  <br/> |
   
## Busy Hour

For peer-to-peer sessions, peak load is calculated using busy hour call attempts (BHCA). This voice industry term assumes that 50% of all calls for the day will be completed in 20% of the time. It is calculated using the following formula:
  
 `BHCA=(total calls * 0.5) / 1.6`
  
Performance testing simulated busy hour by running VoIP and other peer-to-peer sessions at a busy hour load for at least 1.6 hours per day.
  
Conferencing peak load assumes that 75% of all conferences for an eight-hour day happen in 4 peak time hours. Those peak hours have 1.5 times the average conferencing load.
  
## Enterprise Voice to PSTN Calls

The following assumptions apply to Enterprise Voice calls:
  
- 60% of users are enabled for Enterprise Voice, and 60% of these users are enabled for PSTN calling.
    
- Each of these users enabled for PSTN calling makes 4 PSTN calls during the busy hour. Each call duration is 3 minutes.
    
- 65% of these PSTN voice calls use media bypass.
    
## Mobility

40% of registered users are assumed to be enabled for Mobility. For each user that has mobility enabled, we assume that the activity of the mobile client is additive to that of the other MPOP instances for that user, with the exception of conferencing interactions, for which the mobility client is just another client type that can be used to participate in conferences.
  
## Persistent Chat

We assume that 25% of registered users will be involved in Persistent chat sessions, with the following characteristics:
  
- An average of 1.5 chat rooms per user
    
- Each chat room results in 12 polling requests per hour, targeting an average of 10 users each
    
## Response Group and Call Park

We assume that 0.15% of registered users belong to response groups. We assume that 0.02% of registered users have parked calls at any given point of time.
  

