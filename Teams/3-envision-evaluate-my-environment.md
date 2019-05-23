---
title: Evaluate your environment for Microsoft Teams cloud voice workloads
author: rmw2890
ms.author: Rowille
manager: serdars
ms.date: 03/13/2018
ms.topic: conceptual
ms.service: msteams
search.appverid: MET150
ms.reviewer: rowille
description: Use personas and network analysis to assess your organization's readiness, open the correct TCP and UDP ports, perform any network remediation.  
localization_priority: Normal
MS.collection: 
- Teams_ITAdmin_PracticalGuidance
- M365-collaboration
appliesto:
- Microsoft Teams
---

# Evaluate my environment

This article gives an overview of the requirements for properly evaluating your current environment for using cloud voice services. By evaluating your environment, you identify risks and requirements that will influence your overall cloud voice deployment. By identifying these items beforehand, you can adjust your planning to drive success.

## Introduction to evaluating your environment 

To achieve your objective key results (OKRs), you previously made key service
decisions. The next step is to perform environmental discovery to evaluate all
aspects relating to your IT and telephony infrastructure, networking, and
operations to confirm that your organization is ready to implement the solution.

Environmental discovery must include network readiness assessment to ensure your
network can support the implementation of the Audio Conferencing or Phone System
with Calling Plan services.

You identify technical risks as part of an environmental assessment and adoption
readiness evaluation, and develop a mitigation plan for each identified risk.
You should incorporate this information in the risk register.

<!--ENDOFSECTION-->

## Current environment

As part of your environmental discovery, include all matters related to end-user
computing, such as a readiness assessment of PCs and mobile devices to support
Audio Conferencing and Phone System with Calling Plan business use cases, from
hardware requirements to software requirements.

