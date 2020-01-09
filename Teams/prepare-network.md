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

If you've already optimized your network for Office 365, you're probably ready for Microsoft Teams. In any case, check the following before you begin your Teams rollout:

1. Do all your locations have internet access (so they can connect to Office 365)? At a minimum, verify that the following common ports are open to the internet from all locations:

    - Open TCP ports **80** and **443** for outgoing traffic from clients that will use Teams.    
    - Open UDP ports **3478** through **3481** for outgoing traffic from clients that will use Teams.

1. Do you have a verified domain for Office 365 (for example, contoso.com)?
    -   If your organization hasn't rolled out Office 365, see [Getting Started with Office 365 for business](https://support.office.com/article/Get-started-with-Office-365-for-Business-d6466f0d-5d13-464a-adcb-00906ae87029).

    -   If your organization hasn't added or configured a verified domain for Office 365, see [Verify your Office 365 domain](https://support.office.com/article/Verify-your-Office-365-domain-to-prove-ownership-nonprofit-or-education-status-or-to-activate-Yammer-87d1844e-aa47-4dc0-a61b-1b773fd4e590).

1. Has your organization deployed Exchange Online and SharePoint Online?
    - If your organization doesn't have Exchange Online, see [Understand how Exchange and Microsoft Teams interact](exchange-teams-interact.md).

    - If your organization doesn't have SharePoint Online, see [Understand how SharePoint Online and OneDrive for Business interact with Microsoft Teams](sharepoint-onedrive-interact.md).

