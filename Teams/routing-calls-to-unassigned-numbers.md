---
title: Routing calls to unassigned numbers
author: CarolynRowe
ms.author: crowe
manager: pamgreen
ms.reviewer: jenstr
ms.date: 11/17/2023
ms.topic: article
ms.assetid: aa2ec464-3481-4bbb-8c14-e13e18093df5
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - Tier1
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: Medium
f1.keywords: 
  - CSH
ms.custom: 
  - Calling Plans
description: Learn how to route calls to unassigned numbers in your organization.
---

# Routing calls to unassigned numbers

As an administrator, you can route calls to unassigned numbers in your organization. For example, you might want to route calls to unassigned numbers as follows: 

- Route all calls to a given unassigned number to a custom announcement.

- Route all calls to a given unassigned number to the main switchboard.

You can route calls to unassigned numbers to a user, to a resource account associated with an Auto attendant or a Call queue, or to an announcement service that will play a custom audio file to the caller.

You can configure routing of unassigned numbers by using the Teams admin center or by using PowerShell.

## Use Teams admin center

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Phone Numbers**.

2. On the **Routing rules** tab, select **Add**.

3. Give the rule a name, a description, and specify the evaluation order for the rule.

4. Decide which kind of rule you want to add. You can select rules where the type of phone number pattern is preconfigured, and you complete the pattern and the routing option. You can also select advanced setup, where you directly enter the regular expression for the phone number pattern and the routing option.

5. Select **Save**.

You can also create a routing rule directly for an unassigned phone number.

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Phone Numbers**.

2. On the **Numbers** tab, select an unassigned phone number and select **Route** at the top of the view

4. Give the rule a name, a description, and specify the evaluation order for the rule.

4. Select the routing option.

5. Select **Save**.

You can test your routing rules by using the Test number feature.

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Phone Numbers**.

2. On the **Routing rules** tab, select **Test number**.

3. Enter a phone number directly or select **Select a number**, and select one of your unassigned phone numbers from the drop-down.

4. Select **Test**.


## Use PowerShell

To route calls to an unassigned number, use the New/Get/Set/Remove-CsTeamsUnassignedNumberTreatment cmdlet available in Teams PowerShell module 2.5.1 or later.

You need to specify the called number or range of numbers and the associated routing for calls to these numbers. For example, the following command specifies that all calls to the number +1 (555) 222-3333 are routed to the resource account aa@contoso.com:

``` PowerShell
$RAObjectId = (Get-CsOnlineApplicationInstance -Identity aa@contoso.com).ObjectId

New-CsTeamsUnassignedNumberTreatment -Identity MainAA -Pattern "^\+15552223333$" -TargetType ResourceAccount -Target $RAObjectId -TreatmentPriority 1
```

The next example specifies that all calls to the number range +1 (555) 333-0000 to +1 (555) 333-9999 are routed to the announcement service, which will play the audio file MainAnnouncement.wav to the caller.

```PowerShell
$Content = [System.IO.File]::ReadAllBytes('C:\Media\MainAnnouncement.wav')

$AudioFile = Import-CsOnlineAudioFile -FileName "MainAnnouncement.wav" -Content $Content

$fid = [System.Guid]::Parse($AudioFile.Id)

New-CsTeamsUnassignedNumberTreatment -Identity TR1 -Pattern "^\+1555333\d{4}$" -TargetType Announcement -Target $fid.Guid -TreatmentPriority 2
```

## Notes

- If routing to an announcement, the audio file will be played once to the caller.

- To route calls to unassigned Microsoft Calling Plan subscriber numbers, your tenant needs to have available [Communications Credits](what-are-communications-credits.md).

- To route calls to unassigned Microsoft Calling Plan service numbers, your tenant needs to have at least one **Microsoft Teams Phone Resource Account** license.

- The custom audio file supported formats are WAV (uncompressed, linear PCM with 8/16/32-bit depth in mono or stereo), WMA (mono only), and MP3. The audio file content can't be more than 5 MB.

> [!NOTE]
> You're responsible for independently clearing and securing all necessary rights and permissions to use any music or audio file with your Microsoft Teams service. This may include intellectual property and other rights in any music, sound effects, audio, brands, names, and other content in the audio file from all relevant rights holders. Holders may include artists, actors, performers, musicians, songwriters, composers, record labels, music publishers, unions, guilds, rights societies, collective management organizations, and any other parties who own, control or license the music copyrights, sound effects, audio and other intellectual property rights.

- Both inbound calls to Microsoft Teams and outbound calls from Microsoft Teams will have the called number checked against the unassigned number range.

- If a specified pattern/range contains phone numbers that are assigned to a user or resource account in the tenant, calls to these phone numbers will be routed to 
the appropriate target and not routed to the specified unassigned number treatment. There are no other checks of the numbers in the range. If the range contains
a valid external phone number, outbound calls from Microsoft Teams to that phone number will be routed according to the treatment.


## Related articles

- [Get-CsTeamsUnassignedNumberTreatment](/powershell/module/teams/get-csteamsunassignednumbertreatment)

- [New-CsTeamsUnassignedNumberTreatment](/powershell/module/teams/new-csteamsunassignednumbertreatment)

- [Set-CsTeamsUnassignedNumberTreatment](/powershell/module/teams/set-csteamsunassignednumbertreatment)

- [Remove-CsTeamsUnassignedNumberTreatment](/powershell/module/teams/remove-csteamsunassignednumbertreatment)

- [Test-CsTeamsUnassignedNumberTreatment](/powershell/module/teams/test-csteamsunassignednumbertreatment)
