---
title: Use OneDrive and SharePoint for meeting recordings
author: cichur
ms.author: v-cichur
ms.reviewer: hao.moy
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn how to switch from Stream to OneDrive for Business and SharePoint Online meeting recording storage in Microsoft Teams.
localization_priority: Normal
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
ROBOTS: NOINDEX, NOFOLLOW
---

# Use OneDrive for Business and SharePoint Online or Stream for meeting recordings

[!INCLUDE [template](includes/preview-feature.md)]

Microsoft Teams has a new method for saving meeting recordings. As a departure from Stream, the method uses Microsoft OneDrive and SharePoint and offers many benefits:

The benefits of using OneDrive for Business and SharePoint Online for storing recordings include:

- Retention policies for Teams meeting recording (TMR) (S+C E5 auto-retention labels)
- Benefit from OneDrive for Business and SharePoint Online information governance
- Easy to set permissions and sharing
- Share recordings with guests (external users) with explicit share only
- Request access flow
- Provide OneDrive for Business and SharePoint Online shared links
- Increased quota
- Meeting  recordings are available faster
- **Go local** tenant support
- Multi-geo support – recordings are stored in a region specific to that user
- Bring your own key (BYOK) support
- Improved Transcript quality and speaker attribution

There are a some limitations to consider:

- There will be English-only closed captions and transcripts​.
- You won't be able to search transcripts or their content​.
- You won’t be able to edit the transcripts, but you'll be able to toggle captions off/on.
- You can control with whom you share the recording, but you won't be able to block people with shared access from downloading the recording.
- You'll not get an email when the recording finishes saving, but the recording will appear in the meeting chat once it’s finished. This will happen much quicker than it did in Stream previously

## Set up the meeting recording option for OneDrive for Business and SharePoint Online

1. Install the Skype For Business Online Powershell admin console.

    a. Download [Sype for Business Online Powershell](https://docs.microsoft.com/microsoft-365/enterprise/manage-skype-for-business-online-with-microsoft-365-powershell?view=o365-worldwide).

    b. Follow the prompts to install it.

    c. Restart your machine.

2. Launch Powershell as an admin

3. Import the SkypeOnline Connector and log in as a Teams admin.

```PowerShell
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
```

4. Use [set-csteamsmeetingpolicy](https://docs.microsoft.com/powershell/module/skype/set-csteamsmeetingpolicy?view=skype-ps) to set a Teams Meeting Policy to transition from the Stream storage to ODSP.

```PowerShell
   Set-CsTeamsMeetingPolicy -Identity Global -RecordingStorageMode "OneDriveForBusiness"
```

## Opt out of OneDrive for Business and SharePoint Online to continue using Stream

Even if a policy says it’s already set to **Stream**, it might not be set. If it's set to nothing, then the default is Stream. If you want to opt-out you **must** reset the policy to **Stream** to ensure that Stream is the default.

```PowerShell
   Set-CsTeamsMeetingPolicy -Identity Global -RecordingStorageMode "Stream"
```

> [!Note]
> ​​The change from using Microsoft Stream to OneDrive for Business and SharePoint Online for meeting recordings will be a phased approach. At launch you'll be able to opt-in to this experience, in November you'll have to opt-out if you want to continue using Stream, and some time in early 2021 we'll require all customers to OneDrive for Business and SharePoint for meeting recordings.
