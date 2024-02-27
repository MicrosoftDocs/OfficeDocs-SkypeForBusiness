---
title: Manage RTMP-In for Teams meetings, webinars, and town halls
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.topic: article
ms.service: msteams
ms.reviewer: srajay
ms.date: 04/20/2023
audience: admin
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - Tier2
  - m365initiative-meetings
appliesto: 
  - Microsoft Teams
f1.keywords:
- NOCSH
ms.custom: 
  - ms.teamsadmincenter.meetingpolicies.audioandvideo
description: Learn to set up RTMP-In for Teams meetings for admins.
---

# Manage RTMP-In for Teams meetings, webinars, and town halls

**APPLIES TO:** ✔️Meetings ✔️Webinars ✔️Town halls

[!INCLUDE[Teams Premium](includes/teams-premium-ecm.md)]

RTMP-In allows meeting, webinar, and town hall organizers to produce their meetings and events directly from an external hardware or software-based encoder using Real-Time Messaging Protocol (RTMP).

> [!NOTE]
> RTMP-In is a Teams Premium feature for all meeting and event formats, except town halls.

As an admin, you must enable RTMP-In for the organizer. Organizers with an enabled RTMP-In policy can choose the option in their Meeting options and can access the RTMP link and key they need to start streaming from the encoder.

The incoming RTMP feed must deliver:  

- H.264 Advanced Video Coding (AVC)
- Constant Bitrate (CBR)
- Frame rate of 29.97 fps or 30 fps
- Square Pixel Aspect Ratio (PAR)

## RTMP ingest endpoints

As part of the network connectivity principles, ensure that the Microsoft 365 endpoints are reachable as defined in
[Office 365 URLs and IP address ranges](/microsoft-365/enterprise/urls-and-ip-address-ranges). In addition, ensure you also have the following domains/ports:

**Domains**: *.rtmpingest.mcr.teams.microsoft.com<br>
**Ports**: 1935/1936 (for RTMP/RTMPS)

## Manage whether organizers can use RTMP-In with the Teams admin center

1. Open the Teams admin center.
2. Select **Meetings** from the navigation pane.
3. Under **Meetings**, select **Meeting Policies**.
4. Either select an existing policy or create a new one.
5. Navigate to the **Audio & Video section**.
6. For **Allowed streaming media input**, select or deselect **RTMP** from the dropdown.
7. Select Save.

## Manage whether organizers can use RTMP-In with PowerShell

To manage whether organizers can use RTMP-In, use the **`-AllowedStreamingMediaInput`** parameter within the PowerShell [**CsTeamsMeetingPolicy**](/powershell/module/skype/set-csteamsmeetingpolicy) cmdlet.

### Enable RTMP-In

To enable RTMP-In for organizers with this policy, use the following script:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowedStreamingMediaInput "RTMP"  
```

### Disable RTMP-In

To disable RTMP-In for organizers with this policy, use a null value with `-AllowedStreamingMediaInput`. For example:

```powershell
Set-CsTeamsMeetingPolicy -Identity Global -AllowedStreamingMediaInput ""
```

### View the RTMP-In status for a policy

To view the current status of RTMP-In for a meeting policy, use the following script:

```PowerShell
Get-CsTeamsMeetingPolicy -Identity <policy name>|fl AllowedStreamingMediaInput
```

## Related topics

[Teams policies reference](settings-policies-reference.md#audio--video)

[Teams PowerShell overview](teams-powershell-overview.md)

[Assign policies to your users in Teams](policy-assignment-overview.md)
