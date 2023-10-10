---
title: Plan SIP Gateway
author: tonysmit
ms.author: tonysmit
manager: serdars
ms.date: 08/22/2023
ms.topic: article
ms.service: msteams
audience: admin
ms.collection:
  - teams-rooms-devices
  - highpri
  - Tier1
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
- **Hold/Resume and Mute/Unmute:** A SIP device user can hold and resume or mute and unmute a call by using the features for those actions on the device.
- **Voicemail:** SIP device users can listen to electronically stored voice messages that callers leave for them.
- **Message waiting indicator:** SIP device users can receive notifications that alert them when they have new voicemail messages.
- **Sign-in and sign-out:** SIP devices users can sign in and sign out of Teams on the device.
- **Dual-tone multi-frequency:** SIP device users can press number keys to provide input during interactive voice response calls.
- **Teams meetings:** A SIP device user can join a Teams meeting by dialing the meeting access number. Meeting participants can add a SIP device user to the meeting by dialing out to user's phone number or simply adding a participant by clicking on 'Request to Join' will also alert the user's SIP device. Guest users from another organization can be added to a Teams meeting by a participant who dials out to a guest user's number to include that guest.
- **Call transfers:** SIP device users can transfer calls. SIP Gateway supports both blind and consultative transfers.
- **Local call forwarding:** A SIP device user can set forwarding rules (always, on timeout, and busy) for the device. If the device is connected to the SIP Gateway, then the call will be redirected to the target address based on the rule that the device user set. To make local call forwarding work, the admin must set the `AllowCallRedirect` attribute in `Set-CsTeamsCallingPolicy` to `Enabled`.
- **Offboard stale devices:** SIP Gateway supports auto offboarding of stale devices provisioned for a tenant. Paired (signed-in) devices will be offboarded if not connected for 30 days, and unpaired (signed-out) devices after 14 days. An offboarded device can be re-onboarded after a factory reset.
- **Set DND from SIP devices:** You can use your SIP device for setting and fetching your Teams Do Not Disturb (DND) status. To set the DND status for your Teams account from your SIP device, dial the feature code \*30\* on the SIP device. To reset your Teams DND status, dial \*31\* from the SIP device. Dialing \*31\* clears the user-configured presence status, in this case DND.
- **Call Queues and voice apps support:** Customers can use SIP devices as call queue agents with some restrictions, for instance, SIP Gateway doesn't publish presence for devices hence presence based routing is not supported.

## Requirements to use SIP Gateway

Teams users must have a phone number with PSTN calling enabled to use SIP Gateway.

> [!NOTE]
> SIP Gateway is now available for government community cloud (GCC) environment. It is not yet available for GCC High and DoD.

### Hardware, software, and licenses

If you have a 3PIP or SIP device, you must have the following:

