---
title: Prepare your organization's network for Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
manager: lolaj
ms.date: 08/21/2018
ms.topic: article
ms.service: msteams
ms.reviewer: arachman
description: Learn how to prepare and manage your Microsoft Teams network. Information includes network requirements, bandwidth requirements, and additional considerations.
localization_priority: Normal
search.appverid: MET150
MS.collection: Teams_ITAdmin_Help
appliesto:
- Microsoft Teams
---

Prepare your organization's network for Microsoft Teams
=================================================

Teams combines three forms of traffic:

-   Data traffic between the Office 365 online environment and the Teams client (signaling, presence, chat, file upload and download, OneNote synchronization).

-   Peer-to-peer real-time communications traffic (audio, video, desktop sharing).

-   Conferencing real-time communications traffic (audio, video, desktop sharing).

This impacts the network on two levels: traffic will flow between the Microsoft Teams clients directly for peer-to-peer scenarios, and traffic will flow between the Office 365 environment and the Microsoft Teams clients for meeting scenarios. To ensure optimal traffic flow, traffic must be allowed to flow both between the internal network segments (for example, between sites over the WAN) as well as between the network sites and Office 365. Not opening the correct ports or actively blocking specific ports will lead to a degraded experience.

> [!NOTE]
> Meetings are supported on iOS and Android mobile devices. 

To get an optimal experience with real time media within Microsoft Teams, it is required to meet the networking requirements for Office 365. For more information, see [Media Quality and Network Connectivity Performance for Skype for Business Online](https://docs.microsoft.com/SkypeForBusiness/optimizing-your-network/media-quality-and-network-connectivity-performance).

For the two defining network segments (Client to Microsoft Edge and Customer Edge to Microsoft Edge), consider the following recommendations.


|Value  |Client to Microsoft Edge  |Customer Edge to Microsoft Edge  |
|---------|---------|---------|
|**Latency (one way)**     |< 50ms          |< 30ms          |
|**Latency (RTT or Round-trip Time)** |< 100ms         |< 60ms         |
|**Burst packet loss**    |<10% during any 200ms interval         |<1% during any 200ms interval         |
|**Packet loss**     |<1% during any 15s interval          |<0.1% during any 15s interval         |
|**Packet inter-arrival Jitter**    |<30ms during any 15s interval         |<15ms during any 15s interval         |
|**Packet reorder**    |<0.05% out-of-order packets         |<0.01% out-of-order packets         |

To test both network segments, you can use the [Network Assessment Tool](https://go.microsoft.com/fwlink/?linkid=855799). This tool can be deployed on both the client PC directly and on a PC connected to the Customer Network Edge. The tool includes limited documentation, but a deeper documentation around the usage of the tool can be found here: [Network Readiness Assessment](https://go.microsoft.com/fwlink/?linkid=855800). By running this Network Readiness Assessment, you can validate your network’s readiness to run real-time media applications, such as Microsoft Teams.

> [!NOTE]
> This is the same Network Readiness Assessment that is recommended to be run for customers who are looking to successfully deploy Skype for Business.

Bandwidth requirements
----------

Bandwidth calculations for Microsoft Teams are complex and to help with this, a calculator has been created. To access the calculator, go to [Network Planner in MyAdvisor](https://aka.ms/bwcalc/).

> [!NOTE]
> Teams bandwidth handling improves on Skype for Business Online: for a high quality calling or meeting experience (with audio, video, and sharing), Teams requires only 1.2 Mbps. It can also scale up further for super high quality if there is enough available bandwidth. When a Teams request encounters a low bandwidth condition, Teams can quickly readjust bandwidth usage to adapt to available bandwidth.

<!--
The content you will find below can be used as supplemental background information; however, it is recommended that customers use [Network Planner](https://aka.ms/bwcalc) to track their needs.

> [!IMPORTANT]
>If the required bandwidth is not available, the media stack inside Teams will degrade the quality of the audio/video session to accommodate for that lower amount of available bandwidth, impacting the quality of the call/meeting. The Teams client will attempt to prioritize the quality of audio over the quality of video. It is therefore extremely important to have the expected bandwidth available.


|Activity  |Download Bandwidth  |Upload Bandwidth  |Traffic Flow |
|---------|---------|---------|---------|
|**Peer to peer Audio Call**     |0.1 Mb         |0.1Mb         |Client <> Client         |
|**Peer to peer Video Call (full screen)**     |4 Mb         |4Mb         |Client <> Client          |
|**Peer to peer Desktop Sharing (1920*1080 resolution)**     |4 Mb         |4 Mb         |Client <> Client          |
|**2 Participant Meeting**     |4 Mb         |4 Mb         |Client <> Office 365         |
|**3 participant meeting**     |8 Mb         |6.5 Mb         |Client <> Office 365           |
|**4 participant meeting**     |5.5 Mb         |4 Mb         |Client <> Office 365           |
|**5 participant+ meeting**     |6 Mb         |1.5 Mb         |Client <> Office 365           |
-->

Additional network considerations
---------------

#### **External Name Resolution**

Ensure that all the client computers running Teams client can resolve external DNS queries to discover the services provided by Office 365.

#### **NAT Pool Size**

When multiple users/devices access Office 365 using Network Address Translation (NAT) or Port Address Translation (PAT), you need to ensure that the devices hidden behind each publicly routable IP address do not exceed the supported number.

To mitigate this risk, ensure adequate Public IP addresses are assigned to the NAT pools to prevent port exhaustion. Port exhaustion will cause internal end users and devices to face issues when connecting to the Office 365 services. For more information, see [NAT support with Office 365](https://support.office.com/article/NAT-support-with-Office-365-170e96ea-d65d-4e51-acac-1de56abe39b9).

#### **Intrusion Detection and Prevention Guidance**

If your environment has an Intrusion Detection and/or Prevention System (IDS/IPS) deployed for an extra layer of security for outbound connections, ensure that any traffic with destination to Office 365 URLs is whitelisted.

Network health determination
-----------------

When planning on the implementation of Microsoft Teams within your network, you must ensure you have the required bandwidth, you have access to all required IP addresses, the correct ports opened, and you are meeting the performance requirements for real-time media.

If you know you will not meet these criteria, your end users will not get an optimal experience from Teams due to bad quality during calls and meetings.

Should you not meet these criteria, this is the time to consider pausing the project to ensure you meet the criteria before continuing.


|  |  |  |
|---------|---------|---------|
|![Decision Point icon.](media/Prepare_your_organizations_network_for_Microsoft_Teams_image3.png)    |Decision Point         |Have you evaluated your network capabilities for supporting real time media?<br></br>If your network has not been properly assessed, or you know it will not support real time media, will you disable video and screen sharing capabilities to reduce network impact and poor Teams experiences?         |
|![Next Steps icon.](media/Prepare_your_organizations_network_for_Microsoft_Teams_image4.png)     |Next Steps         |Network Quality Unknown: Follow the [Network Readiness Assessment](https://myadvisor.fasttrack.microsoft.com/CloudVoice/Offers?pageState=NetworkReadiness) guidance to determine if your network is ready for Real Time Media.<br></br>Network Quality Poor: Perform network remediation steps to provide a proper environment for high quality Real Time Media.<br></br>Network Satisfactory: Ensure all IP addresses and ports are properly accessible.           |

