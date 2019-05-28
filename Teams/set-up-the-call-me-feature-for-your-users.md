---
title: Set up the Call me feature for your users
author: LanaChin
ms.author: v-lanac
ms.reviewer: macai
manager: serdars
ms.date: 05/24/2019
ms.topic: article
ms.service: msteams
search.appverid: MET150
description: Learn how to set up the Call me feature in Teams so that users can join the audio portion by phone in scenarios where using their computer for audio might not be possible.
localization_priority: Normal
MS.collection: Strat_MT_TeamsAdmin
appliesto: 
- Microsoft Teams
---

# Set up the Call me feature for your users

In Microsoft Teams, the **Call me** feature gives users a way to join the audio portion of a meeting by phone. This is handy in scenarios when using a computer for audio might not be possible. Users get the audio portion of the meeting through their cell phone or land line and the content portion of the meeting&mdash;such when another meeting participant shares their screen or plays a video&mdash;through their computer.

## The user experience

Click **Join** to join a meeting, and then click **Phone audio** on the  **Choose your audio and video settings** screen. From here, users can have the meeting call and join them or dial in manually to the meeting.

![Screen shot of the Phone audio option](media/set-up-the-call-me-feature-for-your-users-phone-audio.png)

**Let the Teams meeting call**

On the **Use phone for audio** screen, the user enters their phone number, and then clicks **Call me**. The meeting calls the user and joins them to the meeting.

![Screen shot of the Call me option on the Use phone for audio screen](media/set-up-the-call-me-feature-for-your-users-call-me.png)

**Dial in manually**

Another way to join is to dial in directly to the meeting. On the **Use phone for audio** screen, click **Dial in manually** to get a list of phone numbers to use to dial in to the meeting.

![Screen shot of the Dial in manually option](media/set-up-the-call-me-feature-for-your-users-dial-in.png)

## Set up the Call me feature

To enable the Call me feature for users in your organization, the following must be configured:

- Audio Conferencing is enabled for users in your organization who schedule meetings (meeting organizers). To learn more, see [Set up Audio Conferencing for Teams](set-up-audio-conferencing-in-teams.md) and [Manage the Audio Conferencing settings for a user in Teams](manage-the-audio-conferencing-settings-for-a-user-in-teams.md).

- Users can dial out from meetings. To learn more, see [Manage the Audio Conferencing settings for a user in Teams](manage-the-audio-conferencing-settings-for-a-user-in-teams.md).

If a user doesn't have dial out from meetings enabled, the **Call me** option isn't available and the user won't receive a call to join them to the meeting. Instead, the user sees a list of phone numbers on the **Use phone for audio** screen that they can use to dial in manually to the meeting on their phone.

