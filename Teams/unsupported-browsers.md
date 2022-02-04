---
title: Microsoft Teams meetings on unsupported browsers
author: SerdarSoysal
ms.author: serdars
manager: serdars
ms.topic: conceptual
ms.service: msteams
audience: admin
MS.collection: 
- M365-collaboration
ms.reviewer: nakulm
f1.keywords:
- NOCSH
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how Teams supports audio and video in unsupported browsers.
appliesto: 
- Microsoft Teams
---

# Microsoft Teams meetings on unsupported browsers

Some browsers, such as Internet Explorer 11, Safari, and Firefox, support the Microsoft Teams web app but don't support some of the Teams calling and meeting features. To work around this limitation, the Teams web app lets users receive audio through a PSTN connection and lets them view presented content (screen share) at a reduced display rate.

> [!Note]
> Microsoft 365 apps and services will not support Internet Explorer 11 starting August 17, 2021 (Microsoft Teams will not support Internet Explorer 11 earlier, starting  November 30, 2020). [Learn more](https://aka.ms/AA97tsw). Please note that Internet Explorer 11 will remain a supported browser. Internet Explorer 11 is a component of the Windows operating system and [follows the Lifecycle Policy](/lifecycle/faq/internet-explorer-microsoft-edge) for the product on which it is  installed.

When Teams detects an unsupported browser, it automatically displays a message explaining the issue and the session limitations. The message provides further instructions for accessing the meeting audio, such as advising the user to leave a call back number so that Teams can call the user, or instructing the user to call the conference number included in the meeting invitation. The message also encourages the user to download and use the [Teams desktop client](https://teams.microsoft.com/downloads) for the full Teams experience.

If PSTN is unavailable, the user won't see the instructions for accessing the meeting and won't be able to join the meeting.

## Browser limitations

People who use the Teams web app on unsupported browsers will experience the following limitations:

- Audio is available through a PSTN connection only. Users can't use their microphone.
- Users can't share their camera or see other participants' videos but can view presented content through image-based screen sharing.
- Users can't share their screen, although they can see a screen that another meeting participant shares.
- Users can't take control during a screen sharing session.
- Users won't receive incoming call notifications.
- If the call is interrupted, the meeting won't automatically reconnect.
- Users can't start meetings.

For more information about browser support in Teams, see [Limits and specifications for Teams](./limits-specifications-teams.md#browsers).

## Related topics

- [Join a Teams meeting on an unsupported browser](https://support.office.com/article/daafdd3c-ac7a-4855-871b-9113bad15907)