---
title: Manage Copilot for Microsoft Teams meetings and events
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.reviewer: elederman
ms.date: 4/19/2024
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
description: Learn how to manage Copilot admin policies in the Teams admin center. Learn how to manage transcripts and transcription for Copilot Microsoft Teams meetings and events.
---

# Manage Copilot for Microsoft Teams meetings and events

**APPLIES TO:** ✔️Meetings ✔️Webinars ✔️Town halls

Copilot for Microsoft Teams meetings and events is an artificial intelligence (AI) tool that can capture important conversation points. Each meeting and webinar participant with a Copilot license can ask prompts that are only visible to them. Participants and organizers can learn things like who said what and where people agree or disagree. Copilot can also recommend follow-up tasks, all in real time during a meeting. Organizers, co-organizers, and presenters can use Copilot during town hall events.

There are two ways for users in your organization to use Copilot in meetings and events:

**1. During and after the meeting**<br>

When organizers create a meeting or event, they can set Copilot’s value to **During and after the meeting** from the dropdown in their meeting options. Once someone starts transcription, licensed users can select the Copilot button for use during, and after the meeting or event.

To learn more about how organizers can use Copilot during, and after the meeting, see [Get started with Copilot in Microsoft Teams meetings](https://support.microsoft.com/office/get-started-with-copilot-in-microsoft-teams-meetings-0bf9dd3c-96f7-44e2-8bb8-790bedf066b1).

**2. Only during the meeting**<br>

When organizers create a meeting or event, they can set Copilot’s value to **Only during the meeting** from the dropdown in their meeting options. Once someone with a Copilot license selects the Copilot button during the meeting or event, Copilot runs for all licensed users. This option relies on a hidden transcript that isn't saved after the meeting or event ends. Users can't access Copilot and its history after the meeting or event.

To learn more about how organizers can use Copilot  only during the meeting, see [Use Copilot without recording a Teams meeting](https://support.microsoft.com/office/use-copilot-without-recording-a-teams-meeting-a59cb88c-0f6b-4a20-a47a-3a1c9a818bd9).

As an admin, you can manage how users in your org use Copilot for Teams meetings and events.

> [!IMPORTANT]
> Copilot for Teams meetings isn’t available in end-to-end encrypted meetings. For more information on end-to-end encryption, see [Require end-to-end encryption for sensitive Teams meetings](end-to-end-encrypted-meetings.md).

> [!NOTE]
> Copilot isn’t available for GCC, GCC High, and DoD.

## Prerequisites

- An add-on Copilot license for intended users. To learn more about the Copilot license, see [Microsoft Copilot for Microsoft 365 documentation](/microsoft-365-copilot).

## Transcription

You can use the **Recording & Transcription** section in the Teams admin center or the **`-AllowTranscription`** parameter in the [**CsTeamsMeetingPolicy**](/powershell/module/teams/set-csteamsmeetingpolicy) PowerShell cmdlet to manage your transcription policy. This setting's value impacts how, or if Copilot works for your users. The following table shows how the transcription policy works with the organizer's Copilot meeting options:

|Admin's transcription policy value |Organizer's Copilot meeting option | Behavior|
|---------|---------|---------------|
|On|Only during the meeting| Licensed users can select the Copilot button for use only during this meeting with a hidden transcript. To use Copilot during, and after the meeting, these users can start a standard transcript. |
|Off|Only during the meeting| Licensed users can select the Copilot button for use during this meeting or event with a hidden transcript. If another participant who can transcribe enables transcription, Copilot is available during, and after the meeting.|
|On|During and after the meeting| Once licensed users turn on transcription, they can select the Copilot button for use during, and after this meeting or event. |
|Off|During and after the meeting| Licensed users can't interact with Copilot unless another participant with permission to transcribe turns on transcription for this meeting.|

To learn more about managing transcription, see [Configure transcription and captions for Teams meetings](meeting-transcription-captions.md).

## Manage Copilot for your Teams users

You can use the Teams admin center or PowerShell to manage how users in your org use Copilot for Teams meetings and events.

The following table shows the behaviors of the settings for the **`-Copilot`** parameter:

|Teams admins center policy value |PowerShell setting value | Behavior|
|---------|---------|---------------|
|On|Enabled| When organizers with this policy create meetings and events, the default value for Copilot in their meeting options is **Only during the meeting**. Meeting organizers can change this value to **During and after the meeting**.  |
|On only with retained transcript|EnabledWithTranscript| **This is the default value**. When organizers with this policy create meetings, the default value for Copilot in their meeting options is **During and after the meeting**. This option is enforced; organizers can't change this value.|

### Manage Copilot in the Teams admin center

1. Open the Teams admin center.
2. Expand **Meetings** from the navigation pane.
3. Under **Meetings**, select **Meeting Policies**.
4. Either select an existing policy or create a new one.
5. Select **On** or **On only with retained transcript** from the dropdown for the **Copilot** setting.
6. Select **Save**

You can apply your Copilot meeting policies to groups or individual users. You can also add Copilot to your meeting templates. To learn how to apply Copilot meeting policies to meeting templates, see [IT admins - Create a custom meeting template in Microsoft Teams](create-custom-meeting-template.md).

### Manage Copilot using PowerShell

To  manage how users in your org use Copilot for Teams meetings and events, use the **`-Copilot`** parameter within the PowerShell [**CsTeamsMeetingPolicy**](/powershell/module/teams/set-csteamsmeetingpolicy) cmdlet.

To allow users in meetings and events that organizers with this policy create to use Copilot **Only during the meeting**, use the following script:

```PowerShell
Set-CsTeamsMeetingPolicy -Identity <policy name> -Copilot Enabled
```

## Related articles

- [Microsoft Copilot for Microsoft 365 documentation](/microsoft-365-copilot)
- [Configure transcription and captions for Teams meetings](meeting-transcription-captions.md)
- [Plan for Teams meetings](plan-meetings.md)
- [Plan for Teams webinars](plan-webinars.md)
- [Plan for Teams town halls](plan-town-halls.md)
