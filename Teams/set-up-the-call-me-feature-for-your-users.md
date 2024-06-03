---
title: Set up the Call me feature for your users
ms.author: wlibebe
author: wlibebe
ms.reviewer: oscarr
ms.date: 3/4/2024
manager: pamgreen
ms.topic: article
ms.service: msteams
audience: admin
search.appverid: MET150
description: Learn how to set up the Call me feature in Teams so that users can join the audio portion by phone when using their computer for audio might not be possible.
ms.localizationpriority: medium
ms.collection: 
  - Tier1
  - m365initiative-meetings
f1.keywords:
- NOCSH
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-mar2020
---

# Set up the Call me feature for your users

In Microsoft Teams, the **Call me** feature allows users to join meeting audio through their phone, which is useful when they can't use computer audio. Users listen to the meeting audio on their phone and watch the meeting content that others share through their computer.

> [!NOTE]
> [!INCLUDE [updating-admin-interfaces](includes/updating-admin-interfaces.md)]

## Enable the Call me feature

To enable the **Call me** feature for users in your org, these prerequisites must be configured:

- Audio Conferencing is enabled for users in your organization who schedule meetings (meeting organizers). To learn more, see [Set up Audio Conferencing for Teams](set-up-audio-conferencing-in-teams.md) and [Manage the Audio Conferencing settings for a user in Teams](manage-the-audio-conferencing-settings-for-a-user-in-teams.md).

- Meeting organizer can dial-out from meetings. To learn more, see [Manage the Audio Conferencing settings for a user in Teams](manage-the-audio-conferencing-settings-for-a-user-in-teams.md).

If the meeting organizer doesn't have dial-out from meetings enabled, the **Phone audio** option on the **Choose your video and audio options** screen isn't available to anyone, and other users can't receive a call to join them to the meeting. For users with dial-out enabled, once they join the meeting, they can join others dialing their number from the **Show participants** icon.

## The user experience

### Join a meeting by using phone for audio

Select **Join** to join a meeting > **Phone audio** on the **Choose your video and audio options** screen > select **Join now**. From here, users can join the meeting call or dial in manually to the meeting.

![Screen shot of the Phone audio option.](media/set-up-the-call-me-feature-for-your-users-phone-audio.png)

#### Use phone for audio

Users have two ways to join the meeting audio via phone.

##### 1. Receive a call

On the **Use phone for audio** screen, the user enters their phone number, and then selects the **Call me** button. The meeting calls the user to join the meeting.

![Screen shot of the Call me option on the Use phone for audio screen.](media/set-up-the-call-me-feature-for-your-users-call-me.png)

##### 2. Dial in manually

Another way to join is to dial in directly to the meeting. On the **Use phone for audio** screen, select **Dial in manually** to get a list of phone numbers to use to dial in to the meeting.

![Screen shot of the Dial in manually option.](media/set-up-the-call-me-feature-for-your-users-dial-in.png)

### Receive a meeting callback for audio issues

If a user experiences audio issues when using their computer during a meeting, the user can easily switch to using their phone for audio. Teams detects when an audio or device issue occurs and redirects the user to use their phone by displaying a **Call me back** option.

Here's an example of the message and the **Call me back** option that Teams displays when no microphone is detected:

![Screen shot of the Call me back option.](media/set-up-the-call-me-feature-for-your-users-no-mic.PNG)

The user selects the **Call me back** button, which brings up the **Use phone for audio** screen. From here, they can enter their phone number dial-in manually or have the Teams meeting call to join them to the meeting.
