---
title: Require a watermark for sensitive Teams meetings
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: 
audience: admin
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.collection: 
  - m365solution-compliantmeetings
  - m365initiative-meetings
appliesto: 
  - Microsoft Teams
description: Learn how to enable or require watermarks on attendee video and shared content in sensitive Teams meetings.
---

# Require a watermark for sensitive Teams meetings

[!INCLUDE[Teams Premium ECM](includes/teams-premium-ecm.md)]

You can enable a watermark to be displayed in Teams meetings both for content shared on screen and for attendee video. The watermark displays the email address of the meeting participant. Meeting participants can't turn the watermark off. 

Watermarks are supported on Teams desktop, Teams mobile, Microsoft Teams Rooms on Windows, and Microsoft Teams Rooms on Surface Hub. (Watermarks are not supported on Microsoft Teams Rooms on Android.) People joining meetings from unsupported platforms, including [Cloud Video Interop (CVI)](cloud-video-interop.md), will be able to see content without watermarks.

The following participants have an audio-only experience when a watermark is in use:

- Participants using the Teams web client
- Virtual Desktop Infrastructure (VDI) participants
- Anonymous participants
- Overflow participants

> [!Note]
> Meeting settings in sensitivity labels, custom meeting templates, and watermarks require Teams Premium.

Meeting watermarks are enabled in the Teams admin center. They can then be added by the meeting organizer or enforced by a template or sensitivity label.

The following table shows where watermarks are configured:

|Setting|Admin policy|Sensitivity label|Template|Meeting organizer|
|:------|:----------:|:---------------:|:------:|:---------------:|
|Apply a watermark to shared content|Yes|Yes|Yes|Yes|
|Apply a watermark to everyone's video feed|Yes|Yes|Yes|Yes|

When a watermark is being used in a meeting, the following features are turned off:

- Meeting recording, including automatic recording

- Large gallery

- Together mode

- PowerPoint Live

- Whiteboard

- Content from camera

## Watermarks for sensitive and highly sensitive meetings

Watermarks can be useful for protecting confidential information shared in meetings. This is most useful when sharing information with people who do not normally have access to the information. For example, a member of the finance organization might use watermarks when sharing quarterly estimates with managers from different divisions.

Since watermarks are designed to reduce the chances that confidential information will be exfiltrated, using them in meetings where all the participants have direct access to the content being shared, may not add to security.

For information about using watermarks with other meeting features to help protect confidential information in meetings, see [Configure Teams meetings with protection for highly sensitive data](/microsoftteams/configure-meetings-highly-sensitive-protection).

## Enable watermarks

For watermarks to be available in templates and sensitivity labels, and to the meeting organizer, they must be enabled in the Teams admin center.

To enable watermarking for meetings

1. In the Teams admin center, expand **Meetings** and select **Meeting policies**.

1. Select the policy you want to update.

1. To enable watermark on attendee video, set **Watermark videos** to **On**.

1. To enable watermark on content shared on screen in a meeting, set **Watermark shared content** to **On**.

    ![Screenshot of Teams admin policy for watermarks](media/watermark-admin-policy.png)

1. To see how the watermark will look on desktop and mobile devices, select **Preview**.

1. Select **Save**.

You can also enable or disable watermarks by using PowerShell. Use the [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy) cmdlet with the `-AllowWatermarkForCameraVideo` and `-AllowWatermarkForScreenSharing` parameters.

For example:

```powershell
Set-CsTeamsMeetingPolicy -Identity Global -AllowWatermarkForCameraVideo $True 

Set-CsTeamsMeetingPolicy -Identity Global -AllowWatermarkForScreenSharing $True 
```

## Related topics

[Configure Teams meetings with three tiers of protection](configure-meetings-three-tiers-protection.md)

[Use Teams meeting templates, sensitivity labels, and admin policies together for sensitive meetings](meeting-templates-sensitivity-labels-policies.md)