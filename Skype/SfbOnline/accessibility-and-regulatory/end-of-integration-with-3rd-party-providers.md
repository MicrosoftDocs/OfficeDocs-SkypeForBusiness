---
title: "End of life program for the integration of Skype for Business with third-party audio conferencing providers "
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: mikedav, allancar
ms.date: 04/02/2018
ms.topic: article
ms.assetid: dc6e95cd-51e8-49ca-bcd3-78dc9dae486a
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
ms.collection: Adm_Skype4B_Online
ms.audience: Admin
appliesto:
- Skype for Business
localization_priority: None
f1keywords: None
ms.custom:
- Legal
hideEdit: true
description: "On April 1, 2019, the end of life program will conclude for the integration of Skype for Business with third-party audio conferencing providers (3rd party ACP)."
---

# End of life program for the integration of Skype for Business with third-party audio conferencing providers 

On April 2018, Microsoft announced the start of the end of life program for the integration of Skype for Business with 3rd party audio conferencing providers (3rd party ACP). 
The end of life program will conclude on April 1, 2019. When the program concludes, the integration of Skype for Business with 3rd Party Audio Conferencing Providers will stop working and the following changes will be observed on that date (April 1, 2019): 

- Participants who attempt to join any Skype for Business meeting via dial-in numbers provided by a 3rd party ACP service will no longer be connected to the Skype for Business meeting.
 
- Users enabled for a 3rd Party ACP service will no longer have their dial-in information automatically included in any new Skype for Business meeting invites. 

As part of the announcement made in April 2018, the following change have taken effect and will continue to be in place until the conclusion of the end of life program. 

- Customers with no Skype for Business users configured to use a 3rd Party ACP service will not be able to configure any users to use a 3rd Party ACP service. 

- Existing customers with Skype for Business users configured to use a 3rd Party ACP service will continue to be able to add new users for the duration of the end of life period. Please note that we do not recommend setting up additional Skype for Business users to use a 3rd Party ACP service as the changes that will come into effect in April 1st of 2019 will also apply to them. 

## Preparing for this change

To prepare for this change, we encourage impacted organizations to notify their enabled users of this planned update prior to April 1, 2019. 

