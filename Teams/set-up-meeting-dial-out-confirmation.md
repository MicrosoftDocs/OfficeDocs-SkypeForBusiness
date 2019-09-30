---
title: Set up meeting dial-out-confirmation for your users in Microsoft Teams
author: LanaChin
ms.author: v-lanac
ms.reviewer: oscarr
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
search.appverid: MET150
description: 
localization_priority: Normal
ms.collection: Strat_MT_TeamsAdmin
appliesto: 
- Microsoft Teams
---

# Set up meeting dial-out confirmation for your users in Microsoft Teams

Meeting dial outs and call-me calls are a very useful way to invite participants to join a meeting or for existing participants to join a meeting using a traditional or mobile phone. However, when the called person is unable to answer the call and the call is answered by a voicemail system, the voicemail system is connected to the meeting and participants will be able to listen to it until it’s removed from the meeting.

To prevent voicemail systems from connecting to meetings when a meeting dial out is sent to a phone number and the called person is unable to answer the call, you can enable Teams to request a confirmation from the called person for them to join the meeting. If the called person can’t answer the call and the call is answered by a voicemail system, the voicemail system won‘t be connected to the meeting because it won’t provide a confirmation to join it.
When this capability is enabled, people that receive a dial out or call-me call must confirm that they want to join the meeting by pressing 1 on their traditional or mobile phone.

To enable this capability for all meetings in your organization, set the **EnableDialOutJoinConfirmation** parameter of the [Set-CsOnlineDialInConferencingTenantSettings](https://docs.microsoft.com/powershell/module/skype/set-csonlinedialinconferencingtenantsettings?view=skype-ps) cmdlet to true. To do this, run the following command:

```
Set-CsOnlineDialInConferencingTenantSettings -EnableDialOutJoinConfirmation $true
```

## Related topics

- [Set up the Call me feature for your users](set-up-the-call-me-feature-for-your-users.md)
- [Teams PowerShell overview](teams-powershell-overview.md)