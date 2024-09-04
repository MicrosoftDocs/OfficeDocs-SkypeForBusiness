---
title: "Explicit recording consent for Audio Conferencing"
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.reviewer: simonibssa
ms.date: 6/3/2024
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
description: Learn how to manage Explicit recording consent for Audio Conferencing in Microsoft Teams. Learn how to require participants to require consent to being recorded when dialing into Microsoft Teams meetings.
---

# Explicit recording consent for Audio Conferencing

Explicit recording consent for Microsoft Teams Audio Conferencing lets you, as an admin, control whether meetings created by organizers with this policy can require participants to explicitly consent to being recorded.

When the explicit recording policy is enabled, all participants are muted once the meeting recording starts. Once a participant decides to unmute, they’re prompted to provide consent. To consent to be recorded, participants can select controls on their dial pad.

## Recording types

Explicit recording consent includes two recording types:  

**Compliance recording:** Compliance recording is a policy-based feature that requires users with an assigned admin recording policy to have all their calls and meetings recorded. To learn more about compliance recording, see [Introduction to Teams policy-based recording for calling and meetings](teams-recording-policy.md).

**Convenience recording:** Users initiate convenience recording, which is the regular meeting recording. To learn more about convenience recording, see [Record a meeting in Microsoft Teams](https://support.microsoft.com/office/record-a-meeting-in-microsoft-teams-34dfbe7f-b07d-4a27-b4c6-de62f1348c24).

## Configure explicit recording consent for Audio Conferencing

You must use PowerShell to configure explicit recording consent for users or groups in your organization. PowerShell must be installed on your machine to manage this policy. For instructions on installing PowerShell on Windows, Mac, or Linux for the first time, see [Install PowerShell on Windows, Linux, and macOS - PowerShell](/powershell/scripting/install/installing-powershell).

For scripts to enable explicit recording consent for Audio Conferencing, see [Manage explicit recording consent through PowerShell](meeting-recording.md#manage-explicit-consent-through-powershell).

## Recording consent dial pad controls

To select their recording preferences, your users can use the following selections on their dial pad:

**1**– Give consent to being recorded in a call and unmute their microphone.

**2** – Deny recording and remain muted.

***6** – Unmute themselves

***5** – Raise Hand in Meeting

### Example scenarios

This list provides examples of how your users can apply the recording consent dial pad controls, depending on their scenario:

**Scenario 1:** Recording started prior to joining the call (as a participant)

- If the user wants to give consent, they press 1 to consent to be recorded and join unmuted.

**Scenario 2:** Recording started prior to joining the call (as the meeting organizer)

- If the user wants to deny consent, they press 2 to deny being recorded, and join the call muted.

**Scenario 3:** Recording started prior to joining the call (as a participant)

- If the user denied consent and would like to unmute themselves and speak, they press *6

> [!NOTE]
> If you use a policy to mute all participants upon joining a meeting, participants must press *5 to raise hand before providing consent again.

## Related articles

- [Set up Audio Conferencing for Microsoft Teams](set-up-audio-conferencing-in-teams.md)
- [Introduction to Teams policy-based recording for calling and meetings](teams-recording-policy.md)
- [Teams meeting recording](meeting-recording.md)
- [Microsoft Teams PowerShell Overview](teams-powershell-overview.md)
- [Install Microsoft Teams PowerShell Module](teams-powershell-install.md)
