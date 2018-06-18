---
title: Prepare my network - Microsoft Teams
author: turgayo
ms.author: turgayo
manager: serdars
ms.date: 06/30/2018
ms.topic: article
ms.service: msteams
ms.reviewer: dearbeen
description: Use this guidance to prepare your network for Teams deployment and rollout   
localization_priority: Priority
ms.custom: Teams-upgrade-guidance
MS.collection: Strat_MT_TeamsAdmin
appliesto:
- Microsoft Teams
---

![Stages of the upgrade journey, with emphasis on the Technical Readiness stage](media/upgrade-banner-tech-readiness.png "Stages of the upgrade journey, with emphasis on the Technical Readiness stage")

This article is part of the Technical Readiness stage of your upgrade journey, an activity you complete in parallel with the User Readiness stage. Before proceeding, confirm that you’ve completed these activities from previous stages:

-   [Enlisted your project stakeholders](upgrade-enlist-stakeholders.md)
-   [Defined your project scope](upgrade-define-project-scope.md)
-   [Understood coexistence and interoperability of Skype for Business and Teams](upgrade-understand-coexistence-and-interoperability.md)

# Prepare my network

Teams uses audio and video technology (codecs) that can adapt to—and therefore perform better under—most network conditions. To ensure optimal and consistent performance, you should prepare your network for Teams.

![Diagram describing the three components of quality, and how service management overlaps all three components. With a focus on the network.](media/evaluate-my-environment-image1.png "Diagram describing the three components of quality, and how service management overlaps all three components. With a focus on the network.")

## Why should you prepare your network?

Before we look at the steps to be taken, it’s important to understand what can affect the performance of Teams and thereby user happiness and satisfaction. Three major risk areas can affect how users perceive network quality:

-   Insufficient bandwidth available

-   Firewall and proxy blockers

-   Network impairments such as jitter and packet loss

The steps described below will help you determine whether your deployment might be affected by any of these factors and will help you move toward a resolution. Failing to prepare your network will likely lead to dissatisfied users and costly, ad-hoc fixes. By preparing your network—and your organization—for Teams, you can dramatically increase your chance of success.

<!--ENDOFSECTION-->

## Bandwidth planning

The first step toward network readiness is ensuring your network has enough bandwidth available for the modalities Teams will provide to users. Planning for sufficient bandwidth is a fairly straightforward task and a very low-barrier start to ensure your users will have a high-quality Teams experience.

