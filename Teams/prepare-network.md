---
title: Prepare your organization's network for Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.topic: reference
ms.service: msteams
ms.reviewer: jastark, kojika
audience: admin
description: Before you roll out Microsoft Teams, evaluate and prepare your network to be sure it's ready for Teams. Information includes network requirements, bandwidth requirements, and network optimization guidance.
localization_priority: Normal
search.appverid: MET150
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# Prepare your organization's network for Microsoft Teams 

## Network requirements

If you've already [optimized your network for Office 365](https://docs.microsoft.com/Office365/Enterprise/assessing-network-connectivity), you're probably ready for Microsoft Teams. In any case, check the following before you begin your Teams rollout:

1. Do all your locations have internet access (so they can connect to Office 365)? At a minimum, verify that the following common ports are open to the internet from all locations:

    - Open TCP ports **80** and **443** for outgoing traffic from clients that will use Teams.    
    - Open UDP ports **3478** through **3481** for outgoing traffic from clients that will use Teams.

1. Do you have a verified domain for Office 365 (for example, contoso.com)?
    -   If your organization hasn't rolled out Office 365, see [Getting Started with Office 365 for business](https://support.office.com/article/Get-started-with-Office-365-for-Business-d6466f0d-5d13-464a-adcb-00906ae87029).
    -   If your organization hasn't added or configured a verified domain for Office 365, see [Verify your Office 365 domain](https://support.office.com/article/Verify-your-Office-365-domain-to-prove-ownership-nonprofit-or-education-status-or-to-activate-Yammer-87d1844e-aa47-4dc0-a61b-1b773fd4e590).

1. Has your organization deployed Exchange Online and SharePoint Online?
    - If your organization doesn't have Exchange Online, see [Understand how Exchange and Microsoft Teams interact](exchange-teams-interact.md).
    - If your organization doesn't have SharePoint Online, see [Understand how SharePoint Online and OneDrive for Business interact with Microsoft Teams](sharepoint-onedrive-interact.md).

Once you've verified that you meet these network requirements, you may be ready to [Roll out Teams](How-to-roll-out-teams.md). If you're a large multinational enterprise, or if you know you've got some network limitations, read on to learn how to assess and optimize your network for Teams.

