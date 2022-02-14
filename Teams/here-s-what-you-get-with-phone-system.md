---
title: "Here's what you get with Phone System"
ms.reviewer: 
author: CarolynRowe
ms.author: crowe
manager: serdars
msreviewer: jastarck, roykuntz
ms.topic: conceptual
ms.assetid: bc9756d1-8a2f-42c4-98f6-afb17c29231c
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: 
  - Phone System
description: "Learn about the features, availability, and how to plan and set up Microsoft Phone System for your business. "
---

# Here's what you get with Phone System

This article describes Phone System features. For more information about using Phone System as your Private Branch Exchange (PBX) replacement, and options for connecting to the Public Switched Telephone Network (PSTN), see [What is Phone System](what-is-phone-system-in-office-365.md).

Clients are available for PC, Mac, and mobile, which provides features on devices from tablets and mobile phones to PCs and desktop IP phones. For more information, see [Get clients for Microsoft Teams](get-clients.md).

 > [!Note]
> For details about Teams phone systems on different platforms, see [Teams features by platform](https://support.microsoft.com/office/teams-features-by-platform-debe7ff4-7db4-4138-b7d0-fcc276f392d3).

To use Phone System features, your organization must have a Phone System license. For more information about licensing, see [Microsoft Teams add-on licensing](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md).

Be aware that most features require you to assign the Phone System license and ensure that users are "voice enabled." To assign the license, use the [Set-CsPhoneNumberAssignment cmdlet](/powershell/module/teams/set-csphonenumberassignment?view=teams-ps) and set the **EnterpriseVoiceEnabled** parameter to $true. A few features, such as cloud auto attendant, do not require a user to be voice enabled. Exceptions are called out in the table below.
  
## Phone System features

Phone System provides the following features.
  
|Phone System feature  |Description |
|:-----|:-----|
|[Cloud auto attendants](what-are-phone-system-auto-attendants.md)  |Lets you create a menu system that enables external and internal callers to locate and place or transfer calls to company users or departments in your organization.  <br/> Note that users *do not* need to be voice enabled to receive calls from the auto attendant dial by name, dial by number directory search. Users *do* need to be voice enabled to receive calls from the auto attendant menu options. |
|[Cloud call queues](create-a-phone-system-call-queue.md) <br> |Lets you configure how call queues are managed for your organization: for example, set up greetings and music on hold, search for the next available call agent to handle the call, and so on.  <br/> Note that users *do* need to be voice enabled to receive calls from a call queue.|
|[Music on hold](music-on-hold.md) | Plays default music defined by the service or custom music uploaded by the tenant administrator when an external call from the Public Switched Telephone Network (PSTN) is placed on hold. This feature works for one-to-one PSTN-to-Teams calls in addition to calls made to a call queue. This feature provides on-hold notification parity with other platforms. |
|Call answer/initiate (by name and number)   |Lets users answer inbound calls with a touch, and place outbound calls either by dialing the full phone number or by clicking a name in the client.   |
|[Call forwarding options and simultaneous ring](https://support.office.com/article/call-forwarding-call-groups-and-simultaneous-ring-in-teams-a88da9e8-1343-4d3c-9bda-4b9615e4183e)  |Lets users set up forwarding rules so calls can go with them anywhere, or calls can be forwarded to colleagues or to voicemail.   |
|[Group call pickup and forward to group](call-sharing-and-group-call-pickup.md)  | Lets users share incoming calls with colleagues so that the colleagues can answer calls that occur while the user is unavailable. Less disruptive to recipients than other forms of call sharing (such as call forwarding or simultaneous ringing) because users can configure how they want to be notified of an incoming shared call. |
|[Transfer a call and consultative transfer](https://support.office.com/article/Transfer-a-call-in-Teams-b7f40f14-e083-46b9-b739-68038c8f73a0)  |Lets users transfers calls to another person. Or, if they need to leave their office but want to continue the conversation, they can transfer the calls from their PC or IP phone to their cell phone.  <br/> Note that users *do not* need to be voice enabled to receive transferred calls from another user. |
|[Transfer to voicemail mid call*](https://support.office.com/article/Transfer-a-call-in-Teams-b7f40f14-e083-46b9-b739-68038c8f73a0)  | Lets users transfer to voicemail during a call. |
|[Call park and retrieve](call-park-and-retrieve.md)   | Lets users place a call on hold in the Teams service in the cloud. When a call is parked, the service generates a unique code for call retrieval. The user who parked the call or someone else can then use that code and a supported app or device to retrieve the call.  |
|Call phone number from search   | Lets users place a call from the search box by using the /call command and specifying a name or a number.  |
|[Caller ID](how-can-caller-id-be-used-in-your-organization.md)   |Calls from inside the company display a detailed caller ID that pulls information from the corporate directory, showing picture ID and job title instead of just a phone number. For calls from external phone numbers, the caller ID as provided by the phone service provider is displayed. If the external phone numbers are secondary numbers in the corporate directory, then the information from the corporate directory will be displayed.   |
|Device switching   |Lets users play a call or meeting on another HID device that is connected to Teams; for example, switching from their PC speakers to a headset.    |
|Presence-based call routing  |Controls inbound communications with presence, enabling the user to block all incoming communication except from those specifically indicated.   |
|[Integrated dial pad](https://support.office.com/article/use-the-dial-pad-in-teams-27bc60b5-74c0-4e9c-808b-da4db9514d89)  | Lets users dial by name or by number anywhere in the search bar and in the dial pad, speeding up the process of making outbound calls.  |
|Federated calling   |Lets users securely connect, communicate, and collaborate with users in federated tenants.   |
|[Make and receive a video call](https://support.office.com/article/abf62493-670f-4b0d-b2cf-fe03b49caf42)  | If the user's account is enabled for video calls, the user can make face-to-face video calls with their contacts. All they need is a camera, their computer’s speakers and microphone. Users can also use a headset if their computer doesn’t have a built-in audio device. |
|[Cloud Voicemail](set-up-phone-system-voicemail.md)  | When a user receives a voicemail, it is delivered to their Exchange mailbox as an email with the voicemail message as an attachment. Users can listen to their messages on their certified desktop phone, and on all Teams or Skype for Business applications. Support for voicemail transcription has been added as of March 2017 and is enabled by default for all organizations and users. <br> Note that users *do not* need a Phone System license, *nor* do they need to be voice enabled to use Cloud Voicemail features.    |
|[Cloud Voicemail user settings](https://support.office.com/article/manage-your-call-settings-in-teams-456cb611-3477-496f-b31a-6ab752a7595f?ui=en-US&rs=en-US&ad=US)  | Lets users configure their client settings for voicemail greetings, call answering rules, and greeting language, including out-of-office greetings. <br> Note that users *do not* need a Phone System license, *nor* do they need to be voice enabled to use Cloud Voicemail features.  |
|[Secondary ringer](https://support.office.com/article/Manage-your-call-settings-in-Teams-456cb611-3477-496f-b31a-6ab752a7595f)  | Users with multiple speaker devices connected to their PC can choose to set a secondary device to ring in addition to their default speaker. For example, a user with a headset connected to the PC and desk speakers can choose to have both headset and desk speakers ring when a call comes in so that they don’t miss a call.  |
|[Distinctive ring alerts](https://support.office.com/article/Manage-your-call-settings-in-Teams-456cb611-3477-496f-b31a-6ab752a7595f) (Teams only) |Lets users choose separate ringtones for  normal calls, forwarded calls, and delegated calls so they can distinguish the type of call.   |
|[Shared Line Appearance](shared-line-appearance.md)  | Lets users share their phone line so that another user can make and receive calls on their behalf.|
|[Busy on Busy](teams-calling-policy.md) (Teams only)  | A calling policy that lets you configure how incoming calls are handled when a user is: <ul><li>in a call </li><li>in a conference</li><li>has a call placed on hold. </li></ul> The caller will receive one of the following responses: <ul><li>hear a busy signal when the callee is on the phone</li> <li>will be routed accordingly to the user's unanswered settings. One option lets the caller leave a voicemail for the user who is already on a call.</li></ul> The callee gets a missed call notification but isn't able to answer incoming calls. This feature is disabled by default, but can be turned on by the tenant admin.|
|[Call blocking](https://support.office.com/article/manage-your-call-settings-in-teams-456cb611-3477-496f-b31a-6ab752a7595f?ui=en-US&rs=en-US&ad=US)  | Lets users add (PSTN) phone numbers to a blocked list so that the next call from that number is blocked from ringing the user.|
|[Common Area Phones](set-up-common-area-phones.md)  | A common area phone is typically placed in an area like a lobby or conference room making it available to multiple people. Common area phones are set up as devices rather than users, and can automatically sign into a network.|
|[Media bypass support](direct-routing-plan-media-bypass.md) (for Teams Direct Routing only)  | For better performance, media is kept between the Session Border Controller (SBC) and the client instead of sending it through the Phone System. |
|[Unassigned number routing](routing-calls-to-unassigned-numbers.md) | Allows routing of unassigned numbers to users, auto attendants, call queues or a custom announcement. |

## Availability in GCC High and DoD clouds
<a name="bkmk_setup"> </a>

The following capabilities are not yet available in GCC High and DoD Clouds. 

- [Call settings for secondary ringer, voicemail, and enhanced delegation](https://support.office.com/article/Manage-your-call-settings-in-Teams-456cb611-3477-496f-b31a-6ab752a7595f)
- [Transfer to voicemail mid call](https://support.office.com/article/Transfer-a-call-in-Teams-b7f40f14-e083-46b9-b739-68038c8f73a0)
- Call phone number from search bar
- Music on hold
- Azure AD reverse number lookup

## Related topics

- [What is Phone System](what-is-phone-system-in-office-365.md)
- [Cloud voice in Microsoft Teams](cloud-voice-landing-page.md)
- [Set up Phone System](setting-up-your-phone-system.md)
- [Which Calling Plan is right for you?](calling-plan-landing-page.md)
- [Monitor and manage call quality](monitor-call-quality-qos.md)
- [Microsoft Teams add-on licensing](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md)
- [Pricing for Phone System](https://products.office.com/microsoft-teams/voice-calling#requirements)
- [Teams for Virtualized Desktop Infrastructure with callings and meetings](teams-for-vdi.md#teams-on-vdi-with-calling-and-meetings)
