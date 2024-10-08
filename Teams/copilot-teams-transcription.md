---
title: Manage Microsoft 365 Copilot in Teams meetings and events
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.reviewer: maryam.ahmad
ms.date: 9/16/2024
ms.topic: how-to
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
  - teams-copilot
  - magic-ai-copilot
description: Learn how to manage Microsoft 365 Copilot in Teams meetings and events admin policies in the Teams admin center. Learn how to manage transcripts and transcription for Copilot Microsoft Teams meetings and events.
---

# Manage Microsoft 365 Copilot in Teams meetings and events

**APPLIES TO:** ✔️Meetings ✔️Webinars ✔️Town halls

Microsoft 365 Copilot in Teams meetings and events is an artificial intelligence (AI) tool that captures important conversation points. Each meeting and webinar participant with a Microsoft 365 Copilot license can ask prompts that are only visible to them. Participants and organizers can learn things like who said what and where people agree or disagree. Microsoft 365 Copilot in Teams can also recommend follow-up tasks, all in real time during a meeting. Organizers, co-organizers, and presenters can use Copilot during town hall events. As an admin, you can manage how users in your org use Copilot for Teams meetings and events.

There are two ways for users in your organization to use Copilot in meetings and events:

**1. During and after the meeting**<br>

When organizers create a meeting or event, they can set Copilot's value to **During and after the meeting** from the dropdown in their meeting options. Once someone starts transcription, licensed users can select the Copilot button for use during, and after the meeting or event.

To learn more about how organizers can use Copilot during and after the meeting, see [Get started with Microsoft 365 Copilot in Teams in Microsoft Teams meetings](https://support.microsoft.com/office/get-started-with-copilot-in-microsoft-teams-meetings-0bf9dd3c-96f7-44e2-8bb8-790bedf066b1).

**2. Only during the meeting**<br>

When organizers create a meeting or event, they can set Copilot's value to **Only during the meeting** from the dropdown in their meeting options. Once someone with a Microsoft 365 Copilot license selects the Copilot button during the meeting or event, Copilot runs for all licensed users. This option relies on a hidden transcript that isn't saved after the meeting or event ends. Users can't access Copilot in Teams and its history after the meeting or event.

To learn more about how organizers can use Copilot only during the meeting, see [Use Microsoft 365 Copilot in Teams without recording a Teams meeting](https://support.microsoft.com/office/use-copilot-without-recording-a-teams-meeting-a59cb88c-0f6b-4a20-a47a-3a1c9a818bd9).

Meeting or event organizers can also set Copilot's value to **Off** to prevent anyone in the meeting from using Copilot. This option disables recording and transcription for the meeting. You have a policy to set the default to **Off**, but your organizers can manage this setting on a per-meeting basis.

> [!IMPORTANT]
> Microsoft 365 Copilot in Teams meetings and events isn’t available in end-to-end encrypted meetings. For more information on end-to-end encryption, see [Require end-to-end encryption for sensitive Teams meetings](end-to-end-encrypted-meetings.md).

> [!NOTE]
> Microsoft 365 Copilot in Teams isn’t available for GCC, GCC High, and DoD.

## Prerequisites

- An add-on Microsoft 365 Copilot license for intended users. To learn more about the Microsoft 365 Copilot license, see [Microsoft 365 Copilot documentation](/microsoft-365-copilot).

## Transcription

You can use the **Recording & Transcription** section in the Teams admin center or the **`-AllowTranscription`** parameter in the [**CsTeamsMeetingPolicy**](/powershell/module/teams/set-csteamsmeetingpolicy) PowerShell cmdlet to manage your transcription policy. This setting's value impacts how, or if Copilot works for your users. The following table shows how the transcription policy works with the organizer's Copilot in Teams meeting options:

|Admin's transcription policy value |Organizer's Copilot meeting option | Behavior|
|---------|---------|---------------|
|On|Only during the meeting| Licensed users can select the Copilot button for use only during this meeting with a hidden transcript. To use Copilot during, and after the meeting, these users can start a standard transcript. |
|Off|Only during the meeting| Licensed users can select the Copilot button for use during this meeting or event with a hidden transcript. If another participant who can transcribe enables transcription, Copilot is available during, and after the meeting.|
|On|During and after the meeting| Once licensed users turn on transcription, they can select the Copilot button for use during, and after this meeting or event. |
|Off|During and after the meeting| Licensed users can't interact with Copilot unless another participant with permission to transcribe turns on transcription for this meeting.|
|Any|Off | Licensed users can’t interact with Copilot in Teams. No one can record or transcribe.|

To learn more about managing transcription, see [Configure transcription and captions for Teams meetings](meeting-transcription-captions.md).

## Manage Copilot for your Teams users

You can use the Teams admin center or PowerShell to manage how users in your org use Copilot in Teams meetings and events.

The following table shows the behaviors of the settings for the **`-Copilot`** parameter:

|Teams admins center policy value |PowerShell setting value | Behavior|
|---------|---------|---------------|
|On|Enabled| When organizers with this policy create meetings and events, Copilot's default value in their meeting options is **Only during the meeting**. Organizers can change this value to **During and after the meeting**.  |
|On with saved transcript required|EnabledWithTranscript| **This is the default value**. When organizers with this policy create meetings and events, Copilot's default value in their meeting options is **During and after the meeting**. This option is enforced; organizers can't change this value.|
|On with transcript saved by default|EnabledWithTranscriptDefaultOn| When organizers with this policy create meetings and events, Copilot's default value in their meeting options is **During and after the meeting**. Organizers can change this value to **Only during the meeting**.|
|Off|Disabled| When organizers with this policy create meetings and events, Copilot's  default value in their meeting options is **Off**. Organizers can change this value to **Only during the meeting** or **During and after the meeting**.|

### Manage Copilot in the Teams admin center

1. Open the Teams admin center.
2. Expand **Meetings** from the navigation pane.
3. Under **Meetings**, select **Meeting Policies**.
4. Either select an existing policy or create a new one.
5. Select **On**, **On with saved transcript required**, **On with transcript saved by default**, or **Off** from the dropdown for the **Copilot** setting.
6. Select **Save**

You can apply your Copilot meeting policies to groups or individual users. You can also add Copilot to your meeting templates. To learn how to apply Copilot to meeting templates, see [IT admins - Create a custom meeting template in Microsoft Teams](create-custom-meeting-template.md).

### Manage Copilot using PowerShell

To manage how users in your org use Copilot in Teams meetings and events, use the **`-Copilot`** parameter within the PowerShell [**CsTeamsMeetingPolicy**](/powershell/module/teams/set-csteamsmeetingpolicy) cmdlet.

To allow users to use Copilot **Only during the meeting** in meetings and events created by organizers with this policy,:

```PowerShell
Set-CsTeamsMeetingPolicy -Identity <policy name> -Copilot Enabled
```

To set the organizer's default Copilot option to **During and after the meeting** and allow them to change it, use the following script:

```PowerShell
Set-CsTeamsMeetingPolicy -Identity <policy name> -Copilot EnabledWithTranscriptDefaultOn
```

To set the organizer's default Copilot option to **Off** and allow them to change it, use the following script:

```PowerShell
Set-CsTeamsMeetingPolicy -Identity <policy name> -Copilot Disabled
```

## Related articles

- [Microsoft 365 Copilot documentation](/microsoft-365-copilot)
- [Configure transcription and captions for Teams meetings](meeting-transcription-captions.md)
- [Plan for Teams meetings](plan-meetings.md)
- [Plan for Teams webinars](plan-webinars.md)
- [Plan for Teams town halls](plan-town-halls.md)
