---
title: Plan SIP Gateway
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.date: 07/15/2024
ms.reviewer: chasing
ms.topic: article
audience: Admin
ms.service: msteams
ms.subservice: itpro-rooms
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - M365-voice
  - Tier1
search.appverid: MET150
f1.keywords:
- NOCSH
- ms.teamsadmincenter.directrouting.overview
description: Learn more about SIP Gateway, such as requirements and benefits.
ms.custom:
 - seo-marvel-apr2020
 - seo-marvel-jun2020
---

# Plan for SIP Gateway

SIP Gateway lets your organization use any compatible SIP device with Microsoft Teams to preserve your investments in SIP devices. Now you can sign-in to Teams with your corporate credentials and make and receive calls with a compatible SIP device. Compatible devices can be Skype for Business IP phones with standard SIP firmware, Cisco IP phones with multiplatform SIP firmware, or SIP devices from vendors such as Poly, Yealink, and AudioCodes. To find out how to configure your SIP devices for SIP Gateway, see [Configure SIP Gateway](sip-gateway-configure.md).

## Benefits of SIP Gateway

A SIP gateway lets compatible SIP devices connect seamlessly to Teams for calling features and lets them do the  following:

- **Make calls:** SIP device users can make calls to the Public Switched Telephone Network (PSTN), to other SIP devices, and to Teams and Skype for Business users. SIP device users can only call users who have phone numbers.
- **Receive calls:** SIP device users can receive a call from the PSTN, from other Teams or Skype for Business users who have SIP devices, and from Teams and Skype for Business applications. The SIP device acts as a Teams endpoint. Inbound calls will be received on the user's SIP device.
- **Multiple simultaneous calls:** A SIP device user in a call can put the call on hold to make or receive other calls. A SIP device user can also conference two calls.
- **Hold/Resume and Mute/Unmute:** A SIP device user can hold and resume or mute and unmute a call by using the features for those actions on the device.
- **Voicemail:** SIP device users can listen to electronically stored voice messages that callers leave for them.
- **Message waiting indicator:** SIP device users can receive notifications that alert them when they have new voicemail messages.
- **Sign-in and sign-out:** SIP devices users can sign in and sign out of Teams on the device.
- **Dual-tone multi-frequency:** SIP device users can press number keys to provide input during interactive voice response calls.
- **Teams meetings:** A user's SIP device can join Teams meetings by dialing into the meeting using a phone number. A meeting participant can add an internal and external guest to a meeting by dialing out to user's phone number or can add them by using the 'Request to Join' button.
- **Call transfers:** SIP device users can transfer calls. SIP Gateway supports both blind and consultative transfers.
- **Local call forwarding:** A user can set forwarding rules (always, on timeout, and busy) for the device. If the device is connected to the SIP Gateway, then the call will be sent to the calls endpoint based on the rule that the user has set. To make local call forwarding work, the admin must set the `AllowCallRedirect` attribute in `Set-CsTeamsCallingPolicy` to `Enabled`.
- **Off board stale devices:** A SIP gateway supports auto offboarding of stale devices provisioned for a tenant. Paired (signed-in) devices will be off boarded if not connected for 30 days, and unpaired (signed-out) devices after 14 days. A device that has been off boarded can be onboarded again after a factory reset.
- **Set DND from SIP devices:** You can use your SIP device for setting and fetching your Teams Do Not Disturb (DND) status. To set the DND status for your Teams account from your SIP device, dial the feature code \*30\* on the SIP device. To reset your Teams DND status, dial \*31\* from the SIP device. Dialing \*31\* clears the user-configured presence status, in this case DND.
- **Call Queues and voice apps support:** Customers can use SIP devices as call queue agents with some restrictions, for instance, SIP Gateway doesn't publish presence for devices hence presence based routing isn't supported.

## Requirements to use SIP Gateway

Teams users must have a phone number with PSTN calling enabled to use SIP Gateway.

> [!NOTE]
> SIP Gateway is now available for government community cloud (GCC) environment. It isn't yet available for GCC High and DoD.

