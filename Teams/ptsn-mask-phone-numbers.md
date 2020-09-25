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

During a Microsoft Teams meeting or phone call, a participants’ phone number can be visible to all meeting attendees. Seeing phone numbers is helpful because you can gather someone’s contact information. However, seeing a participant's phone number can be a security and privacy risk. To remediate this issue, Teams provides a feature that masks attendees' phone numbers. Teams lets you implement the solution properly on service side. Also, Teams has a tenant setting that allows admins to toggle masking on or off. The admin can choose whether masking is enabled for all meeting participants or only for external participants. The solution can work for healthcare, justice, government, enterprise, and EDU.

For added privacy, the phone numbers of participants who dial in to a Teams meeting using audio conferencing are fully displayed to the internal participants and masked from the participants outside of your organization. This setting is the default for all organizations.

(ADD IMAGE FROM ANA here it would be good to provide an image of the actual masking, I'll send it to you)

Admins have the ability to choose how the audio conferencing participants' phone numbers appear in the meetings organized in their tenant based on their specific industry use cases. They can choose from 3 options:

- phone numbers are masked only from external participants. The participants who belong to the meeting organizer's tenant still see the full phone number.
- phone numbers are masked from everyone in the meeting except the organizer.
- phone numbers are unmasked, which makes them visible to everyone in the meeting.

This setting is applied to all the surfaces in the meeting where phone numbers are exposed.

## Enable masking for specific participants in the admin console

![An icon showing the Microsoft Teams logo](media/teams-logo-30x30.png) **Using the Microsoft Teams admin center**

1. In the left navigation, go to **Meetings** > **Conference Bridges**.

2. At the top of the Conference Bridges page, select **Bridge settings**.

3. Choose an option under **Mask phone numbers**.

4. Select **Save**.

IMAGE for method 1

GET IMAGE FROM ANA. The image you currently have in the article is some old mock. I will provide you an image when the feature is implemented in MoPo.

## Enable masking for specific participants using Microsoft PowerShell

To change the PSTN masking setting, set the MaskPstnNumbersType parameter of the Set-CsOnlineDialInConferencingTenantSettings cmdlet to one of the available options.

To mask phone numbers only from external participants, run the following command:

```PowerShell
Set-CsOnlineDialInConferencingTenantSettings -MaskPstnNumbersType "MaskedForExternalUsers"
```

To mask phone numbers only from all participants in the meeting, run the following command:

```PowerShell
Set-CsOnlineDialInConferencingTenantSettings -MaskPstnNumbersType "MaskedForAllUsers"
```

To disable phone number masking, run the following command:

```PowerShell
Set-CsOnlineDialInConferencingTenantSettings -MaskPstnNumbersType "NoMasking"
```
