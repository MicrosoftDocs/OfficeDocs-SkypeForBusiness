---
title: Require end-to-end encryption for sensitive Teams meetings
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.topic: article
ms.service: msteams
ms.reviewer: maahma
ms.date: 12/15/2023
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
description: Learn how to enable end-to-end encryption for Teams meetings.
---

# Require end-to-end encryption for sensitive Teams meetings

[!INCLUDE[Teams Premium ECM](includes/teams-premium-ecm.md)]

End-to-end encryption is the encryption of information at its origin and decryption at its intended destination without the ability for intermediate nodes to decrypt. When meetings in Teams are end-to-end encrypted, nobody except for the participants in the meeting can hear or see the communication. No other party, including Microsoft, has access to the decrypted conversation.

End-to-end encrypted meetings can be made between two parties when: the parties are using the latest version of the Teams desktop client for Windows or Mac or they are on a mobile device with the latest update for iOS and Android.

Web, Virtual Desktop (VDI), and Cloud Video Interoperability(CVI) devices aren't currently supported. Participants trying to join an end-to-end encrypted meeting from one of these platforms are blocked.

A maximum of 200 participants can attend an end-to-end encrypted meeting.

> [!Note]
> End-to-end meeting encryption requires Teams Premium.

If you don't enable end-to-end encryption, Teams still secures meetings using encryption based on industry standards. Data exchanged during meetings is always secure while in transit and at rest. For more information, see [Media encryption for Teams](teams-security-guide.md#media-encryption).

During an end-to-end encrypted meeting, Teams secures the following features:

- Audio

- Video

- Screen sharing

[Encryption in Microsoft 365](/microsoft-365/compliance/encryption) protects chat, file sharing, presence, and other content in the meeting. Apps, avatars, reactions, chat, and Q&A aren't end-to-end encrypted.

Some features aren't available during an end-to-end encrypted meeting, including:

- Breakout rooms

- Microsoft 365 Copilot in Teams meetings and events

- Excel Live

- Live captions and transcription

- People dialing in by phone

- PowerPoint Live

- Recording

- Request control of shared content

- Together mode, companion mode, large gallery

If your organization uses compliance recording for 1:1 calls, end-to-end encryption isn't available. An individual who needs compliance recording can't join an end-to-end encrypted meeting. For more info on how Teams supports compliance recording, see [Introduction to Teams policy-based recording for callings & meetings](teams-recording-policy.md).

## Manage who can create meetings with end-to-end encryption

End-to-end meeting encryption is controlled by Teams admin enhanced encryption policies. It is on by default in the Global (Org-wide default) policy, giving meeting organizers who have a Teams Premium license the ability to schedule meetings, including channel meetings, that use end-to-end encryption. You can update the default policy or create additional policies as needed to manage end-to-end meeting encryption for different users.

If the policy is turned on for a meeting organizer, you can enforce end-to-end meeting encryption by using a meeting template. Sensitivity labels can enforce end-to-end encryption even if the policy isn't enabled for the meeting organizer.

To manage the end-to-end meeting encryption policy

1. In the Teams admin center, select **Enhanced encryption policy**.

1. Select the policy you want to update.

1. Set **End-to-end meeting encryption**, to **Not enabled** or **Not enabled, but users can enable**.

1. Select **Save**.

## Related topics

[Configure Teams meetings with three tiers of protection](configure-meetings-three-tiers-protection.md)

[Use end-to-end encryption for one-to-one Microsoft Teams calls](teams-end-to-end-encryption.md)
