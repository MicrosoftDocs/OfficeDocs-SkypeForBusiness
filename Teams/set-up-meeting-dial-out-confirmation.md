---
title: Set up meeting dial-out-confirmation for your users in Microsoft Teams
ms.author: jenz
author: jenzamora
manager: pamgreen
ms.reviewer: oscarr
ms.date: 12/14/2023
ms.topic: article
ms.service: msteams
ms.subservice: teams-audio-conferencing
audience: admin
search.appverid: MET150
description: Learn how to set up Teams to request a dial-out confirmation to prevent voicemail systems from connecting to meetings when the called person is unable to answer the call.
ms.localizationpriority: medium
ms.collection: 
  - Tier1
  - m365initiative-meetings
appliesto: 
  - Microsoft Teams
---

# Set up meeting dial-out confirmation for your users in Microsoft Teams

Sending meeting invitations through dial outs and Call me calls are useful ways to invite participants to join a meeting, allowing both new and existing participants to join using either a traditional or a mobile phone. However, when the person who is called doesn't pick up and a voicemail system answers the call instead, the voicemail system joins the meeting. In this scenario, the participants listen to the voicemail until it's removed from the meeting.

You can configure Teams to request a confirmation from the called person to join the meeting when a meeting dial out goes to a phone number and the person who is called can't answer the call. This way, you can prevent voicemail systems from connecting to meetings. When the voicemail system answers a call, the voicemail system doesn't connect to the meeting because it can't provide a confirmation to join.

This policy requires anyone who gets dial outs or Call me calls to accept the meeting invitation by pressing 1 on their phone keypad or saying "Okay." The confirmation prevents the user's voicemail message from joining the meeting.

## Set up meeting dial-out confirmation for your users with PowerShell

To enable this policy for all meetings in your organization, set
the  **`-EnableDialOutJoinConfirmation`** parameter of the [Set-CsOnlineDialInConferencingTenantSettings](/powershell/module/teams/set-csonlinedialinconferencingtenantsettings) cmdlet to ```true```. To set this parameter, run the following command:

```PowerShell
Set-CsOnlineDialInConferencingTenantSettings -EnableDialOutJoinConfirmation $true
```

## Related topics

- [Set up the Call me feature for your users](set-up-the-call-me-feature-for-your-users.md)
- [Teams PowerShell overview](teams-powershell-overview.md)
