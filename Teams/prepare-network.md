---
title: Prepare your organization's network for Teams
author: SerdarSoysal
ms.author: serdars
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: jastark, kojika
audience: admin
description: Learn about preparing your organization's network for Microsoft Teams, including network requirements, network optimization, and bandwidth requirements.
ms.localizationpriority: high
search.appverid: MET150
ms.collection: 
  - M365-collaboration
  - m365initiative-deployteams
f1.keywords:
- NOCSH
appliesto: 
  - Microsoft Teams
ms.custom: 
  - seo-marvel-mar2020
---

# Prepare your organization's network for Microsoft Teams 

## Network requirements

If you've already [optimized your network for Microsoft 365 or Office 365](/Office365/Enterprise/assessing-network-connectivity), you're probably ready for Microsoft Teams. In any case - and especially if you're rolling out Teams quickly as your first Microsoft 365 or Office 365 workload to support **remote workers** - check the following before you begin your Teams rollout:

1.  Do all your locations have internet access (so they can connect to Microsoft 365 or Office 365)? In addition to normal web traffic, make sure you've opened the TCP ports and IP addresses listed for Teams in [Office 365 URLs and IP address ranges](/office365/enterprise/urls-and-ip-address-ranges#skype-for-business-online-and-microsoft-teams).

    > [!IMPORTANT]
    > If you need to federate with Skype for Business, either on-premises or online, you will need to configure an additional DNS record.
    >
    >|DNS record  |Service  |Protocol  |Priority  |Weight  |Port  |Target  |
    >|---------|---------|---------|---------|---------|---------|---------|
    >|SRV     |sipfederationtls     |TCP     |100     |1     |5061     |sipfed.online.lync.com     |
    
2.  Do you have a verified domain for Microsoft 365 or Office 365 (for example, contoso.com)?
    
    - If your organization hasn't rolled out Microsoft 365 or Office 365, see [Get started](/microsoft-365/admin/admin-overview/get-started-with-office-365).
    - If your organization hasn't added or configured a verified domain for Microsoft 365 or Office 365, see the [Domains FAQ](/microsoft-365/admin/setup/domains-faq).

3.  Has your organization deployed Exchange Online and SharePoint Online?
    
    - If your organization doesn't have Exchange Online, see [Understand how Exchange and Microsoft Teams interact](exchange-teams-interact.md).
    - If your organization doesn't have SharePoint Online, see [Understand how SharePoint Online and OneDrive for Business interact with Microsoft Teams](sharepoint-onedrive-interact.md).

Once you've verified that you meet these network requirements, you may be ready to [Roll out Teams](./deploy-overview.md). If you're a large multinational enterprise, or if you know you've got some network limitations, read on to learn how to assess and optimize your network for Teams.

> [!IMPORTANT]
> **For educational institutions**: If your organization is an educational institution and you use a Student Information System (SIS), [deploy School Data Sync](/schooldatasync/) before you roll out Teams.
>  
> **Running on-premises Skype for Business Server**: If your organization is running on-premises Skype for Business Server (or Lync Server), you must [configure Azure AD Connect](/skypeforbusiness/hybrid/configure-azure-ad-connect) to synchronize your on-premises directory with Microsoft 365 or Office 365.

### Best practice: Monitor your network using CQD and call analytics 

Use the [Call Quality Dashboard (CQD)](turning-on-and-using-call-quality-dashboard.md) to gain insight into the quality of calls and meetings in Teams. CQD can help you optimize your network by keeping a close eye on quality, reliability, and the user experience. CQD looks at aggregate telemetry for an entire organization where overall patterns can become apparent, which lets you identify problems and plan remediation. Additionally, CQD provides rich metrics reports that provide insight into overall quality, reliability, and user experience. 

You'll use [call analytics](set-up-call-analytics.md) to investigate call and meeting problems for an individual user.

## Network optimization

The following tasks are optional and aren't required for rolling out Teams, especially if you're a small business and you've already rolled out Microsoft 365 or Office 365. Use this guidance to optimize your network and Teams performance or if you know you've got some network limitations.

You might want to do additional network optimization if:

  - Teams runs slowly (maybe you have insufficient bandwidth)
  - Calls keep dropping (might be due to firewall or proxy blockers)
  - Calls have static and cut out, or voices sound like robots (could be jitter or packet loss)

For an in-depth discussion of network optimization, including guidance for identifying and fixing network impairments, read [Microsoft 365 and Office 365 Network Connectivity Principles](/microsoft-365/enterprise/microsoft-365-network-connectivity-principles).

