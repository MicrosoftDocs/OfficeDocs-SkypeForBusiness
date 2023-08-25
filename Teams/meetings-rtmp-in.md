---
title: Manage RTMP-In for Teams meetings
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: 
ms.date: 04/20/2023
audience: admin
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - Tier2
appliesto: 
  - Microsoft Teams
f1.keywords:
- NOCSH
ms.custom: 
  - ms.teamsadmincenter.meetingpolicies.audioandvideo
description: Learn to set up RTMP-In for Teams meetings.
---

# Manage RTMP-In for Teams meetings

RTMP-In allows meeting organizers to produce their Teams Meeting directly from an external hardware or software-based encoder using Real-Time Messaging Protocol (RTMP). RTMP-In must be turned on for the meeting organizer via a Teams meeting policy.

Meeting organizers who are enabled for RTMP-In can choose the option in meeting options and can access the RTMP link and key which they can use to start streaming from the encoder.

The incoming RTMP feed must deliver:  
- H.264 Advanced Video Coding (AVC)
- Constant Bitrate (CBR)
- Frame rate of 29.97 or 30 fps
- Square Pixel Aspect Ratio (PAR)

## Turn RTMP-In on or off

The RTMP-In meeting policy control is configured by using PowerShell. (See [Manage Teams with Microsoft Teams PowerShell](teams-powershell-managing-teams.md) to get started.)

#### View the RTMP-In status for a policy

To view the current status of RTMP-In for a meeting policy, use the [Get-CsTeamsMeetingPolicy](/powershell/module/skype/get-csteamsmeetingpolicy) cmdlet:


```PowerShell
Get-CsTeamsMeetingPolicy -Identity <policy name>|fl AllowedStreamingMediaInput
```

For example:
```PowerShell
Get-CsTeamsMeetingPolicy -Identity Global|fl AllowedStreamingMediaInput
```

#### Turn RTMP-In on for a policy

To turn RTMP-In on for a meeting policy, use the [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy) cmdlet:


```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowedStreamingMediaInput "RTMP"  
```

For example:

```powershell
Set-CsTeamsMeetingPolicy -Identity Global -AllowedStreamingMediaInput "RTMP"  
```

#### Turn RTMP-In off for a policy

To turn RTMP-In off, use a null value with `-AllowedStreamingMediaInput`. For example:

```powershell
Set-CsTeamsMeetingPolicy -Identity Global -AllowedStreamingMediaInput ""
```

## Related topics

[Teams policies reference](settings-policies-reference.md#audio--video)

[Teams PowerShell overview](teams-powershell-overview.md)

[Assign policies to your users in Teams](policy-assignment-overview.md)
