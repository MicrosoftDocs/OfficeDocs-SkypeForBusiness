---
title: "Routing calls to unassigned numbers"
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: jenstr
ms.topic: article
ms.assetid: aa2ec464-3481-4bbb-8c14-e13e18093df5
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
audience: Admin
appliesto: 
  - Microsoft Teams
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: 
  - Calling Plans
description: "Learn how to route calls to unassigned numbers in your organization."
---

# Routing calls to unassigned numbers

> [!NOTE]
> This feature is available as a Public Preview release.

As an administrator, you can route calls to unassigned numbers in your organization. For example, you might want to route calls to unassigned numbers as follows: 

- Route all calls to a given unassigned number to a custom announcement.

- Route all calls to a given unassigned number to the the main switchboard.

You can route calls to unassigned numbers to a user, to a resource account associated with an Auto Attendant or a Call Queue, or to an announcement service that will play a custom audio file to the caller. The audio file will play repeatedly until the caller hangs up.

## Configuration

To route calls to an unassigned number, use the New/Get/Set/Remove-CsTeamsUnassignedNumberTreatment cmdlet available in Teams PowerShell module 2.5.1 or later.

You need to specify the called number or range of numbers and the associated routing for calls to these numbers. For example, the following command specifies that all calls to the number +1 (555) 222-3333 will be routed to the resource account aa@contoso.com:

``` PowerShell
$RAObjectId = (Get-CsOnlineApplicationInstance -Identity aa@contoso.com).ObjectId


New-CsTeamsUnassignedNumberTreatment -Identity MainAA -Pattern "^\+15552223333$" -TargetType ResourceAccount -Target $RAObjectId -Priority 1
```

The next example specifies that all calls to the number range +1 (555) 333-0000 to +1 (555) 333-9999 will be routed to the announcement service, which will play the audio file MainAnnouncement.wav to the caller.

```PowerShell
$Content = Get-Content "C:\Media\MainAnnoucement.wav" -Encoding byte -ReadCount 0

$AudioFile = Import-CsOnlineAudioFile -FileName "MainAnnouncement.wav" -Content $Content

$fid = [System.Guid]::Parse($AudioFile.Id)

New-CsTeamsUnassignedNumberTreatment -Identity TR1 -Pattern "^\+1555333\d{4}$" -TargetType Announcement -Target $fid.Guid -Priority 2
```

## Notes

- If routing to an announcement, the audio file will be played once to the caller.

- To route calls to unassigned Microsoft Calling Plan subscriber numbers, your tenant needs to have available [Communications Credits](what-are-communications-credits.md).

- To route calls to unassigned Microsoft Calling Plan service numbers, your tenant needs to have at least one Phone System – Virtual User license.

## Related topics

- [Get-CsTeamsUnassignedNumberTreatment](/powershell/module/teams/get-csteamsunassignednumbertreatment)

- [New-CsTeamsUnassignedNumberTreatment](/powershell/module/teams/new-csteamsunassignednumbertreatment)

- [Set-CsTeamsUnassignedNumberTreatment](/powershell/module/teams/set-csteamsunassignednumbertreatment)

- [Remove-CsTeamsUnassignedNumberTreatment](/powershell/module/teams/remove-csteamsunassignednumbertreatment)