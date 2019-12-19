---
title: Optimize your network
author: JuDegn
ms.author: JuDegn
manager: serdars
ms.date: 01/28/2019
ms.topic: article
audience: admin
ms.service: msteams
ms.reviewer: lolaj
description: Optimize your network
localization_priority: Priority
search.appverid: MET150
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# Optimize your network

Checklist for optimizing your network
- Validate the Network Assessment Tool (NAT) pool size required for user connectivity
- Implement the most efficient routing to MS datacenters
- Configure firewall ports requested for connectivity to Teams
- Configure proxy servers
- Configure split-tunnel VPN
- Configure packet prioritization by using QoS
- Optimize Wi-Fi networks for quality and performance
- Validate network connectivity by using the Network Assessment Tool
- Monitor your network using CQC/DA
- Validate the Network Assessment Tool (NAT) pool size required for user connectivity
- Ensure that adequate public IP addresses are assigned to the NAT pools to prevent port exhaustion. Port exhaustion will contribute to internal users and devices being unable to connect to the Office 365 service. See also, NAT support with Office 365.

## Step 1: Validate the Network Assessment Tool (NAT) pool size required for user connectivity]()
Ensure that adequate public IP addresses are assigned to the NAT pools to prevent port exhaustion. Port exhaustion will contribute to internal users and devices being unable to connect to the Office 365 service.

## Step 1: Implement the most efficient routing to MS datacenters
Identify locations that can use local or regional egress points to connect to the Microsoft network as efficiently as possible. See also, Office 365 Client Connectivity.

## Step 1: Configure firewall ports requested for connectivity to Teams
Review Office 365 URLs and IPs to identify and test the firewall ports that are required for connectivity between on-premises clients and servers and Office 365 services. You must open all ports on your firewalls. Failing to open some ports or ranges will negatively affect user experience. See also, Firewall and proxy requirements.

## Step 1: Configure proxy servers]()
Configure your environment so that proxy servers are bypassed, and you can connect users directly to Office 365 by using UDP, for the best audio and video quality. When real-time media is forced to traverse a proxy server, the media stack in Teams is forced to fail back to TCP, which negatively affects quality.

> [!NOTE]
> When it comes to Teams traffic over proxies, Microsoft recommends bypassing proxies. Proxies don't make Teams more secure because the traffic is already encrypted.

Using a proxy can cause issues. Performance-related problems can be introduced to the environment through latency and packet loss. Issues such as these will result in a negative experience in such Teams scenarios as audio and video, where real-time streams are essential. If you need to use a proxy server, Microsoft strongly recommends:

- using external DNS resolution
- using direct UDP based routing
- allowing UDP traffic
- following the other recommendations in our networking guidelines: Media Quality and Network Connectivity Performance in Skype for Business.

*See also*, Proxy servers for Teams Limits and specifications for Microsoft Teams

## [Step 2: Configure split-tunnel VPN](prepare-environment-prepare-network#vpn)
We recommend that you provide an alternate path for Teams traffic that bypasses the VPN, commonly known as split-tunnel VPN. Split tunneling means that traffic for Office 365 won’t traverse the VPN but goes directly to Office 365. This change will have a positive impact on quality, but also provides the secondary benefit of reducing load from the VPN devices and the organization’s network.

To implement a split-tunnel VPN, consult with your VPN vendor for configuration details. 

## Step 3: Configure packet prioritization by using QoS
Use Quality of Service (QoS) to improve call quality in Microsoft Teams and to monitor and troubleshoot call quality in Teams. QoS should be implemented on all segments of a managed network. Even when a network has been adequately provisioned for bandwidth, QoS provides risk mitigation in the event of unanticipated network events. When QoS is implemented, voice traffic is prioritized so that these unanticipated events don’t negatively affect quality. See also, Quality of Service in Microsoft Teams.

## Step 4: Optimize Wi-Fi networks for quality and performance
Several factors come into play when you optimize your Wi-Fi network:

## Step 5: Implementing QoS or Wi-Fi Multimedia (WMM) to ensure that media traffic over the Wi-Fi networks is prioritized.
Planning and optimizing Wi-Fi bands and access point placement. The 2.4 GHz range might provide adequate performance, depending on access point placement.
Consult your Wi-Fi vendor for specific guidance.

*See also*, Wi-Fi recommendations for endpoints.

## Step 6: Validate network connectivity by using the Network Assessment Tool
Use the Network Assessment Tool for Teams to test connectivity to all IP addresses and ports used in Teams calls and meetings. Download the tool and see Usage.docx for details about how to use the tool and interpret the test results. We recommend that you run the tool from a client PC in each location where Teams will be used.

*See also*, Teams Network Assessment Tool.

## Step 7: Monitor your network using CQD/CA
You use the Call Quality Dashboard (CQD) to gain insight into the quality of calls made by using Teams. CQD is designed to help you optimize your network and keep a close eye on quality, reliability, and the user experience. CQD looks at aggregate telemetry for an entire organization where overall patterns can become apparent, allowing staff to make informed assessments and plan remediation activities to maximize impact. Additionally, CQD provides reports of metrics that provide insight into overall quality, reliability, and user experience.

See also, CQD Online.

## Related Topics

[Video: Network Planning](https://aka.ms/teams-networking)