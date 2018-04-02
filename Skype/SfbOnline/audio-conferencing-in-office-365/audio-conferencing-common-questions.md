---
title: "Audio Conferencing common questions"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: oscarr
ms.date: 01/22/2018
ms.topic: article
ms.assetid: a90ea695-aabf-4f10-ae92-24b3f6b27c56
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
ms.collection: 
- Adm_Skype4B_Online
- Strat_SB_PSTN
ms.audience: Admin
appliesto:
- Skype for Business 
- Microsoft Teams
localization_priority: Normal
f1keywords: None
ms.custom:
- Strat_SB_PSTN
- Audio Conferencing
description: "The following are some of the top questions we get from our customers who want to use Audio Conferencing."
---

# Audio Conferencing common questions

The following are some of the top questions we get from our customers who want to use Audio Conferencing. 
  
## What are the benefits of Audio Conferencing?

Calling in to meetings is very useful when people are on the road, for example, and can't attend a meeting using the Skype for Business or Microsoft Teams app on their laptop or mobile devices. But there are other scenarios in which using a phone to attend a Skype for Business or Microsoft Teams meeting can be a better option than using an app on a computer:
  
- Internet connectivity is limited.
    
- A meeting is audio only.
    
- The person tried to join a Skype for Business meeting and it failed.
    
- The call quality is better if they dial in.
    
- People can join a meeting "hands free" using Bluetooth devices.
    
- People find it's easier and more convenient for their situation.
    
## Who can attend an Audio Conferencing meeting? And who can I hear?

Anyone who has the dial-in number and conference ID can join a Skype for Business or Microsoft Teams meeting, unless the meeting organizer has locked the meeting.
  
Whether you're calling in using a phone or the Skype for Business or Microsoft Teams apps, you'll be able to hear everyone else on the call, and they can hear you. The meeting organizer has the ability to "mute" meeting attendees if they don't want to hear them. 
  
## Can I add a toll-free number for my Audio Conferencing users?

Yes, toll-free phone numbers (service numbers) are available but only in some countries/regions. To see a list of the numbers that are available, go [here](../country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md).
  
## How many local dial-in numbers are currently supported?

There are local dial-in numbers that are assigned to you when you purchase the licenses for Audio Conferencing. The dial-in numbers will be included in the meeting invite. These local numbers will be only available to your organization. The phone assigned to your organization and that number is shared by the users within that organization that are enabled for Audio Conferencing. So, Skype for Business or Microsoft Teams meetings scheduled by User A and another User B will both have the same dial-in number.
  
Local dial-in numbers, and also in some cases international dial-in numbers from the country where your organization is located, will be included on the meeting invite. If a meeting attendee uses a different number that is include in the invite, it will be a shared phone number.
  
## How many international dial-in numbers does Audio Conferencing in Office 365 support?

For a current list of countries/regions, see [Phone numbers for Audio Conferencing](phone-numbers-for-audio-conferencing.md).
  
## Can I set up local numbers for Audio Conferencing from additional cities in the country?

