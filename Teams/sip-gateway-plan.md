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

SIP Gateway lets your organization use any compatible SIP phone with Microsoft Teams to preserve your investments in SIP phones. Now you can sign-in to Teams with your corporate credentials and make and receive calls with a compatible SIP phone. Compatible phones can be Skype for Business IP phones with standard SIP firmware, Cisco IP phones with multiplatform SIP firmware, or SIP phones from vendors such as Poly, Yealink, and AudioCodes. To find out how to configure your SIP devices for SIP Gateway, see [Configure SIP Gateway](sip-gateway-configure.md)

## Benefits of SIP Gateway

SIP Gateway connects compatible SIP phones not certified by Microsoft Teams to Teams to help your users migrate seamlessly to Teams telephony. Using SIP Gateway, your users can do all of the following:

- **Make calls:** SIP phone users can make calls to the PSTN, to other SIP phones, and to Teams and Skype for Business users. SIP phone users can only call users who have phone numbers.
- **Receive calls:** SIP phone users can receive a call from the PSTN, from Teams or Skype for Business users who have SIP phones, and from Teams and Skype for Business client applications. The SIP phone acts as a Teams endpoint. Inbound calls will also be forked to the user’s SIP device.
- **Multiple simultaneous calls:** A SIP phone user in a call can put the call on hold to make or receive other calls. A SIP phone user can also conference two calls.
- **Do not disturb:** A SIP phone user can set do not disturb on the phone so that the phone will not ring for incoming calls. This has no impact on the user’s status on all other Teams endpoints.
- **Hold/Mute and Mute/Unmute:** **[How?]**
- **DTMF:** **[What is this?]**
- **Teams meetings:** A SIP phone user can join a Teams meeting by dialing the meeting access number. Dialing out to a same tenant **[do we need to explain that?]** user’s phone number is not supported. However, guest users from another tenant can be added to a Teams meeting by a participant who dials out to a guest user’s number to include that guest. **Note:** Adding a Teams meeting participant via “request to join” won’t alert a SIP device during the preview period.
- **Blind transfer:** SIP phone users can transfer calls. Only single-step/blind transfers **[What are those?]** are supported during the preview period. Consulted transfers **[What's this?]** will be added at General Availability.
- **Local call forwarding:** A SIP phone user can set forwarding rules (always, on timeout, and busy) for the phone. If the phone is connected to the SIP Gateway, then the call will be redirected to the target address based on the rule that the phone user set.

For more information about what you can do with SIP devices, see [?](https://www.whatarticle?)


## Requirements to use SIP Gateway

Teams users must have an phone number with PTSN calling enabled to use SIP Gateway.

### Hardware, software, and licenses

If you have a 3PIP or SIP phone, you must have: 
- An Office 365 E5 plan, or
- An Office 365 E3 or Office 365 E1 plan plus a Phone System license. 

You must also have PSTN capability through a Microsoft Calling Plan, Direct Routing, or Operator Connect. Any Common-area devices you use must have a Common Area Phone license.

### Policy requirements

TBD

## Devices supported by SIP Gateway

|Vendor	   |Model      |Minimum firmware version|Approved firmware version|Remarks|Links|
|----------|-----------|------------|-----------|------------|------------|
|**Cisco** |           |            |           |Phones running enterprise firmware must be converted to multiplatform firmware. Read the guide at the right to learn how.|[Cisco firmware conversion guide](https://www.cisco.com/c/en/us/products/collateral/collaboration-endpoints/unified-ip-phone-7800-series/guide-c07-742786.html)|
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
|**Poly**  |           |            |           |The phone will auto-reboot and install the selected firmware.|   |
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
|          |T41S       |83          |66.85.0.5  |   |   |
|          |T42G       |83          |29.83.0.130|   |   |
|          |T42S       |83          |66.85.0.5  |   |   |
|          |T46S       |83          |66.85.0.5  |   |   |
|          |T48S       |83          |66.85.0.5  |   |   |
|          |T48G       |83          |35.83.0.130|   |   |
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
|**AudioCodes**|       |            |           |Download and install a file for any AudioCodes Skype for Business phone at the URL at the right. |[Downloadable files for affected devices at AudioCodes](https://audiocodes.sharefile.com/share/view/sc9cdf17f9ec45d09/fo19ecda-cf14-4a53-842b-5eab33a0b9b0)|
|          |405         |2.2.8      |2.2.16.525 |   |   |
|          |405HD       |3.2.1      |2.2.16.525 |   |   |
|          |420HD       |3.2.1      |2.2.16.525 |   |   |
|          |430HD       |3.2.1      |2.2.16.525 |   |   |
|          |440HD       |3.2.1      |2.2.16.525 |   |   |
|          |450HD       |3.2.1      |3.4.6.558  |   |   |
|          |C450HD      |3.2.1      |3.4.6.558  |   |   |
|          |445HD       |3.2.1      |3.4.6.558  |   |   |