- [Microsoft Teams](https://www.microsoft.com/en-us/microsoft-teams/group-chat-software)
- Skype for Business Online (Plan 2)
  - *Skype for Business Online (Plan 2)* isn't a standalone license that can be purchased.
- [Microsoft Phone System](what-is-phone-system-in-office-365.md)
- [PSTN Connectivity](pstn-connectivity.md)

## Compatible devices

|Vendor    |Model      |Minimum firmware version|Approved firmware version|Remarks|Links|
|----------|-----------|------------|-----------|------------|------------|
|**Cisco** |           |            |           |Devices running enterprise firmware must be converted to multiplatform firmware. Read the guide at the right to learn how.|[Cisco firmware conversion guide](https://www.cisco.com/c/en/us/products/collateral/collaboration-endpoints/unified-ip-phone-7800-series/guide-c07-742786.html)|
|          |8832<sup>1</sup>       |11.3.5MPP   |12-0-1MPP  |   |   |
|          |6821<sup>1</sup>       |11.1.1MPP   |12-0-1MPP  |   |   |
|          |6841<sup>1</sup>       |11.1.1MPP   |12-0-1MPP  |   |   |
|          |6851<sup>1</sup>       |11.1.1MPP   |12-0-1MPP  |   |   |
|          |6861<sup>1</sup>       |11.1.1MPP   |12-0-1MPP  |   |   |
|          |6871<sup>1</sup>       |11.1.1MPP   |12-0-1MPP  |   |   |
|          |7811<sup>1</sup>       |11.1.1MPP   |12-0-1MPP  |   |   |
|          |7821<sup>1</sup>       |11.1.1MPP   |12-0-1MPP  |   |   |
|          |7841<sup>1</sup>       |11.1.1MPP   |12-0-1MPP  |   |   |
|          |7861<sup>1</sup>       |11.1.1MPP   |12-0-1MPP  |   |   |
|          |8811<sup>1</sup>       |11.1.1MPP   |12-0-1MPP  |   |   |
|          |8841<sup>1</sup>       |11.1.1MPP   |12-0-1MPP  |   |   |
|          |8845<sup>1</sup>       |11.1.1MPP   |12-0-1MPP  |   |   |
|          |8851<sup>1</sup>       |11.1.1MPP   |12-0-1MPP  |   |   |
|          |8861<sup>1</sup>       |11.1.1MPP   |12-0-1MPP  |   |   |
|          |8865<sup>1</sup>       |11.1.1MPP   |12-0-1MPP  |   |   |
|          |ATA191-MPP       |11.2.2MPP   |11-2-2MPP0101-013  |   |   |
|          |ATA192-MPP       |11.2.2MPP   |11-2-2MPP0101-013  |   |   |
|**Poly**  |           |            |           |The device will auto-reboot and install the selected firmware.|   |
|          |Trio 8500  |5.9.5.3182  |7.2.2.1094 |   |   |
|          |Trio 8800  |5.9.5.3182  |7.2.2.1094 |   |   |
|          |VVX150<sup>1</sup>    |5.9.5       |6.4.3.5814 |   |   |
|          |VVX201<sup>1</sup>    |5.9.5       |6.4.3.5814 |   |   |
|          |VVX250<sup>1</sup>    |5.9.5       |6.4.3.5814 |   |   |
|          |VVX300     |5.9.5       |5.9.7.3480 |   |   |
|          |VVX301<sup>1</sup>    |5.9.5       |6.4.3.5814 |   |   |
|          |VVX310     |5.9.5       |5.9.7.3480 |   |   |
|          |VVX311<sup>1</sup>    |5.9.5       |6.4.3.5814 |   |   |
|          |VVX350<sup>1</sup>    |5.9.5       |6.4.3.5814 |   |   |
|          |VVX400     |5.9.5       |5.9.7.3480 |   |   |
|          |VVX401<sup>1</sup>    |5.9.5       |6.4.3.5814 |   |   |
|          |VVX410     |5.9.5       |5.9.7.3480 |   |   |
|          |VVX411<sup>1</sup>    |5.9.5       |6.4.3.5814 |   |   |
|          |VVX450<sup>1</sup>    |5.9.5       |6.4.3.5814 |   |   |
|          |VVX500     |5.9.5       |5.9.7.3480 |   |   |
|          |VVX501<sup>1</sup>    |5.9.5       |6.4.3.5814 |   |   |
|          |VVX600     |5.9.5       |5.9.7.3480 |   |   |
|          |VVX601<sup>1</sup>    |5.9.5       |6.4.3.5814 |   |   |
|          |Rove B1    |8.0.5.0002  |8.0.5.0002 |   |   |
|          |Rove B2    |8.0.5.0002  |8.0.5.0002 |   |   |
|          |Rove B4    |8.0.5.0002  |8.0.5.0002 |   |   |
|          |Rove 20    |8.0.5.0003  |8.0.5.0003 |   |   |
|          |Rove 30    |8.0.5.0002  |8.0.5.0002 |   |   |
|          |Rove 40    |8.0.5.0002  |8.0.5.0002 |   |   |
|          |Edge E100  |8.1.0.12774  |8.1.0.12774 |   |   |
|          |Edge E220  |8.1.0.12774  |8.1.0.12774 |   |   |
|          |Edge E300  |8.1.0.12774  |8.1.0.12774 |   |   |
|          |Edge E320  |8.1.0.12774  |8.1.0.12774 |   |   |
|          |Edge E350  |8.1.0.12774  |8.1.0.12774 |   |   |
|          |Edge E400  |8.1.0.12774  |8.1.0.12774 |   |   |
|          |Edge E450  |8.1.0.12774  |8.1.0.12774 |   |   |
|          |Edge E500  |8.1.0.12774  |8.1.0.12774 |   |   |
|          |Edge E550  |8.1.0.12774  |8.1.0.12774 |   |   |
|          |OBi 300  |3.2.4.8441     |3.2.5.8732  |   |   |
|          |OBi 302  |3.2.4.8441     |3.2.5.8732  |   |   |
|**Yealink**|          |            |           |   |[Yealink support](https://support.yealink.com/)|
|          |T21P       |83          |34.72.0.75 |   |   |
|          |T21P_E2    |83          |52.84.0.125|   |   |
|          |T23G       |83          |44.84.0.140|   |   |
|          |T27G<sup>1</sup>      |83          |69.86.0.15 |   |   |
|          |T29G       |83          |46.83.0.130|   |   |
|          |T30<sup>1</sup>       |83          |124.86.0.40|   |   |
|          |T30P<sup>1</sup>      |83          |124.86.0.40|   |   |
|          |T31G<sup>1</sup>      |83          |124.86.0.40|   |   |
|          |T31P<sup>1</sup>      |83          |124.86.0.40|   |   |
|          |T33G<sup>1</sup>      |83          |124.86.0.40|   |   |
|          |T40G       |83          |76.84.0.125|   |   |
|          |T40P       |83          |54.84.0.125|   |   |
|          |T41P       |83          |36.83.0.120|   |   |
|          |T41S<sup>1</sup>      |83          |66.86.5.1  |   |   |
|          |T42G       |83          |29.83.0.130|   |   |
|          |T42S<sup>1</sup>      |83          |66.86.5.1  |   |   |
|          |T42U<sup>1</sup>      |83          |108.86.5.1 |   |   |
|          |T43U<sup>1</sup>      |83          |108.86.5.1 |   |   |
|          |T46G       |83          |28.83.0.130|   |   |
|          |T46S<sup>1</sup>      |83          |66.86.5.1  |   |   |
|          |T46U<sup>1</sup>      |83          |108.86.5.1 |   |   |
|          |T48G       |83          |35.83.0.130|   |   |
|          |T48S<sup>1</sup>      |83          |66.86.5.1  |   |   |
|          |T48U<sup>1</sup>      |83          |108.86.5.1 |   |   |
|          |T53<sup>1</sup>       |83          |96.86.5.1  |   |   |
|          |T53W<sup>1</sup>      |83          |96.86.5.1  |   |   |
|          |T54W<sup>1</sup>      |83          |96.86.5.1  |   |   |
|          |T57W<sup>1</sup>      |83          |96.86.5.1  |   |   |
|          |W56H                  |            |61.85.0.56 |   |   |
|          |W73H                  |            |116.85.0.38|   |   |
|          |W59R                  |            |115.85.0.56|   |   |
|          |W70B NOAM             |            |146.85.5.4 |   |   |
|          |W70B EMEA             |            |146.85.5.2 |   |   |
|          |W70B APAC             |            |146.85.5.3 |   |   |
|          |W80 NOAM              |            |130.85.5.5 |   |   |
|          |W80 EMEA              |            |130.85.5.6 |   |   |
|          |W80 APAC              |            |130.85.5.4 |   |   |
|          |W90 NOAM              |            |130.85.5.5 |   |   |
|          |W90 EMEA              |            |130.85.5.6 |   |   |
|          |W90 APAC              |            |130.85.5.4 |   |   |
|**AudioCodes**|       |            |           |Some AudioCodes SIP devices need a provisioning URL setting. Download and install upgrade files for the affected AudioCodes devices at the right. |[Downloadable files for affected devices at AudioCodes](https://audiocodes.sharefile.com/share/view/sc9cdf17f9ec45d09/fo7914a2-4f3a-4000-8957-47bd6f35a3a5)|
|          |405<sup>1</sup>        |2.2.8      |2.2.16.600 |   |   |
|          |405HD<sup>1</sup>      |3.2.1      |2.2.16.600 |   |   |
|          |405HDG<sup>1</sup>     |3.2.1      |2.2.16.600 |   |   |
|          |420HD<sup>1</sup>      |3.2.1      |2.2.16.600 |   |   |
|          |420HDG<sup>1</sup>     |3.2.1      |2.2.16.600 |   |   |
|          |430HD<sup>1</sup>      |3.2.1      |2.2.16.600 |   |   |
|          |430HDG<sup>1</sup>     |3.2.1      |2.2.16.600 |   |   |
|          |440HD<sup>1</sup>      |3.2.1      |2.2.16.600 |   |   |
|          |445HD<sup>1</sup>      |3.2.1      |3.4.6.717 |   |   |
|          |445HDG<sup>1</sup>     |3.2.1      |3.4.6.717 |   |   |
|          |450HD<sup>1</sup>      |3.2.1      |3.4.6.717  |   |   |
|          |C450HD<sup>1</sup>     |3.2.1      |3.4.6.717  |   |   |
|          |445HD<sup>1</sup>      |3.2.1      |3.4.6.717  |   |   |
|          |RX50<sup>1</sup>       |3.2.1      |3.4.6.717  |   |   |
|          |MP112                  |6.60A.367.001      |6.60A.367.001  |ATA   | All ports available [AudioCodes ATA Setup Guide](https://www.audiocodes.com/media/pafhki3d/onboarding-audiocodes-ata-to-microsoft-sip-gateway-for-teams.pdf)  |
|          |MP114-FXS              |6.60A.367.001      |6.60A.367.001  |ATA   | 3 out of 4 ports available   |
|          |MP114-FXS-FXO          |6.60A.367.001      |6.60A.367.001  |ATA   | 3 out of 4 ports available   |
|          |MP118-FXS              |6.60A.367.001      |6.60A.367.001  |ATA   | 6 out of 8 ports available  |
|          |MP118-FXS-FXO          |6.60A.367.001      |6.60A.367.001  |ATA   | 6 out of 8 ports available  |
|          |MP124-FXS              |6.60A.367.001      |6.60A.367.001  |ATA   | 18 out of 24 ports available  |
|          |MP1288-FXS             |7.40A.400.063      |7.40A.400.063  |ATA   | All ports available  |
|          |MP502                  |7.26A.356.075      |7.26A.356.075  |ATA   | All ports available  |
|          |MP504                  |7.26A.356.075      |7.26A.356.075  |ATA   | All ports available  |
|          |MP508                  |7.26A.356.075      |7.26A.356.075  |ATA   | All ports available  |
|**Spectralink**|       |           |           |   |[Spectralink Support](https://support.spectralink.com)|
|          |7202        |PCS22B     |PCS22B     |Handset |   |
|          |7212        |PCS22B     |PCS22B     |Handset |   |
|          |7502        |PCS22B     |PCS22B     |Handset |   |
|          |7522        |PCS22B     |PCS22B     |Handset |   |
|          |7532        |PCS22B     |PCS22B     |Handset |   |
|          |7622        |PCS22B     |PCS22B     |Handset |   |
|          |7642        |PCS22B     |PCS22B     |Handset |   |
|          |7722        |PCS22B     |PCS22B     |Handset |   |
|          |7742        |PCS22B     |PCS22B     |Handset |   |
|          |S33         |PCS23Ca    |PCS23Ca    |Handset |   |
|          |S35         |PCS23Ca    |PCS23Ca    |Handset |   |
|          |S37         |PCS23Ca    |PCS23Ca    |Handset |   |
|          |IP-DECT Server 200 |PCS22Ab |PCS22Ab |IP-DECT Server |   |
|          |IP-DECT Server 400 |PCS22Ab |PCS22Ab |IP-DECT Server |   |
|          |IP-DECT Server 6500 |PCS22Ab |PCS22Ab |IP-DECT Server |   |
|          |Virtual IP-DECT Server One |PCS22Ab |PCS22Ab |IP-DECT Server |   |
|          |IP-DECT Base Station |PCS22Ab |PCS22Ab |IP-DECT Server |   |
|**Ascom**|       |           |           |   |[Ascom Support](https://www.ascom.com/products-and-services/services/support-and-maintenance/)|
|          |Ascom d43        |2.11.4     |3.0.8     |Handset |   |
|          |Ascom d63        |2.11.4     |3.0.8     |Handset |   |
|          |Ascom d81        |4.13.1     |4.17.3     |Handset |   |
|          |Ascom d83        |1.3.2     |1.5.5     |Handset |   |
|          |Ascom i63        |5.0.1     |5.0.1     |VoWiFi Handset |   |
|          |Ascom Myco 3 DECT        |3.4.1     |3.4.1     |Wireless Handset |   |
|          |IP-DECT Access Point IPBSx        |11.8.8     |11.9.11     |IP-DECT Access Point |   |
|          |IP-DECT Gateway IPBL     |11.8.8     |11.9.11     |IP-DECT Gateway |   |
|          |TDM Base Station        |R3N     |R4B     |IP-DECT Base Station |   |
|          |IP-DECT Virtual Appliance IPVM        |11.8.8     |11.9.11     |IP-DECT Server |   |
|**Gigaset**|       |           |           |   |[Gigaset Support](https://www.gigaset.com/en_en/cms/home/support/support.html)|
|          |N610 IP PRO        |2.52.0     |2.52.0     |Base Station |   |
|          |N670 IP PRO        |2.52.0     |2.52.0     |Base Station |   |
|          |N870 IP PRO        |2.52.0     |2.52.0     |Base Station |   |
|          |N870E IP PRO        |2.52.0     |2.52.0     |Base Station |   |
|          |N870 VI PRO        |2.52.0     |2.52.0     |Base Station |   |
|**Algo**|       |           |           |   |[Algo Support](https://www.algosolutions.com/post-sale-technical-support/)|
|          |8180g2        |5.3     |5.3     |Speaker |   |
|          |8186          |5.3     |5.3     |Speaker |   |
|          |8188          |5.3     |5.3     |Speaker |   |
|          |8189          |5.3     |5.3     |Speaker |   |
|          |8190          |5.3     |5.3     |Speaker |   |
|          |8190s         |5.3     |5.3     |Speaker |   |
|          |8196          |5.3     |5.3     |Speaker |   |
|          |8198          |5.3     |5.3     |Speaker |   |
|          |8028g2        |5.3     |5.3     |Intercom|   |
|          |8063          |5.3     |5.3     |Intercom|   |
|          |8201          |5.3     |5.3     |Intercom|   |
|          |8128g2        |5.3     |5.3     |Visual Alerter |   |
|          |8138          |5.3     |5.3     |Visual Alerter |   |
|          |8301          |5.3     |5.3     |Paging Adapter |   |
|          |8373          |5.3     |5.3     |Paging Adapter |   |
|          |8410          |5.3     |5.3     |Display Speaker |   |
|          |8420          |5.3     |5.3     |Display Speaker |   |

<sup>1</sup> Device supports dynamic emergency calling (E911) with SIP Gateway.

> [!NOTE]
> Customers can use AudioCodes OVOC and Poly Lens to manage device side configuration of their AudioCodes 400 series and Poly VVX/Trio devices respectively.

> [!NOTE]
> Spectralink Handsets receive firmware updates over the air from Spectralink IP-DECT servers.

> [!NOTE]
> Ascom Handsets receive firmware updates over the air from Ascom IP-DECT servers.

> [!NOTE]
> Gigaset Handsets receive firmware updates over the air from Gigaset IP-DECT servers. All Gigaset PRO DECT Handset models are compatible with Microsoft Teams SIP Gateway.

> [!NOTE]
> For Yealink DECT Base Stations, please use the appropriate region specific firmware version listed above for having the best calling experience.

> [!NOTE]
> For support queries, customers using IP-DECT systems with Teams SIP Gateway should reach out to their DECT manufacturer or their implementation channel partners.

> [!NOTE]
> For some devices, the minimum firmware version is greater than the approved firmware version. This is because the 3.X version is the Skype for Business version. We update the SIP version which is 2.X.

> [!NOTE]
> For support queries, customers using the above listed Algo Solutions' SIP enabled endpoints with Teams SIP Gateway should reach out to Algo Solutions.
> [General Information on Algo integration with Teams](https://www.algosolutions.com/solutions/compatibility/msteams/)
> [Configuration Guide](https://www.algosolutions.com/wp-content/uploads/2023/04/Configuration-Guide-Teams-2023.pdf)
> [Troubleshooting Guide](https://www.algosolutions.com/wp-content/uploads/2023/07/Troubleshooting-Algo-Devices-in-MS-Teams.pdf)

> [!NOTE]
> Customers should contact their Tango Extend Reseller for support queries related to Tango Extend eSIM endpoints. Help and Support information are provided in the Tango Extend Teams App.
> 
> **Emergency Calling** - Emergency calling is supported from the Tango Extend eSIM and this uses the Teams number. Teams is not notified of emergency calls made from the eSIM but will receive returned calls towards the Teams number.
>
> **Tango Extend Supported Features** - Sign-in/out using Tango Extend Teams App with Teams policy sync, Make/receive calls with hold/resume and DTMF, dial-in to meeting, request to join, voicemail and MWI, Teams DND and Call Forwarding.
>
> **Currently Unsupported Features** - Sign-out / sign-in currently creates redundant (signed out) entries for the eSIM endpoint in Teams Admin Center.
> Remote Sign-in from TAC is currently not supported by Tango Extend.
> Teams mobile client – If users have both Tango Extend eSIM and Teams mobile client on their phones, then inbound calls will prioritize the Teams mobile client.
> Call transfer – where presented by mobile dialler menu option this is not supported by Tango Extend.
 