<table>
<thead>
<tr class="header">
<th>Network optimization task</th>
<th>Details</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Network planner</td>
<td><p>For help assessing your network, including bandwidth calculations and network requirements across your org's physical locations, check out the <a href="/microsoftteams/network-planner">Network Planner</a> tool, in the <a href="https://admin.teams.microsoft.com">Teams admin center</a>. When you provide your network details and Teams usage, the Network Planner calculates your network requirements for deploying Teams and cloud voice across your organization's physical locations.</p>
<p>For an example scenario, see <a href="/microsoftteams/tutorial-network-planner-example">Using Network Planner - example scenario</a>.</p></td>
</tr>
<tr class="even">
<td>Advisor for Teams</td>
<td><a href="/microsoftteams/use-advisor-teams-roll-out">Advisor for Teams</a> is part of the <a href="https://admin.teams.microsoft.com">Teams admin center</a>. It assesses your Microsoft 365 or Office 365 environment and identifies the most common configurations that you may need to update or modify before you can successfully roll out Teams.</td>
</tr>
<tr class="odd">
<td>External Name Resolution</td>
<td>Be sure that all computers running the Teams client can resolve external DNS queries to discover the services provided by Microsoft 365 or Office 365 and that your firewalls are not preventing access. For information about configuring firewall ports, go to <a href="/microsoftteams/office-365-urls-ip-address-ranges">Microsoft 365 and Office 365 URLs and IP ranges</a>.</td>
</tr>
<tr class="odd">
<td>Maintain session persistence</td>
<td>Make sure your firewall doesn't change the mapped Network Address Translation (NAT) addresses or ports for UDP.</td>
</tr><tr class="odd">
<td>Validate NAT pool size</td>
<td>Validate the network address translation (NAT) pool size required for user connectivity. When multiple users and devices access Microsoft 365 or Office 365 using <a href="/office365/enterprise/nat-support-with-office-365">Network Address Translation (NAT) or Port Address Translation (PAT)</a>, you need to ensure that the devices hidden behind each publicly routable IP address do not exceed the supported number. Ensure that adequate public IP addresses are assigned to the NAT pools to prevent port exhaustion. Port exhaustion will contribute to internal users and devices being unable to connect to the Microsoft 365 or Office 365 service.</td>
</tr>
<tr class="even">
<td>Routing to Microsoft data centers</td>
<td><a href="/office365/enterprise/client-connectivity">Implement the most efficient routing to Microsoft data centers</a>. Identify locations that can use local or regional egress points to connect to the Microsoft network as efficiently as possible.</td>
</tr>
<tr class="odd">
<td>Intrusion Detection and Prevention Guidance</td>
<td>If your environment has an <a href="/azure/network-watcher/network-watcher-intrusion-detection-open-source-tools">Intrusion Detection</a> or Prevention System (IDS/IPS) deployed for an extra layer of security for outbound connections, be sure to allow all Microsoft 365 or Office 365 URLs.</td>
</tr>
<tr class="even">
<td>Configure split-tunnel VPN</td>
<td><p>We recommend that you provide an alternate path for Teams traffic that bypasses the virtual private network (VPN), commonly known as <a href="/windows/security/identity-protection/vpn/vpn-routing">split-tunnel VPN</a>. Split tunneling means that traffic for Microsoft 365 or Office 365 doesn't go through the VPN but instead goes directly to Microsoft 365 or Office 365. Bypassing your VPN will have a positive impact on Teams quality, and it reduces load from the VPN devices and the organization's network. To implement a split-tunnel VPN, work with your VPN vendor.</p>
<p>Other reasons why we recommend bypassing the VPN: 
<ul>
<li><p>VPNs are typically not designed or configured to support real-time media.</p></li> 
<li><p>Some VPNs might also not support UDP (which is required for Teams).</p></li> 
<li><p>VPNs also introduce an extra layer of encryption on top of media traffic that's already encrypted.</p></li> 
<li><p>Connectivity to Teams might not be efficient due to hair-pinning traffic through a VPN device.</p></li></td>
</tr>
<tr class="odd">
<td>Implement QoS</td>
<td><a href="/microsoftteams/qos-in-teams">Use Quality of Service (QoS)</a> to configure packet prioritization. This will improve call quality in Teams and help you monitor and troubleshoot call quality. QoS should be implemented on all segments of a managed network. Even when a network has been adequately provisioned for bandwidth, QoS provides risk mitigation in the event of unanticipated network events. With QoS, voice traffic is prioritized so that these unanticipated events don't negatively affect quality.</td>
</tr>
<tr class="even">
<td>Optimize WiFi</td>
<td><p>Similar to VPN, WiFi networks aren't necessarily designed or configured to support real-time media. Planning for, or optimizing, a WiFi network to support Teams is an important consideration for a high-quality deployment. Consider these factors:</p>
<ul>
<li><p>Implement QoS or WiFi Multimedia (WMM) to ensure that media traffic is getting prioritized appropriately over your WiFi networks.</p></li>
<li><p>Plan and optimize the WiFi bands and access point placement. The 2.4 GHz range might provide an adequate experience depending on access point placement, but access points are often affected by other consumer devices that operate in that range. The 5 GHz range is better suited to real-time media due to its dense range, but it requires more access points to get sufficient coverage. Endpoints also need to support that range and be configured to leverage those bands accordingly.</p></li>
<li><p>If you're using dual-band WiFi networks, consider implementing band steering. <em>Band steering</em> is a technique implemented by WiFi vendors to influence dual-band clients to use the 5 GHz range.</p></li>
<li><p>When access points of the same channel are too close together, they can cause signal overlap and unintentionally compete, resulting in a bad experience for the user. Ensure that access points that are next to each other are on channels that don't overlap.</p></li>
</ul>
<p>Each wireless vendor has its own recommendations for deploying its wireless solution. Consult your WiFi vendor for specific guidance.</p></td>
</tr>
</tbody>
</table>

