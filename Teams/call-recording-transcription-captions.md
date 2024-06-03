---
title: 'Configure call recording, transcription, and captions in Teams'
author: mkbond007
ms.author: mabond
manager: pamgreen
ms.topic: conceptual
ms.service: msteams
ms.reviewer: roykuntz
ms.date: 01/30/2024
audience: admin
search.appverid: MET150
description: Learn how to enable users to record, transcribe, and turn on captions for calls in Microsoft Teams.
ms.localizationpriority: medium
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - Tier1
f1.keywords:
- CSH
ms.custom: 
appliesto: 
  - Microsoft Teams
---

# Configure call recording, transcription, and captions in Teams

In Microsoft Teams, users can record, transcribe, and view captions in their Teams calls. This article explains how to configure these features for your users.

For compliance call recording information, see [Policy-based recording for calls & meetings](teams-recording-policy.md).

For for optimal accessibility, follow the guides and resources [Accessibility guide for Microsoft Teams admins](accessibility-guide-admin.md) to configure Teams.

## Enable call recording

You can use the Microsoft Teams admin center or PowerShell to set a Teams calling policy to control whether users' calls can be recorded.

Many users use calls and meetings interchangeably depending on their needs. We recommend you check your meeting recording policy settings as well. If the settings are different for calls and meetings, it might cause confusion for your users.

To allow or prevent *call recordings*:

1. In the Microsoft [Teams admin center](https://admin.teams.microsoft.com/), expand **Voice**.
1. Select **Calling policies**.
1. Select the policy that you want to edit.
1. Turn **Cloud recording for calling** On or Off.
1. Select **Save**.

With PowerShell, you can configure the `-AllowCloudRecordingForCalls` parameter in [Set-CsTeamsCallingPolicy](/powershell/module/teams/set-csteamscallingpolicy).

To allow or prevent *meeting recordings*, see [Teams meeting recording](meeting-recording.md).

## Enable call transcription

Transcription is automatically generated, recorded text of what was said in a call. When turned on, the transcript is available to users to review after a call ends. This setting is off by default.

### Using the Teams admin center

To turn on call transcription for users:

1. In the Microsoft Teams admin center, go to **Voice**, and then select **Calling policies**.

2. Select the policy you want to modify.

3. Turn **Transcription** to **On**, then select **Save**.

### Using PowerShell

With PowerShell, you can configure the `-AllowTranscriptionForCalling` parameter with the following cmdlets:

- [Get-CsTeamsCallingPolicy](/powershell/module/teams/get-csteamscallingpolicy)
- [New-CsTeamsCallingPolicy](/powershell/module/teams/new-csteamscallingpolicy)
- [Set-CsTeamsCallingPolicy](/powershell/module/teams/set-csteamscallingpolicy)
- [Remove-CsTeamsCallingPolicy](/powershell/module/teams/remove-csteamscallingpolicy)
- [Grant-CsTeamsCallingPolicy](/powershell/module/teams/grant-csteamscallingpolicy)

For example, this script enables transcription for the global policy:

```powershell
Set-CsTeamsCallingPolicy -Identity Global -AllowTranscriptionForCalling $true
```

## Enable call captions

### Using the Teams admin center

Captions are real-time automatically generated text of what is said in a call. They appear a few lines at a time for a user who turns them on. Captions aren’t saved.

To turn on real-time captions for calls for users:

1. In the Microsoft Teams admin center, go to **Voice**, and then select **Calling policies**.

2. Select the policy you want to modify.

3. Turn **Real-time captions in Teams calls** to **On**, then select **Save**.

### Using PowerShell

With PowerShell, you configure the `-LiveCaptionsEnabledTypeForCalling` parameter with the following cmdlets:

- [Get-CsTeamsCallingPolicy](/powershell/module/teams/get-csteamscallingpolicy)
- [New-CsTeamsCallingPolicy](/powershell/module/teams/new-csteamscallingpolicy)
- [Set-CsTeamsCallingPolicy](/powershell/module/teams/set-csteamscallingpolicy)
- [Remove-CsTeamsCallingPolicy](/powershell/module/teams/remove-csteamscallingpolicy)
- [Grant-CsTeamsCallingPolicy](/powershell/module/teams/grant-csteamscallingpolicy)

For example, this script allows the user to turn on real-time captions in the global policy:

```powershell
Set-CsTeamsCallingPolicy -Identity Global -LiveCaptionsEnabledTypeForCalling DisabledUserOverride
```

In this example, the script prevents the user from turning on real-time captions in the global policy:

```powershell
Set-CsTeamsCallingPolicy -Identity Global -LiveCaptionsEnabledTypeForCalling Disabled
```

## Related articles

[Accessibility guide for Microsoft Teams Admins](accessibility-guide-admin.md)

[Teams meeting recording](meeting-recording.md)

[Configure transcription and captions for Teams meetings](meeting-transcription-captions.md)

[Configure calling policies](teams-calling-policy.md)
