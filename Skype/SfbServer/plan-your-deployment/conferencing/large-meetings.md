---
title: "Plan for large meetings in Skype for Business Server"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 21507e18-bd79-4019-9c3a-0867fccaa3b4
description: "Summary: Read this topic to learn about best practices for implementing and managing large meetings in Skype for Business Server."
---

# Plan for large meetings in Skype for Business Server
 
**Summary:** Read this topic to learn about best practices for implementing and managing large meetings in Skype for Business Server.
  
The size of meetings that Skype for Business Server can support depends on whether conferencing is hosted on a shared or dedicated pool: anywhere from 250 participants on a shared pool to 1000 participants on a dedicated pool. 
  
> [!NOTE]
> This topic focuses on best practices for large meetings supported by Skype for Business Server. If your organization requires larger meeting capabilities, you should consider implementing a hybrid environment that takes advantage of Skype Meeting Broadcast, a new online service that is part of Office 365. 

> [!NOTE]
> Skype Meeting Broadcast enables users to host and broadcast meetings to large online audiences of up to 10,000 participants. The use of Skype Meeting Broadcast requires that Skype for Business Server already be configured in a hybrid setup with a production Office 365 tenant. All users must have an online tenant established as a prerequisite. If you are interested in deploying a hybrid solution that can take advantage of Skype Meeting Broadcast, see [What is a Skype Meeting Broadcast?](https://go.microsoft.com/fwlink/?LinkId=617071) and [Configure your on-premises deployment for Skype Meeting Broadcast](../../deploy/configure-skype-meeting-broadcast.md). 
  
Large meetings typically have the following characteristics:
  
- The meeting format is a one-to-many presentation.
    
- One or a few users are presenters, and everyone else participates only as attendees.
    
- PowerPoint presentation sharing is the main data collaboration activity.
    
- Audio is required and video may also be used.
    
- A dedicated person, generally either the meeting organizer or an assistant to the organizer, sets up the meeting well in advance.
    
- Dedicated staff (not the presenters) runs the meeting, including connecting to an online meeting, verifying that audio, video, and slide sharing work, managing lobby and user roles, muting and unmuting participants, taking questions, and managing recordings, as appropriate.
    
When a user schedules a meeting, Skype for Business Server creates a record in the conferencing database, which stores conferencing data, but does not reserve any hardware resources for the scheduled meeting ahead of time. Instead, Skype for Business Server has built-in load balancing logic to dynamically allocate conferencing resources on Front End Servers in a way that distributes loads equally across all Front End Servers in the pool. This effectively provisions and uses hardware resources, but it is important that you plan appropriately to support very large meetings. 
  
For example, when a Skype for Business Server pool is running close to its top capacity, each Front End Server might host approximately 125 average-size meetings. Adding another small meeting would not be a problem, but adding a meeting for 1000 users would be a problem because the Front End Servers would probably not be able to support such a large meeting at the same time as the other 125 meetings.
  
Supporting large meetings of up to 1000 participants requires addressing the issues related to both the shared hardware model and the no-reservation model. In general, you need to plan for a dedicated pool and follow best practices as described in the following sections. 
  
## Plan for a dedicated pool

If your organization requires meetings with greater than 250 participants, you need to plan for a dedicated pool to support the load. 
  
To have sufficient CPU and memory resources for meetings of up to 1000 users, the hosting Front End Servers should not host any other instant messaging (IM) and presence or Enterprise Voice workloads. The servers should also not host any other meetings, regardless of the size of the other meetings. To host meetings of up to 1000 users, you need to set up a separate Skype for Business Server pool that is dedicated to hosting large meetings.
  
A Skype for Business Server pool that is dedicated to hosting large meetings should host one and only one meeting of up to 1000 users at the same time, so meeting times need to be reserved in advance via an out of band scheduling process to ensure dedicated support from the Front End Servers. To support more than one large meeting at the same time, you should set up multiple dedicated large-meeting pools.
  
For more information about hardware and software requirements, and planning a topology that supports large meetings, see [Hardware and software requirements for conferencing in Skype for Business Server](hardware-and-software-requirements.md) and [Plan your conferencing topology for Skype for Business Server](conferencing-topology.md).
  
## Implement best practices for large meetings

After setting up a dedicated pool for large meetings, you can take steps to help ensure that large meetings hosted in the pool provide the best user experience. The following sections provide guidelines for managing large meetings:
  
- Create dedicated meeting organizers
    
- Create dedicated moderators
    
- Maintain a separate calendar of large meetings
    
- Implement a large-meeting scheduling process
    
- Specify appropriate scheduling details
    
- Create a conferencing policy for large meetings
    
### Create dedicated meeting organizers

To minimize the real-time communications traffic in the large-meeting pool, Microsoft does not recommend hosting users who regularly sign in using Skype for Business clients and participate in instant messaging (IM), presence, conferencing, and voice sessions. Instead, do one of the following:
  
- Create one or more dedicated user accounts just for scheduling large meetings
    
- Home the user accounts of the staff responsible for scheduling large meetings on a large-meeting pool
    
### Create dedicated moderators

With several hundred to a thousand users in a meeting, it is a good practice to have a dedicated person moderate the online session of a large meeting. This dedicated person can be a delegate of the meeting organizer or a member of the organization's large-meeting support staff. It is important to add the dedicated meeting moderator as a presenter at the time that the meeting is scheduled, although it is possible to promote an online meeting attendee to the presenter role while the meeting is in progress.
  
The meeting moderator can use all presenter functionalities of Skype for Business clients to manage the large meeting. These functionalities include:
  
- Monitoring the lobby and admitting or rejecting users in the lobby
    
- Removing any users from the meeting who should not be in the meeting
    
- Changing meeting access types
    
- Changing participant roles
    
- Inviting additional participants during the meeting using drag and drop functionality, phone dial out, or email
    
- Muting and unmuting the audience or individual users
    
- Managing meeting content, including uploading content, deleting content, and switching active content

    
### Maintain a separate calendar

For each large-meeting pool, you should maintain a separate calendar of large meetings scheduled on that pool. For example, you can home a single user account on the large-meeting pool and use Outlook with Exchange and Online Meeting Add-in for Skype for Business to maintain a separate calendar. If you use multiple user accounts to enable a support staff to create large meetings, you can set up a separate calendar that aggregates all large meetings created by the members of the support staff. 
  
Maintaining a separate large meeting calendar helps to prevent conflicts and ensure that only one large meeting is active at any time.
  
### Implement a scheduling process

Because only one large meeting at a time is supported on the dedicated large meeting pool, you should implement a large meeting scheduling process to facilitate setting up large meetings and help prevent conflicts. Such capability is not provided directly by Skype for Business Server or Skype for Business clients. One way to implement such a process is to use your organization's support team's ticketing system, if available.
  
Scheduling a large meeting involves completing the following steps:
  
- The meeting organizer or delegate determines the time, duration, and size of an upcoming meeting, in addition to the list of presenters. If the anticipated meeting size exceeds 250 users or to ensure the best user experience for a meeting of fewer than 250 users, the organizer or the delegate submits a request for a large meeting.
    
- The scheduling staff checks to see whether the requested date and time is available. Since we support only a single large meeting on the dedicated pool at a time, the scheduling staff needs to check the large-meeting calendar to determine whether there is another meeting scheduled for the requested date and time. If the requested time is available, the staff approves the meeting request.
    
- If the request is approved, the scheduling staff (using credentials on the dedicated pool) uses Online Meeting Add-in for Skype for Business with Outlook to set up a meeting on the dedicated large-meeting pool. The URL to be used to join the meeting is provided to the requester as part of the approval notice.
    
- The meeting organizer or delegate uses Outlook to schedule the upcoming meeting, adding the URL for joining the meeting to the meeting invitation. The meeting organizer or delegate then specifies the users to be invited and sends out the meeting invitation.
    
### Specify appropriate scheduling details

After checking to ensure that no other meeting is scheduled at the requested time, the large meeting support staff that handles the request schedules the meeting on the large-meeting pool. 
  
To ensure the best user experience, it is important to schedule the large meeting with the right access levels and meeting settings that are appropriate to the meeting organizer's needs. Consider the following scheduling settings configured in Skype for Business Meeting options:
  
- Use a new meeting space for each large meeting instead of reusing the dedicated meeting space. 
    
- Specify the meeting access level as follows:
    
  - If at least one invitee is external to the organization, set the meeting access type to **Anyone (no restrictions)**. This enables you to avoid having to manage a potentially large lobby when the meeting is in progress.
    
  - If the meeting is an internal-only meeting, set the meeting access type to **Anyone from my organization**.
    
    > [!NOTE]
    > Avoid setting the meeting access type to **People I invite from my company** because when you use this setting, organizers must add all user email addresses to the invitee list and you cannot invite a distribution group. Avoid setting the meeting access type to **Only me, the meeting organizer** because this setting requires that every meeting participant, including presenters, must be put in the lobby at meeting run time. The person responsible for running the large meeting must then constantly monitor the lobby roster and admit new users who are in the lobby.
  
- Allow users who dial-in from phones to enter the meeting automatically by checking the **Callers get in directly** setting.
    
- Explicitly invite the following users:
    
  - Meeting organizer and delegate (requester)
    
  - The list of presenters provided by a meeting requester
    
    > [!NOTE]
    > If the meeting access type is set to **People I choose**, you need to explicitly add each participant of a large meeting as an invitee of the meeting. 
  
- Explicitly manage presenters, instead of setting the presenter option to one of the auto-promote values. Be sure to add the following users as presenters:
    
  - Meeting organizer and delegate (requester)
    
  - The list of presenters provided by large meeting requesters
    
    By explicitly managing presenters, you can limit presenters to a small enough number to make it possible to have an effective large meeting. If the majority of meeting participants have the attendee role, it helps reduce the chance of people accidentally taking control of the presentation, deleting a PowerPoint presentation, muting/unmuting presenters, and other disruptions to the meeting. 
    
- Check the **Mute all attendees** setting to make sure that only presenters can broadcast audio into the meeting.
    
- Check the **Block attendees' video** setting to make sure only presenters can broadcast video into the meeting.
    
### Create a conferencing policy

Create a new conferencing policy specifically for large meetings, and then assign the conferencing policy to the users who are homed on the dedicated large-meeting pool. Configure the conferencing policy using the following settings:
  
- Set the **MaxMeetingSize** option to 1000. (The default is 250.)
    
- Set the **AllowLargeMeetings** option to **True**. 
    
- Set the **EnableAppDesktopSharing** option to **None**.
    
- Set the **AllowUserToScheduleMeetingsWithAppSharing** option to **False**.
    
- Set the **AllowSharedNotes** option to **False**.
    
- Set the **AllowAnnotations** option to **False**.
    
- Set the **DisablePowerPointAnnotations** option to **True**.
    
- Set the **AllowMultiview** option to **False**.
    
- Set the **EnableMultiviewJoin** option to **False**.
    
> [!NOTE]
> Support for large meetings in Skype for Business Server requires that the **AllowLargeMeetings** setting be set to true. When this setting is set to true, the Skype for Business experience will be optimized for extra-large meetings when users join the meeting. Specifically, in a large meeting, Skype for Business will not show the initial or update of the full meeting participant list, which is a performance bottleneck for both the client and Skype for Business Server. Instead, Skype for Business will only show information about the user and the list of presenters of the meeting. Skype for Business will still show the total number of participants available in the large meetings.


  
Except for the **Maximum meeting size** setting, all the other conferencing policy settings specified here are required in order to disable conferencing capabilities that are not necessary in large meetings.
  
Additionally, you need to configure the dedicated large-meeting pool so that each Skype for Business Server user who is homed on the pool and responsible for managing the meeting schedule has the appropriate permissions. To do this, do the following:
  
- Set the **Designate as presenter** option to **None**. Typically, one or just a few users of all the participants of a large meeting are presenters, so participants should not be automatically admitted to large meetings as presenters. Instead, the presenters should be explicitly designated at meeting scheduling time, or be explicitly promoted during the large meeting.
    
- Make sure that the **Assigned conference type by default** check box is not selected. This setting controls whether the Online Meeting Add-in for Skype for Business always schedules conferences using the organizer's assigned conference, which means that scheduled meetings have the same join URL and audio information. In small group collaboration scenarios, having such assigned conference type works well because everyone has their own individual assigned conference, and the constant join URL and audio information helps to facilitate faster meeting joining. However, in the large-meeting scenario, the large meeting support staff schedules the large meetings using a single set of user credentials, and then provides join URLs and audio information to the meeting requesters. In this case, using a different URL to join each meeting works better.
    
- Ensure that the **Admit anonymous users by default** check box is not selected, unless it is required. This setting affects the default meeting access type scheduled by the Online Meeting Add-in for Skype for Business when not using an assigned conference. The appropriate option for this setting depends on your organization's needs. If most large meetings for your organization are internal meetings, do not select this option. If most large meetings require that external users be able to join, select this option.
    
For more information about creating a conferencing policy, see [Manage conferencing policies in Skype for Business Server](../../manage/conferencing/conferencing-policies.md).
  

