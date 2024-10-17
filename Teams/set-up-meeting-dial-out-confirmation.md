---
title: Set up meeting dial-out-confirmation for your users in Microsoft Teams
ms.author: jenz
author: jenzamora
manager: pamgreen
ms.reviewer: oscarr
ms.date: 10/16/2024
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

Sending meeting invitations through dial outs and Call me calls is an effective way to invite participants to join a meeting, whether they're new or existing participants, using either a traditional or mobile phone. However, if the person being called doesn't pick up and a voicemail system answers instead, the voicemail system joins the meeting. This results in participants having to listen to the voicemail until someone removes it from the meeting.

To prevent this, you can configure Teams to request a confirmation from the called person before they join the meeting. When a meeting dial out goes to a phone number and the person can't answer, the voicemail system can't connect because it can't provide the required confirmation.

This policy requires anyone receiving dial outs or Call me calls to accept the meeting invitation by pressing 1 on their phone keypad or saying "Okay." This confirmation step ensures that voicemail systems don't join the meeting.

## Set up meeting dial-out confirmation for your users with PowerShell

To enable this policy for all meetings in your organization, set
the  **`-EnableDialOutJoinConfirmation`** parameter of the [Set-CsOnlineDialInConferencingTenantSettings](/powershell/module/teams/set-csonlinedialinconferencingtenantsettings) cmdlet to ```true```. To set this parameter, run the following command:

```PowerShell
Set-CsOnlineDialInConferencingTenantSettings -EnableDialOutJoinConfirmation $true
```

## Related topics

- [Set up the Call me feature for your users](set-up-the-call-me-feature-for-your-users.md)
- [Teams PowerShell overview](teams-powershell-overview.md)