If phone numbers for Audio Conferencing aren't available in your area or don't meet the needs of your organization, please send us feedback at [SkypeFeedback forums](http://www.skypefeedback.com/forums/299910--preview/category/119971-pstn-conferencing).
  
## What is the maximum length of the Audio Conferencing meetings?

The maximum length of time depends on who is in the meeting and the type of authentication they used to join the meeting.
  
|**Meeting attendees**|**Meeting end time**|
|:-----|:-----|
|There are users who have joined using the Skype for Business or Microsoft Teams app or have dialed in to the meeting.  <br/> |The meeting ends if there are no changes to the attendee list after 24 hours.  <br/> |
|All of the users are dialed in to the meeting but someone has used a PIN to enter the meeting.  <br/> |The meeting ends after 24 hours.  <br/> |
|All of the users are dialed in to the meeting but there wasn't anyone who used a PIN to enter the meeting.  <br/> |The meeting ends after 4 hours.  <br/> |
   
## How many total phone participants can I have in meetings?

Audio Conferencing allows up to 250 phone attendees.
  
To find out about meeting limits, see [Skype for Business Online Limits](https://technet.microsoft.com/en-us/library/skype-for-business-online-limits.aspx#bkmk_Meeting_LyncOnlineLimits).
  
## Why did users start receiving emails with their Audio Conferencing information?

We added a new feature that allows you, the [admin](https://support.office.com/en-us/article/eac4d046-1afd-4f1a-85fc-8219c79e1504), to send and update Audio Conferencing information and PIN in email. To learn more about it, including how to disable it, see [Enable or disable sending emails when Audio Conferencing settings change](enable-or-disable-sending-emails-when-their-settings-change.md).
  
## Can Audio Conferencing be used by the users who are part of an on-premises deployment of Skype for Business Server 2015?

We're not quite there. However, you can continue to use audio conferencing that is available in Skype for Business Server 2015 along with a PSTN gateway for your on-premise users. 
  
## Can a user get a personal conference ID?

Skype for Business and Microsoft Teams users will be randomly assigned conferencing IDs and can't reserve or set a static conference ID that only they can use. 
  
## Can I use Audio Conferencing with Skype Meeting Broadcast?

There isn't support currently for users enabled for Audio Conferencing to join a Skype Meeting Broadcast.
  
## Can a user get operator assistance during a meeting?

No, a user can't get any operator assistance or support by pressing *0 during the meeting. If there are issues with Audio Conferencing, an administrator for an organization can contact [Microsoft support for Office 365](https://support.office.com/en-us/article/Microsoft-support-for-Office-365-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b).
  
## How does a user access or change their conference ID?

A Skype for Business or Microsoft Teams user can find the conference ID that is assigned to them by scheduling a meeting in Outlook and Outlook on the web. Also, users can find the conference ID in the email that will be sent to them after they are set up.
  
> [!NOTE]
> Users won't be able to reset their conference ID. The conference ID can only be reset by you, the [admin](https://support.office.com/en-us/article/admin-eac4d046-1afd-4f1a-85fc-8219c79e1504), for the organization. 
  
We are working on a solution that will let the user access and reset a conference ID without help from an organization's admin.
  
## How does a user access or change his/her PIN?

The Skype for Business or Microsoft Teams user can find the PIN in an email that will be sent to them once they are set up.
  
> [!NOTE]
> A Skype for Business or Microsoft Teams user won't be able to reset their PIN. The PIN can only be reset by you, the admin. When a PIN is reset, an email is sent to the user. 
  
We are working on a solution that will let the user access and reset a PIN without help from a organization's administrator.
  
## What in-meeting dial-pad commands are supported?

- *6 (Mute/unmute themselves)
    
- *1 (Plays the descriptions of dial-pad commands that are available) 
    
## Can attendees dial out to international phone numbers when they are in a Skype for Business or Microsoft Teams meeting?

Yes, attendees can dial out internationally and invite other callers into a Skype for Business or Microsoft Teams meeting. See [Dialing out from a meeting so other people can join it](dialing-out-from-a-meeting-so-other-people-can-join-it.md).
  
## How does a Skype for Business or Microsoft Teams user schedule a meeting with Audio Conferencing meeting details?

When a user is assigned an **Audio Conferencing** license and the user creates a new Skype for Business or Microsoft Teams meeting in Outlook or Outlook on the web, the dial-in phone numbers and conferencing IDs are added to the meeting invite automatically.
  
## How does a user schedule and start a meeting when all attendees will be using a phone to dial-in?

Scheduling a meeting that will be joined by all attendees using a phone to dial-in is not different from scheduling a regular online meeting. However, there are two ways to start a meeting on which all of the participants use a phone to dial-in:

- **Option #1**: By default, if the meeting organizer and all participants are joining a meeting using a phone, the meeting organizer needs to input his or her Audio Conferencing PIN to start it. Callers get asked if they wish to authenticate as the organizer of a given meeting when they dial the phone number of an online meeting. All participants that join the meeting via dial-in before the organizer starts will be placed in the lobby and will listen to music on hold. Once the organizer starts it by inputting his or her Audio Conferencing PIN, all participants in the lobby will automatically join the meeting.

- **Option #2**: If the “Allow unauthenticated callers to be the first people in a meeting“ setting (disabled by default) is enabled for a given organizer, then all meetings scheduled by that user will be able to be started without having the organizer input is or her Audio Conferencing PIN. When this setting is enabled, the meeting will start as soon as the first participant joins it via a dial-in phone number and he or she will not be put in the lobby. For additional information see, [Manage Audio Conferencing settings for a user](manage-the-audio-conferencing-settings-for-a-user.md)
   
## Related topics

[Set up Skype for Business Online](../set-up-skype-for-business-online/set-up-skype-for-business-online.md)
  
[Phone numbers for Audio Conferencing](phone-numbers-for-audio-conferencing.md)
  
