---
title: "Skype for Business certification program - Video"
ms.author: jambirk
author: jambirk
manager: serdars
ms.reviewer: dougand
ms.topic: article
ms.tgt.pltfrm: lync
ms.service: skype-for-business-online-admin
ms.collection: Skype for Business
audience: Admin
appliesto:
- Skype for Business Server
- Skype for Business 
localization_priority: Normal
f1keywords: None
ms.custom:
- Skype for Business Certification
- mt779140
description: "Microsoft tests and qualifies video teleconference systems (VTCs), and gateways for interoperability with Skype for Business."
---

# Video for Skype for Business
Microsoft tests and qualifies video teleconference systems (VTCs), and gateways for interoperability with Skype for Business through our Video Interoperability Program. Our Video Interoperability program tests:
- Video endpoints for direct registration as an end point on Lync 2013 and Skype for Business Server 2015.
- Video infrastructure for providing a gateway that allows legacy SIP and H.323 based VTCs to join scheduled Skype for Business meetings, and in some cases to conduct peer-to-peer calling with native Skype for Business endpoints.

Always check if your Skype for Business version was tested to interoperate with the video systems.

## Video endpoints
The tables that follow describe the features available for the 3rd party VTC as certified for Skype for Business. Here, we compare the capabilities of the VTC in Skype for Business interop mode to the capabilities of Skype Room Systems (Native Meeting Room Devices).

#### General information

|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|Polycom RealPresence Group Series for Skype for Business|Skype Room Systems (Native Meeting Room Devices)|
|:---------|:---------|:--------|
|**Product type**| VTC |Room System|
|**Description**  |3rd party endpoint running non-Skype for Business media stack, interoperating with Skype for Business |Purpose-build Windows UWP app, a native Skype for Business client for conference rooms (native Teams client coming soon)|
|**Qualification date** |June 2017|December 2016 (first release)|
|**Version Tested** |6.1.1|3.0.16.0 (current)|
|**Skype version supported**|Skype for Business Server 2015 <br>Skype for Business Online|Skype for Business Server 2015 <br>Skype for Business Online|
|     |         |         |


#### Skype for Business Experience

|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|Polycom RealPresence Group Series for Skype for Business|Skype Room Systems (Native Meeting Room Devices)|
|:--- |:--- |:---: |
|Skype for Business UI|Partial \*| &#x2714; |
|Configuration Settings|3rd party| &#x2714; |
|Single touch meeting join|&#x2714;|&#x2714; |
|Viewing shared files or content uploaded in Skype meeting|         | &#x2714;|
|Sharing content in Skype for Business meeting|         | &#x2714;|
|Viewing shared Desktop in Skype for Business meeting|&#x2714;| &#x2714; |
|Viewing PowerPoint application shared by Skype for Business| \*\* |&#x2714; |
|Desktop Sharing from device in a Skype meeting|         | &#x2714;|
|Sharing from device in P2P call   |  \*\*       | &#x2714; |
| | | |

\* Skype for Business user experience with Group Series is limited to use of the Polycom RealPresence Touch Controller when Skype for Business mode is enabled. This experience is not present in the front of room view. Additionally, certain capabilities such as admitting attendees, locking spotlight, and promoting as presenter or demoting participants to attendee are not available on VTC.

\*\*  Desktop sharing using RDP from a device sends content as video over the people channel. Polycom support for VBSS is currently planned for certification.


#### Manageability 

|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|Polycom RealPresence Group Series for Skype for Business|Skype Room Systems (Native Meeting Room Devices)|
|:--- |:---: |:---: |
|**OOB Experience** |3rd party |&#x2714; |
|**Skype for Business in-band provisioning**| |&#x2714; |
|**Monitoring with OMS**| |&#x2714; |
|**In-band update**| &#x2714;| &#x2714;|
|**Management platform**|3rd party |Windows PC based (Group Policies, SCCM, and others) |
| | | |

#### Interop with Skype for Business