### For educational institutions
If your organization is an educational institution and you use a Student Information System (SIS), [deploy School Data Sync](https://docs.microsoft.com/schooldatasync/) before you roll out Teams.

### Running on-premises Skype for Business Server
If your organization is running on-premises Skype for Business Server (or Lync Server), you must [configure Azure AD Connect](../Skype/SfbHybrid/hybrid/configure-azure-ad-connect.md) to synchronize your on-premises directory with Office 365. 

Once you've got your network ready for Teams, go to [How to roll out Teams](How-to-roll-out-teams.md) to get started.

## Use Advisor for Teams
For a guided journey through your Teams rollout, use [Advisor for Teams](use-advisor-teams-roll-out.md). In addition to creating a Deployment team that helps you manage your rollout, Advisor for Teams assesses your Office 365 environment and identifies the most ocmmon configurations that you may need to update or modify before you can successfully roll out Teams. Advisor for Teams is part of the [Teams admin center](https://admin.teams.microsoft.com) (click the **Start** button in the **Deployment Teams workload** widget on the Dashboard).

## Use Network Planner

For help assessing your network, including bandwidth calculations and network requirements across your org's physical locations, check out the [Network Planner](network-planner.md) tool, in the [Teams admin center](https://admin.teams.microsoft.com) (**Planner** > **Network planner**). When you provide your network details and Teams usage, the Network Planner calculates your network requirements for deploying Teams and cloud voice across your organization’s physical locations.

For an example scenario, see [Using Network Planner - example scenario](tutorial-network-planner-example).

**========> From Julia's optimize-network topic. This MAY include everything we need from prepare-environment-prepare-network and original prepare-network.**
## Network optimization

The following steps are optional and aren't required for Teams to be up and running. Use this guidance to optimize your network if you want to improve Teams performance.

Reasons why you might want to do additional network optimization:

**LOLA: I want to list SYMPTOMS instead of root causes here. What are the SYMPTOMS of each of these items?**

- Insufficient bandwidth available
- Firewall and proxy blockers
- Network impairments such as jitter and packet loss

For an in-depth discussion of network optimization for Teams, read [Media Quality and Network Connectivity Performance for Teams and Skype for Business Online](../Skype/SfbOnline/optimizing-your-network/media-quality-and-network-connectivity-performance.md).

**HEIDI: Can you de-geek the following sections at all? If it's possible to explain these things in plainer English, please do!**
**HEIDI: I'm finding that a lot of the in-depth info from upgrade-prepare-environment-prepare-network is NOT included here. Trying to decide how to handle this. Keep the Upgrade topic & link to it (bookmarks)? Or pull everything into THIS topic?**

[Validate the network address translation (NAT) pool size required for user connectivity](https://docs.microsoft.com/office365/enterprise/nat-support-with-office-365?redirectSourcePath=%252farticle%252fNAT-support-with-Office-365-170e96ea-d65d-4e51-acac-1de56abe39b9)
When multiple users and devices access Office 365 using Network Address Translation (NAT) or Port Address Translation (PAT), you need to ensure that the devices hidden behind each publicly routable IP address do not exceed the supported number. Ensure that adequate public IP addresses are assigned to the NAT pools to prevent port exhaustion. Port exhaustion will contribute to internal users and devices being unable to connect to the Office 365 service.

[Implement the most efficient routing to Microsoft data centers](https://docs.microsoft.com/office365/enterprise/client-connectivity?redirectSourcePath=%252farticle%252fClient-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b): Identify locations that can use local or regional egress points to connect to the Microsoft network as efficiently as possible. 

**Intrusion Detection and Prevention Guidance**: If your environment has an Intrusion Detection and/or Prevention System (IDS/IPS) deployed for an extra layer of security for outbound connections, ensure that any traffic with destination to Office 365 URLs is whitelisted.

**External Name Resolution**: Ensure that all the client computers running the Teams client can resolve external DNS queries to discover the services provided by Office 365 and that your firewalls are not preventing access. For information about configuring firewall ports, go to [Office 365 URLs and IP ranges](office-365-urls-ip-address-ranges.md).

[Configure split-tunnel VPN](upgrade-prepare-environment-prepare-network.md#vpn): We recommend that you provide an alternate path for Teams traffic that bypasses the VPN, commonly known as split-tunnel VPN. Split tunneling means that traffic for Office 365 won’t traverse the VPN but goes directly to Office 365. This change will have a positive impact on quality, but also provides the secondary benefit of reducing load from the VPN devices and the organization’s network. To implement a split-tunnel VPN, work with your VPN vendor. 

[Configure packet prioritization by using QoS](qos-in-teams.md): Use Quality of Service (QoS) to improve call quality in Teams and to monitor and troubleshoot call quality. QoS should be implemented on all segments of a managed network. Even when a network has been adequately provisioned for bandwidth, QoS provides risk mitigation in the event of unanticipated network events. With QoS, voice traffic is prioritized so that these unanticipated events don’t negatively affect quality. 

[Optimize Wi-Fi networks for quality and performance](upgrade-prepare-environment-prepare-network.md#wi-fi): Like VPN, Wi-Fi networks aren’t necessarily designed or configured to support real-time media. Planning for, or optimizing, a Wi-Fi network to support Teams is an important consideration for a high-quality deployment.

[Implementing QoS or Wi-Fi Multimedia (WMM) to ensure that media traffic over the Wi-Fi networks is prioritized](upgrade-plan-for-quality.md): Planning and optimizing Wi-Fi bands and access point placement. The 2.4 GHz range might provide adequate performance, depending on access point placement. Consult your Wi-Fi vendor for specific guidance.

*See also*, [Wi-Fi recommendations for endpoints](envision-planning-for-service-management-and-quality-complete-guide.md#wi-fi).  **LOLA: THIS IS NOT IN THE TOC AND IS GOING AWAY. FIGURE OUT WHAT TO DO WITH THIS INFORMATION. DO NOT LINK TO IT HERE.**

[Validate network connectivity by using the Network Assessment Tool](https://www.microsoft.com/download/details.aspx?id=53885): Use the Network Assessment Tool for Teams to test connectivity to all IP addresses and ports used in Teams calls and meetings. Download the tool and see Usage.docx for details about how to use the tool and interpret the test results. We recommend that you run the tool from a client PC in each location where Teams will be used.

[Monitor your network using CQD and call analytics](turning-on-and-using-call-quality-dashboard.md): You use the Call Quality Dashboard (CQD) to gain insight into the quality of calls made by using Teams. CQD is designed to help you optimize your network and keep a close eye on quality, reliability, and the user experience. CQD looks at aggregate telemetry for an entire organization where overall patterns can become apparent, allowing staff to make informed assessments and plan remediation activities to maximize impact. Additionally, CQD provides reports of metrics that provide insight into overall quality, reliability, and user experience. To investigate call problems for individual users, use [per-user call analytics](set-up-call-analytics.md).

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

**HEIDI: The following information was commented out of the article. It's in more depth than the bandwidth-requirements article included above. We should verify this table with PM and either add it to bandwidth-requirements or kill it.**

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



## Related Topics

[Video: Network Planning](https://aka.ms/teams-networking)

[Identity models and authentication in Teams](identify-models-authentication)
