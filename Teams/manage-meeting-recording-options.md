---
title: Manage Microsoft Teams meeting recording options for sensitive meetings
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: 
ms.date: 09/28/2022
audience: admin
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.collection: 
  - m365solution-compliantmeetings
  - m365initiative-meetings
appliesto: 
  - Microsoft Teams
description: Learn how to manage who can record Teams meetings, automatic recording, and the recording lifecycle.
---

# Manage Microsoft Teams meeting recording options for sensitive meetings

[!INCLUDE[Teams Premium ECM](includes/teams-premium-ecm.md)]

Teams is designed to allow easy recording for meeting participants. If you have compliance requirements around how meeting recordings are used, there are several options available for administrators and meeting organizers to help you use meeting recordings in a compliant way.

The following table shows the features available to help you manage meeting recordings and where they're configured.

|Setting|Admin policy|Sensitivity label|Template|Meeting organizer|
|:------|:----------:|:---------------:|:------:|:---------------:|
|Meeting recording overall|Yes|No|No|No|
|Who can record|No|Yes|Yes|Yes|
|Record automatically|No|Yes|Yes|Yes|
|Recording expiration|Yes|No|No|No|

The Teams Administrator has overall control over whether meeting recording is enabled. Both meeting organizers and administrators can configure who can record and whether meetings are automatically recorded by using sensitivity labels, meeting templates, and meeting organizer settings.

To manage explicit consent for recordings, see [Meeting Recording.](meeting-recording.md)

## Manage who can record meetings

There are two options for who can record a meeting:

- Organizers and co-organizers
- Organizers and presenters

This choice is normally made by the meeting organizer when they create the meeting. If you have meetings where sensitive information is being shared and you want to limit the ability to record to organizers only, you can enforce this setting by using a meeting template or sensitivity label. 

If you need to prevent meetings from being recorded entirely, you must configure the **Meeting recording** meetings policy in the Teams admin center. This setting applies to the people or groups that you specify and can't be applied via a meeting template or sensitivity label.

## Automatic recording

Meetings can be set to record automatically when they start. Normally, the meeting organizer makes this choice when they create the meeting.

If there are certain types of meetings that should always be recorded, you can enforce this option by using a meeting template or a sensitivity label.

If all of a particular type of meeting must be recorded (for example, all sensitive meetings), consider enforcing this by using a sensitivity label. If only certain sensitive meetings need to be recorded, consider using meeting templates to configure this setting. You can create two templates that both use the *sensitive* label, one which automatically records and another which doesn't.

## Recording lifecycle

By default, meeting recordings are deleted after 120 days. This is configured by using two policies in the Teams admin center:

- **Recordings automatically expire** determines if meeting recordings are automatically deleted after a specified time.
- **Default expiration time** specifies the number of days after which recordings are deleted. The default is 120.

When a meeting participant records a meeting, the recording is stored in their OneDrive. Channel meetings are stored in the SharePoint site associated with the channel. Because meeting recordings are .mp4 files, they can be moved or deleted like any other file. If a meeting recording is moved from its original location, the expiration setting will no longer affect it.

The expiration feature is meant for removing old recordings to save storage space. It's not meant for enforcing compliance requirements. If you have compliance requirements around how long meeting recordings are retained or when they're deleted, consider storing them in a SharePoint library where you can apply [Microsoft Purview retention policies](/microsoft-365/compliance/retention).

## Configure recording options for your organization

For information about configuring admin meeting policies for meeting recordings and enabling explicit recording consent, see [Teams meeting recording](/microsoftteams/meeting-recording).

For details about enforcing settings by using meeting templates and sensitivity labels, see [Configure Teams meetings with protection for sensitive data](configure-meetings-sensitive-protection.md) and [Configure Teams meetings with protection for highly sensitive data](configure-meetings-highly-sensitive-protection.md).

## Related topics

[Introduction to Teams policy-based recording for callings & meetings](teams-recording-policy.md)

[Configure Teams meetings with three tiers of protection](configure-meetings-three-tiers-protection.md)
