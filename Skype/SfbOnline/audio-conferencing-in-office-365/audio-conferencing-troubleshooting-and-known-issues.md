---
title: "Audio Conferencing troubleshooting and known issues"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: oscarr
ms.topic: article
ms.assetid: 72979911-5319-4de2-a275-4dd9a0f44fe6
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
search.appverid: MET150
ms.collection: 
- Adm_Skype4B_Online
- Strat_SB_PSTN
audience: Admin
appliesto:
- Skype for Business 
localization_priority: Normal
f1keywords: None
ms.custom:
- Audio Conferencing
description: "Get a list of known issues when using Microsoft as their dial-in conference provider, status, and some workarounds. "
---

# Audio Conferencing troubleshooting and known issues

 **This article is for Skype for Business users using Microsoft as their audio conferencing provider. It does not apply to customers who are using a third-party audio conferencing provider (ACP).**
  
## Troubleshooting and known issues

Audio Conferencing that uses Microsoft as the audio conferencing provider has current issues that are being tracked and actively investigated and will be potentially resolved when the feature is updated in future releases of Office 365.
  
For now, use this as a reference when you are troubleshooting potential issues with getting Audio Conferencing set up and working for the people using Skype for Business in your organization.

|**Issue**|**Behavior/Symptoms**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Entry and exit notifications are turned on when a meeting starts, but they're turned off shortly after the meeting starts.  <br/> |By default, entry and exit notifications are disabled for meetings where participants join from both Skype for Business apps and when they dial in. You can enable the announcements in the **Skype Meeting Options** in the Skype for Business app. For a meeting where all participants dial in and join a meeting, entry and exit notifications are enabled by default as the participant roster isn't available to any participant. When a meeting has started with only participants calling in, the entry and exit notifications will be turned on, but when a participant joins using a Skype for Business app, the notifications will be turned off. When turned off, the notifications can be enabled back using **Skype Meeting Options** in the Skype for Business app. <br/> |No workaround.  <br/> |8/30/2017  <br/> |
|If a user is provisioned the first time by being assigned an E5 license, it might be possible for the Audio Conferencing welcome email to not be delivered to the user if the mailbox isn't enabled.  <br/> |If this happens, you can always resend the audio conferencing information of the user using **Audio conferencing** in the Skype for Business admin center or using PowerShell. See [Enable or disable sending emails when Audio Conferencing settings change](enable-or-disable-sending-emails-when-their-settings-change.md).  <br/> **Note:** In order to resend the audio conferencing PIN to the user, the PIN has to be reset. This can also be done by using **Audio conferencing** in the Skype for Business admin center or by using PowerShell.          |No workaround.  <br/> |8/30/2017  <br/> |
|Audio conferencing calls could take up to 24 hours to show in the usage reports.  <br/> |We're looking forward to making improvements on this area in future service updates.  <br/> |No workaround.  <br/> |8/30/2017  <br/> |
|When a caller dials in to a conference bridge after the meeting has been locked by a Skype for Business user, there isn't a notification in the Skype for Business app stating that the user is waiting in the lobby.  <br/> |This is currently by design, but we've taken the feedback in regard to supporting this capability in future service updates.  <br/> |No workaround.  <br/> |8/30/2017  <br/> |
   
## Related topics

[Try or purchase Audio Conferencing in Office 365](../audio-conferencing-in-office-365/try-or-purchase-audio-conferencing-in-office-365.md)
