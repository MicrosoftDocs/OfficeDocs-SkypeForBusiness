---
title: Plan for quality 
author: lanachin
ms.author: v-lanac
manager: serdars
ms.topic: conceptual
ms.service: msteams
ms.reviewer: dearbeen
audience: admin
description: Use this guidance to learn about the requirements that are necessary to deliver and maintain a high-quality Microsoft Teams deployment. 
localization_priority: Normal
search.appverid: MET150
ms.custom: Teams-guidance
ms.collection: 
- Teams_ITAdmin_JourneyFromSfB
- M365-collaboration
appliesto:
- Microsoft Teams
---

# Plan for quality

If you’re deploying audio, video, or meetings, you can take some additional steps to optimize your environment for that functionality. This content will provide an overview of the requirements that are necessary to deliver and maintain a high-quality Microsoft Teams deployment. You can help ensure a successful deployment by planning for service management and quality, before your first pilot or production deployment.

The guidance is organized into the following sections:

- First is an overview of user experience and the key components that underpin quality. This highlights the areas to focus on prior to onboarding to Microsoft Teams.

- Second, guidance is given for planning a support model to manage Microsoft Teams prior to the first user pilot or production deployment. This section describes the tasks that need to be performed on a regular basis to maintain a high-quality Teams deployment. In addition, this section introduces you to further guidance which you can use to start understanding and operationalizing these tasks.

- Third, specific guidance helps with planning your network and endpoints in your organization to support Microsoft Teams.

- Lastly, next steps are summarized with references to related content.

## Key technical components that affect user experience

The key technical components that affect user experience will be reviewed in this section. Before reviewing the key components, it’s critical that you understand user experience and its importance in realizing your organization’s business goals. Let’s review how we define the user experience first.

### User experience defined

Business goals can be realized when you deploy Microsoft Teams and when users adopt Teams as their core collaboration and communication solution. Quality can help ensure a positive user experience, a key attribute in driving usage and adoption. By delivering a high-quality service that delights people, individuals and teams can gain confidence and find new and innovative ways of using the service that drive business benefits.

At the heart of this is the user’s experience with Teams—the person’s emotions and attitudes toward the service. So what contributes to the user experience? It ranges from users’ knowing how and why to use Teams and incorporating it into their daily workflow to experiencing exceptional call quality and being able to connect reliably, regardless of where they are. User experience is very broad in nature; this article focuses only on those technical elements that can be controlled by your organization. Additional information about user readiness can be found in [Prepare your organization for Teams](https://aka.ms/SkypeToTeams-UserReadiness).

There are specific requirements to the deployment that are critically important to deliver a fantastic user experience—especially when using the Cloud Voice features in Teams. It is critical to treat Microsoft Teams as a first-class citizen with other communication and collaboration investments, prioritizing real-time traffic accordingly. The following section gives an overview of the key components that affect user experience. In further sections, we will provide you guidance on how to start planning to deploy and maintain the key components that comprise quality.

### Key components of quality

An organization or supporting partner should start planning for three key components during the Technical Readiness stage of a Teams deployment: service management, network, and endpoints. The combination of all three areas is fundamental to the quality of the user experience.

#### Network

In most organizations, networks were initially designed to provide access to data and applications that resided in their datacenters. Cloud-based applications like Office 365 require changes to these networks to support the new access and data flows that Teams requires. Before you can enable users for Teams in your organization, you must evaluate and optimize your current network. This is critically important when leveraging cloud voice capabilities.

In traditional networks, users will need to traverse the perimeter networks of an organization to access Teams. Many organizations will have security-based devices such as proxy servers, firewalls, and VPNs that can block, impede, or provide an un-optimized path for network traffic.

Furthermore, the core internal networks need to be optimized and right-sized to provide sufficient capacity and quality for supporting the Teams workloads, including real-time media. You can use bandwidth planning, remediation, and optimization to help ensure your network provides a high-quality and efficient path to Office 365.

For detailed guidance about network planning, see [Planning and preparing your network](planning-and-preparing-your-network.md).

### Endpoints

Microsoft Teams supports a variety of endpoints. From PCs to tablets to phones, you can access Teams anywhere from virtually any device.

To give your users the best experience possible, you need to consider these important aspects: Do your endpoints meet the Teams hardware and software requirements? Have you configured and optimized endpoints to support Wi-Fi networks? Which devices will you use to make and receive voice calls? Are those devices optimized for Teams?

For detailed guidance about endpoint planning, see [Plan for endpoint quality](#plan-for-endpoint-quality).

## Plan for network quality

Planning for network quality will be the focus for the following section.

![Diagram illustrating the three components of quality](media/envision-planning-for-service-management-and-quality-complete-guide-image4.png "Diagram illustrating the three components of quality, and how service management overlaps all three components. With a focus on the network.")

As previously mentioned, planning for network quality prior to onboarding to Microsoft Teams is critical. For further guidance for network readiness, see [Prepare your organization's network for Microsoft Teams](prepare-network.md).

In most organizations, networks can comprise both managed and unmanaged networks.

Managed networks are components of the network infrastructure that an organization has direct control over. As a result, managed networks have a direct influence on the quality that can be provided to real-time traffic workloads.

Conversely, unmanaged networks are segments of the network that a customer has limited control, or no control, over.

Internet connections between the organization and Office 365 are networks where a customer has limited control. The networks are managed by an ISP, but organizations should be able to influence the quality of the network by upgrading their bandwidth, advocating for route optimizations, or—if all else fails—switching ISPs.

Home networks or networks in hotels or coffee shops are examples of networks where a customer has no control.

In the following sections, we will focus on the quality requirements of managed networks.

### Key network planning areas

The following sections focus on the important areas for delivering a high-quality network.

> [!NOTE]
> Many networks evolve over time due to upgrades, expansion, or other business requirements. Ensure that you have operational processes in place to maintain these areas as part of your service management planning.

#### Bandwidth

Bandwidth planning is a critical aspect of the network readiness activity. Ensuring that there's enough bandwidth for the Microsoft Teams workloads is imperative. To be able to right-size an existing network, you must understand what’s currently provisioned, the current utilization, and—ultimately—the remaining available bandwidth.

To measure current utilization, you need to monitor the network. This measurement can then be used as the starting point for bandwidth planning. In addition, the network should be continually monitored during the deployment and after the deployment to ensure that the network is sufficiently provisioned.

> [!NOTE]
> When monitoring network utilization, it’s important to avoid using averages over the day. These averages can include non-core hours that skew the result. Averages can hide peak periods and mask an underlying problem.

#### Quality of service (QoS)

QoS should be implemented on all segments of the managed network, even networks that have been adequately provisioned for bandwidth. In the latter case, QoS acts as a risk mitigation in the event of unanticipated network load. When QoS is implemented, voice traffic will be prioritized so that these unanticipated events don’t affect quality.

A QoS implementation should include areas of the network, from the endpoint all the way up to the egress points and from the egress points back to the endpoint. This will ensure that voice traffic is being prioritized in both directions. QoS should be implemented on both wired and Wi-Fi networks.

For implementing QoS on your network, the following guidance can help [Quality of Service in Microsoft Teams](qos-in-teams.md)

