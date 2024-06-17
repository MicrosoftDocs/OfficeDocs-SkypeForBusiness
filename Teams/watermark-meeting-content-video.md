---
title: Require a watermark for sensitive Teams meetings
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.topic: article
ms.service: msteams
ms.reviewer: mudrapatel
ms.date: 12/14/2023
audience: admin
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.collection: 
  - m365solution-compliantmeetings
  - m365initiative-meetings
  - highpri
  - Tier1
appliesto: 
  - Microsoft Teams
description: Learn how to enable or require watermarks on attendee video and shared content in sensitive Teams meetings.
---

# Require a watermark for sensitive Teams meetings

[!INCLUDE[Teams Premium ECM](includes/teams-premium-ecm.md)]

You can enable a watermark to be displayed in Teams meetings both for content shared on screen and for attendee video. The watermark displays the email address of the meeting participant. Each participant will see their own email address overlaid on the meeting video or shared content. This deters participants from taking unauthorized screenshots of the meeting content.

Watermarks are supported on Teams desktop, mobile, and Microsoft Teams Rooms. People joining meetings from unsupported platforms will have an audio-only experience.

The following participants have an audio-only experience when a watermark is in use:

- Virtual Desktop Infrastructure (VDI) participants
- Anonymous participants
- Overflow participants
- Older Teams clients
- [Direct Guest Join on Microsoft Teams Rooms devices](/microsoftteams/rooms/third-party-join)

> [!NOTE]
> Meeting settings in sensitivity labels, custom meeting templates, and watermarks require Teams Premium.

Meeting watermarks are enabled in the Teams admin center. They can then be added by the meeting organizer (the organizer must have a Teams Premium license) or enforced by a template or sensitivity label.

The following table shows where watermarks are configured:

|Setting|Admin policy|Sensitivity label|Template|Meeting organizer|
|:------|:----------:|:---------------:|:------:|:---------------:|
|Apply a watermark to shared content|Yes|Yes|Yes|Yes|
|Apply a watermark to everyone's video feed|Yes|Yes|Yes|Yes|

When a watermark is being used in a meeting, the following features are turned off:

- Large gallery

- Together mode

- Content from camera

## Watermarks for sensitive and highly sensitive meetings

Watermarks can be useful for protecting confidential information shared in meetings. This is most useful when sharing information with people who don't normally have access to the information. For example, a member of the finance organization might use watermarks when sharing quarterly estimates with managers from different divisions.

Since watermarks are designed to reduce the chances that confidential information will be exfiltrated, using them in meetings where all the participants have direct access to the content being shared may not add to security.

For information about using watermarks with other meeting features to help protect confidential information in meetings, see [Configure Teams meetings with protection for highly sensitive data](/microsoftteams/configure-meetings-highly-sensitive-protection).

## Meeting recordings

If a meeting with a watermark is recorded, the watermark is applied at playback time by Microsoft Stream. Viewers of the recording see their own email address as a watermark on the video. If the recording file is edited or moved, the watermark won't be available at playback time.

By default, download of the meeting recording (.mp4) file is disabled for recordings of meetings with a watermark. However, the person who recorded the meeting can change that permission. Downloaded .mp4 files don't contain a watermark.

## Configure watermarks

For watermarks to be available to the meeting organizer, they must be enabled in the Teams admin center. (Watermarks are enabled by default.) Note that sensitivity labels can enforce watermarks even if they're turned off for the meeting organizer in the Teams admin meeting policy.

To configure watermarking for meetings

1. In the Teams admin center, expand **Meetings** and select **Meeting policies** > **Content Protection**.

1. Select the policy you want to update.

1. To configure watermark on attendee video, set **Watermark videos** to **On** or **Off**.

1. To configure watermark on content shared on screen in a meeting, set **Watermark shared content** to **On** or **Off**.

1. To set the watermark pattern or transparency, or see a preview, select **Edit settings**. Select **Apply** if you make changes.

1. Select **Save**.

You can also enable or disable watermarks by using PowerShell. Use the [Set-CsTeamsMeetingPolicy](/powershell/module/teams/set-csteamsmeetingpolicy) cmdlet with the `-AllowWatermarkForCameraVideo` and `-AllowWatermarkForScreenSharing` parameters.

For example:

```powershell
Set-CsTeamsMeetingPolicy -Identity Global -AllowWatermarkForCameraVideo $True 

Set-CsTeamsMeetingPolicy -Identity Global -AllowWatermarkForScreenSharing $True 
```

## Related topics

- [Configure Teams meetings with three tiers of protection](configure-meetings-three-tiers-protection.md)

- [Use Teams meeting templates, sensitivity labels, and admin policies together for sensitive meetings](meeting-templates-sensitivity-labels-policies.md)

- [Teams policies reference - Watermark](settings-policies-reference.md#content-protection)
