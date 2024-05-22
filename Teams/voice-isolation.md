---
title: Manage voice isolation for your users' Microsoft Teams calls and meetings
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.reviewer: elaineho
ms.date: 5/1/2024
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
f1.keywords:
- CSH
ms.custom: 
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
  - highpri
  - Tier1
description: Learn how to manage whether users can use voice isolation for IT Admins in Microsoft Teams. 
---

# Manage voice isolation for your users' Microsoft Teams calls and meetings

**APPLIES TO:** ✔️Meetings ✔️Webinars ✔️Town halls ✔️Calls

Voice isolation reduces noise and uses the personalized deep voice quality enhancement artificial intelligence (AI) model to separate the user's voice from other sounds and voices in Microsoft Teams calls and meetings. As an admin, you can control whether your users can use voice isolation in calls and meetings.

The voice isolation feature relies on the voice profile, stored on the user's local device, to remove any sounds or voices during a call or meeting that don't match the profile. Your users' voice profiles are only used for the reason they gave their permission for; Microsoft doesn't use their voice profiles for anything else. To use the voice isolation feature, your users must have a voice profile. To learn about how your users can set up a voice isolation profile, see [Use Microsoft Teams Intelligent Speakers to identify in-room participants in a meeting transcription](https://support.microsoft.com/office/use-microsoft-teams-intelligent-speakers-to-identify-in-room-participants-in-a-meeting-transcription-a075d6c0-30b3-44b9-b218-556a87fadc00#bkmk_setupvoiceprofile).

To learn about enrollment, see [Overview of voice and face enrollment](/microsoftteams/rooms/voice-and-face-recognition).

To learn more about voice isolation troubleshooting, setup, and the experience for your users, see [Voice isolation in Microsoft Teams calls and meetings](https://prod.support.services.microsoft.com/office/voice-isolation-in-microsoft-teams-calls-and-meetings-a9756ea9-4cec-44c4-aefb-6f5d17c89427).

## Prerequisites

Verify that the following URL is included in your allowlist:

- https://aiinfrastructure.static.microsoft/public/aiinfrastructure/tsg_model_file/d1579e8339689379a218e26beea3825b68b9e75ec9dbb41aeb2be78510fead3c/model.gz

## Manage whether your users can use voice isolation

You must use both the **`-VoiceIsolation`** and **`-EnrollUserOverride`** parameters within the PowerShell [**CsTeamsMeetingPolicy**](/powershell/module/teams/set-csteamsmeetingpolicy) cmdlet to manage whether your users can use voice isolation.

| **`-VoiceIsolation`** parameter value in PowerShell| Behavior|
|---------|---------------|
|Enabled| **This is the default value.** Users with this policy can use voice isolation in Teams calls and meetings. |
|Disabled| Users with this policy can't use voice isolation in Teams calls and meetings.|

| **`-EnrollUserOverride`** parameter value in PowerShell| Behavior|
|---------|---------------|
|Enabled| Users with this policy can set the voice profile capture and enrollment through the **Recognition** tab in their Teams client settings.  |
|Disabled| **This is the default value.** Users with this policy can't use or access the voice profile capture or enrollment.|

Before you can run these cmdlets, you must be connected to Microsoft Teams PowerShell. For more information, see [Manage Teams with Microsoft Teams PowerShell](/microsoftteams/teams-powershell-managing-teams).

For more information on PowerShell cmdlets for Teams meetings, see the [Related topics](#related-topics) section.

### Allow users to use voice isolation

To allow users with this policy to use voice isolation, use both of the following scripts:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -EnrollUserOverride Enabled
```

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -VoiceIsolation Enabled
```

### Prevent users from using voice isolation

To prevent users with this policy from using voice isolation, use the following script:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -VoiceIsolation Disabled
```

## Related topics

- [Plan for meetings with external participants in Microsoft Teams](plan-meetings-external-participants.md)
- [Plan for meetings](plan-meetings.md)
- [Meetings, webinars, and live events overview](quick-start-meetings-live-events.md)
- [Feature comparison](meeting-webinar-town-hall-feature-comparison.md)
- [New-CsTeamsMeetingPolicy](/powershell/module/teams/new-csteamsmeetingpolicy)
- [Set-CsTeamsMeetingPolicy](/powershell/module/teams/set-csteamsmeetingpolicy)
- [Grant-CsTeamsMeetingPolicy](/powershell/module/teams/grant-csteamsmeetingpolicy)
- [Get-CsTeamsMeetingPolicy](/powershell/module/teams/get-csteamsmeetingpolicy)
- [Remove-CsTeamsMeetingPolicy](/powershell/module/teams/remove-csteamsmeetingpolicy)