>[!note]
>SIP Gateway Feature Codes:
> DND -
> \*30\* (Set DND From SIP Device)
> \*31\* (Reset Teams DND Status from SIP Device)
> Call Forwarding - (https://support.microsoft.com/en-us/office/call-forwarding-call-groups-and-simultaneous-ring-in-microsoft-teams-a88da9e8-1343-4d3c-9bda-4b9615e4183e)
> \*32\* - Reset Call Forwarding Status
> \*33\* (Set "Call Forwarded To" Number)
> \*34\* (Set "Forward on Timeout")
> \*35\* (Setup Simultaneous Ring)
> Device Validation -
> \*55\* - OTP validation from devices provisioned through Teams Admin Center
> Voicemail -
> \*99\* - Check voicemail

### Hardware, software, and licenses

If you have a 3PIP or SIP device, you must have the following:

- [Microsoft Teams](https://www.microsoft.com/microsoft-teams/group-chat-software)
- Skype for Business Online (Plan 2)
  - *Skype for Business Online (Plan 2)* isn't a standalone license that can be purchased.
- [Microsoft Phone System](what-is-phone-system-in-office-365.md)
- [PSTN Connectivity](pstn-connectivity.md)

## Compatible devices

|Vendor    |Model      |Minimum firmware version|Approved firmware version|Remarks|Links|
|----------|-----------|------------|-----------|------------|------------|
|**Cisco** |           |            |           |Devices running enterprise firmware must be converted to multiplatform firmware. Read the guide at the right to learn how.|[Cisco firmware conversion guide](https://www.cisco.com/c/en/us/products/collateral/collaboration-endpoints/unified-ip-phone-7800-series/guide-c07-742786.html)|
|          |8832<sup>1</sup>       |11.3.5MPP   |12-0-3MPP  |   |   |
|          |6821<sup>1</sup>       |11.1.1MPP   |12-0-3MPP  |   |   |
|          |6841<sup>1</sup>       |11.1.1MPP   |12-0-3MPP  |   |   |
|          |6851<sup>1</sup>       |11.1.1MPP   |12-0-3MPP  |   |   |
|          |6861<sup>1</sup>       |11.1.1MPP   |12-0-3MPP  |   |   |
|          |6871<sup>1</sup>       |11.1.1MPP   |12-0-3MPP  |   |   |
|          |7811<sup>1</sup>       |11.1.1MPP   |12-0-3MPP  |   |   |
|          |7821<sup>1</sup>       |11.1.1MPP   |12-0-3MPP  |   |   |
|          |7841<sup>1</sup>       |11.1.1MPP   |12-0-3MPP  |   |   |
|          |7861<sup>1</sup>       |11.1.1MPP   |12-0-3MPP  |   |   |
|          |8811<sup>1</sup>       |11.1.1MPP   |12-0-3MPP  |   |   |
|          |8841<sup>1</sup>       |11.1.1MPP   |12-0-3MPP  |   |   |
|          |8845<sup>1</sup>       |11.1.1MPP   |12-0-3MPP  |   |   |
|          |8851<sup>1</sup>       |11.1.1MPP   |12-0-3MPP  |   |   |
|          |8861<sup>1</sup>       |11.1.1MPP   |12-0-3MPP  |   |   |
|          |8865<sup>1</sup>       |11.1.1MPP   |12-0-3MPP  |   |   |
|          |ATA191-MPP<sup>3</sup>       |11.2.2MPP   |11-2-2MPP0101-013  |   |   |
|          |ATA192-MPP<sup>3</sup>       |11.2.2MPP   |11-2-2MPP0101-013  |   |   |
|**Poly**  |           |            |           |The device will auto reboot and install the selected firmware.|[Poly Lens Provisioning Guide](https://info.lens.poly.com/docs/category/lens-assisted-provisioning)|
|          |Trio 8500<sup>2</sup> |5.9.5.3182  |7.2.4.0185 |   |   |
|          |Trio 8800<sup>2</sup> |5.9.5.3182  |7.2.4.0185 |   |   |
|          |VVX150<sup>2</sup>    |5.9.5       |6.4.3.5814 |   |   |
|          |VVX201<sup>2</sup>    |5.9.5       |6.4.3.5814 |   |   |
|          |VVX250<sup>2</sup>    |5.9.5       |6.4.3.5814 |   |   |
|          |VVX300<sup>3</sup>     |5.9.5       |5.9.7.3480 |   |   |
|          |VVX301<sup>2</sup>    |5.9.5       |6.4.3.5814 |   |   |
|          |VVX310<sup>3</sup>     |5.9.5       |5.9.7.3480 |   |   |
|          |VVX311<sup>2</sup>    |5.9.5       |6.4.3.5814 |   |   |
|          |VVX350<sup>2</sup>    |5.9.5       |6.4.3.5814 |   |   |
|          |VVX400<sup>3</sup>     |5.9.5       |5.9.7.3480 |   |   |
|          |VVX401<sup>2</sup>    |5.9.5       |6.4.3.5814 |   |   |
|          |VVX410<sup>3</sup>     |5.9.5       |5.9.7.3480 |   |   |
|          |VVX411<sup>2</sup>    |5.9.5       |6.4.3.5814 |   |   |
|          |VVX450<sup>2</sup>    |5.9.5       |6.4.3.5814 |   |   |
|          |VVX500<sup>3</sup>     |5.9.5       |5.9.7.3480 |   |   |
|          |VVX501<sup>2</sup>    |5.9.5       |6.4.3.5814 |   |   |
|          |VVX600<sup>3</sup>     |5.9.5       |5.9.7.3480 |   |   |
|          |VVX601<sup>2</sup>    |5.9.5       |6.4.3.5814 |   |   |
|          |Rove B1<sup>1</sup>    |8.0.5.0002  |8.0.5.0002 |   |   |
|          |Rove B2<sup>1</sup>    |8.0.5.0002  |8.0.5.0002 |   |   |
|          |Rove B4<sup>1</sup>    |8.0.5.0002  |8.0.5.0002 |   |   |
|          |Rove 20<sup>1</sup>    |8.0.5.0003  |8.0.5.0003 |   |   |
|          |Rove 30<sup>1</sup>    |8.0.5.0002  |8.0.5.0002 |   |   |
|          |Rove 40<sup>1</sup>    |8.0.5.0002  |8.0.5.0002 |   |   |
|          |Edge E100<sup>2</sup>  |8.1.0.12774  |8.1.0.12774 |   |   |
|          |Edge E220<sup>2</sup>  |8.1.0.12774  |8.1.0.12774 |   |   |
|          |Edge E300<sup>2</sup>  |8.1.0.12774  |8.1.0.12774 |   |   |
|          |Edge E320<sup>2</sup>  |8.1.0.12774  |8.1.0.12774 |   |   |
|          |Edge E350<sup>2</sup>  |8.1.0.12774  |8.1.0.12774 |   |   |
|          |Edge E400<sup>2</sup>  |8.1.0.12774  |8.1.0.12774 |   |   |
|          |Edge E450<sup>2</sup>  |8.1.0.12774  |8.1.0.12774 |   |   |
|          |Edge E500<sup>2</sup>  |8.1.0.12774  |8.1.0.12774 |   |   |
|          |Edge E550<sup>2</sup>  |8.1.0.12774  |8.1.0.12774 |   |   |
|          |ATA 400<sup>3</sup>  |4.0.1.6480     |4.0.1.6480  |   |[Poly ATA 400 Series Configuration Guide](https://kaas.hpcloud.hp.com/pdf-public/pdf_10029605_en-US-1.pdf)|
|          |ATA 402<sup>3</sup>  |4.0.1.6480     |4.0.1.6480  |   |   |
|          |OBi 300<sup>3</sup>  |3.2.4.8441     |3.2.5.8732  |   |   |
|          |OBi 302<sup>3</sup>  |3.2.4.8441     |3.2.5.8732  |   |   |
|**Yealink**|          |            |           |   |[Yealink support](https://www.yealink.com)|
|          |T21P<sup>3</sup>       |83          |34.72.0.75 |   |   |
|          |T21P_E2<sup>3</sup>    |83          |52.84.0.125|   |   |
|          |T23G<sup>3</sup>       |83          |44.84.0.140|   |   |
|          |T27G<sup>1</sup>      |83          |69.86.0.15 |   |   |
|          |T29G<sup>3</sup>       |83          |46.83.0.130|   |   |
|          |T30<sup>1</sup>       |83          |124.86.0.147|   |   |
|          |T30P<sup>1</sup>      |83          |124.86.0.147|   |   |
|          |T31G<sup>1</sup>      |83          |124.86.0.147|   |   |
|          |T31P<sup>1</sup>      |83          |124.86.0.147|   |   |
|          |T33G<sup>1</sup>      |83          |124.86.0.147|   |   |
|          |T40G<sup>3</sup>       |83          |76.84.0.125|   |   |
|          |T40P<sup>3</sup>       |83          |54.84.0.125|   |   |
|          |T41P<sup>3</sup>       |83          |36.83.0.120|   |   |
|          |T41S<sup>2</sup>      |83          |66.86.5.1  |   |   |
|          |T42G<sup>3</sup>       |83          |29.83.0.130|   |   |
|          |T42S<sup>2</sup>      |83          |66.86.5.1  |   |   |
|          |T42U<sup>2</sup>      |83          |108.86.5.1 |   |   |
|          |T43U<sup>2</sup>      |83          |108.86.5.1 |   |   |
|          |T46G<sup>3</sup>       |83          |28.83.0.130|   |   |
|          |T46S<sup>2</sup>      |83          |66.86.5.1  |   |   |
|          |T46U<sup>2</sup>      |83          |108.86.5.1 |   |   |
|          |T48G<sup>3</sup>       |83          |35.83.0.130|   |   |
|          |T48S<sup>2</sup>      |83          |66.86.5.1  |   |   |
|          |T48U<sup>2</sup>      |83          |108.86.5.1 |   |   |
|          |T53<sup>2</sup>       |83          |96.86.5.1  |   |   |
|          |T53W<sup>2</sup>      |83          |96.86.5.1  |   |   |
|          |T54W<sup>2</sup>      |83          |96.86.5.1  |   |   |
|          |T57W<sup>2</sup>      |83          |96.86.5.1  |   |   |
|          |W56H<sup>3</sup>                  |            |61.85.0.56 |   |   |
|          |W73H<sup>3</sup>                  |            |116.85.0.38|   |   |
|          |W57R<sup>3</sup>                  |            |118.85.0.27|   |   |
|          |W59R<sup>3</sup>                  |            |115.85.0.56|   |   |
|          |W70B NOAM<sup>3</sup>             |            |146.85.5.4 |   |   |
|          |W70B EMEA<sup>3</sup>             |            |146.85.5.2 |   |   |
|          |W70B APAC<sup>3</sup>             |            |146.85.5.3 |   |   |
|          |W80 NOAM<sup>3</sup>              |            |130.85.5.5 |   |   |
|          |W80 EMEA<sup>3</sup>              |            |130.85.5.6 |   |   |
|          |W80 APAC<sup>3</sup>              |            |130.85.5.4 |   |   |
|          |W90 NOAM<sup>3</sup>              |            |130.85.5.5 |   |   |
|          |W90 EMEA<sup>3</sup>              |            |130.85.5.6 |   |   |
|          |W90 APAC<sup>3</sup>              |            |130.85.5.4 |   |   |
|**AudioCodes**|       |            |           |Some AudioCodes SIP devices need a provisioning URL setting. Download and install upgrade files for the affected AudioCodes devices at the right. |[Downloadable files for affected devices at AudioCodes](https://audiocodes.sharefile.com/share/view/sc9cdf17f9ec45d09/fo7914a2-4f3a-4000-8957-47bd6f35a3a5)|
|          |405<sup>1</sup>        |2.2.8      |2.2.16.681 |   |   |
|          |405HD<sup>1</sup>      |3.2.1      |2.2.16.681 |   |   |
|          |405HDG<sup>1</sup>     |3.2.1      |2.2.16.681 |   |   |
|          |420HD<sup>1</sup>      |3.2.1      |2.2.16.681 |   |   |
|          |420HDG<sup>1</sup>     |3.2.1      |2.2.16.681 |   |   |
|          |430HD<sup>1</sup>      |3.2.1      |2.2.16.681 |   |   |
|          |430HDG<sup>1</sup>     |3.2.1      |2.2.16.681 |   |   |
|          |440HD<sup>1</sup>      |3.2.1      |2.2.16.681 |   |   |
|          |445HD<sup>2</sup>      |3.2.1      |3.4.8.808 |   |   |
|          |445HDG<sup>2</sup>     |3.2.1      |3.4.8.808 |   |   |
|          |450HD<sup>2</sup>      |3.2.1      |3.4.8.808 |   |   |
|          |C450HD<sup>2</sup>     |3.2.1      |3.4.8.808 |   |   |
|          |C448HD<sup>2</sup>                 |3.2.1      |3.4.8.808 |   |   |
|          |445HD<sup>2</sup>      |3.2.1      |3.4.8.808 |   |   |
|          |RX50<sup>2</sup>       |3.2.1      |3.4.8.808 |   |   |
|          |MP112<sup>3</sup>                  |6.60A.367.001      |6.60A.367.005  |ATA   | All ports available [AudioCodes ATA Setup Guide](https://www.audiocodes.com/media/pafhki3d/onboarding-audiocodes-ata-to-microsoft-sip-gateway-for-teams.pdf)  |
|          |MP114-FXS<sup>3</sup>              |6.60A.367.001      |6.60A.367.005  |ATA   | 3 out of 4 ports available   |
|          |MP114-FXS-FXO<sup>3</sup>          |6.60A.367.001      |6.60A.367.005  |ATA   | 3 out of 4 ports available   |
|          |MP118-FXS<sup>3</sup>              |6.60A.367.001      |6.60A.367.005  |ATA   | 6 out of 8 ports available  |
|          |MP118-FXS-FXO<sup>3</sup>          |6.60A.367.001      |6.60A.367.005  |ATA   | 6 out of 8 ports available  |
|          |MP124-FXS<sup>3</sup>              |6.60A.367.001      |6.60A.367.005  |ATA   | 18 out of 24 ports available  |
|          |MP1288-FXS<sup>3</sup>             |7.40A.400.063      |7.40A.600.014  |ATA   | All ports available  |
|          |MP502<sup>3</sup>                  |7.26A.356.075      |7.26A.356.773  |ATA   | All ports available  |
|          |MP504<sup>3</sup>                  |7.26A.356.075      |7.26A.356.773  |ATA   | All ports available  |
|          |MP508<sup>3</sup>                  |7.26A.356.075      |7.26A.356.773  |ATA   | All ports available  |
|          |MP516<sup>3</sup>                  |7.26A.356.075      |7.26A.356.773  |ATA   | All ports available  |
|          |MP524<sup>3</sup>                  |7.26A.356.075      |7.26A.356.773  |ATA   | All ports available  |
|          |MP532<sup>3</sup>                  |7.26A.356.075      |7.26A.356.773  |ATA   | All ports available  |
|**Spectralink**|       |           |           |   |[Spectralink Support](https://support.spectralink.com)|
|          |7202<sup>3</sup>        |PCS22B     |PCS22D     |Handset |   |
|          |7212<sup>3</sup>        |PCS22B     |PCS22D     |Handset |   |
|          |7502<sup>3</sup>        |PCS22B     |PCS22D     |Handset |   |
|          |7522<sup>3</sup>        |PCS22B     |PCS22D     |Handset |   |
|          |7532<sup>3</sup>        |PCS22B     |PCS22D     |Handset |   |
|          |7622<sup>3</sup>        |PCS22B     |PCS22D     |Handset |   |
|          |7642<sup>3</sup>        |PCS22B     |PCS22D     |Handset |   |
|          |7722<sup>3</sup>        |PCS22B     |PCS22D     |Handset |   |
|          |7742<sup>3</sup>        |PCS22B     |PCS22D     |Handset |   |
|          |S33<sup>3</sup>         |PCS23Ca    |PCS24G    |Handset |   |
|          |S35<sup>3</sup>         |PCS23Ca    |PCS24G    |Handset |   |
|          |S37<sup>3</sup>         |PCS23Ca    |PCS24G    |Handset |   |
|          |IP-DECT Server 400<sup>3</sup> |PCS22Ab |PCS24B |IP-DECT Server |   |
|          |IP-DECT Server 6500<sup>3</sup> |PCS22Ab |PCS24B|IP-DECT Server |   |
|          |Virtual IP-DECT Server One<sup>3</sup> |PCS22Ab |PCS24B |IP-DECT Server |   |
|          |IP-DECT Base Station<sup>3</sup> |PCS22Ab |PCS24B |IP-DECT Base Station|   |
|          |RFP6 TDM Digital Base Station<sup>3</sup> |PCS16E_ |PCS16E_ |DECT Base Station |   |
|          |IP-DECT Gateway<sup>3</sup> |PCS24Ab |PCS24B |IP-DECT Gateway |   |
|**Ascom**|       |           |           |   |[Ascom Support](https://www.ascom.com/products-and-services/services/support-and-maintenance/)|
|          |Ascom d43<sup>3</sup>        |2.11.4     |3.0.8     |Handset |   |
|          |Ascom d63<sup>3</sup>        |2.11.4     |3.0.8     |Handset |   |
|          |Ascom d81<sup>3</sup>        |4.13.1     |4.17.3     |Handset |   |
|          |Ascom d83<sup>3</sup>        |1.3.2     |1.5.5     |Handset |   |
|          |Ascom i63<sup>3</sup>        |5.0.1     |5.0.1     |VoWiFi Handset |   |
|          |Ascom Myco 3 DECT<sup>3</sup>        |3.4.1     |3.4.1     |Wireless Handset |   |
|          |IP-DECT Access Point IPBSx<sup>3</sup>        |11.8.8     |11.9.11     |IP-DECT Access Point |   |
|          |IP-DECT Gateway IPBL<sup>3</sup>     |11.8.8     |11.9.11     |IP-DECT Gateway |   |
|          |TDM Base Station<sup>3</sup>        |R3N     |R4B     |IP-DECT Base Station |   |
|          |IP-DECT Virtual Appliance IPVM<sup>3</sup>        |11.8.8     |11.9.11     |IP-DECT Server|   |
|**Gigaset**|       |           |           |   |[Gigaset Support](https://www.gigaset.com/en_en/cms/home/support/support.html)|
|          |N610 IP PRO<sup>3</sup>        |2.52.0     |2.52.0     |Base Station |   |
|          |N670 IP PRO<sup>3</sup>        |2.52.0     |2.52.0     |Base Station |   |
|          |N870 IP PRO<sup>3</sup>        |2.52.0     |2.52.0     |Base Station |   |
|          |N870E IP PRO<sup>3</sup>        |2.52.0     |2.52.0     |Base Station |   |
|          |N870 VI PRO<sup>3</sup>        |2.52.0     |2.52.0     |Base Station |   |
|**Algo**|       |           |           |   |[Algo Support](https://www.algosolutions.com/post-sale-technical-support/)|
|          |8180g2<sup>3</sup>        |5.3     |5.3     |Speaker |   |
|          |8186<sup>3</sup>          |5.3     |5.3     |Speaker |   |
|          |8188<sup>3</sup>          |5.3     |5.3     |Speaker |   |
|          |8189<sup>3</sup>          |5.3     |5.3     |Speaker |   |
|          |8190<sup>3</sup>          |5.3     |5.3     |Speaker |   |
|          |8190s<sup>3</sup>         |5.3     |5.3     |Speaker |   |
|          |8196<sup>3</sup>          |5.3     |5.3     |Speaker |   |
|          |8198<sup>3</sup>          |5.3     |5.3     |Speaker |   |
|          |8028g2<sup>3</sup>        |5.3     |5.3     |Intercom|   |
|          |8063<sup>3</sup>          |5.3     |5.3     |Intercom|   |
|          |8201<sup>3</sup>          |5.3     |5.3     |Intercom|   |
|          |8203<sup>3</sup>          |5.4     |5.4     |Intercom|   |
|          |8128g2<sup>3</sup>        |5.3     |5.3     |Visual Alerter |   |
|          |8138<sup>3</sup>          |5.3     |5.3     |Visual Alerter |   |
|          |8301<sup>3</sup>          |5.3     |5.3     |Paging Adapter |   |
|          |8373<sup>3</sup>          |5.3     |5.3     |Paging Adapter |   |
|          |8305<sup>3</sup>          |5.4     |5.4     |Paging Adapter |   |
|          |8410<sup>3</sup>          |5.3     |5.3     |Display Speaker |   |
|          |8420<sup>3</sup>          |5.3     |5.3     |Display Speaker |   |
|**Alcatel-Lucent Enterprise**|       |     |              |                |   |
|          |M3<sup>3</sup>          |2.14.03.000.2345     |2.14.03.000.2345 |   |   |
|          |M5<sup>3</sup>          |2.14.03.000.2345     |2.14.03.000.2345 |   |   |
|          |M7<sup>3</sup>          |2.14.03.000.2345     |2.14.03.000.2345 |   |   |
|          |M8<sup>3</sup>          |2.14.05.000.2352     |2.14.05.000.2352 |   |   |
|**Snom**|       |     |              |                |   |
|          |D717<sup>3</sup>          |10.1.141.13     |10.1.141.13 |IP Phone   |   |
|          |D735<sup>3</sup>          |10.1.141.13     |10.1.141.13 |IP Phone   |   |

<sup>1</sup> Device supports dynamic location discovery through LLDP with SIP Gateway.

<sup>2</sup> Device supports dynamic location discovery with SIP Gateway.

<sup>3</sup> Device supports only static location with SIP Gateway.

> [!NOTE]
> For Poly devices, LLDP must be turned on at switch level for subnet length based dynamic location discovery.

> [!NOTE]
> Compatible Cisco SIP IP phones support dynamic location discovery over LLDP only.

> [!NOTE]
> Customers can use AudioCodes OVOC and Poly Lens to manage device side configuration of their AudioCodes 400 series and Poly VVX/Trio devices respectively.

> [!NOTE]
> Spectralink Handsets receive firmware updates over the air from Spectralink IP-DECT servers.

> [!NOTE]
> Ascom Handsets receive firmware updates over the air from Ascom IP-DECT servers.

> [!NOTE]
> Gigaset Handsets receive firmware updates over the air from Gigaset IP-DECT servers. All Gigaset PRO DECT Handset models are compatible with Microsoft Teams SIP Gateway.

> [!NOTE]
> For Yealink DECT Base Stations, please use the appropriate region specific firmware version from the list to have the best calling experience.

> [!NOTE]
> For support queries, customers using IP-DECT systems with Teams SIP Gateway should reach out to their DECT manufacturer or their implementation channel partners.

> [!NOTE]
> For some devices, the minimum firmware version is greater than the approved firmware version. This is because the 3.X version is the Skype for Business version. We update the SIP version which is 2.X.

> [!NOTE]
> For support queries, customers using the Algo Solutions' SIP enabled endpoints listed with Teams SIP Gateway should reach out directly to Algo Solutions.
> [General Information on Algo integration with Teams](https://www.algosolutions.com/solutions/compatibility/msteams/)
> [Configuration Guide](https://www.algosolutions.com/wp-content/uploads/2023/04/Configuration-Guide-Teams-2023.pdf)
> [Troubleshooting Guide](https://www.algosolutions.com/wp-content/uploads/2023/07/Troubleshooting-Algo-Devices-in-MS-Teams.pdf)

> [!NOTE]
> Customers should contact their Tango Extend Reseller for support queries related to Tango Extend eSIM endpoints. Help and Support information are provided in the Tango Extend Teams App.
>
> **Emergency Calling** - Emergency calling is supported from the Tango Extend eSIM and this uses the Teams number. Teams isn't notified of emergency calls made from the eSIM but will receive returned calls towards the Teams number.
>
> **Tango Extend Supported Features** - Sign-in/out using Tango Extend Teams App with Teams policy sync, Make/receive calls with hold/resume and DTMF, dial-in to meeting, request to join, voicemail and MWI, Teams DND and Call Forwarding.
>
> **Currently Unsupported Features** - Sign-out / sign-in currently creates redundant (signed out) entries for the eSIM endpoint in Teams Admin Center.
> Remote Sign-in from TAC is currently not supported by Tango Extend.
> Teams mobile client – If users have both Tango Extend eSIM and Teams mobile client on their phones, then inbound calls will prioritize the Teams mobile client.
> Call transfer – where presented by mobile dialler menu option this isn't supported by Tango Extend.
