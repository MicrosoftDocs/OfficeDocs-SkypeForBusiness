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

Microsoft Teams has a new method for saving meeting recordings. As a departure from Stream, the method uses Microsoft OneDrive/SharePoint and offers many benefits:

The benefits of using OneDrive/SharePoint for storing recordings include:

- Retention policies for Teams meeting recording (TMR) (S+C E5 auto-retention labels)
- Benefit from OneDrive SharePoint information governance
- Easy to set permissions and sharing
- Share recordings with guests (external users) with explicit share only
- Request access flow
- Provide OneDrive SharePoint shared links
- Increased quota
- Meeting  recordings are available faster
- **Go local** tenant support
- Multi-geo support – recordings are stored in a region specific to that user
- Bring your own key (BYOK) support
- Improved Transcript quality and speaker attribution

There are a some limitations to consider:

- English only transcripts​
- Unable to search transcripts and transcript content​
- Can't edit transcripts
- Unable to download videos

You'll still receive an email notification that the TMR is ready to view, and the notification in Teams chat will still be present.

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

## Opt out of OneDrive/SharePoint to continue using Stream

Even if a policy says it’s already set to **Stream**, it might not be set. If it's set to nothing, then the default is Stream. If you want to opt-out you **must** reset the policy to **Stream** to ensure that Stream is the default.

```PowerShell
   Set-CsTeamsMeetingPolicy -Identity Global -RecordingStorageMode "Stream "
```

> [!Note]
> Outstanding questions: Only guaranteeing the closed captions connected to the file for a max of 60 days, after 60 days its possible the transcript might not show on the video recording. The CELA disclaimer around transcript and closed captions??