Environmental discovery can also uncover whether you need to [transfer phone
numbers to
Microsoft](https://docs.microsoft.com/SkypeForBusiness/what-are-calling-plans-in-office-365/transfer-phone-numbers-to-office-365).
Knowing this will help your organization adjust its project plan accordingly and
prepare the necessary information for number porting. You can use the [Environmental discovery for Microsoft Teams rollout](environmental-discovery-for-microsoft-teams-rollout.md)
from MyAdvisor to perform environmental discovery.

<table>
<tr><td><img src="media/audio_conferencing_image7.png" alt="An icon depicting decision points"/> <br/>Decision points</td><td><ul><li>Who will be responsible for completing an environment assessment?</li></ol></td></tr>
<tr><td><img src="media/audio_conferencing_image9.png" alt="An icon depicting the next steps"/><br/>Next steps</td><td><ul><li>Document the results of the environment assessment.</li></ol></td></tr>
</table>

<!--ENDOFSECTION-->

## Adoption and change management assessment capabilities 

Deployment puts a new technology at a user's fingertips, but business results are only realized after users truly adopt that solution as their own. To help ensure sustained adoption of a new solution, you'll need to focus your efforts on user readiness and change management. For optimal results, conduct user readiness planning as a parallel workstream to your technical readiness activities and incorporate the following activities:

-   **Organizational and user profiling:** Analysis of organizational receptiveness to change in addition to use case and persona analysis

-   **Readiness and resource preparation:** Creation of targeted and broad-reach awareness, training, and support resources, including focused value messaging to accelerate user buy-in

Use the following considerations to assess your organization’s preparedness to address user change management.

<table>
<tr><td><img src="media/audio_conferencing_image7.png" alt="An icon depicting decision points"/> <br/>Decision points</td><td><ul><li>Have you had previous success with user adoption of software or services?</li><li>Can you track usage uptake?</li><li>Do you have the resources to design and manage an initial&mdash;and ongoing&mdash;adoption campaign (awareness, training, and support)?</li><li>Do you have a dedicated user adoption/change management team, or can you invest in those resources to ensure business outcomes?</li></ol></td></tr>
<tr><td><img src="media/audio_conferencing_image9.png" alt="An icon depicting the next steps"/><br/>Next steps</td><td><ul><li>If you answered &quot;yes&quot; to all of the above, identify the right user change management stakeholders and begin your user readiness planning.</li><li>If you answered &quot;no&quot; to some or all of the above, consider engaging outside resources to assist with driving change management and adoption-related activities for your organization.</li></ol></td></tr>
</table>


<!--ENDOFSECTION-->

## Network readiness

Teams uses audio and video technology (codecs) that can adapt to—and therefore
perform better under—most network conditions. To ensure optimal and consistent
performance, you should prepare your network for Teams.

![Diagram describing the three components of quality, and how service management overlaps all three components](media/evaluate-my-environment-image1.png "Diagram describing the three components of quality, and how service management overlaps all three components. With a focus on the network.")

## Key takeaways

These are the main takeaways from this guidance. You must:

-   Open TCP ports 80 and 443 outgoing from clients that will use Teams.

-   Open UDP ports 3478 through 3481 outgoing from clients that will use Teams.

-   Ensure that you have sufficient bandwidth for deploying Teams by completing
    the [Network
    Planner](https://myadvisor.fasttrack.microsoft.com/CloudVoice/NetworkPlanner).

-   Run the [Network Assessment
    Tool](https://www.microsoft.com/download/details.aspx?id=53885) and ensure
    that you meet the requirements described in [Media quality and network
    connectivity
    performance](https://docs.microsoft.com/SkypeForBusiness/optimizing-your-network/media-quality-and-network-connectivity-performance)
    from both the edge segment and the client segment.

## Why should you prepare your network?

Before we look at the steps to be taken, it’s important to understand what can
affect the performance of Teams and thereby user happiness and satisfaction.
Three major risk areas can affect how users perceive network quality:

-   Insufficient bandwidth available

-   Firewall and proxy blockers

-   Network impairments such as jitter and packet loss

The steps described below will help you determine whether your deployment might
be affected by any of these factors and will help you move toward a resolution.
Failing to prepare your network will likely lead to dissatisfied users and
costly, ad-hoc fixes. By preparing your network—and your organization—for Teams,
you can dramatically increase your chance of success.

<!--ENDOFSECTION-->

## Bandwidth planning

The first step toward network readiness is ensuring your network has enough
bandwidth available for the modalities Teams will provide to users. Planning for
sufficient bandwidth is a fairly straightforward task and a very low-barrier
start to ensure your users will have a high-quality Teams experience.

You start your bandwidth planning journey for Teams on the [My Advisor
website](https://myadvisor.fasttrack.microsoft.com/) by using the Network
Planner. The Network Planner provides per-site bandwidth planning for Teams and
offers recommendations for optimizing network performance.

### Local internet egress

Many networks were designed to use a hub and spoke topology. In this topology,
internet traffic typically traverses the WAN to a central datacenter before it
emerges (egresses) to the internet. Often, this is done to centralize network
security devices with the goal of reducing overall cost.

Back-hauling traffic across the WAN increases latency and has a negative impact
on quality and the user experience. Because Microsoft Teams runs on Microsoft’s
large global network, there’s often a network peering location close to the
user. A user will most likely get better performance by egressing out of a local
internet point close to their location and on to our voice-optimized network as
soon as possible. For some workloads, DNS requests are used to send traffic to
the nearest front-end server. In such cases, it’s important that when using a
local egress point, it’s paired with local DNS resolution.

Optimizing the network path to Microsoft’s global network will improve
performance and ultimately provide the best experience for users. For more
detail, see the blog post [Getting the best connectivity and performance in
Office
365](https://techcommunity.microsoft.com/t5/Office-365-Blog/Getting-the-best-connectivity-and-performance-in-Office-365/ba-p/124694).

### VPN

VPNs provide a valuable service to many organizations. Unfortunately, they’re
typically not designed or configured to support real-time media. Some VPNs might
also not support UDP. VPNs also introduce an extra layer of encryption on top of
media traffic that’s already encrypted. In addition, connectivity to the Teams
service might not be efficient due to hair-pinning traffic through a VPN device.
Furthermore, they aren’t necessarily designed from a capacity perspective to
accommodate the anticipated loads that Teams will require.

The recommendation is to provide an alternate path that bypasses the VPN for
Teams traffic. This is commonly known as *split-tunnel VPN*. Split tunneling
means that traffic for Office 365 won’t traverse the VPN but will go directly to
Office 365. This change will have a positive impact on quality, but also
provides the secondary benefit of reducing load from the VPN devices and the
organization’s network.

To implement a split-tunnel, consult with your VPN vendor for the configuration
details.

### Wi-Fi

Like VPN, Wi-Fi networks aren’t necessarily designed or configured to support
real-time media. Planning for, or optimizing, a Wi-Fi network to support Teams
is an important consideration for a high-quality deployment.

There are several factors that come into play for optimizing a Wi-Fi network:

-   Implementing QoS or Wi-Fi Multimedia (WMM) to ensure that media traffic is
    getting prioritized accordingly over the Wi-Fi networks.

-   Planning and optimizing the Wi-Fi bands and access point placement. The 2.4
    GHz range may provide an adequate experience depending on access point
    placement, but access points are often affected by other consumer devices
    that operate in that range. The 5 GHz range is better suited to real-time
    media due to their dense range but requires more access points to get
    sufficient coverage. Endpoints also need to support that range and be
    configured to leverage those bands accordingly.

-   If dual-band Wi-Fi networks are deployed, consider implementing band
    steering. Band steering is a technique implemented by Wi-Fi vendors to
    influence dual-band clients to use the 5 GHz range.

-   When access points of the same channel are too close together they can cause
    signal overlap and unintentionally compete, resulting in a bad experience
    for the user. Ensure that access points that are next to each other are on
    channels that don’t overlap.

Each wireless vendor has its own recommendations for deploying its wireless
solution. We recommend that you consult your vendor for specific guidance.

<!--ENDOFSECTION-->

## Firewall and proxy requirements

Microsoft Teams connects to Microsoft Online Services and needs internet
connectivity for this. For Teams to function correctly, you must open TCP ports
80 and 443 from the clients to the internet, and UDP ports 3478 through 3481
from the clients to the internet. The TCP ports are used to connect to web-based
content such as SharePoint Online, Exchange Online, and the Teams Chat services.
Plug-ins and connectors also connect over these TCP ports. The four UDP ports
are used for media such as audio and video, to ensure they flow correctly.

Opening these ports is essential for a reliable Teams deployment. Blocking these
ports is unsupported and will have an effect on media quality.

If your organization requires that you specify the exact IP address ranges and
domains to which these ports should be opened, you can restrict the target IP
ranges and domains for these ports. For a list of exact ports, protocols, and IP
ranges, see [Office 365 URLs and IP address
ranges](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_teams).
If you choose to restrict the target IP address ranges and domains, you must
ensure that you keep the list of ports and ranges up to date because they might
change. You can subscribe to [this RSS
feed](https://go.microsoft.com/fwlink/p/?linkid=236301) to be updated when
changes occur. It’s also a good practice to test whether all ports are opened by
running the [Skype for Business Network Assessment
Tool](https://www.microsoft.com/download/details.aspx?id=53885) on a
regular basis. You can find out more about the functionality of this tool in the
next section.

In the event of a proxy server being deployed, we recommend that you bypass the
proxy server for all Teams services. Although using a proxy might work, it’s
very likely that quality will be reduced due to media’s being forced to use TCP
instead of UDP. For more information about proxy servers and bypassing, see
[Office 365 URLs and IP address
ranges](https://docs.microsoft.com/MicrosoftTeams/office-365-urls-ip-address-ranges).

<!--ENDOFSECTION-->

## Test the network

After you’ve completed your planning and network preparation—including upgrading
bandwidth and opening ports in the firewall—you should test your network’s
performance. The results of this testing will paint a clearer picture of any
network optimization or remediation required for the success of your Audio
Conferencing or Phone System with Calling Plan implementation.

You can download the [Skype for Business Network Assessment
Tool](https://www.microsoft.com/download/details.aspx?id=53885) to test whether
your network is ready for Teams. The tool offers dual functionality: it can test
whether all the correct ports have been opened, and it can test for network
impairments.

After you download and install the tool, you can find it in C:\\Program
Files\\Microsoft Skype for Business Network Assessment Tool. A detailed guide
for how to use the tool, Usage.docx, is included in that directory.

### Test for opened ports

Open a Command prompt window and navigate to the Network Assessment Tool
directory by entering **cd C:\\Program Files\\Microsoft Skype for Business
Network Assessment Tool**. At the command prompt, start the test for opened
ports by entering **networkassessmenttool.exe /connectivitycheck**

After running the checks, the tool will either display the message
“Verifications Completed Successfully” or report on the ports that were blocked.
It also generates a file named Connectivity_results.txt, which contains the
output from the tool and stores it in the
%userprofile%\\appdata\\local\\microsoft skype for business network assessment
tool\\ directory.

We recommend that you run the connectivity checks on a regular basis to ensure
the ports have been opened and are functioning correctly.

### Test for network impairments

To increase user satisfaction, you should limit any impairments on your network.
The most common network impairments are delay (latency), packet loss, and
jitter:

-   **Latency:** This is the time it takes to get an IP packet from point A to
    point B on the network. This network propagation delay is essentially tied
    to physical distance between the two points and the speed of light,
    including additional overhead taken by the various routers in between.
    Latency is measured as one-way or round-trip time.

-   **Packet loss**: This is often defined as a percentage of packets that are
    lost in a given window of time. Packet loss directly affects audio
    quality—from small, individual lost packets having almost no impact to
    back-to-back burst losses that cause audio to cut out completely.

-   **Inter-packet arrival jitter, or simply jitter:** This is the average
    change in delay between successive packets. Most modern VoIP software,
    including Skype for Business, can adapt to some levels of jitter through
    buffering. It's only when the jitter exceeds the buffering that a
    participant will notice the effects of jitter.

The maximum values for these impairments are described in [Media quality and
network connectivity
performance](https://docs.microsoft.com/SkypeForBusiness/optimizing-your-network/media-quality-and-network-connectivity-performance).
When testing for these impairments, we distinguish between two separate
segments:

-   The *edge segment* is the segment in which your router lives. This is the
    closest logical network segment connected to the internet at each of your
    locations. In most cases, this is the connection point of the router, or
    possibly a perimeter network (also known as *DMZ*, *demilitarized zone*, and
    *screened subnet*). No further traffic that affects devices other than the
    router should occur between this segment and the internet.

-   The *client segment* is the logical network segment in which your clients
    reside.

You should test both segments by using the Network Assessment Tool. To test the
segment, navigate to the directory and enter **networkassessmenttool.exe** at
the command prompt. The results are written to a file named Results.tsv, and you
can compare them to the
[requirements](https://docs.microsoft.com/SkypeForBusiness/optimizing-your-network/media-quality-and-network-connectivity-performance)
for each segment.

Note that both segments must meet the requirements for a high-quality
deployment. We recommend that you run the tool multiple times for one hour
straight to get a good indication of your network’s performance.

<!--ENDOFSECTION-->

## Network remediation

If the results of bandwidth planning, port testing, or network requirements
testing show that your current network needs remediation before you deploy
Teams, you can accomplish this in several ways:

-   For insufficient bandwidth, upgrade connections so that traffic to Office
    365 can flow unhindered.

-   For blocked ports, change firewall rules and retest the ports.

-   For network impairments, always perform a root-cause analysis.

Quality of service (QoS) can be used to battle impairments by prioritizing and
separating traffic. Some organizations choose to deploy QoS to overcome
bandwidth issues or restrict the amount of traffic flowing. This won’t improve
quality and will lead to new problems. A root-cause analysis should always be
performed when network impairments exceed requirements. QoS can be a solution.
For more information, see [Quality of Service in Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/qos-in-teams).

>[!NOTE]
>Many networks evolve over time due to upgrades, expansion, or other
business requirements. Ensure that you have operational processes in place to
maintain these areas as part of your service management planning.


<table>
<tr><td><img src="media/audio_conferencing_image7.png" alt="An icon depicting decision points"/> <br/>Decision points</td><td><ul><li>Who will be responsible for completing proper network assessments across all network segments and organization locations?</li></ol></td></tr>
<tr><td><img src="media/audio_conferencing_image9.png" alt="An icon depicting the next steps"/><br/>Next steps</td><td><ul><li>You can perform a detailed network assessment to help ensure your network is ready for your Microsoft Teams deployment. For more information, see <a href="https://myadvisor.fasttrack.microsoft.com/CloudVoice/Offers?pageState=NetworkReadiness" data-raw-source="[Network Readiness Assessment](https://myadvisor.fasttrack.microsoft.com/CloudVoice/Offers?pageState=NetworkReadiness)">Network Readiness Assessment</a>.</li><li>Perform network remediation based on the results of the Network Readiness Assessment for every network segment.</li></ol></td></tr>
</table>

<!--ENDOFSECTION-->