---
title: See a list of Audio Conferencing numbers
ms.author: jenz
author: jenzamora
manager: pamgreen
ms.reviewer: oscarr
ms.date: 10/16/2024
ms.topic: article
ms.assetid: 2d6b4ed4-e12b-4691-8405-fae720d69425
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.subservice: teams-audio-conferencing
search.appverid: MET150
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
  - Tier1
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: 
  - Audio Conferencing
  - seo-marvel-apr2020
description: Learn how to look up the dial-in conferencing numbers that are available for audio conferencing from within Microsoft Teams.
---

# See a list of Audio Conferencing numbers in Microsoft Teams

When you set up Audio Conferencing for your Microsoft Teams users, you can see the phone numbers that are available to them for audio conferencing. This list has all the audio conferencing phone numbers that are available to your organization.

**Looking for prices?** Review the **Audio Conferencing rates** section in [Audio Conferencing](https://www.microsoft.com/microsoft-teams/audio-conferencing).
  
When there's only one phone number available in your organization, it serves as the default number for all of your users. When multiple phone numbers are available, you can select the default phone number for each user. The default number is included in Microsoft Teams meeting invitations.
  
To change the dial-in phone number for a single user, see [Set the phone numbers included on invites](set-the-phone-numbers-included-on-invites-in-teams.md).

> [!NOTE]
> [!INCLUDE [updating-admin-interfaces](includes/updating-admin-interfaces.md)]

## See your audio conferencing phone numbers in the Teams admin center

Using the Microsoft Teams admin center:

1. In the left navigation, go to **Meetings** > **Conference bridges**.
2. View the phone numbers that are available for audio conferencing.

      - You can also see the location and primary language that the audio conferencing auto attendant uses.

## See your audio conferencing phone numbers using PowerShell

To see your audio conferencing phone numbers with PowerShell, use the PowerShell [Get-CsOnlineDialInConferencingServiceNumber](/powershell/module/teams/get-csonlinedialinconferencingservicenumber) cmdlet.

To see all the audio conferencing phone numbers in your organization, use the following script:

```powershell
Get-CsOnlineDialInConferencingServiceNumber | fl
```

For more examples, see [Get-CsOnlineDialInConferencingServiceNumber](/powershell/module/teams/get-csonlinedialinconferencingservicenumber).

## Related topics

- [Change the settings for an audio conferencing bridge](change-the-settings-for-an-audio-conferencing-bridge.md)