You start your bandwidth planning journey for Teams on the [My Advisor website](https://myadvisor.fasttrack.microsoft.com/) by using the Network Planner. The Network Planner provides per-site bandwidth planning for Teams and offers recommendations for optimizing network performance.

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

### Local internet egress

Many networks were designed to use a hub and spoke topology. In this topology, internet traffic typically traverses the WAN to a central datacenter before it emerges (egresses) to the internet. Often, this is done to centralize network security devices with the goal of reducing overall cost.

Back-hauling traffic across the WAN increases latency and has a negative impact on quality and the user experience. Because Microsoft Teams runs on Microsoft’s large global network, there’s often a network peering location close to the user. A user will most likely get better performance by egressing out of a local internet point close to their location and on to our voice-optimized network as soon as possible. For some workloads, DNS requests are used to send traffic to the nearest front-end server. In such cases, it’s important that when using a local egress point, it’s paired with local DNS resolution.

Optimizing the network path to Microsoft’s global network will improve performance and ultimately provide the best experience for users. For more detail, see the blog post [Getting the best connectivity and performance in Office 365](https://techcommunity.microsoft.com/t5/Office-365-Blog/Getting-the-best-connectivity-and-performance-in-Office-365/ba-p/124694).


To get an optimal experience with real time media within Microsoft Teams, it is required to meet the networking requirements for Office 365. For more information, see [Media Quality and Network Connectivity Performance for Skype for Business Online](https://docs.microsoft.com/SkypeForBusiness/optimizing-your-network/media-quality-and-network-connectivity-performance).

The two defining network segments (Client to Microsoft Edge and Customer Edge to Microsoft Edge) must meet the following requirements:


|**Value**  |**Client to Microsoft Edge**  |**Customer Edge to Microsoft Edge**  |
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


### VPN

VPNs provide a valuable service to many organizations. Unfortunately, they’re typically not designed or configured to support real-time media. Some VPNs might also not support UDP. VPNs also introduce an extra layer of encryption on top of media traffic that’s already encrypted. In addition, connectivity to the Teams service might not be efficient due to hair-pinning traffic through a VPN device. Furthermore, they aren’t necessarily designed from a capacity perspective to accommodate the anticipated loads that Teams will require.

The recommendation is to provide an alternate path that bypasses the VPN for Teams traffic. This is commonly known as *split-tunnel VPN*. Split tunneling means that traffic for Office 365 won’t traverse the VPN but will go directly to Office 365. This change will have a positive impact on quality, but also provides the secondary benefit of reducing load from the VPN devices and the organization’s network.

To implement a split-tunnel, consult with your VPN vendor for the configuration details.

### Wi-Fi

Like VPN, Wi-Fi networks aren’t necessarily designed or configured to support real-time media. Planning for, or optimizing, a Wi-Fi network to support Teams is an important consideration for a high-quality deployment.

There are several factors that come into play for optimizing a Wi-Fi network:

-   Implementing QoS or Wi-Fi Multimedia (WMM) to ensure that media traffic is getting prioritized accordingly over the Wi-Fi networks.

-   Planning and optimizing the Wi-Fi bands and access point placement. The 2.4 GHz range may provide an adequate experience depending on access point  placement, but access points are often affected by other consumer devices that operate in that range. The 5 GHz range is better suited to real-time media due to their dense range but requires more access points to get sufficient coverage. Endpoints also need to support that range and be configured to leverage those bands accordingly.

-   If dual-band Wi-Fi networks are deployed, consider implementing band steering. Band steering is a technique implemented by Wi-Fi vendors to influence dual-band clients to use the 5 GHz range.

-   When access points of the same channel are too close together they can cause signal overlap and unintentionally compete, resulting in a bad experience for the user. Ensure that access points that are next to each other are on channels that don’t overlap.

Each wireless vendor has its own recommendations for deploying its wireless solution. We recommend that you consult your vendor for specific guidance.

<!--ENDOFSECTION-->

## Firewall and proxy requirements

Microsoft Teams connects to Microsoft Online Services and needs internet connectivity for this. For Teams to function correctly, you must open TCP ports 80 and 443 from the clients to the internet, and UDP ports 3478 through 3481 from the clients to the internet. The TCP ports are used to connect to web-based content such as SharePoint Online, Exchange Online, and the Teams Chat services. Plug-ins and connectors also connect over these TCP ports. The four UDP ports are used for media such as audio and video, to ensure they flow correctly.

Opening these ports is essential for a reliable Teams deployment. Blocking these ports is unsupported and will have an effect on media quality.

If your organization requires that you specify the exact IP address ranges and domains to which these ports should be opened, you can restrict the target IP ranges and domains for these ports. For a list of exact ports, protocols, and IP ranges, see [Office 365 URLs and IP address ranges](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_teams). If you choose to restrict the target IP address ranges and domains, you must ensure that you keep the list of ports and ranges up to date because they might change. You can subscribe to [this RSS feed](https://go.microsoft.com/fwlink/p/?linkid=236301) to be updated when changes occur. It’s also a good practice to test whether all ports are opened by running the [Skype for Business Network Assessment Tool](https://www.microsoft.com/download/details.aspx?id=53885) on a regular basis. You can find out more about the functionality of this tool in the next section.

In the event of a proxy server being deployed, we recommend that you bypass the proxy server for all Teams services. Although using a proxy might work, it’s very likely that quality will be reduced due to media’s being forced to use TCP instead of UDP. For more information about proxy servers and bypassing, see [Office 365 URLs and IP address ranges](https://docs.microsoft.com/MicrosoftTeams/office-365-urls-ip-address-ranges).

<!--ENDOFSECTION-->

## Additional network considerations
### External Name Resolution

Ensure that all the client computers running Teams client can resolve external DNS queries to discover the services provided by Office 365.

### NAT Pool Size

When multiple users/devices access Office 365 using Network Address Translation (NAT) or Port Address Translation (PAT), you need to ensure that the  devices hidden behind each publicly routable IP address do not exceed the supported number.

To mitigate this risk, ensure adequate Public IP addresses are assigned to the NAT pools to prevent port exhaustion. Port exhaustion will cause internal end users and devices to face issues when connecting to the Office 365 services. For more information, see [NAT support with Office 365](https://support.office.com/article/NAT-support-with-Office-365-170e96ea-d65d-4e51-acac-1de56abe39b9).

### Intrusion Detection and Prevention Guidance

If your environment has an Intrusion Detection and/or Prevention System (IDS/IPS) deployed for an extra layer of security for outbound connections, ensure that any traffic with destination to Office 365 URLs is whitelisted.

## Test the network

After you’ve completed your planning and network preparation—including upgrading bandwidth and opening ports in the firewall—you should test your network’s performance. The results of this testing will paint a clearer picture of any network optimization or remediation required for the success of your Audio Conferencing or Phone System with Calling Plan implementation.

You can download the [Skype for Business Network Assessment Tool](https://www.microsoft.com/download/details.aspx?id=53885) to test whether your network is ready for Teams. The tool offers dual functionality: it can test whether all the correct ports have been opened, and it can test for network impairments.

After you download and install the tool, you can find it in C:\\Program Files\\Microsoft Skype for Business Network Assessment Tool. A detailed guide for how to use the tool, Usage.docx, is included in that directory.

### Test for opened ports

Open a Command prompt window and navigate to the Network Assessment Tool directory by entering **cd C:\\Program Files\\Microsoft Skype for Business Network Assessment Tool**. At the command prompt, start the test for opened ports by entering **networkassessmenttool.exe /connectivitycheck**

After running the checks, the tool will either display the message “Verifications Completed Successfully” or report on the ports that were blocked. It also generates a file named Connectivity_results.txt, which contains the output from the tool and stores it in the %userprofile%\\appdata\\local\\microsoft skype for business network assessment tool\\ directory.

We recommend that you run the connectivity checks on a regular basis to ensure the ports have been opened and are functioning correctly.

### Test for network impairments

To increase user satisfaction, you should limit any impairments on your network. The most common network impairments are delay (latency), packet loss, and jitter:

-   **Latency:** This is the time it takes to get an IP packet from point A to point B on the network. This network propagation delay is essentially tied to physical distance between the two points and the speed of light, including additional overhead taken by the various routers in between. Latency is measured as one-way or round-trip time.

-   **Packet loss**: This is often defined as a percentage of packets that are lost in a given window of time. Packet loss directly affects audio     quality—from small, individual lost packets having almost no impact to back-to-back burst losses that cause audio to cut out completely.

-   **Inter-packet arrival jitter, or simply jitter:** This is the average change in delay between successive packets. Most modern VoIP software, including Skype for Business, can adapt to some levels of jitter through buffering. It's only when the jitter exceeds the buffering that a participant will notice the effects of jitter.

The maximum values for these impairments are described in [Media quality and network connectivity performance](https://docs.microsoft.com/SkypeForBusiness/optimizing-your-network/media-quality-and-network-connectivity-performance). When testing for these impairments, we distinguish between two separate segments:

-   The *edge segment* is the segment in which your router lives. This is the closest logical network segment connected to the internet at each of your locations. In most cases, this is the connection point of the router, or possibly a perimeter network (also known as *DMZ*, *demilitarized zone*, and *screened subnet*). No further traffic that affects devices other than the router should occur between this segment and the internet.

-   The *client segment* is the logical network segment in which your clients reside.

You should test both segments by using the Network Assessment Tool. To test the segment, navigate to the directory and enter **networkassessmenttool.exe** at the command prompt. The results are written to a file named Results.tsv, and you can compare them to the [requirements](https://docs.microsoft.com/SkypeForBusiness/optimizing-your-network/media-quality-and-network-connectivity-performance) for each segment.

Note that both segments must meet the requirements for a high-quality deployment. We recommend that you run the tool multiple times for one hour straight to get a good indication of your network’s performance.

<!--ENDOFSECTION-->

## Network remediation

If the results of bandwidth planning, port testing, or network requirements testing show that your current network needs remediation before you deploy Teams, you can accomplish this in several ways: 

-   For insufficient bandwidth, upgrade connections so that traffic to Office 365 can flow unhindered.

-   For blocked ports, change firewall rules and retest the ports.

-   For network impairments, always perform a root-cause analysis.

Quality of service (QoS) can be used to battle impairments by prioritizing and separating traffic. Some organizations choose to deploy QoS to overcome bandwidth issues or restrict the amount of traffic flowing. This won’t improve quality and will lead to new problems. A root-cause analysis should always be performed when network impairments exceed requirements. QoS can be a solution. For more information, see [Quality of Service in Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/qos-in-teams).

>[!NOTE]
>Many networks evolve over time due to upgrades, expansion, or other business requirements. Ensure that you have operational processes in place to maintain these areas as part of your service management planning.


<table>
<tr><td>![](media/audio_conferencing_image7.png) <br/>Decision points</td><td><ul><li>Who will be responsible for completing proper network assessments across all network segments and organization locations?</li></ol></td></tr>
<tr><td>![](media/audio_conferencing_image9.png)<br/>Next steps</td><td><ul><li>You can perform a detailed network assessment to help ensure your network is ready for your Microsoft Teams deployment. For more information, see [Network Readiness Assessment](https://myadvisor.fasttrack.microsoft.com/CloudVoice/Offers?pageState=NetworkReadiness).</li><li>Perform network remediation based on the results of the Network Readiness Assessment for every network segment.</li></ol></td></tr>
</table>

<!--ENDOFSECTION-->

## Key takeaways

These are the main takeaways from this guidance. You must:

-   Open TCP ports 80 and 443 outgoing from clients that will use Teams.

-   Open UDP ports 3478 through 3481 outgoing from clients that will use Teams.

-   Ensure that you have sufficient bandwidth for deploying Teams by completing the [Network Planner](https://myadvisor.fasttrack.microsoft.com/CloudVoice/NetworkPlanner).

-   Run the [Network Assessment Tool](https://www.microsoft.com/download/details.aspx?id=53885) and ensure that you meet the requirements described in [Media quality and network connectivity performance](https://docs.microsoft.com/SkypeForBusiness/optimizing-your-network/media-quality-and-network-connectivity-performance) from both the edge segment and the client segment.
