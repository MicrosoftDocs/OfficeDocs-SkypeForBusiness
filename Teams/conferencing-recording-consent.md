---
title: "Explicit recording consent for audio conferencing"
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.reviewer: simonibssa
ms.date: 03/28/2024
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - m365initiative-meetings
  - M365-collaboration
  - m365initiative-meetings
  - Tier1
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
 - CSH
ms.custom: 
  - Audio Conferencing
  - ms.teamsadmincenter.audioconferencing
description: Learn how to manage Explicit recording consent for audio conferencing in Microsoft Teams. Learn how to require participants to require consent to being recorded.
---

# Explicit recording consent for audio conferencing

Explicit recording consent for Microsoft Teams audio conferencing lets you, as an admin, control whether meetings created by organizers with this policy can require participants to explicitly consent to being recorded. When the explicit recording policy is enabled, all participants are muted once the meeting recording starts.  

When a participant decides to unmute, they’re prompted to provide consent. Participants can consent to be recorded by selecting controls on their dial pad.  

## Recording types

There are two types of recordings included in Explicit Recording Consent:  

**Compliance recording:** Compliance recording is a policy-based feature that requires users with an assigned admin recording policy to have all their calls and meetings recorded. To learn more about compliance recording, see [Introduction to Teams policy-based recording for calling and meetings](teams-recording-policy.md).

**Convenience recording:** Users initiate convenience recording, which is the regular meeting recording. To learn more about convenience recording, see [Record a meeting in Microsoft Teams](https://support.microsoft.com/office/record-a-meeting-in-microsoft-teams-34dfbe7f-b07d-4a27-b4c6-de62f1348c24).

## Configure explicit recording consent for audio conferencing

You must use PowerShell to configure explicit recording consent for users or groups in your organization. You must have PowerShell installed on your machine to manage this policy. For instructions on installing PowerShell on Windows, Mac, or Linux for the first time, see [Install PowerShell on Windows, Linux, and macOS - PowerShell](/powershell/scripting/install/installing-powershell).

For cmdlets to enable explicit recording consent for audio conferencing, see [Manage explicit recording consent through PowerShell](meeting-recording.md#manage-explicit-recording-consent-through-powershell).

To learn about blocking or allowing the downloads of channel meeting recordings, recording expiration, setting custom privacy policy URLs, and more, see [Teams meeting recording](meeting-recording.md).

## Recording consent in action

To select their recording preferences, your users can use the following selections on their dial pad:

**1**– Give consent to being recorded in a call and unmute their microphone.

**2** – Deny recording and remain muted.

***6** – Unmute themselves

***5** – Raise Hand in Meeting

### Example scenarios

This list provides examples of how your users can apply the controls from the previous section, depending on their scenario:

1. If they join the meeting unmuted, and would like to remain unmuted:

    - Press 1 to consent to being recorded.

2. If they join the meeting unmuted, and would like to be muted (not recorded):
    - Press 2 to deny consent and stay muted.

3. If they’d like to unmute themselves:
    - Press *6  

4. If they join the meeting muted by the organizer, and would like to speak:
    - Press *5 to raise hand, and then press 1 to consent to being recorded.

## Related articles

- [Set up Audio Conferencing for Microsoft Teams](set-up-audio-conferencing-in-teams.md)
- [Introduction to Teams policy-based recording for calling and meetings](teams-recording-policy.md)
- [Teams meeting recording](meeting-recording.md)
- [Microsoft Teams PowerShell Overview](teams-powershell-overview.md)
- [Install Microsoft Teams PowerShell Module](teams-powershell-install.md)