|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|Polycom RealPresence Group Series for Skype for Business|Skype Room Systems (Native Meeting Room Devices)|
|:--- |:---: |:---: |
|**Searchable from Lync or Skype client** |&#x2714; | &#x2714; <br />(with Exchange resource account)|
|**Point-toPoint and PSTN calls** |&#x2714; |&#x2714; |
|**Video calls over UDP and TCP** |&#x2714; |&#x2714; <br />(with Exchange resource account)|
|**Presence (available, busy, offline)** |&#x2714; |&#x2714; |
| | | |


#### Media quality with Skype for Business

|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|Polycom RealPresence Group Series for Skype for Business|Skype Room Systems (Native Meeting Room Devices)|
|:--- |:---: |:---: |
|**VBSS-based content sharing**|\*\*  |&#x2714;  |
|**RDP-based content sharing**| &#x2714; | &#x2714; |
|**HD video (RTVideo - 720p)**| &#x2714; | &#x2714; |
|**HD Video (H.264 SVC – 1080p)**| &#x2714; | &#x2714; |
|**Audio (wideband, narrowband)**| &#x2714; | &#x2714; |
|**Firewall traversal**| &#x2714; | &#x2714; <br>(same as Skype for Business client)|
|**FEC (forward error correction)**| &#x2714; |&#x2714;<br>(same as Skype for Business client)  |
|**Encryption Support (TLS and SRTP)**| &#x2714; | &#x2714;<br>(same as Skype for Business client) |
| |  |  |

\*\*
Desktop sharing using RDP from a device sends content as video over the people channel. Polycom support for VBSS is currently planned for certification.

#### Other feature support with Skype for Business

|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|Polycom RealPresence Group Series for Skype for Business|Skype Room Systems (Native Meeting Room Devices)|
|:--- |:---: |:---: |
|**Web proxy support**| | &#x2714;<br>(same as Skype for Business client) |
|**Support for large meetings ( >75 users )**  |  | &#x2714;<br>(same as Skype for Business client) |
|  |  |  |


## Video infrastructure

|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|Polycom RealConnect for Office 365  |Pexip Infinity  |
|:--- |:--- |:--- |
|**Qualification Date** |April 2017 |July 2017 |
|**Version Tested** |N/A for Service <sup>1</sup> |V15.1 |
|**Skype version supported** | Online (Office 365) |On-premise (Skype for Business Server 2015) |
|**Product Type** |Service |Server |
|**Description** |Gateway |Gateway |
|**Searchable from Lync Client** |No <sup>2</sup> |No |
|**Join Skype Online Supported mMeeting types** |Online |Onprem |
|**Point-to-Point Calls** |No <sup>2</sup> |Yes |
|**VBSS based content sharing** | Yes |No <sup>3</sup> |
|**RDP based content sharing** |Yes |Yes |
|**HD Video (RTVideo – 720p)** | Yes|Yes |
|**HD Video (H.264 SVC – 1080p)** |Yes|Yes |
|**Panoramic video** |Yes | No |
|**Audio (wideband, narrowband)** |Yes|Yes |
|**Presence (available, busy, offline)** |No <sup>2</sup> | Yes |
|**Firewall Traversal** |N/A for Online meeting interop |Yes |
|**FEC (forward error correction)** |Yes|Yes |
|**Encryption Support (TLS and SRTP)** |Yes|Yes |
|**H.323 Signaling** |Yes|Yes |
|**SIP Signaling** |Yes|Yes |
|     | | |

  1. Cloud service based video interop solutions are updated frequently and don't have set version numbers. Instead of testing a specific version, cloud services have implemented real time telemetry and have live-site support process coordination with Microsoft.
  2. Features supported for Online differ from those supported for On-premise. Video interop for O365 is focused on meeting join, and does not require VTCs to be authenticated or in any way registered to the service, as long as the meeting organizer is licensed for the service. For this reason, point-to-point calling and presence status for VTCs is not supported for online video interop.
  3. Pexip support for VBSS is currently in tech preview state.

If you are a vendor seeking to join the certification program, see [How to Join](how-to-join.md) for requirements and available programs.
