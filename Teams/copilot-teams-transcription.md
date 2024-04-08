---
title: Manage Copilot for Microsoft Teams meetings and events
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.reviewer: elederman
ms.date: 4/5/2024
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
  - teams-copilot
description: Learn how to manage Copilot admin policies in the Teams admin center. Learn how to manage transcripts and transcription for Copilot Microsoft Teams meetings and events.
---

# Manage Copilot for Microsoft Teams meetings and events

**APPLIES TO:** ✔️Meetings ✔️Webinars ✔️Town halls

Copilot for Microsoft Teams meetings and events is an artificial intelligence (AI) tool that can capture important conversation points. Each meeting and webinar participant with a Copilot license can ask prompts that are only visible to them. Participants and organizers can learn things like who said what and where people agree or disagree. Copilot can also recommend follow-up tasks, all in real time during a meeting. For town halls, organizers, co-organizers, presenters can use Copilot during the event.

There are two ways for users in your organization to use Copilot in meetings:

**1. Copilot during and after the meeting**<br>

When organizers create a meeting or event, they can set Copilot’s value to **During and after the meeting** from the dropdown in their meeting options. Once someone with a Copilot license selects the Copilot button and enables transcription during the meeting or event, Copilot starts running for all licensed users. Copilot is available both during and after the meeting. If you assign a policy that disables transcription, organizers with this policy can’t use Copilot with transcription in their meetings. Instead, they must use Copilot only during the meeting.

To learn more about how organizers can use Copilot during and after the meeting, see [Get started with Copilot in Microsoft Teams meetings](https://support.microsoft.com/office/get-started-with-copilot-in-microsoft-teams-meetings-0bf9dd3c-96f7-44e2-8bb8-790bedf066b1).

**2. Copilot only during the meeting**<br>

When organizers create a meeting or event, they can set Copilot’s value to **Only during the meeting** from the dropdown in their meeting options. Once someone with a Copilot license selects the Copilot button during the meeting or event, Copilot starts running for all licensed users. This option relies on a temporary transcript that gets deleted when the meeting or event ends, so Copilot isn't accessible after the meeting or event. If you assign organizers a policy that disables transcription, any organizers with this policy must use Copilot only during the meeting to access Copilot in their meetings and events.

To learn more about how organizers can use Copilot  only during the meeting, see [Use Copilot without recording a Teams meeting](https://support.microsoft.com/office/use-copilot-without-recording-a-teams-meeting-a59cb88c-0f6b-4a20-a47a-3a1c9a818bd9).

For more information about transcription policies, see [Configure transcription and captions for Teams meetings](meeting-transcription-captions.md).

As an admin, you can manage the default value for Copilot that  your organizers have in their meeting options. Meeting organizers can change their Copilot setting for each meeting they create.

> [!IMPORTANT]
> Copilot for Teams meetings isn’t available in end-to-end encrypted meetings. For more information on end-to-end encryption, see [Require end-to-end encryption for sensitive Teams meetings](end-to-end-encrypted-meetings.md).

> [!NOTE]
> Copilot isn’t available for GCC, GCC High, DoD, and EDU.

## Prerequisites

- A Copilot license for intended users. To learn more about the Copilot license, see [Microsoft Copilot for Microsoft 365 documentation](/microsoft-365-copilot).

## Manage Copilot in the Teams admin center

1. Open the Teams admin center.
2. Expand **Meetings** from the navigation pane.
3. Under **Meetings**, select **Meeting Policies**.
4. Either select an existing policy or create a new one.
5. Navigate to the **Recording & transcription** section and note your setting for the **Transcription** policy.
6. Select one of the following values from the dropdown for the **Copilot** setting:

    - **On**- Select this value if you want your organizers to use Copilot only during the meeting. You should use this value if you disabled **Transcription** for organizers with this policy. When organizers with this policy create meetings, Copilot isn’t accessible once the meeting is over.
    - **On with transcript**- Select this value if you want your organizers to use Copilot during and after the meeting. You should use this value if you enabled **Transcription** for organizers with this policy. Copilot is available both during and after meetings that organizers with this policy create meetings.

7. Select **Save**

You can apply your Copilot meeting policies to groups or individual users. You can also add Copilot to your meeting templates. To learn how to apply Copilot meeting policies to meeting templates, see [IT admins - Create a custom meeting template in Microsoft Teams](create-custom-meeting-template.md).

## Manage Copilot using PowerShell

To manage the default value for Copilot in your organizers’ meeting options, use the **`-Copilot`** parameter within the PowerShell [**CsTeamsMeetingPolicy**](/powershell/module/teams/set-csteamsmeetingpolicy) cmdlet.

The following table shows the behaviors of the settings for the **`-Copilot`** parameter:

|Setting value| Behavior|
|---------|---------------|
|Enabled| When organizers with this policy create meetings, the default value for Copilot in their meeting options is **Only during the meeting**. If the organizer keeps the default, transcription isn’t required to use Copilot for the meeting. Copilot starts once a licensed user selects the Copilot button and is only available to use during the meeting. |
|EnabledWithTranscript| **This is the default value**. When organizers with this policy create meetings, the default value for Copilot in their meeting options is **During and after the meeting**. If the organizer keeps the default, transcription must be enabled to use Copilot for the meeting. Copilot is still available to use after the meeting ends.|

For organizers with this policy to have the default value for Copilot set to **Only during the meeting**, use the following script:

```PowerShell
Set-CsTeamsMeetingPolicy -Identity <policy name> -Copilot Enabled
```

## Related articles

- [Microsoft Copilot for Microsoft 365 documentation](/microsoft-365-copilot)
- [Configure transcription and captions for Teams meetings](meeting-transcription-captions.md)
