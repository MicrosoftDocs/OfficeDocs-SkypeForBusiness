---
title: Mask phone numbers in Microsoft Teams meetings 
author: cichur
ms.author: v-cichur
manager: serdars
ms.reviewer: 
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
- M365-collaboration
- Teams_ITAdmin_Help
f1.keywords:
- NOCSH
appliesto: 
- Microsoft Teams
localization_priority: Normal
search.appverid: MET150
description: Learn how to mask phone numbers in Microsoft Teams meetings
---

# Mask phone numbers in Microsoft Teams meetings

For added privacy, the phone numbers of participants who dial in to a Teams meeting using audio conferencing are fully displayed to the internal participants and masked from the participants outside of your organization. This setting is the default for all organizations.

(ADD IMAGE FROM ANA here it would be good to provide an image of the actual masking, I'll send it to you)

For specific industry use cases, admins have the ability to choose how the audio conferencing participants' phone numbers appear in meetings that are organized in their tenant. The admins can choose from 3 options:

- Phone numbers are masked only from external participants. The participants who belong to the meeting organizer's tenant still see the full phone number.
- Phone numbers are masked from everyone in the meeting except the organizer.
- Phone numbers are unmasked, which makes them visible to everyone in the meeting.

This setting is applied to all the surfaces in the meeting where phone numbers are exposed.

## Set whether the phone numbers of dial-in participants are masked

### Using the Microsoft Teams admin center

![An icon showing the Microsoft Teams logo](media/teams-logo-30x30.png) **Using the Microsoft Teams admin center**

1. In the left navigation, go to **Meetings** > **Conference Bridges**.

2. At the top of the Conference Bridges page, select **Bridge settings**.

3. Choose an option under **Mask phone numbers**.

4. Select **Save**.

IMAGE for method 1

GET IMAGE FROM ANA. The image you currently have in the article is some old mock. I will provide you an image when the feature is implemented in MoPo.

### Using Microsoft PowerShell

To change the PSTN masking setting, set the **`MaskPstnNumbersType`** parameter of the [Set-CsOnlineDialInConferencingTenantSettings](https://docs.microsoft.com/powershell/module/skype/set-csonlinedialinconferencingtenantsettings?view=skype-ps) cmdlet to one of the available options.

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
