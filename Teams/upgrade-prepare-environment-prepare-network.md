---
title: Prepare your network for Microsoft Teams|  Port Firewall Requirements
author: lolajacobsen
ms.author: lolaj
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
ms.reviewer: jastark, kojika
description: Use this guidance to prepare your network for Teams deployment and rollout 
localization_priority: Normal
search.appverid: MET150
ms.custom: Teams-upgrade-guidance
ms.collection: 
- Teams_ITAdmin_JourneyFromSfB
- M365-collaboration
appliesto:
- Microsoft Teams
---

![Upgrade journey diagram, emphasizing the Technical Readiness stage](media/upgrade-banner-tech-readiness.png "Stages of the upgrade journey, with emphasis on the Technical Readiness stage")

This article is part of the Technical Readiness stage of your upgrade journey, an activity you complete in parallel with the User Readiness stage. Before proceeding, confirm that you’ve completed these activities from previous stages:

- [Enlisted your project stakeholders](upgrade-enlist-stakeholders.md)
- [Defined your project scope](https://aka.ms/SkypetoTeams-Scope)
- [Understood coexistence and interoperability of Skype for Business and Teams](https://aka.ms/SkypeToTeams-Coexist)
- [Chosen your upgrade journey](upgrade-and-coexistence-of-skypeforbusiness-and-teams.md)

> [!Tip]
> Watch the following session to learn how to Teams leverages your network and how to best plan for optimal network connectivity: [Teams Network Planning](https://aka.ms/teams-networking)

# Prepare your network for upgrading to Teams

If you’re deploying audio, video, or meetings, you can take some additional steps to optimize your network for that functionality. Teams uses audio and video technology (codecs) that can adapt to—and therefore perform better under—most network conditions. To ensure optimal and consistent performance, you should prepare your network for Teams.

![Diagram describing the three components of quality](media/evaluate-my-environment-image1.png "Diagram describing the three components of quality, and how service management overlaps all three components. With a focus on the network.")

## Why should you prepare your network?

Before we look at the steps to be taken, it’s important to understand what can affect the performance of Teams and thereby user happiness and satisfaction. Three major risk areas can affect how users perceive network quality:

- Insufficient bandwidth available

- Firewall and proxy blockers

- Network impairments such as jitter and packet loss

The steps described below will help you determine whether your deployment might be affected by any of these factors and will help you move toward a resolution. Failing to prepare your network will likely lead to dissatisfied users and costly, ad-hoc fixes. By preparing your network—and your organization—for Teams, you can dramatically increase your chance of success.

<!--ENDOFSECTION-->

## Bandwidth planning

Microsoft Teams gives you the best audio, video and content sharing experience regardless of your network conditions. With variable codecs, media can be negotiated in limited bandwidth environments with minimal impact. But where bandwidth is not a concern, experiences can be optimized for quality, including up to 1080p video resolution, up to 30fps for video and 15fps for content, and high-fidelity audio.

[!INCLUDE [Bandwidth requirements](includes/bandwidth-requirements.md)]

### Local internet egress

Back-hauling traffic across the WAN increases latency and has a negative impact on quality and the user experience. Because Microsoft Teams runs on Microsoft’s large global network, there’s often a network peering location close to the user. A user will most likely get better performance by egressing out of a local internet point close to their location and on to our voice-optimized network as soon as possible. For some workloads, DNS requests are used to send traffic to the nearest front-end server. In such cases, it’s important that when using a local egress point, it’s paired with local DNS resolution.

Optimizing the network path to Microsoft’s global network will improve performance and ultimately provide the best experience for users. For more detail, see the blog post [Getting the best connectivity and performance in Office 365](https://techcommunity.microsoft.com/t5/Office-365-Blog/Getting-the-best-connectivity-and-performance-in-Office-365/ba-p/124694).

To get an optimal experience using real-time media within Microsoft Teams, you must meet the networking requirements for Office 365. For more information, see [Media Quality and Network Connectivity Performance for Skype for Business Online](/SkypeForBusiness/optimizing-your-network/media-quality-and-network-connectivity-performance).

The two defining network segments (Client to Microsoft Edge and Customer Edge to Microsoft Edge) must meet the following requirements:

|**Value** |**Client to Microsoft Edge** |**Customer Edge to Microsoft Edge** |
|---|---|---|
|**Latency (one way)** |< 50 ms |< 30 ms |
|**Latency (round-trip time, or RTT)** |< 100 ms |< 60 ms |
|**Burst packet loss** |<10% during any 200-ms interval |<1% during any 200-ms interval |
|**Packet loss** |<1% during any 15-sec interval |<0.1% during any 15-sec interval |
|**Packet inter-arrival jitter** |<30 ms during any 15-sec interval |<15 ms during any 15-sec interval |
|**Packet reorder** |<0.05% out-of-order packets |<0.01% out-of-order packets |

To test both network segments, you can use the [Network Assessment Tool](https://go.microsoft.com/fwlink/?linkid=855799). This tool can be deployed on both the client PC directly and on a PC connected to the Customer Network Edge. The tool includes limited documentation, but a deeper documentation around the usage of the tool can be found here: [Network Readiness Assessment](https://go.microsoft.com/fwlink/?linkid=855800). By running this Network Readiness Assessment, you can validate your network’s readiness to run real-time media applications, such as Microsoft Teams.

> [!NOTE]
> This is the same Network Readiness Assessment that we recommend be run by customers who are looking to successfully deploy Skype for Business.

## Test the network

After you’ve completed your planning and network preparation—including upgrading bandwidth and opening ports in the firewall—you should test your network’s performance. The results of this testing will paint a clearer picture of any network optimization or remediation required for the success of your Teams implementation.

You can download the [Skype for Business Network Assessment Tool](https://www.microsoft.com/download/details.aspx?id=53885) to test whether your network is ready for Teams. The tool offers dual functionality: it can test whether all the correct ports have been opened, and it can test for network impairments.

After you download and install the tool, you can find it in C:\Program Files (x86)\Microsoft Skype for Business Network Assessment Tool. A detailed guide for how to use the tool, Usage.docx, is included in that directory.

### Test for opened ports

Open a Command prompt window and navigate to the Network Assessment Tool directory by entering **cd C:\Program Files (x86)\Microsoft Skype for Business Network Assessment Tool**. At the command prompt, start the test for opened ports by entering **networkassessmenttool.exe /connectivitycheck**

After running the checks, the tool will either display the message “Verifications Completed Successfully” or report on the ports that were blocked. It also generates a file named Connectivity_results.txt, which contains the output from the tool and stores it in the %userprofile%\\appdata\\local\\microsoft skype for business network assessment tool\\ directory.

We recommend that you run the connectivity checks on a regular basis to ensure the ports have been opened and are functioning correctly.

### Test for network impairments

To increase user satisfaction, you should limit any impairments on your network. The most common network impairments are delay (latency), packet loss, and jitter:

- **Latency:** This is the time it takes to get an IP packet from point A to point B on the network. This network propagation delay is essentially tied to physical distance between the two points and the speed of light, including additional overhead taken by the various routers in between. Latency is measured as one-way or round-trip time.

- **Packet loss**: This is often defined as a percentage of packets that are lost in a given window of time. Packet loss directly affects audio quality—from small, individual lost packets having almost no impact to back-to-back burst losses that cause audio to cut out completely.

- **Inter-packet arrival jitter, or simply jitter:** This is the average change in delay between successive packets. Most modern VoIP software, including Skype for Business, can adapt to some levels of jitter through buffering. It's only when the jitter exceeds the buffering that a participant will notice the effects of jitter.

The maximum values for these impairments are described in [Media quality and network connectivity performance](/SkypeForBusiness/optimizing-your-network/media-quality-and-network-connectivity-performance). When testing for these impairments, we distinguish between two separate segments:

- The *edge segment* is the segment in which your router lives. This is the closest logical network segment connected to the internet at each of your locations. In most cases, this is the connection point of the router, or possibly a perimeter network (also known as *DMZ*, *demilitarized zone*, and *screened subnet*). No further traffic that affects devices other than the router should occur between this segment and the internet.

- The *client segment* is the logical network segment in which your clients reside.

You should test both segments by using the Network Assessment Tool. To test the segment, navigate to the directory and enter **networkassessmenttool.exe** at the command prompt. The results are written to a file named Results.tsv, and you can compare them to the [requirements](/SkypeForBusiness/optimizing-your-network/media-quality-and-network-connectivity-performance) for each segment.

Note that both segments must meet the requirements for a high-quality deployment. We recommend that you run the tool multiple times for one hour straight to get a good indication of your network’s performance.

## Network remediation

If the results of bandwidth planning, port testing, or network requirements testing show that your current network needs remediation before you deploy Teams, you can accomplish this in several ways:

- For insufficient bandwidth, upgrade connections so that traffic to Office 365 can flow unhindered.

- For blocked ports, change firewall rules and retest the ports.

- For network impairments, always perform a root-cause analysis.

Quality of service (QoS) can be used to battle impairments by prioritizing and separating traffic. Some organizations choose to deploy QoS to overcome bandwidth issues or restrict the amount of traffic flowing. This won’t improve quality and will lead to new problems. A root-cause analysis should always be performed when network impairments exceed requirements. QoS can be a solution. For more information, see [Quality of Service in Microsoft Teams](qos-in-teams.md).

>[!NOTE]
>Many networks evolve over time due to upgrades, expansion, or other business requirements. Ensure that you have operational processes in place to maintain these areas as part of your service management planning.

## Key takeaways

These are the main takeaways from this guidance. You must:

- Open TCP ports 80 and 443 outgoing from clients that will use Teams.

- Open UDP ports 3478 through 3481 outgoing from clients that will use Teams.

- Ensure that you have sufficient bandwidth for deploying Teams.

- Run the [Network Assessment Tool](https://www.microsoft.com/download/details.aspx?id=53885) and ensure that you meet the requirements described in [Media quality and network connectivity performance](/SkypeForBusiness/optimizing-your-network/media-quality-and-network-connectivity-performance) from both the edge segment and the client segment.

## Related Topics

[Video: Network Planning](https://aka.ms/teams-networking)
