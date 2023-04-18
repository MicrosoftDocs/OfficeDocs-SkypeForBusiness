---
title: Require end-to-end encryption for sensitive Teams meetings
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

Web, Virtual Desktop (VDI), Cloud Video Interoperability(CVI), Windows and Android Teams Room devices, and Surface Hub are not currently supported. If trying to join from one of these platforms, you will be blocked from joining the end-to-end encrypted meeting.

> [!Note]
> End-to-end meeting encryption requires Teams Premium.

If you don't enable end-to-end encryption, Teams still secures meetings using encryption based on industry standards. Data exchanged during meetings is always secure while in transit and at rest. For more information, see [Media encryption for Teams](teams-security-guide.md#media-encryption).

During an end-to-end encrypted meeting, Teams secures the following features:

- Audio

- Video

- Screen sharing

[Encryption in Microsoft 365](/microsoft-365/compliance/encryption) protects chat, file sharing, presence, and other content in the meeting. Apps, avatars, reactions, chat, and Q&A are not end-to-end encrypted.

The following features aren't available during an end-to-end encrypted meeting:

- Live captions and transcription

- Recording

- Together mode, companion mode, large gallery

- Breakout rooms

- PowerPoint Live

- Excel Live

If your organization uses compliance recording for 1:1 calls, end-to-end encryption isn't available. For an end-to-end encrypted meeting if an individual who needs compliance recording tries to join, they will be blocked from joining. For more info on how Teams supports compliance recording, see [Introduction to Teams policy-based recording for callings & meetings](teams-recording-policy.md).

## Enable end-to-end encryption for meetings

By default, end-to-end encryption for meetings is not enabled. You can enable it by using a Teams admin enhanced encryption policy.

Once end-to-end encryption is enabled, meeting organizers have the option of choosing end-to-end encryption then they create a meeting, including channel meetings. You can also enforce end-to-end encryption by using a meeting template or a sensitivity label.

To enable end-to-end encryption for meetings

1. In the Teams admin center, select **Enhanced encryption policy**.

1. Select the policy you want to update.

1. Set **End-to-end meeting encryption**, to **Off, but organizers and co-organizers can turn them on**.

1. Select **Save**.

## Related topics

[Configure Teams meetings with three tiers of protection](configure-meetings-three-tiers-protection.md)

[Use end-to-end encryption for one-to-one Microsoft Teams calls](teams-end-to-end-encryption.md)
