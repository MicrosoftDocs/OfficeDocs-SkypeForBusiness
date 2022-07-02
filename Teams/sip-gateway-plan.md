---
title: Plan SIP Gateway
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.date: 09/30/2021
ms.topic: article
ms.service: msteams
audience: admin
ms.collection:
  - M365-voice
  - m365initiative-voice
ms.reviewer: crowe
search.appverid: MET150
f1.keywords:
- NOCSH
- ms.teamsadmincenter.directrouting.overview
description: Learn more about SIP Gateway, such as requirements and benefits.
ms.custom:
 - seo-marvel-apr2020
 - seo-marvel-jun2020
appliesto:
  - Microsoft Teams
---

# Plan for SIP Gateway

SIP Gateway lets your organization use any compatible SIP device with Microsoft Teams to preserve your investments in SIP devices. Now you can sign-in to Teams with your corporate credentials and make and receive calls with a compatible SIP device. Compatible devices can be Skype for Business IP phones with standard SIP firmware, Cisco IP phones with multiplatform SIP firmware, or SIP devices from vendors such as Poly, Yealink, and AudioCodes. To find out how to configure your SIP devices for SIP Gateway, see [Configure SIP Gateway](sip-gateway-configure.md).

## Benefits of SIP Gateway

SIP Gateway connects compatible SIP devices to Teams to help your users migrate seamlessly to Teams telephony. Using SIP Gateway, your users can do all of the following:

- **Make calls:** SIP device users can make calls to the Public Switched Telephone Network (PSTN), to other SIP devices, and to Teams and Skype for Business users. SIP device users can only call users who have phone numbers.
- **Receive calls:** SIP device users can receive a call from the PSTN, from Teams or Skype for Business users who have SIP devices, and from Teams and Skype for Business client applications. The SIP device acts as a Teams endpoint. Inbound calls will also be forked to the user's SIP device.
- **Multiple simultaneous calls:** A SIP device user in a call can put the call on hold to make or receive other calls. A SIP device user can also conference two calls.
- **Do not disturb:** A SIP device user can set do not disturb on the device so that the device will not ring for incoming calls. This has no impact on the user's status on all other Teams endpoints.
- **Hold/Resume and Mute/Unmute:** A SIP device user can hold and resume or mute and unmute a call by using the features for those actions on the device.
- **Voicemail:** SIP device users can listen to electronically stored voice messages that callers leave for them.
- **Message waiting indicator:** SIP device users can receive notifications that alert them when they have new voicemail messages.
- **Sign-in and sign-out:** SIP devices users can sign in and sign out of Teams on the device.
- **Dual-tone multi-frequency:** SIP device users can press number keys to provide input during interactive voice response calls.
- **Teams meetings:** A SIP device user can join a Teams meeting by dialing the meeting access number. Meeting participants can add a SIP device user to the meeting by dialing out to user's phone number or simply adding a participant by clicking on 'Request to Join' will also alert the user's SIP device. Guest users from another organization can be added to a Teams meeting by a participant who dials out to a guest user's number to include that guest.
- **Call transfers:** SIP device users can transfer calls. SIP Gateway supports both blind and consultative transfers.
- **Local call forwarding:** A SIP device user can set forwarding rules (always, on timeout, and busy) for the device. If the device is connected to the SIP Gateway, then the call will be redirected to the target address based on the rule that the device user set. To make local call forwarding work, the admin must set the `AllowCallRedirect` attribute in `Set-CsTeamsCallingPolicy` to `Enabled`.

## Requirements to use SIP Gateway

Teams users must have a phone number with PSTN calling enabled to use SIP Gateway.

### Hardware, software, and licenses

If you have a 3PIP or SIP device, you must have:

- A license for Phone System (via E5 or a standalone license)
- PSTN enablement (i.e., a phone number) via a Microsoft Teams Calling Plan, Direct Routing, or Operator Connect
- A Common Area Phone license for any common area devices

## Compatible devices

