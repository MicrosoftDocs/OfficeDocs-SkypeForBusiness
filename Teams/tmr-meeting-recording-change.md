---
title: Use ODSP for meeting recordings
author: cichur
ms.author: v-cichur
ms.reviewer: hao.moy
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn how to switch from Stream to OneDrive/SharePoint meeting recording storage in Microsoft Teams.
localization_priority: Normal
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
ROBOTS: NOINDEX, NOFOLLOW
---

# Use OneDrive/SharePoint or Stream for meeting recordings

[!INCLUDE [template](includes/preview-feature.md)]

Microsoft Teams has a new method for saving meeting recordings. As a departure from Stream, the method uses Microsoft OneDrive/SharePoint (ODSP) and offers many benefits:

ADD TABLE From Hao

## Set up the meeting recording option for OneDrive/SharePoint

1. Install the Skype For Business Online Powershell admin console.

    a. Download [Sype for Business Online Powershell](https://docs.microsoft.com/microsoft-365/enterprise/manage-skype-for-business-online-with-microsoft-365-powershell?view=o365-worldwide).

    b. Follow the prompts to install it.

    c. Restart your machine.

Launch Powershell as an admin

4. Import the SkypeOnline Connector and log in as a Teams admin.

```PowerShell
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
```

5. Use [set-csteamsmeetingpolicy](https://docs.microsoft.com/powershell/module/skype/set-csteamsmeetingpolicy?view=skype-ps) to set a Teams Meeting Policy to transition from the Stream storage to ODSP.

```PowerShell
   Set-CsTeamsMeetingPolicy -Identity Global -RecordingStorageMode "OneDriveForBusiness "
```

## Opt out of ODSP to continue using Stream

Even if a policy says it’s already set to **Stream**, it might not be set. If it's set to nothing, then the default is Stream. If you want to opt-out you **must** reset the policy to **Stream** to ensure that Stream is the default.

```PowerShell
   Set-CsTeamsMeetingPolicy -Identity Global -RecordingStorageMode "Stream "
```

> [!Note]
> Outstanding questions: Only guaranteeing the closed captions connected to the file for a max of 60 days, after 60 days its possible the transcript might not show on the video recording. The CELA disclaimer around transcript and closed captions??
