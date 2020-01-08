---
title: Prepare your organization's network for Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 03/25/2019
ms.topic: reference
ms.service: msteams
ms.reviewer: jastark, kojika
audience: admin
description: Learn how to prepare and manage your Microsoft Teams network. Information includes network requirements, bandwidth requirements, and additional considerations.
localization_priority: Normal
search.appverid: MET150
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# Prepare your organization's network for Microsoft Teams

# Plan and prepare your network and environment
## Why should you plan and prepare your network and environment?

Failing to prepare your network and environment will likely lead to dissatisfied users and costly, ad-hoc fixes. By preparing your network—and your organization—for Teams, you can dramatically increase your chance of optimal and consistent performance.

Before we look at the steps to be taken, it’s important to understand what can affect the performance of Teams and thereby user happiness and satisfaction. Three major risk areas can affect how users perceive network quality:

- Insufficient bandwidth available

- Firewall and proxy blockers

- Network impairments such as jitter and packet loss

The steps described below will help you determine whether your deployment might be affected by any of these factors and will help you move toward a resolution.
Failing to prepare your network will likely lead to dissatisfied users and costly, ad-hoc fixes. By preparing your network—and your organization—for Teams, you can dramatically increase your chance of success.


## Where do I begin?

Plan for your network by reviewing the following network planning tasks.
**LOLA - see what she did with these. Any rewriting? If so, compare & evaluate. If NOT... Sigh...**

[Step 1: Check your environment's readiness for Teams](network.readiness.md)

[Step 2: Prepare your organization's network for Teams](prepare-environment-prepare-network.md)

[Step 3: Verify you've got Teams licenses for all users](teams-add-on-licensing/microsoft-teams-add-on-licensing.md)

=====> From Julia's get-started article:
# Get Teams up and running quickly (RENAME to something like "you MUST do this stuff")

We assume you already know your way around the Microsoft Teams Admin Center, and you are familiar with what you need to do to plan your network for Teams. 
To quickly get Teams up and running, complete the following tasks:

1. Verify all locations have internet access so they can connect to Office 365. At a minimum, verify that the following common ports are open to the internet from all locations:

    - Open TCP ports **80** and **443** for outgoing traffic from clients that will use Teams.    
    - Open UDP ports **3478** through **3481** for outgoing traffic from clients that will use Teams.

1. Verify your organization has deployed Exchange Online and SharePoint Online, and a verified domain for Office 365 (for example, contoso.com).If your organization does not have Exchange Online, see Understand how Exchange and Microsoft Teams interact.

    - If your organization does not have Exchange Online, see [Understand how Exchange and Microsoft Teams interact](exchange-teams-interact.md).        

    - If your organization does not have SharePoint Online, see [Understand how SharePoint Online and OneDrive for Business interact with Microsoft Teams](sharepoint-onedrive-interact.md).


## Using Network Planner

If you want help assessing your network, including bandwidth calculations and network requirements across your org's physical locations, check out the [Network Planner](network-planner.md) tool located in the Teams Admin Center. When you provide your network details and Teams usage, the Network Planner calculates your network requirements for deploying Teams and cloud voice across your organization’s physical locations.

For an example scenario, see [Using Network Planner - example scenario](tutorial-network-planner-example).

========> From Julia's optimize-network topic. This MAY include everything we need from prepare-environment-prepare-network (and one other? I don't remember.)
# Optimize your network for Microsoft Teams

The following steps are optional and not required for Teams to be up and running. You can complete the following tasks to optimize your network for added performance and features in any order.

[Step 1: Validate the Network Assessment Tool (NAT) pool size required for user connectivity](https://docs.microsoft.com/en-us/office365/enterprise/nat-support-with-office-365?redirectSourcePath=%252farticle%252fNAT-support-with-Office-365-170e96ea-d65d-4e51-acac-1de56abe39b9)
Ensure that adequate public IP addresses are assigned to the NAT pools to prevent port exhaustion. Port exhaustion will contribute to internal users and devices being unable to connect to the Office 365 service.

[Step 2: Implement the most efficient routing to MS datacenters](https://docs.microsoft.com/en-us/office365/enterprise/client-connectivity?redirectSourcePath=%252farticle%252fClient-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
Identify locations that can use local or regional egress points to connect to the Microsoft network as efficiently as possible. 

[Step 3: Configure split-tunnel VPN](prepare-environment-prepare-network.md#vpn)
We recommend that you provide an alternate path for Teams traffic that bypasses the VPN, commonly known as split-tunnel VPN. Split tunneling means that traffic for Office 365 won’t traverse the VPN but goes directly to Office 365. This change will have a positive impact on quality, but also provides the secondary benefit of reducing load from the VPN devices and the organization’s network.

> [!NOTE]
> To implement a split-tunnel VPN, consult with your VPN vendor for configuration details. 

[Step 4: Configure packet prioritization by using QoS](qos-in-teams.md)
Use Quality of Service (QoS) to improve call quality in Microsoft Teams and to monitor and troubleshoot call quality in Teams. QoS should be implemented on all segments of a managed network. Even when a network has been adequately provisioned for bandwidth, QoS provides risk mitigation in the event of unanticipated network events. When QoS is implemented, voice traffic is prioritized so that these unanticipated events don’t negatively affect quality. 

[Step 5: Optimize Wi-Fi networks for quality and performance](prepare-environment-prepare-network.md)
Like VPN, Wi-Fi networks aren’t necessarily designed or configured to support real-time media. Planning for, or optimizing, a Wi-Fi network to support Teams is an important consideration for a high-quality deployment.

[Step 6: Implementing QoS or Wi-Fi Multimedia (WMM) to ensure that media traffic over the Wi-Fi networks is prioritized](plan-for-quality).
Planning and optimizing Wi-Fi bands and access point placement. The 2.4 GHz range might provide adequate performance, depending on access point placement.
Consult your Wi-Fi vendor for specific guidance.

*See also*, [Wi-Fi recommendations for endpoints](envision-planning-for-service-management-and-quality-complete-guide#wi-fi-recommendations-for-endpoints).

[Step 7: Validate network connectivity by using the Network Assessment Tool](3-envision-evaluate-my-environment.md)
Use the Network Assessment Tool (NAT) for Teams to test connectivity to all IP addresses and ports used in Teams calls and meetings. Download the tool and see Usage.docx for details about how to use the tool and interpret the test results. We recommend that you run the tool from a client PC in each location where Teams will be used.

[Step 8: Monitor your network using CQD/CA](turning-on-and-using-call-quality-dashboard.md)
You use the Call Quality Dashboard (CQD) to gain insight into the quality of calls made by using Teams. CQD is designed to help you optimize your network and keep a close eye on quality, reliability, and the user experience. CQD looks at aggregate telemetry for an entire organization where overall patterns can become apparent, allowing staff to make informed assessments and plan remediation activities to maximize impact. Additionally, CQD provides reports of metrics that provide insight into overall quality, reliability, and user experience.

## Related Topics

[Video: Network Planning](https://aka.ms/teams-networking)

