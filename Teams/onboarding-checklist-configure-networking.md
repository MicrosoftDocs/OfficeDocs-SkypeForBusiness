---
title: Onboarding checklist for configuring networking for Microsoft Teams
author: lanachin
ms.author: v-lanac
manager: serdars
ms.date: 03/13/2018
ms.topic: article
ms.service: msteams
ms.reviewer: rowille
description: Follow the core, to-do tasks and activities in this checklist when you configure your network for Teams.
localization_priority: Normal
search.appverid: MET150
MS.collection: 
- Teams_ITAdmin_PracticalGuidance
- M365-collaboration
appliesto:
- Microsoft Teams
---

# Configure networking

| No | Activity or task | Description | Completed? | Additional information |
|----|--------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1  | Review network requirements for Teams | Have an overall view of your network requirements before going into the networking details. | | [Prepare your organization's network for Microsoft Teams](https://docs.microsoft.com/microsoftteams/prepare-network)                                                               |
| 2  | Deliver the Network Readiness workshop | Perform a network readiness assessment. | |  |
| 3  | Use the Network Planner | Perform network bandwidth planning. | | |
| 4  | Validate the NAT pool size required for user connectivity | Ensure that adequate public IP addresses are assigned to the NAT pools to prevent port exhaustion. Port exhaustion will contribute to internal users and devices being unable to connect to the Office 365 service. <br/><br/>Connectivity problems are a leading cause of user perception issues for cloud services. | | [NAT support with Office 365](https://support.office.com/article/NAT-support-with-Office-365-170e96ea-d65d-4e51-acac-1de56abe39b9) |
| 5  | Implement the most efficient routing to Microsoft datacenters | Identify locations that can use local or regional egress points to connect to the Microsoft network as efficiently as possible. <br/><br/>The article in the **Additional information** column describes how clients can take advantage of features in Office 365 name resolution and IP routing to be efficiently connected to the closest regional datacenter. | | [Office 365 Client Connectivity](https://support.office.com/article/Client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b) |
| 6  | Configure firewall ports requested for connectivity to Teams | Review Office 365 URLs and IPs to identify and test the firewall ports that are required for connectivity between on-premises clients and servers and Office 365 services. <br/><br/>For a supported environment, you must open all ports on your firewalls. Failing to open some ports or ranges will negatively affect user experience. Configure media ports on your firewalls based on the guidance in the **Additional information** column. | | [Office 365 URLs and IP Addresses – Microsoft Teams](https://support.office.com/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_teams) |
| 7  | Configure proxy servers | Configure your environment so that proxy servers are bypassed and you can connect users directly to Office 365 by using UDP, for the best audio and video quality. When real-time media is forced to traverse a proxy server, the media stack in Teams is forced to fail back to TCP, which negatively affects quality. <br/><br/>For the highest-quality user experience, always prefer UDP over TCP. | | [Planning for Service Management and Quality](https://docs.microsoft.com/MicrosoftTeams/envision-planning-for-service-management-and-quality-complete-guide) |
| 8  | Configure split tunnel VPN | We recommend that you provide an alternate path for Teams traffic that bypasses the VPN, commonly known as *split-tunnel VPN*. Split tunneling means that traffic for Office 365 won’t traverse the VPN but goes directly to Office 365. This change will have a positive impact on quality, but also provides the secondary benefit of reducing load from the VPN devices and the organization’s network. | | To implement a split-tunnel VPN, consult with your VPN vendor for configuration details. |
| 9  | Configure packet prioritization by using QoS | QoS should be implemented on all segments of a managed network. Even when a network has been adequately provisioned for bandwidth, QoS provides risk mitigation in the event of unanticipated network events. When QoS is implemented, voice traffic is prioritized so that these unanticipated events don’t negatively affect quality. | | [Planning for Service Management and Quality](https://docs.microsoft.com/MicrosoftTeams/envision-planning-for-service-management-and-quality-complete-guide) <br/><br/>[Quality of Service in Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/qos-in-teams) |
| 10 | Optimize Wi-Fi networks for quality and performance | Several factors come into play when you optimize your Wi-Fi network: <ul><li>Implementing QoS or Wi-Fi Multimedia (WMM) to ensure that media traffic over the Wi-Fi networks is prioritized.</li><li>Planning and optimizing Wi-Fi bands and access point placement. The 2.4 GHz range might provide adequate performance, depending on access point placement.</li></ul> Consult your Wi-Fi vendor for specific guidance. | | [Wi-Fi recommendations for endpoints](https://docs.microsoft.com/MicrosoftTeams/envision-planning-for-service-management-and-quality-complete-guide#wi-fi-recommendations-for-endpoints) |
| 11 | Validate network connectivity by using the Network Assessment Tool | Use the Network Assessment Tool for Skype for Business and Teams to test connectivity to all IP addresses and ports used in Skype for Business Online and Teams calls and meetings. Download the tool, and see Usage.docx for details about how to use the tool and interpret the test results. We recommend that you run the tool from a client PC in each location where Teams will be used. | | [Skype for Business and Teams Network Assessment Tool](https://go.microsoft.com/fwlink/?linkid=855799) |