After April 1, 2019, users can continue to use Skype for Business with no interruption to their online meetings,however organizations will need to enable their users for Audio Conferencing provided by Microsoft if they require dial-in audio conferencing with Skype for Business or Microsoft Teams. To learn more about Microsoft Audio Conferencing, see [Audio Conferencing](https://products.office.com/en-us/skype-for-business/audio-conferencing). 

Depending on the desired end state of an organization, there are three paths that can be followed:

- Migrating to Microsoft Audio Conferencing. 
- Continuing to separately use a 3rd party audio conferencing provider. 
- Stop using dial-in conferencing all together.

### Path #1: Migrating to Microsoft Audio Conferencing   

Organizations that decide to migrate to Microsoft Audio Conferencing prior to April 1st, 2019 will not experience any service impact during or after that date. The migration to Microsoft Audio Conferencing will introduce the following changes to an organization: 

- The service will be billed with all other Office 365 services. 

- If the standard subscription is purchased, toll dial-in cost will be included in the per user monthly subscription cost. 

- A new set of dial-in phone numbers will be provided to each organization and its users. To see the geographical coverage of Microsoft Audio Conferencing service, see [Country and region availability for Audio Conferencing and Calling Plans](../country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md) 
- Meetings that have been already scheduled by users enabled with a 3rd party ACP will be automatically rescheduled to include Microsoft Audio Conferencing dial-in information.
 
- The conference IDs of each meeting will be dynamic, meaning that each meeting will have its own dedicated conference ID. Dynamic conference IDs provide enhance security and an improved experience for back-to-back meetings.

Migrating to Microsoft Audio Conferencing is simple and it can be done in just a couple of steps after acquiring the licenses for the service. To learn about how to migrate to Microsoft Audio Conferencing, see:

- [Try or purchase Audio Conferencing in Office 365](../audio-conferencing-in-office-365/try-or-purchase-audio-conferencing-in-office-365.md)
 
**Summary:**

- Organizations that migrate to Microsoft Audio Conferencing before April 1, 2019 won’t see any impact to their service during or after that date.

- To learn more about migrating to Microsoft Audio Conferencing, see [Try or purchase Audio Conferencing in Office 365](../audio-conferencing-in-office-365/try-or-purchase-audio-conferencing-in-office-365.md). 

### Path #2: Continuing to separately use a third-party audio conferencing provider

Organizations that decide to continue using a 3rd party ACP on and after April 1, 2019 will experience service impact as the 3rd party ACP dial-in information will no longer be able to be used to join the audio portion of a Skype for Business Meeting. 

To prevent the fragmentation of audio in the Skype for Business meetings, by having some participants joining via VoIP and other via the 3rd party ACP, it’s recommended for these organizations to disable using VoIP on their users’ meetings. This way, all participants will need to join the audio portion of a meeting using the 3rd party ACP and all other workloads of the meeting (i.e. chat or screen sharing) can continue to be supported over Skype for Business. 

- To disable VoIP from all meetings of a given organizer, set the AllowIPAudio parameter of his or her Conferencing Policy to false via the Set-CsConferencingPolicy cmdlet. For additional information, see [Set-CsConferencingPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/set-csconferencingpolicy?view=skype-ps).
 
In terms of scheduling, and as of April 1, 2019 the dial-in information of a 3rd party ACP will no longer be automatically included in Skype for Business meeting invites. Users will need to manually add the dial-in information on their Skype for Business meeting invites if they wish to continue including this information as part of their meetings. 

Please note that on April 1, 2019, the existing meetings of users will not be automatically rescheduled to remove any 3rd party ACP dial-in information. Organizations that decide to keep VoIP enabled for the meetings of their users should consider disabling the integration of 3rd party ACP for their users and reschedule their meetings using the meeting migration service to remove the 3rd party audio conferencing dial-in information from their existing meetings and prevent the fragmentation of audio on already scheduled meetings. 

- To disable the integration of 3rd party audio conferencing for a given organizer, use the Remove-CsUserAcp cmdlet. For additional information, see [Remove-CsUserAcp](https://docs.microsoft.com/en-us/powershell/module/skype/remove-csuseracp?view=skype-ps). 

- To automatically reschedule the meetings of users after disabling the integration with a 3rd party audio conferencing provider, see “How do I run Meeting Migration manually for a user?” on [Setting up the Meeting Migration Service (MMS)](../audio-conferencing-in-office-365/setting-up-the-meeting-migration-service-mms.md). 

**Summary:**

- Organizations that decide to continue using a 3rd party ACP on and after April 1, 2019 will be impacted as a 3rd party ACP won’t be able to be used to join a Skype for Business meeting and new meetings will not include 3rd party ACP dial-in information. 

- It’s recommended that VoIP is disabled for all meetings of all affected users to prevent the audio from being fragmented across participants joining via VoIP and via a 3rd party ACP. 

    - To disable VoIP from all meetings of a given organizer, set the AllowIPAudio parameter of the user’s Conferencing Policy to false via the Set-CsConferencingPolicy cmdlet. For additional information, see [Set-CsConferencingPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/set-csconferencingpolicy?view=skype-ps). 

### Path #3: Stop using dial-in conferencing altogether

Organizations that decide to stop using dial-in conferencing completely (neither provided by Microsoft nor by a 3rd party ACP) can fully rely on VoIP to support the audio portion of a Skype for Business meeting. 

These organizations would need to disable their users from using a 3rd party audio conferencing provider and have their meetings automatically rescheduled using the meeting migration service to remove their dial-in conferencing information. 

- To disable the integration of 3rd party audio conferencing for a given organizer, use the Remove-CsUserAcp cmdlet. For additional information, see [Remove-CsUserAcp](https://docs.microsoft.com/en-us/powershell/module/skype/remove-csuseracp?view=skype-ps). 

- To automatically reschedule the meetings of users after disabling the integration with a 3rd party audio conferencing provider, see “How do I run Meeting Migration manually for a user?” on [Setting up the Meeting Migration Service (MMS)](../audio-conferencing-in-office-365/setting-up-the-meeting-migration-service-mms.md). 

**Summary:** 

- Organizations that decide to stop using audio conferencing all together before April 1, 2019, will not be impacted.

- To disable the integration of 3rd party audio conferencing for a given organizer, use the Remove-CsUserAcp cmdlet. For additional information, see [Remove-CsUserAcp](https://docs.microsoft.com/en-us/powershell/module/skype/remove-csuseracp?view=skype-ps). 

- To automatically reschedule the meetings of users after disabling the integration with 3rd party audio conferencing providers, see “How do I run Meeting Migration manually for a user?” on [Setting up the Meeting Migration Service (MMS)](../audio-conferencing-in-office-365/setting-up-the-meeting-migration-service-mms.md).
