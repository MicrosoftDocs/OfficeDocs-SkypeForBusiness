---
title: Mask phone numbers in Microsoft Teams meetings
ms.author: jenz
author: jenzamora
manager: pamgreen
ms.reviewer: moakram
ms.date: 02/22/2024
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.subservice: teams-audio-conferencing
audience: Admin
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
f1.keywords: 
  - NOCSH
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how to mask phone numbers in Microsoft Teams.
---

# Mask phone numbers in Microsoft Teams meetings

For added privacy, the phone numbers of participants who dial in to a Teams meeting using audio conferencing are fully displayed to the internal participants. The numbers are masked from the participants outside of your organization. This setting is the default for all organizations. The masked number is displayed as shown in the following image:

![an example of a masked phone number.](media/hiddenPhoneNum.png)

For specific industry use cases, admins can choose how the audio conferencing participants' phone numbers appear in meetings organized in their tenant. Admins can choose from three options:

- Phone numbers are masked only from external participants. The participants who belong to the meeting organizer's tenant still see the full phone number.
- Phone numbers are masked from everyone in the meeting except the organizer.
- Phone numbers are unmasked, which makes them visible to everyone in the meeting.

This setting is applied to all the surfaces in the meeting where phone numbers are exposed.

## Use Teams admin center to set phone-number masking

To change the Public Switched Telephone Network (PSTN) masking setting in the Teams admin center, log into the Teams admin center as an administrator, select **Meetings** > **Conference Bridges** in the left-hand navigation panel, and then select **Bridge settings**. **Display masked caller IDs** is a dropdown at the bottom of the Bridge settings pane, and allows you to choose the following:

- Participants outside your organization
- All meeting participants
- Disabled

## Use Microsoft PowerShell to set phone-number masking

To change the PSTN masking setting in PowerShell, set the **`MaskPstnNumbersType`** parameter of the [Set-CsOnlineDialInConferencingTenantSettings](/powershell/module/teams/set-csonlinedialinconferencingtenantsettings) cmdlet to one of the available options.

To mask phone numbers only from external participants, run the following command:

```PowerShell
Set-CsOnlineDialInConferencingTenantSettings -MaskPstnNumbersType "MaskedForExternalUsers"
```

To mask phone numbers from all participants in the meeting (except the organizer), run the following command:

```PowerShell
Set-CsOnlineDialInConferencingTenantSettings -MaskPstnNumbersType "MaskedForAllUsers"
```

To disable phone number masking, run the following command:

```PowerShell
Set-CsOnlineDialInConferencingTenantSettings -MaskPstnNumbersType "NoMasking"
```
