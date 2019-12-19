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
The following steps are optional and not required for Teams to be up and running. You can complete the following tasks to optimize your network for added performance and features in any order.

[Step 1: Validate the Network Assessment Tool (NAT) pool size required for user connectivity](https://docs.microsoft.com/en-us/office365/enterprise/nat-support-with-office-365?redirectSourcePath=%252farticle%252fNAT-support-with-Office-365-170e96ea-d65d-4e51-acac-1de56abe39b9)
Ensure that adequate public IP addresses are assigned to the NAT pools to prevent port exhaustion. Port exhaustion will contribute to internal users and devices being unable to connect to the Office 365 service.

[Step 2: Implement the most efficient routing to MS datacenters](https://docs.microsoft.com/en-us/office365/enterprise/client-connectivity?redirectSourcePath=%252farticle%252fClient-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
Identify locations that can use local or regional egress points to connect to the Microsoft network as efficiently as possible. 

[Step 3: Configure firewall ports requested for connectivity to Teams](prepare-environment-prepare-network.md)
Review Office 365 URLs and IPs to identify and test the firewall ports that are required for connectivity between on-premises clients and servers and Office 365 services. You must open all ports on your firewalls. Failing to open some ports or ranges will negatively affect user experience. 

[Step 4: Configure proxy servers](proxy-servers-for-Teams.md)
Configure your environment so that proxy servers are bypassed, and you can connect users directly to Office 365 by using UDP, for the best audio and video quality. When real-time media is forced to traverse a proxy server, the media stack in Teams is forced to fail back to TCP, which negatively affects quality.

> [!NOTE]
> When it comes to Teams traffic over proxies, Microsoft recommends bypassing proxies. Proxies don't make Teams more secure because the traffic is already encrypted.

[Step 5: Configure split-tunnel VPN](prepare-environment-prepare-network.md#vpn)
We recommend that you provide an alternate path for Teams traffic that bypasses the VPN, commonly known as split-tunnel VPN. Split tunneling means that traffic for Office 365 won’t traverse the VPN but goes directly to Office 365. This change will have a positive impact on quality, but also provides the secondary benefit of reducing load from the VPN devices and the organization’s network.

> [!NOTE]
> To implement a split-tunnel VPN, consult with your VPN vendor for configuration details. 

[Step 6: Configure packet prioritization by using QoS](qos-in-teams.md)
Use Quality of Service (QoS) to improve call quality in Microsoft Teams and to monitor and troubleshoot call quality in Teams. QoS should be implemented on all segments of a managed network. Even when a network has been adequately provisioned for bandwidth, QoS provides risk mitigation in the event of unanticipated network events. When QoS is implemented, voice traffic is prioritized so that these unanticipated events don’t negatively affect quality. S

[Step 7: Optimize Wi-Fi networks for quality and performance](prepare-environment-prepare-network.md) 
Like VPN, Wi-Fi networks aren’t necessarily designed or configured to support real-time media. Planning for, or optimizing, a Wi-Fi network to support Teams is an important consideration for a high-quality deployment.

[Step 8: Implementing QoS or Wi-Fi Multimedia (WMM) to ensure that media traffic over the Wi-Fi networks is prioritized](plan-for-quality).
Planning and optimizing Wi-Fi bands and access point placement. The 2.4 GHz range might provide adequate performance, depending on access point placement.
Consult your Wi-Fi vendor for specific guidance.

*See also*, [Wi-Fi recommendations for endpoints](envision-planning-for-service-management-and-quality-complete-guide#wi-fi-recommendations-for-endpoints).

[Step 9: Validate network connectivity by using the Network Assessment Tool](3-envision-evaluate-my-environment.md)
Use the Network Assessment Tool (NAT) for Teams to test connectivity to all IP addresses and ports used in Teams calls and meetings. Download the tool and see Usage.docx for details about how to use the tool and interpret the test results. We recommend that you run the tool from a client PC in each location where Teams will be used.

[Step 10: Monitor your network using CQD/CA](turning-on-and-using-call-quality-dashboard.md)
You use the Call Quality Dashboard (CQD) to gain insight into the quality of calls made by using Teams. CQD is designed to help you optimize your network and keep a close eye on quality, reliability, and the user experience. CQD looks at aggregate telemetry for an entire organization where overall patterns can become apparent, allowing staff to make informed assessments and plan remediation activities to maximize impact. Additionally, CQD provides reports of metrics that provide insight into overall quality, reliability, and user experience.

## Related Topics

[Video: Network Planning](https://aka.ms/teams-networking)