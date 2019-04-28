---
title: "Plan network requirements for Skype for Business"
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection:
- IT_Skype16
- Strat_SB_Admin
ms.custom:
ms.assetid: 35c7bb3f-8e0f-48b7-8a2c-857d4b42a4c4
description: "Summary: Review the network component considerations below before implementing Skype for Business Server."
---

# Plan network requirements for Skype for Business

**Summary:** Review the network component considerations below before implementing Skype for Business Server.

The information in these topics is also discussed in the whitepaper [Network Planning, Monitoring, and Troubleshooting with Lync Server](https://www.microsoft.com/en-us/download/details.aspx?id=39084) with additional details and depth. While the content refers explicitly to Lync 2010 and Lync 2013, the considerations for Skype for Business Server are unchanged.

Likewise, if your network involves wi-fi as well as wired access, the whitepaper [Delivering Lync 2013 Real-Time Communications over Wi-Fi](https://www.microsoft.com/en-us/download/details.aspx?id=36494) is a good reference and is equally applicable to Skype for Business Server.

<!-- Deprecated tools
Network performance and needs are directly linked to the traffic load placed on them. When planning your network and server implementations we recommend making use of the [Skype for Business Server 2015 Planning Tool](../../management-tools/planning-tool/planning-tool.md), the [Skype for Business Server 2015 Capacity Planning Calculator](../../management-tools/capacity-planning-calculator.md), and the [Skype for Business Server 2015 Stress and Performance Tool](../../management-tools/stress-and-performance-tool/stress-and-performance-tool.md).    -->

## Server hardware
<a name="S_hard"> </a>

The network adapter of each server in the Skype for Business Server topology must support at least 1 gigabit per second (Gbps). In general, you should connect all server roles within the Skype for Business Server topology using a low latency and high bandwidth local area network (LAN). The size of the LAN depends on the size of the topology:

- In Standard Edition topologies, servers should be in a network that supports 1 Gbps Ethernet or equivalent.

- In Enterprise Edition topologies, most servers should be in a network that supports more than 1 Gbps, especially when supporting audio/video (A/V) conferencing and application sharing.

For public switched telephone network (PSTN) integration, you can integrate by using either T1/E1 lines or SIP trunking.

## Audio/Video network requirements
<a name="AV_req"> </a>

Network requirements for audio/video (A/V) in a Skype for Business Server deployment include the following:

- If you are deploying a single Edge Server or an Edge pool using DNS load balancing, you can configure the  _external_ firewall to perform network address translation (NAT). You can't configure the _internal_ firewall to perform NAT. For details, see [Port and firewall planning](../edge-server-deployments/edge-environmental-requirements.md#port-and-firewall-planning).

    > [!IMPORTANT]
    > If you have an Edge pool and are using a hardware load balancer, you must use public IP addresses on the Edge Servers and you can't use NAT for the servers or the pool at your NAT-capable device (for example, a firewall appliance or LAN switch. For details, see [Edge Server scenarios in Skype for Business Server](../edge-server-deployments/scenarios.md).

- If your organization uses a Quality of Service (QoS) infrastructure, the media subsystem is designed to work within this existing infrastructure.

- If you use Internet Protocol security (IPsec), we recommend disabling IPsec over the port ranges used for A/V traffic. For details, see [IPsec exceptions](#ipsec-exceptions).

To provide optimal media quality, do the following:

- Provision the network links to support throughput of 65 kilobits per second (Kbps) per audio stream and 500 Kbps per video stream, if they are enabled, during peak usage periods. A two-way audio or video session uses two streams, so a simple audio/phone connection will require 130Kbps to cover each stream. Video will likewise use 1000 Kbps total to carry an upstream and downstream connection.

- To cope with unexpected spikes in traffic and increased usage over time, Skype for Business Server media endpoints can adapt to varying network conditions and support three times the throughput for audio and video while still maintaining acceptable quality. Do not assume that this adaptability will mask the problem when a network is under-provisioned. In an under-provisioned network, the ability of the Skype for Business Server media endpoints to dynamically deal with varying network conditions (for example, temporary high packet loss) is reduced.

- For network links where provisioning is very costly and difficult, you may have to consider provisioning for a lower volume of traffic. In this scenario, let the elasticity of the Skype for Business Server media endpoints absorb the difference between the traffic volume and the peak traffic level, at the cost of some reduction in the voice quality. Also, there will be a decrease in the headroom otherwise available to absorb sudden peaks in traffic.

- For links that cannot be provisioned correctly in the short term (for example, a site that uses very poor WAN links), consider disabling video for certain users.

- Provision the network to guarantee a maximum end-to-end delay (latency) of 150 milliseconds (ms) under peak load. Latency is the one network impairment that Skype for Business Server media components can't reduce, and it is important to find and eliminate the weak points.

- For servers that are running antivirus software, include all servers that are running Skype for Business Server in the exception list to provide optimal performance and audio quality.

## IPsec exceptions

For enterprise networks where Internet Protocol security (IPsec) (see IETF RFC 4301-4309) has been deployed, IPsec must be disabled over the range of ports used for the delivery of audio, video, and panorama video. The recommendation is motivated by the need to avoid any delay in the allocation of media ports due to IPsec negotiation.

The following table explains the recommended IPsec exception settings.

**Recommended IPsec Exceptions**

|Rule name |Source IP |Destination IP |Protocol |Source port |Destination port |Authentication Requirement |
|:--- |:--- |:--- |:--- |:---|:---|:--- |
|A/V Edge Server Internal Inbound|Any  |A/V Edge Server Internal|UDP and TCP|Any |Any |Do not authenticate|
|A/V Edge Server External Inbound|Any  |A/V Edge Server External|UDP and TCP|Any |Any |Do not authenticate|
|A/V Edge Server Internal Outbound|A/V Edge Server Internal  |A/V Edge Server External |UDP and TCP|Any |Any |Do not authenticate|
|A/V Edge Server External Outbound|A/V Edge Server External |Any |UDP and TCP|Any |Any |Do not authenticate|
|Mediation Server Inbound|Any  |Mediation Server(s) |UDP and TCP|Any |Any |Do not authenticate|
|Mediation Server Outbound|Mediation Server(s)  |Any|UDP and TCP|Any |Any |Do not authenticate|
|Conferencing Attendant Inbound|Any  |Front End Server running Conferencing Attendant |UDP and TCP|Any |Any |Do not authenticate|
|Conferencing Attendant Outbound|Front End Server running Conferencing Attendant  |Any|UDP and TCP|Any |Any |Do not authenticate|
|A/V Conferencing Inbound|Any|Front End Servers|UDP and TCP|Any |Any |Do not authenticate|
|A/V Conferencing Outbound|Front End Servers|Any|UDP and TCP|Any |Any |Do not authenticate|
|Exchange Inbound|Any|Exchange Unified Messaging|UDP and TCP|Any |Any |Do not authenticate|
|Application Sharing Servers Inbound|Any|Application Sharing Servers|UDP and TCP|Any |Any |Do not authenticate|
|Application Sharing Server Outbound|Application Sharing Servers| Any |UDP and TCP|Any |Any |Do not authenticate|
|Exchange Outbound|Exchange Unified Messaging|Any|UDP and TCP|Any |Any |Do not authenticate|
|Clients| Any  |Any|UDP and TCP|Any |Any |Do not authenticate|
|         |         |         |         |         |         |         |


## Conferencing network requirements
<a name="Conf_req"> </a>

The bandwidth used to download conference content from the Internet Information Services (IIS) server depends on the size of the content. You may choose to monitor the actual usage and adjust bandwidth planning accordingly.

## Network bandwidth requirements for media traffic
<a name="Conf_req"> </a>

An important part of network planning is ensuring that your network can handle the media traffic generated by Skype for Business Server. This section helps you plan for that media traffic.

### Media traffic network usage
<a name="Net_req"> </a>

The media traffic bandwidth usage can be challenging to calculate because of the number of different variables, such as codec usage, resolution, and activity levels. The bandwidth usage is a function of the codec that is used and the activity of the stream, which can vary between scenarios. The following table lists the audio codecs typically used in Skype for Business Server scenarios.

**Audio codec bandwidth**

|**Audio codec**|**Scenario**|**Audio payload bit rate (KBPS)**|**Bandwidth audio payload and IP header only (Kbps)**|**Bandwidth audio payload, IP header, UDP, RTP and SRTP (Kbps)**|**Bandwidth audio payload, IP header, UDP, RTP, SRTP and forward error correction (Kbps)**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|RTAudio Wideband  <br/> |Peer-to-peer  <br/> |29.0  <br/> |45.0  <br/> |57.0  <br/> |86.0  <br/> |
|RTAudio Narrowband  <br/> |Peer-to-peer PSTN  <br/> |11.8  <br/> |27.8  <br/> |39.8  <br/> |51.6  <br/> |
|G.722  <br/> |Conferencing  <br/> |64.0  <br/> |80.0  <br/> |95.6  <br/> |159.6  <br/> |
|G.722 Stereo  <br/> |Peer-to-peer Conferencing  <br/> |128.0  <br/> |144.0  <br/> |159.6  <br/> |223.6  <br/> |
|G.711  <br/> |PSTN, Conferencing  <br/> |64.0  <br/> |80.0  <br/> |92.0  <br/> |156.0  <br/> |
|Siren  <br/> |Conferencing  <br/> |16.0  <br/> |32.0  <br/> |47.6  <br/> |63.6  <br/> |
|SILK Wideband  <br/> |Peer-to-peer  <br/> |36.0  <br/> |52.0  <br/> |64.0  <br/> |100.0  <br/> |
|SILK Wideband  <br/> |Peer-to-peer  <br/> |26.0  <br/> |42.0  <br/> |54.0  <br/> |80.0  <br/> |
|SILK Wideband  <br/> |Peer-to-peer  <br/> |20.0  <br/> |36.0  <br/> |48.0  <br/> |68.0  <br/> |
|SILK wideband/narrowband  <br/> |Peer-to-peer  <br/> |13.0  <br/> |29.0  <br/> |41.0  <br/> |54.0  <br/> |

> [!NOTE]
> If enough bandwidth is not available for that codec, then calls can fail with an error that resembles the following in the Media logs. Note: Media logs (.blog) files can be decoded by Microsoft support personnel only. 
“Atleast one codec must be enabled, hr: c0042004”.

The bandwidth numbers in the previous table are based on 20ms packetization (50 packets per second) and for the Siren and G.722 codecs include the additional secure real-time transport protocol (SRTP) overhead from conferencing scenarios and assume the stream is 100% active. Forward Error Correction (FEC) is used dynamically when there is packet loss on the link to help maintain the quality of the audio stream.

The stereo version of the G.722 codec is used by systems that are based on the Lync Room System, which uses a single stereo microphone or a pair of mono microphones to allow listeners to better distinguish multiple speakers in the meeting room.

**Video Resolution Bandwidth**

|**Video codec**|**Resolution and aspect ratio**|**Maximum video payload bit rate (Kbps)**|**Minimum video payload bit rate (Kbps)**|
|:-----|:-----|:-----|:-----|
|H.264  <br/> |320x180 (16:9)  <br/> 212x160 (4:3)  <br/> |250  <br/> |15  <br/> |
|H.264/RTVideo  <br/> |424x240 (16:9)  <br/> 320x240 (4:3)  <br/> |350  <br/> |100  <br/> |
|H.264  <br/> |480x270 (16:9)  <br/> 424x320 (4:3)  <br/> |450  <br/> |200  <br/> |
|H.264/RTVideo  <br/> |640x360 (16:9)  <br/> 640x480 (4:3)  <br/> |800  <br/> |300  <br/> |
|H.264  <br/> |848x480 (16:9)  <br/> |1500  <br/> |400  <br/> |
|H.264  <br/> |960x540 (16:9)  <br/> |2000  <br/> |500  <br/> |
|H.264/RTVideo  <br/> |1280x720 (16:9)  <br/> |2500  <br/> |700  <br/> |
|H.264  <br/> |1920x1080 (16:9)  <br/> |4000  <br/> |1500  <br/> |
|H.264/RTVideo  <br/> |960x144 (20:3)  <br/> |500  <br/> |15  <br/> |
|H.264  <br/> |1280x192 (20:3)  <br/> |1000  <br/> |250  <br/> |
|H.264  <br/> |1920x288 (20:3)  <br/> |2000  <br/> |500  <br/> |

The default codec for video is the H.264/MPEG-4 Part 10 Advanced Video Coding standard, together with its scalable video coding extensions for temporal scalability. To maintain interoperability with legacy clients, the RTVideo codec is still used for peer-to-peer calls between Skype for Business Server and legacy clients. In conference sessions with both Skype for Business Server and legacy clients the Skype for Business Server endpoint may encode the video using both video codecs and send the H.264 bitstream to the Skype for Business Server clients and the RTVideo bitstream to legacy clients.

The bandwidth required depends on the resolution, quality, frame rate, and the amount of motion or change in the picture. For each resolution, there are two pertinent bit rates:

- **Maximum payload bit rate** This is the bit rate that an endpoint will use for resolution at the maximum frame rate. This is the value that allows the highest video and sound quality.

- **Minimum payload bit rate** This is the bit rate below which a Skype for Business Server endpoint will switch to the next lower resolution. To guarantee a certain resolution, the available video payload bit rate must not fall below this minimum bit rate for that resolution. This value is helps you understand the lowest value possible if the maximum bit rate is not available or practical. For some users, such a low bit rate video might provide an unacceptable video experience so use caution with these minimum video payload bitrates. Note that for static, unchanging video scenes the actual bit rate may temporarily fall below the minimum bit rate.

Skype for Business Server supports many resolutions. This allows Skype for Business Server to adjust to different network bandwidth and receiving client capabilities. The default aspect ratio for Skype for Business Server is 16:9. The legacy 4:3 aspect ratio is still supported for webcams which don't allow capture in the 16:9 aspect ratio.

Video FEC is always included in the video payload bit rate when it is used so there are no separate values for with video FEC and without video FEC.

Endpoints do not stream audio or video packets continuously. Depending on the scenario there are different levels of stream activity which indicate how often packets are sent for a stream. The activity of a stream depends on the media and the scenario, and does not depend on the codec being used. In a peer-to-peer scenario:

- Endpoints only send audio streams when the users speak.

- Both participants receive audio streams.

- If video is used, both endpoints send and receive video streams during the call.

- For static video scenes the actual bit rate may temporarily be very low as the video codec will skip encoding regions of the video without a change since the prior sample.

In a conferencing scenario:

- Endpoints send audio streams only when the users speak.

- All participants receive audio streams.

- If video is used, all participants can receive up to five receive video streams and one panoramic (for example, aspect ratio 20:3) video stream. By default the five receive video streams are based on active speaker history but users can also manually select the participants from which they want to receive a video stream. If multi-video is enabled, the resolution and bandwidth requirement for each of the video streams will be lower.

- Each participant that turns on the user's send video stream will send one or more video streams. Skype for Business Server has the capability of sending up to five video streams to optimize the video quality for all the receiving clients. The actual number of video streams being sent is determined by the sender based on CPU capability, available uplink bandwidth, and the number of receiving clients requesting a certain video stream. The most common case is that one H.264 and one RTVideo video stream are being sent in case a legacy client joins the conference. Another common scenario is that several H.264 video streams (for example, with different video resolutions) are sent to accommodate different receiver requests.

In addition to the bandwidth required for the real-time transport protocol (RTP) traffic for audio and video media, bandwidth is required for real-time transport control protocol (RTCP). RTCP is used for reporting statistics and out-of-band control of the RTP stream. For planning, use the bandwidth numbers in the following table for RTCP traffic. These values represent the maximum bandwidth used for RTCP and are different for audio and video streams because of differences in the control data

**RTCP Bandwidth**

|**Media**|**RTCP maximum bandwidth (Kbps)**|
|:-----|:-----|
|Audio  <br/> |5  <br/> |
|Video (Only H.264 or RTVideo being sent/received)  <br/> |10  <br/> |
|Video (H.264 and RTVideo being sent/received)  <br/> |15  <br/> |

For capacity planning, the following two statistics are of interest:

- **Maximum bandwidth without FEC** The maximum bandwidth that a stream will consume. This includes the typical activity of the stream and the typical codec that is used in the scenario without FEC. This is the bandwidth when the stream is at 100% activity and there is no packet loss triggering the use of FEC. This is useful for computing how much bandwidth must be allocated to allow the codec to be used in a given scenario. FEC is not expected to be a requirement on a managed network.

- **Maximum bandwidth with FEC** The maximum bandwidth that a stream consumes. This includes the typical activity of the stream and the typical codec that is used in the scenario with FEC. This is the bandwidth when the stream is at 100% activity and there is packet loss triggering the use of FEC to improve quality. This is useful for computing how much bandwidth must be allocated to allow the codec to be used in a given scenario and allow the use of FEC to preserve quality under packet-loss conditions.

The following tables also list an additional bandwidth value, **Typical bandwidth**. This is the average bandwidth that a stream consumes. This includes the typical activity of the stream and the typical codec that is used in the scenario. This bandwidth can be used for approximating how much bandwidth is being consumed by media traffic at a specific time, but should not be used for capacity planning, because individual calls will exceed this value when the activity level is greater than average. The typical video stream bandwidth in the tables below is based on a mix of different video resolutions as observed in measured customer data, and smaller installations are likely to have actual numbers that differ from the table data. For example, in peer-to-peer sessions most users would use the default video render window whereas some percentage of users would increase or maximize the Skype for Business Server application to allow better video resolutions.

The following tables provide values for the various scenarios.

**Audio/Video Capacity Planning for Peer-to-Peer Sessions**

|**Media**|**Codec**|**Typical stream bandwidth (Kbps)**|**Maximum stream bandwidth without FEC**|**Maximum stream bandwidth with FEC**|
|:-----|:-----|:-----|:-----|:-----|
|Audio  <br/> |RTAudio Wideband  <br/> |39.8  <br/> |62  <br/> |91  <br/> |
|Audio  <br/> |RTAudio Narrowband  <br/> |29.3  <br/> |44.8  <br/> |56.6  <br/> |
|Audio  <br/> |SILK Wideband  <br/> |44.3  <br/> |69  <br/> |105  <br/> |
|Main video when calling Skype for Business Server endpoints  <br/> |H.264  <br/> |460  <br/> |4010 (for maximum resolution of 1920x1080)  <br/> |Already included  <br/> |
|Main video when calling Lync 2010 or Office Communicator 2007 R2 endpoints  <br/> |RTVideo  <br/> |460  <br/> |2510 (for maximum resolution of 1280x720)  <br/> |Already included  <br/> |
|Panoramic video when calling Skype for Business Server endpoints  <br/> |H.264  <br/> |190  <br/> |2010 (for maximum resolution of 1920x288)  <br/> |Already included  <br/> |
|Panoramic video when calling Lync 2010 endpoints  <br/> |RTVideo  <br/> |190  <br/> |510 (for maximum resolution of 960x144)  <br/> |Already included  <br/> |

**Audio/Video Capacity Planning for Conferences**

|**Media**|**Typical codec**|**Typical stream bandwidth (Kbps)**|**Maximum stream bandwidth without FEC**|**Maximum stream bandwidth with FEC**|
|:-----|:-----|:-----|:-----|:-----|
|Audio  <br/> |G.722  <br/> |46.1  <br/> |100.6  <br/> |164.6  <br/> |
|Audio  <br/> |Siren  <br/> |25.5  <br/> |52.6  <br/> |68.6  <br/> |
|Main video receive  <br/> |H.264 and RTVideo¹  <br/> |260  <br/> |8015  <br/> |Not applicable  <br/> |
|Main video send  <br/> |H.264 and RTVideo  <br/> |270  <br/> |8015  <br/> |Not applicable  <br/> |
|Panoramic video receive  <br/> |H.264 and RTVideo  <br/> |190  <br/> |2010 (for maximum resolution of 1920x288)  <br/> |Not applicable  <br/> |
|Panoramic video send  <br/> |H.264 and RTVideo  <br/> |190  <br/> |2515 ²  <br/> |Not applicable  <br/> |

1. RT Video is sent in addition to H.264 when Lync 2010 clients are connected to the conference.

2. If there are multiple streams, they dynamically share the allocated bandwidth.

For the main video the typical stream bandwidth is the aggregated bandwidth over all received video streams and the maximum stream is the bandwidth over all send video streams. Even with multiple video streams the typical video bandwidth is smaller than in the peer-to-peer scenario because many video conferences are using content sharing that leads to much smaller video windows and therefore smaller video resolutions. The maximum supported aggregated video payload bandwidth is 8000 Kbps for both, send and receive streams which would be used (e.g. if there are two incoming 1920x1080p video streams). Maximum values are only rarely seen in actual implementations.

When building out a multiparty conference that uses the gallery view feature, bandwidth utilization increases initially as participants join, then decreases as resolutions are dropped to fit within the maximum.

||**2 Participants**|**3 Participants**|**4 Participants**|**5 Participants**|**6 Participants**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|**Max resolutions received** <br/> |1920x1080  <br/> |1280x720  <br/> |640x360  <br/> |640x360 320x240  <br/> |640x360 320x240  <br/> |
|**Total average bit rate** <br/> |2128  <br/> |4050  <br/> |1304  <br/> |1224  <br/> |1565  <br/> |
|**Total Maximum bit rate** <br/> |4063  <br/> |5890  <br/> |2860  <br/> |2699  <br/> |3017  <br/> |

The typical stream bandwidth for panoramic video is based on devices that only stream up to 960x144 panoramic video. Expect the typical stream bandwidth to increase when using devices with 1920x288 panoramic video.

**Audio Capacity Planning for PSTN**

|**Media**|**Typical codec**|**Typical stream bandwidth (Kbps)**|**Maximum stream bandwidth without FEC**|**Maximum stream bandwidth with FEC**|
|:-----|:-----|:-----|:-----|:-----|
|Audio  <br/> |G.711 (this includes PSTN participants in conferences)  <br/> |64.8  <br/> |97  <br/> |161  <br/> |
|Audio  <br/> |RTAudio Narrowband  <br/> |30.9  <br/> |44.8  <br/> |56.6  <br/> |

The network bandwidth numbers in these tables represent one-way traffic only and include 5 Kbps for RTCP traffic overhead for each stream.

## Managing Quality of Service
<a name="man_QOS"> </a>

Quality of Service (QoS) is a networking technology that is used in some organizations to help provide an optimal end-user experience for audio and video communications. QoS is most frequently used on networks where bandwidth is limited: with a large number of network packets competing for a fairly small amount of available bandwidth, QoS enables administrators to assign higher priorities to packets carrying audio or video data. By giving these packets a higher priority, audio and video communications are likely to complete faster, and with less interruption, than network sessions involving things such as file transfers, web browsing, or database backups. That's because network packets used for file transfers or database backups are assigned a "best effort" priority.

> [!NOTE]
> As a rule, QoS applies only to communication sessions on your internal network. When you implement QoS, you configure your servers and routers to support packet marking in a particular manner that may not be supported on the Internet or on other networks. Even if Quality of Service is supported on other networks, there is no guarantee that QoS will be configured in exactly the same way you configured the service. If you are using MPLS, you'll need to work with your MPLS provider.

Skype for Business Server does not require QoS, but it is strongly recommended. If you experience packet loss issues on the network your available solutions are to add more bandwidth or to implement QoS. If adding more bandwidth is not possible, then implementing QoS might be your only toll to resolve the problem.

Skype for Business Server offers full support for QoS: that means that organizations that are already using QoS can easily integrate Skype for Business Server into their existing network infrastructure. To do this you must follow these steps:

- [Enabling QoS in Skype for Business Server for devices that are not based on Windows](../../manage/network-management/qos/enabling-qos-for-devices-that-are-not-based-on-windows.md). By default, QoS is disabled for computers and other devices (such as iPhones) that run other operating systems. Although you can use Skype for Business Server to enable and disable Quality of Service for devices, you typically cannot use the product to modify the DSCP codes used by these devices.

- [Configuring port ranges and a Quality of Service policy for your Conferencing, Application, and Mediation servers](../../manage/network-management/qos/configuring-port-ranges-for-your-conferencing-application-and-mediation-servers.md). You must reserve a unique set of ports for different packet types, such as audio and video. By using Skype for Business Server you do not enable or disable QoS by setting a property value to True or to False. Instead, you enable QoS by configuring port ranges and then creating and applying Group Policy. If you later decide not to use QoS you can "disable" QoS by removing the appropriate Group Policy objects.

- [Configuring port ranges and a Quality of Service policy for your Edge Servers](../../manage/network-management/qos/configuring-port-ranges-for-your-edge-servers.md). Although not required, you can configure your Edge servers to use the same port ranges as your other servers. Configuring a QoS policy only be done for the internal side of your Edge servers. That's because QoS is designed for use on your internal network and not on the Internet.

- [Configuring port ranges and a Quality of Service policy for your clients in Skype for Business Server](../../manage/network-management/qos/configuring-port-ranges-for-your-skype-clients.md). These port ranges apply only to client computers and are typically different from the port ranges configured on your servers. Note that Skype for Business Server does not support QoS for Windows operating systems other than Windows 10.


> [!NOTE]
> If you are using Windows Server 2012 or Windows Server 2012 R2 you might be interested in the new set of Windows PowerShell cmdlets available for managing QoS on that platform. For more information, see [Network QoS Cmdlets in Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=285379).

QoS is also discussed in the whitepaper [Network Planning, Monitoring, and Troubleshooting with Lync Server](https://www.microsoft.com/en-us/download/details.aspx?id=39084) with additional details and depth. While the content refers explicitly to Lync 2010 and Lync 2013, the considerations for Skype for Business Server are unchanged.

## See also
<a name="man_QOS"> </a>

[Plan for IPv6 in Skype for Business](ipv6.md)

[Load balancing requirements for Skype for Business](load-balancing.md)

[DNS requirements for Skype for Business Server](dns.md)