|Vendor    |Model      |Minimum firmware version|Approved firmware version|Remarks|Links|
|----------|-----------|------------|-----------|------------|------------|
|**Cisco** |           |            |           |Devices running enterprise firmware must be converted to multiplatform firmware. Read the guide at the right to learn how.|[Cisco firmware conversion guide](https://www.cisco.com/c/en/us/products/collateral/collaboration-endpoints/unified-ip-phone-7800-series/guide-c07-742786.html)|
|          |8832       |11.3.5MPP   |11.3.5MPP  |   |   |
|          |6821       |11.1.1MPP   |11-3-3MPP  |   |   |
|          |7811       |11.1.1MPP   |11-3-3MPP  |   |   |
|          |7821       |11.1.1MPP   |11-3-3MPP  |   |   |
|          |7841       |11.1.1MPP   |11-3-3MPP  |   |   |
|          |7861       |11.1.1MPP   |11-3-3MPP  |   |   |
|          |8811       |11.1.1MPP   |11-3-3MPP  |   |   |
|          |8841       |11.1.1MPP   |11-3-3MPP  |   |   |
|          |8845       |11.1.1MPP   |11-3-3MPP  |   |   |
|          |8851       |11.1.1MPP   |11-3-3MPP  |   |   |
|          |8861       |11.1.1MPP   |11-3-3MPP  |   |   |
|          |8865       |11.1.1MPP   |11-3-3MPP  |   |   |
|**Poly**  |           |            |           |The device will auto-reboot and install the selected firmware.|   |
|          |Trio 8500  |5.9.5.3182  |7.1.1.0997 |   |   |
|          |Trio 8800  |5.9.5.3182  |7.1.1.0997 |   |   |
|          |VVX150     |5.9.5       |6.3.1.8427 |   |   |
|          |VVX201     |5.9.5       |6.3.1.8427 |   |   |
|          |VVX250     |5.9.5       |6.3.1.8427 |   |   |
|          |VVX300     |5.9.5       |5.9.6.2327 |   |   |
|          |VVX301     |5.9.5       |6.3.1.8427 |   |   |
|          |VVX310     |5.9.5       |5.9.6.2327 |   |   |
|          |VVX311     |5.9.5       |6.3.1.8427 |   |   |
|          |VVX350     |5.9.5       |6.3.1.8427 |   |   |
|          |VVX400     |5.9.5       |5.9.6.2327 |   |   |
|          |VVX401     |5.9.5       |6.3.1.8427 |   |   |
|          |VVX410     |5.9.5       |5.9.6.2327 |   |   |
|          |VVX411     |5.9.5       |6.3.1.8427 |   |   |
|          |VVX450     |5.9.5       |6.3.1.8427 |   |   |
|          |VVX500     |5.9.5       |5.9.6.2327 |   |   |
|          |VVX501     |5.9.5       |6.3.1.8427 |   |   |
|          |VVX600     |5.9.5       |5.9.6.2327 |   |   |
|          |VVX601     |5.9.5       |6.3.1.8427 |   |   |
|**Yealink**|          |            |           |   |[Yealink support](https://support.yealink.com/)|
|          |T40P       |83          |54.84.0.125|   |   |
|          |T41S       |83          |66.85.0.5  |   |   |
|          |T41S       |83          |66.85.0.5  |   |   |
|          |T41S       |83          |66.85.0.5  |   |   |
|          |T42G       |83          |29.83.0.130|   |   |
|          |T42S       |83          |66.85.0.5  |   |   |
|          |T42U       |83          |108.86.0.20|   |   |
|          |T43U       |83          |108.86.0.20|   |   |
|          |T46S       |83          |66.85.0.5  |   |   |
|          |T46U       |83          |108.86.0.20|   |   |
|          |T48S       |83          |66.85.0.5  |   |   |
|          |T48G       |83          |35.83.0.130|   |   |
|          |T48U       |83          |108.86.0.20|   |   |
|          |T53        |83          |96.85.0.5  |   |   |
|          |T53W       |83          |96.85.0.5  |   |   |
|          |T54W       |83          |96.85.0.5  |   |   |
|          |T57W       |83          |96.85.0.5  |   |   |
|          |T21P       |83          |52.84.0.140|   |   |
|          |T23G       |83          |44.84.0.140|   |   |
|          |T27G       |83          |69.85.0.5  |   |   |
|          |T29G       |83          |46.83.0.130|   |   |
|          |T30        |83          |124.85.0.40|   |   |
|          |T30P       |83          |124.85.0.40|   |   |
|          |T31G       |83          |124.85.0.40|   |   |
|          |T33G       |83          |124.85.0.40|   |   |
|          |T40G       |83          |76.84.0.125|   |   |
|          |T41P       |83          |36.83.0.120|   |   |
|          |T46G       |83          |28.83.0.130|   |   |
|**AudioCodes**|       |            |           |Some AudioCodes SIP devices need a provisioning URL setting. Download and install upgrade files for the affected AudioCodes devices at the right. |[Downloadable files for affected devices at AudioCodes](https://audiocodes.sharefile.com/share/view/sc9cdf17f9ec45d09/fo7914a2-4f3a-4000-8957-47bd6f35a3a5)|
|          |405         |2.2.8      |2.2.16.570 |   |   |
|          |405HD       |3.2.1      |2.2.16.570 |   |   |
|          |420HD       |3.2.1      |2.2.16.570 |   |   |
|          |430HD       |3.2.1      |2.2.16.570 |   |   |
|          |440HD       |3.2.1      |2.2.16.570 |   |   |
|          |450HD       |3.2.1      |3.4.6.687  |   |   |
|          |C450HD      |3.2.1      |3.4.6.687  |   |   |
|          |445HD       |3.2.1      |3.4.6.687  |   |   |
|          |RX50        |3.2.1      |3.4.6.687  |   |   |

> [!NOTE]
> For some devices, the minimum firmware version is greater than the approved firmware version. This is because the 3.X version is the Skype for Business version. We update the SIP version which is 2.X.