### For educational institutions
If your organization is an educational institution and you use a Student Information System (SIS), [deploy School Data Sync](https://docs.microsoft.com/schooldatasync/) before you roll out Teams.

### Running on-premises Skype for Business Server
If your organization is running on-premises Skype for Business Server (or Lync Server), you must [configure Azure AD Connect](../Skype/SfbHybrid/hybrid/configure-azure-ad-connect.md) to synchronize your on-premises directory with Office 365. 

## Network optimization

The following tasks are optional and aren't required for rolling out Teams. Use this guidance to optimize your network if you want to improve Teams performance.

Reasons why you might want to do additional network optimization:

- Teams runs slowly (maybe you have insufficient bandwidth)
- Calls keep dropping (might be due to firewall or proxy blockers)
- Calls are static-y and cut out, or voices sound like robots (could be jitter or packet loss)

For an in-depth discussion of network optimization for Teams, including guidance for identifying and fixing network impairments, read [Media Quality and Network Connectivity Performance for Teams and Skype for Business Online](../Skype/SfbOnline/optimizing-your-network/media-quality-and-network-connectivity-performance.md).

[Network Planner](network-planner.md): For help assessing your network, including bandwidth calculations and network requirements across your org's physical locations, check out the Network Planner tool, in the [Teams admin center](https://admin.teams.microsoft.com). When you provide your network details and Teams usage, the Network Planner calculates your network requirements for deploying Teams and cloud voice across your organization’s physical locations.

For an example scenario, see [Using Network Planner - example scenario](tutorial-network-planner-example.md).

[Advisor for Teams](use-advisor-teams-roll-out.md): Advisor for Teams is part of the [Teams admin center](https://admin.teams.microsoft.com). It assesses your Office 365 environment and identifies the most common configurations that you may need to update or modify before you can successfully roll out Teams. 


[Validate network connectivity by using the Network Assessment Tool](https://www.microsoft.com/download/details.aspx?id=53885): Use the Network Assessment Tool for Teams to test connectivity to all IP addresses and ports used in Teams calls and meetings. Download the tool and see Usage.docx for details about how to use the tool and interpret the test results. We recommend that you run the tool from a client PC in each location where Teams will be used.


[Validate the network address translation (NAT) pool size required for user connectivity](https://docs.microsoft.com/office365/enterprise/nat-support-with-office-365?redirectSourcePath=%252farticle%252fNAT-support-with-Office-365-170e96ea-d65d-4e51-acac-1de56abe39b9): When multiple users and devices access Office 365 using Network Address Translation (NAT) or Port Address Translation (PAT), you need to ensure that the devices hidden behind each publicly routable IP address do not exceed the supported number. Ensure that adequate public IP addresses are assigned to the NAT pools to prevent port exhaustion. Port exhaustion will contribute to internal users and devices being unable to connect to the Office 365 service.

[Implement the most efficient routing to Microsoft data centers](https://docs.microsoft.com/office365/enterprise/client-connectivity?redirectSourcePath=%252farticle%252fClient-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b): Identify locations that can use local or regional egress points to connect to the Microsoft network as efficiently as possible. 

Intrusion Detection and Prevention Guidance: If your environment has an [Intrusion Detection](https://docs.microsoft.com/azure/network-watcher/network-watcher-intrusion-detection-open-source-tools) or Prevention System (IDS/IPS) deployed for an extra layer of security for outbound connections, be sure to whitelist all Office 365 URLs.

External Name Resolution: Ensure that all the client computers running the Teams client can resolve external DNS queries to discover the services provided by Office 365 and that your firewalls are not preventing access. For information about configuring firewall ports, go to [Office 365 URLs and IP ranges](office-365-urls-ip-address-ranges.md).

Configure split-tunnel VPN: We recommend that you provide an alternate path for Teams traffic that bypasses the virtual private network (VPN), commonly known as split-tunnel VPN. Split tunneling means that traffic for Office 365 doesn't go through the VPN but instead goes directly to Office 365. Bypassing your VPN will have a positive impact on Teams quality, and it reduces load from the VPN devices and the organization’s network. To implement a split-tunnel VPN, work with your VPN vendor. 

Other reasons why we recommend bypassing the VPN: VPNs are typically not designed or configured to support real-time media. Some VPNs might also not support UDP (which is required for Teams). VPNs also introduce an extra layer of encryption on top of media traffic that’s already encrypted. Connectivity to Teams might not be efficient due to hair-pinning traffic through a VPN device. 

[Configure packet prioritization by using QoS](qos-in-teams.md): Use Quality of Service (QoS) to improve call quality in Teams and to monitor and troubleshoot call quality. QoS should be implemented on all segments of a managed network. Even when a network has been adequately provisioned for bandwidth, QoS provides risk mitigation in the event of unanticipated network events. With QoS, voice traffic is prioritized so that these unanticipated events don’t negatively affect quality. 

Optimize your Wi-Fi networks: Like VPN, Wi-Fi networks aren’t necessarily designed or configured to support real-time media. Planning for, or optimizing, a Wi-Fi network to support Teams is an important consideration for a high-quality deployment.

There are several factors that come into play for optimizing a Wi-Fi network:

- Implementing QoS or Wi-Fi Multimedia (WMM) to ensure that media traffic is getting prioritized accordingly over the Wi-Fi networks.

- Planning and optimizing the Wi-Fi bands and access point placement. The 2.4 GHz range might provide an adequate experience depending on access point placement, but access points are often affected by other consumer devices that operate in that range. The 5 GHz range is better suited to real-time media due to their dense range but requires more access points to get sufficient coverage. Endpoints also need to support that range and be configured to leverage those bands accordingly.

- If dual-band Wi-Fi networks are deployed, consider implementing band steering. _Band steering_ is a technique implemented by Wi-Fi vendors to influence dual-band clients to use the 5 GHz range.

- When access points of the same channel are too close together they can cause signal overlap and unintentionally compete, resulting in a bad experience for the user. Ensure that access points that are next to each other are on channels that don’t overlap.

Each wireless vendor has its own recommendations for deploying its wireless solution. Consult your vendor for specific guidance.

[Monitor your network using CQD and call analytics](turning-on-and-using-call-quality-dashboard.md): You use the Call Quality Dashboard (CQD) to gain insight into the quality of calls made by using Teams. CQD is designed to help you optimize your network and keep a close eye on quality, reliability, and the user experience. CQD looks at aggregate telemetry for an entire organization where overall patterns can become apparent, allowing staff to make informed assessments and plan remediation activities to maximize impact. Additionally, CQD provides reports of metrics that provide insight into overall quality, reliability, and user experience. To investigate call problems for individual users, use [per-user call analytics](set-up-call-analytics.md).

## Test the network

After you're done optimizing your network, test it to see if your optimizations worked. Did your changes give you the network-performance improvements you were looking for?

Best practice: Take baseline readings once in a while, when your network is working well. This gives you something to compare against when you're having problems. Similarly, if you do a major update to your network, take another baseline.

Download the [Skype for Business Network Assessment Tool](https://www.microsoft.com/download/details.aspx?id=53885) to test whether your network is ready for Teams. This tool tests whether all the correct ports are open, and it can identify network impairments.

After you download and install the tool, you'll find it in C:\Program Files (x86)\Microsoft Skype for Business Network Assessment Tool. A detailed guide for how to use the tool, Usage.docx, is included in that directory.

### Test for opened ports

To test for opened ports, open a Command prompt window and navigate to the Network Assessment Tool directory by entering **cd C:\Program Files (x86)\Microsoft Skype for Business Network Assessment Tool**. At the command prompt, start the test for opened ports by entering **networkassessmenttool.exe /connectivitycheck**.

After running the checks, the tool will either display the message “Verifications Completed Successfully” or report on the ports that were blocked. It also generates a file named Connectivity_results.txt, which contains the output from the tool and stores it in the %userprofile%\\appdata\\local\\microsoft skype for business network assessment tool\\ directory.

Best practice: Run the connectivity checks on a regular basis to ensure that ports are open and functioning correctly.

### Test for network impairments

Network impairments affect Teams performance, so you'll want to find and remediate them. The most common network impairments are delay (latency), packet loss, and jitter.

- **Latency:** This is the time it takes to get an IP packet from point A to point B on the network. This network propagation delay is essentially tied to physical distance between the two points and the speed of light, including additional overhead taken by the various routers in between. Latency is measured as one-way or round-trip time.

- **Packet loss**: This is often defined as a percentage of packets that are lost in a given window of time. Packet loss directly affects audio quality—from small, individual lost packets having almost no impact to back-to-back burst losses that cause audio to cut out completely.

- **Inter-packet arrival jitter, or simply jitter:** This is the average change in delay between successive packets. Most modern VoIP software, including Skype for Business, can adapt to some levels of jitter through buffering. It's only when the jitter exceeds the buffering that a participant will notice the effects of jitter.

The maximum values for these impairments are described in [Media quality and network connectivity performance](/SkypeForBusiness/optimizing-your-network/media-quality-and-network-connectivity-performance). When testing for these impairments, we distinguish between two separate segments:

- The *edge segment* is the segment in which your router lives. This is the closest logical network segment connected to the internet at each of your locations. In most cases, this is the connection point of the router, or possibly a perimeter network (also known as *DMZ*, *demilitarized zone*, and *screened subnet*). No further traffic that affects devices other than the router should occur between this segment and the internet.

- The *client segment* is the logical network segment in which your clients reside.

You should test both segments by using the Network Assessment Tool. To test the segment, navigate to the directory and enter **networkassessmenttool.exe** at the command prompt. The results are written to a file named Results.tsv, and you can compare them to the [requirements](/SkypeForBusiness/optimizing-your-network/media-quality-and-network-connectivity-performance) for each segment.

For best Teams performance, both segments should meet the requirements. Best practice: Run the tool multiple times for one hour straight to get a good indication of your network’s performance.

## How network traffic flows in Teams

Teams combines three forms of traffic:

-   Data traffic between the Office 365 online environment and the Teams client (signaling, presence, chat, file upload and download, OneNote synchronization).
-   Peer-to-peer real-time communications traffic (audio, video, desktop sharing).
-   Conferencing real-time communications traffic (audio, video, desktop sharing).

This impacts the network on two levels: traffic will flow between the Microsoft Teams clients directly for peer-to-peer scenarios, and traffic will flow between the Office 365 environment and the Microsoft Teams clients for meeting scenarios. To ensure optimal traffic flow, traffic must be allowed to flow both between the internal network segments (for example, between sites over the WAN) as well as between the network sites and Office 365. Not opening the correct ports or actively blocking specific ports will lead to a degraded experience.

For the two defining network segments (Client to Microsoft Edge and Customer Edge to Microsoft Edge), consider the following recommendations.

|Value  |Client to Microsoft Edge  |Customer Edge to Microsoft Edge  |
|:--- |:--- |:--- |
|**Latency (one way)** \*  |< 50ms          |< 30ms         |
|**Latency (RTT or Round-trip Time)** \* |< 100ms   |< 60ms |
|**Burst packet loss**    |<10% during any 200ms interval         |<1% during any 200ms interval         |
|**Packet loss**     |<1% during any 15s interval          |<0.1% during any 15s interval         |
|**Packet inter-arrival Jitter**    |<30ms during any 15s interval         |<15ms during any 15s interval         |
|**Packet reorder**    |<0.05% out-of-order packets         |<0.01% out-of-order packets         |

\* The latency metric targets assume your company site or sites and the Microsoft edges are on the same continent.

Your company site connection to the Microsoft network edge includes first hop network access, which can be WiFi or another wireless technology.

The network performance targets assume proper bandwidth and/or [QoS planning](QoS-in-Teams.md). In other words, the requirements apply directly to Teams real-time media traffic when the network connection is under a peak load.

## Bandwidth requirements
Microsoft Teams gives you the best audio, video and content sharing experience regardless of your network conditions. With variable codecs, media can be negotiated in limited bandwidth environments with minimal impact. But where bandwidth is not a concern, experiences can be optimized for quality, including up to 1080p video resolution, up to 30fps for video and 15fps for content, and high-fidelity audio.

[!INCLUDE [Bandwidth requirements](includes/bandwidth-requirements.md)]

**<font color="red">REVIEWERS: The following information was commented out of the article. It's in more depth than the bandwidth-requirements article included above. Keep or kill?</font>**

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

## Firewall and proxy requirements

TCP ports 80 and 443 are used to connect to web-based content such as SharePoint Online, Exchange Online, and Teams Chat services. Plug-ins and connectors also connect over these TCP ports. The four UDP ports (3478 through 3481) are used for media such as audio and video, to ensure they flow correctly.

If your organization requires that you specify the exact IP address ranges and domains to which these ports should be opened, you can restrict the target IP ranges and domains for these ports. For a list of exact ports, protocols, and IP ranges, see [Office 365 URLs and IP address ranges](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges). If you choose to restrict the target IP address ranges and domains, you must ensure that you keep the list of ports and ranges up to date because they might change. It’s also a good practice to test whether all ports are opened by running the [Skype for Business Network Assessment Tool](https://www.microsoft.com/download/details.aspx?id=53885) on a regular basis. 

If you use one, we recommend that you bypass the proxy server for all Teams services. Although using a proxy might work, it’s likely that quality will be reduced due to media using TCP instead of UDP. For more information about proxy servers and bypassing them, see [Office 365 URLs and IP address ranges](office-365-urls-ip-address-ranges.md).


## Related Topics

[Video: Network Planning](https://aka.ms/teams-networking)

[Identity models and authentication in Teams](identify-models-authentication)

[How to roll out Teams](How-to-roll-out-teams.md)