## Bandwidth requirements

Teams is designed to give the best audio, video, and content sharing experience regardless of your network conditions. That said, when bandwidth is insufficient, Teams prioritizes audio quality over video quality.

Where bandwidth isn't limited, Teams optimizes media quality, including high-fidelity audio, up to 1080p video resolution, and up to 30fps (frames per second) for video and content.

This table describes how Teams uses bandwidth. Teams is always conservative on bandwidth utilization and can deliver HD video quality in under 1.5Mbps. The actual bandwidth consumption in each audio/video call or meeting will vary based on several factors, such as video layout, video resolution, and video frames per second. When more bandwidth is available, quality and usage will increase to deliver the best experience.

:::row:::
   :::column span="":::
      **Modality**
   :::column-end:::
   :::column span="3":::
      **Bandwidth requirements (bitrate kilobit/s up/down)**    
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="":::
   :::column-end:::
   :::column span="":::
      **Minimum**
   :::column-end:::
   :::column span="":::
      **Recommended**
   :::column-end:::
   :::column span="":::
      **Best performance**
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="4":::
      **Audio**
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="":::
        One-to-one
   :::column-end:::
   :::column span="":::
        10/10
   :::column-end:::
   :::column span="":::
        58/58
   :::column-end:::
   :::column span="":::
        76/76
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="":::
        Meetings
   :::column-end:::
   :::column span="":::
        10/10
   :::column-end:::
   :::column span="":::
        58/58
   :::column-end:::
   :::column span="":::
        76/76
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="4":::
      **Video**
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="":::
        One-to-one
   :::column-end:::
   :::column span="":::
        150/150
   :::column-end:::
   :::column span="":::
        1,500/1,500
   :::column-end:::
   :::column span="":::
        4,000/4,000
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="":::
        Meetings
   :::column-end:::
   :::column span="":::
        150/200
   :::column-end:::
   :::column span="":::
        2,500/4,000
   :::column-end:::
   :::column span="":::
        4,000/4,000
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="4":::
      **Screen sharing**
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="":::
        One-to-one
   :::column-end:::
   :::column span="":::
        200/200
   :::column-end:::
   :::column span="":::
        1,500/1,500
   :::column-end:::
   :::column span="":::
        4,000/4,000
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="":::
        Meetings
   :::column-end:::
   :::column span="":::
        250/250
   :::column-end:::
   :::column span="":::
        2,500/2,500
   :::column-end:::
   :::column span="":::
        4,000/4,000
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="4":::
      **Together Mode**
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="":::
        One-to-one
   :::column-end:::
   :::column span="":::
        N/A
   :::column-end:::
   :::column span="":::
        N/A
   :::column-end:::
   :::column span="":::
        N/A
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="":::
        Meetings
   :::column-end:::
   :::column span="":::
        1,000/1,500
   :::column-end:::
   :::column span="":::
        1,500/2,500
   :::column-end:::
   :::column span="":::
        2,500/4,000
   :::column-end:::
:::row-end:::

**Minimum**, **Recommended**, and **Best performance** bandwidth requirements are based on per-endpoint usage. Typically, there's one endpoint per user, such as a computer or mobile device. However, if a user joins a Teams meeting on *both* a computer *and* a mobile device, two endpoints are associated with that user.

- **Minimum** Bandwidth requirements for video calls are up to 240p resolution, screen sharing content frame rates adaptive 1.875 to 7.5fps, and Together Mode/Large Gallery video up to 540p resolution.  

- **Recommended** Bandwidth requirements for video calls are up to 1080p resolution<sup>\*</sup>, screen sharing content frame rates adaptive 7.5 to 30fps, and Together Mode/Large Gallery video up to 1080p resolution<sup>\*</sup>.  

- **Best Performance** Guidance allows higher fidelity video for larger attendee meetings, high loss environments, and higher motion content with screen sharing content frame rates adaptive 15 to 30fps.

<sup>\*</sup>Expect up to 1080p quality but depending on your network conditions, video resolution and quality will be optimized accordingly.  

## Related Topics

[Microsoft 365 and Office 365 Network Connectivity Principles](/microsoft-365/enterprise/microsoft-365-network-connectivity-principles)

[Worldwide endpoints: Skype for Business Online and Teams](/office365/enterprise/urls-and-ip-address-ranges#skype-for-business-online-and-microsoft-teams)

[Proxy servers for Teams](proxy-servers-for-skype-for-business-online.md)

[Media in Teams: Why meetings are simple](https://aka.ms/teams-media)

[Media in Teams: Deep dive into media flows](https://aka.ms/teams-media-flows)

[Identity models and authentication in Teams](identify-models-authentication.md)

[How to roll out Teams](./deploy-overview.md)

[Teams Troubleshooting](/MicrosoftTeams/troubleshoot/teams)
