---
title: Implement Quality of Service in Microsoft Teams
ms.author: crowe
author: CarolynRowe
manager: pamgreen
ms.topic: article
ms.service: msteams
ms.reviewer: siunies
ms.date: 04/12/2024
audience: admin
description: Learn how to prepare your organization's network for Quality of Service (QoS) in Microsoft Teams.
ms.localizationpriority: medium
search.appverid: MET150
f1.keywords:
  - CSH
ms.custom: 
  - ms.teamsadmincenter.meetingsettings.qos
  - ms.teamsadmincenter.meetingsettings.network.qosmarkers
  - seo-marvel-apr2020
ms.collection: 
  - M365-collaboration
appliesto: 
  - Classic Microsoft Teams
  - New Microsoft Teams
---

# Implement Quality of Service (QoS) in Microsoft Teams

This article is for administrators and IT professionals who are implementing Quality of Service (QoS) in Microsoft Teams.

Quality of Service (QoS) in Microsoft Teams enables you to prioritize real-time network traffic that's sensitive to network delays over traffic that's less sensitive. For example, you'd prioritize voice and video streams over downloading a new app (where an extra second to download isn't that noticeable). 

QoS uses Differentiated Services Code Point (DSCP) markings together with port-based Access Control Lists (ACLs) to identify, mark, and classify all packets in real-time streams. This ensures that voice, video, and screen share streams receive preferential treatment at the expense of other types of traffic.

Without some form of QoS, you might see the following quality issues in voice and video:

- Jitter – Media packets arrive at different rates, which can result in missing words or syllables in calls.

- Packet loss – Packets dropped, which can also result in lower voice quality and hard-to-understand speech.

- Delayed round-trip time (RTT) – Media packets take a long time to reach their destinations, which results in noticeable delays between two parties in a conversation and causes people to talk over each other.

If you support a large group of users who are experiencing any of the problems described in this article, then you should implement QoS. A small business with few users might not need QoS, but should consider it if experiencing network delays.

The least complex way to address these issues is to increase the size of the data connections, both internally and out to the internet, but this method is often cost-prohibitive. QoS enables you to manage the resources you have instead of adding bandwidth. To address quality issues, we recommend that you use QoS first, then add bandwidth where necessary.

For QoS to be effective, you must apply consistent QoS settings throughout your organization. Any part of the path that fails to support your QoS priorities can degrade the quality of calls, video, and screen sharing. You need to apply settings to all user PCs or devices, network switches, routers to the internet, and the Teams service.

_Figure 1. The relationship between an organization's networks and Microsoft 365 or Office 365 services_

![Illustration of the relationship between networks and services.](media/Qos-in-Teams-Image1.png "The relationship between an organization's networks and Microsoft 365 or Office 365 services: on-premises network and devices connect with an interconnect network, which in turn connects with Microsoft 365 or Office 365 Cloud Voice and Audio Conferencing services.")

## QoS implementation checklist

The following checklist provides an overview of the steps required to implement QoS. The steps are described in more detail throughout this article.

1. [Make sure your network is ready](#step-1-make-sure-your-network-is-ready).

2. [Select a QoS implementation method](#step-2-select-a-qos-implementation-method).

3. [Choose initial port ranges for each media type](#step-3-choose-initial-port-ranges-for-each-media-type).

4. [Implement QoS settings](#step-4-implement-qos-settings) for clients, routers, media traffic.
   
5. [Validate your QoS implementation](#step-5-validate-your-qos-implementation) by analyzing Teams traffic on the network.

6. [Manage source ports](#step-6-manage-source-ports)

Keep the following guidelines in mind:

- The shortest path to Microsoft 365 is best.
- Closing ports leads to quality degradation.
- Any obstacles in between, such as proxies, aren't recommended.
- Limit the number of hops:
  - Client to network edge – 3 to 5 hops
  - ISP to Microsoft network edge – 3 hops
  - Microsoft network edge to final destination – irrelevant

For information about configuring firewall ports, see [Office 365 URLs and IP ranges](office-365-urls-ip-address-ranges.md).

## Introduction to QoS queues

To provide QoS, network devices must have a way to classify traffic, and must be able to distinguish voice or video from other network traffic.

When network traffic enters a router, the traffic is placed into a queue. If a QoS policy isn't configured, there is only one queue, and all data is treated as first-in, first-out with the same priority. That means voice traffic (which is very sensitive to delays) might get stuck behind traffic where a delay of a few extra milliseconds isn't a problem.

When you implement QoS, you define multiple queues using one of several congestion management features, such as Cisco’s priority queuing and [Class-Based Weighted Fair Queueing (CBWFQ)](https://www.cisco.com/en/US/docs/ios/12_0t/12_0t5/feature/guide/cbwfq.html#wp17641) and congestion avoidance features, such as [weighted random early detection (WRED)](https://en.wikipedia.org/wiki/Weighted_random_early_detection).

_Figure 2. Examples of QoS queues_

![Illustration of QoS queues and bandwidth division.](media/Qos-in-Teams-Image2.png "Total available bandwidth is divided among multiple queues—audio, video, and other traffic—that have been assigned different priorities.")

A simple analogy is that QoS creates virtual "carpool lanes" in your data network so some types of data never or rarely encounter a delay. Once you create those lanes, you can adjust their relative size and much more effectively manage the connection bandwidth you have, while still delivering business-grade experiences for your organization's users.


## Step 1. Make sure your network is ready

If you're considering a QoS implementation, you should've already determined your [bandwidth and other network requirements](prepare-network.md).
  
Traffic congestion across a network greatly impacts media quality. A lack of bandwidth leads to performance degradation and a poor user experience. As Teams adoption and usage grows in your organization, you'll need to monitor and manage your network performance. To identify problems, and then make adjustments using QoS and selective bandwidth additions, use the following tools: [reporting](./teams-analytics-and-reports/teams-reporting-reference.md), [per-user call analytics](use-call-analytics-to-troubleshoot-poor-call-quality.md), and [Call Quality Dashboard (CQD)](turning-on-and-using-call-quality-dashboard.md).

### VPN considerations

QoS works as expected only when implemented on all links between callers. If you use QoS on an internal network, and a user signs in from a remote location, you can prioritize only within your internal, managed network. 

Although remote locations can receive a managed connection by implementing a virtual private network (VPN), a VPN inherently adds packet overhead and creates delays in real-time traffic. We recommend that you avoid running real-time communications traffic over a VPN.

In a global organization with managed links that span continents, we recommend QoS because bandwidth for those links is limited in comparison to the LAN.


## Step 2. Select a QoS implementation method

You can implement QoS by using the following methods:

- Port-based DSCP (Differentiated Services Code Point) tagging at router
- Client inserts DSCP markers in IP packet headers

Both of these methods are based on [DSCP](https://tools.ietf.org/html/rfc2474) markers. DSCP markers can be likened to postage stamps that indicate to postal workers how urgent the delivery is, and how best to sort a package for speedy delivery. Once you've configured your network to give priority to real-time media streams, lost packets and late packets should diminish greatly.

### Port-based tagging at router

Using port-based tagging, your network's router examines incoming packets to determine which ports are used. If the packet arrives using a certain port or range of ports, the router identifies the packet as a certain media type. The router then puts the packet in the queue for that type, adding a predetermined DSCP mark to the IP Packet header so other devices can recognize its traffic type and give it priority in their queue.

You implement port-based tagging by using Access Control Lists (ACLs) on your network's routers.   For instructions on implementing port-based tagging, refer to your router manufacturer's documentation.

Port-based tagging is the most reliable method because it works in mixed Windows, Mac, and Linux environments. It is also the easiest to implement. Although port-based tagging works across platforms, it only marks traffic at the WAN edge (not all the way to the client machine) and creates management overhead. 

### Client inserts DSCP markers 

You can also implement QoS by requiring client endpoints to insert a DSCP marker in IP packet headers. There are multiple ways to achieve this, depending on the type of endpoint (Windows, Mac, iOS, Android, Microsoft Teams Room system); this will be covered in the implementation section of this article.

The DSCP markers identify the packet as a particular type of traffic (for example, voice). You can configure routers and other network devices to recognize the DSCP marker, and put the traffic in a separate, higher-priority queue.

### Best practice

We recommend using a combination of DSCP markings at client endpoints and port-based tagging ACLs on routers if possible. Managed devices (for example with Intune) would benefit from the centralized policy controls allowing for the configuration of DSCP markings, while port-based ACLs on routers would allow for identification of traffic coming from devices that are unable to configure client-side DSCP markings.

Once all devices in the network are using the same classifications, markings, and priorities, it's possible to reduce or eliminate delays, dropped packets, and jitter by changing the size of the port ranges assigned to the queues used for each traffic type.

From a Teams perspective, the most important configuration step is the classification and marking of packets. However, for end-to-end QoS to be successful, you also need to carefully align the application's configuration with the underlying network configuration. Once QoS is fully implemented, ongoing management is a question of adjusting the port ranges assigned to each traffic type based on your organization's needs and actual usage.

## Step 3. Choose initial port ranges for each media type

The relative size of the port ranges for different real-time streaming workloads sets the proportion of the total available bandwidth dedicated to that workload. Using the postal service analogy: a letter with an "Air Mail" stamp might get taken within an hour to the nearest airport, while a small package marked "Bulk Mail" can wait for a day before traveling over land on a series of trucks.

The DSCP value tells a correspondingly configured network what priority to give a packet or stream, whether the DSCP mark is assigned by clients or the network itself based on ACL settings. Each media workload gets its own unique DSCP value, and a defined and separate port range used for each media type. (While other services might allow workloads to share a DSCP marking, Teams does not.) Other environments might have an existing QoS strategy in place, which will help you determine the priority of network workloads.

_Recommended initial port ranges_

|Media traffic type| Client source port range |Protocol|DSCP value|DSCP class|
|:--- |:--- |:--- |:--- |:--- |
|Audio| 50,000–50,019|TCP/UDP|46|Expedited Forwarding (EF)|
|Video| 50,020–50,039|TCP/UDP|34|Assured Forwarding (AF41)|
|Application/Screen Sharing| 50,040–50,059|TCP/UDP|18|Assured Forwarding (AF21)|
|||||

Be aware of the following when you use these settings:

- All clients, including mobile clients and Teams devices, will use these port ranges and will be affected by any DSCP policy you implement that uses these source port ranges. The only clients that will continue to use dynamic ports are the browser-based clients (clients that let participants join meetings by using their browsers).

- Although the Mac and mobile (iOS and Android) clients use these source port ranges, these clients will use hard-coded values for audio (EF) and video and application/screen sharing (AF41). These values aren't configurable.

- If you later need to adjust the port ranges to improve user experience, the port ranges can't overlap and should be adjacent to each other.

## Step 4. Implement QoS settings

Implement QoS settings for clients and network devices, and determine how you want to handle media traffic for meetings.

- As a pre-requisite, enable QoS globally in the Teams Admin Center. See [Configure QoS in the Teams admin center](meetings-real-time-media-traffic.md) for details on enabling the **Insert Quality of Service (QoS) markers for real-time media traffic** setting.

- For information on configuring DSCP markings for Windows endpoints, see [Implement QoS in Teams clients](QoS-in-Teams-clients.md).

  > [!NOTE]
  > As part of the transition from classic Teams to new Teams, the executable name has changed from teams.exe (classic Teams) to ms-teams.exe (new Teams).

- Mac and mobile (iOS and Android) clients use hard-coded values for audio (EF) and video and application/screen sharing (AF41). Teams Phone devices also use the default value for audio (EF). However, QoS must be enabled globally in the Teams Admin Center for this to function. See [Configure QoS in the Teams admin center](meetings-real-time-media-traffic.md) for details on enabling the **Insert Quality of Service (QoS) markers** for real-time media traffic” setting.

- For information on configuring DSCP markings for Microsoft Teams Rooms (Windows and Android), see [Quality of Service (QoS) configuration on Teams Rooms devices](./devices/qos-on-teams-devices.md).

- For information on configuring DSCP markings for Surface Hub devices running Windows 10 Team OS , see [Manage Surface Hub with an MDM Provider](/surface-hub/manage-settings-with-mdm-for-surface-hub).

- For information on implementing QoS for routers, see your manufacturer's documentation.

- Setting QoS on network devices might include using port-based Access Control Lists (ACLs), defining the QoS queues and DSCP markings, or all of these.

  > [!IMPORTANT]
  > We recommend implementing these QoS policies using the client source ports and a source and destination IP address of “any.” This will catch both incoming and outgoing media traffic on the internal network.  


## Step 5. Validate your QoS implementation

For QoS to be effective, the DSCP value set needs to be present at both ends of a call. By analyzing the traffic generated by the Teams client, you can verify that the DSCP value isn’t changed or stripped out when the Teams workload traffic moves through the network.

Preferably, you capture traffic at the network egress point. You can use port mirroring on a switch or router to help with this.

## Step 6. Manage source ports 

For Teams, after you've chosen initial port ranges for each media type ([see Step 3](#step-3-choose-initial-port-ranges-for-each-media-type)), you need to monitor and adjust the QoS source ports used by the different workloads as necessary. More or fewer ports might be needed for a given media type. 

For information about how to monitor and manage ports, see the following:

- [Per-user call analytics](use-call-analytics-to-troubleshoot-poor-call-quality.md)
- [Call Quality Dashboard (CQD)](turning-on-and-using-call-quality-dashboard.md).

- [Configure QoS in the Teams admin center](meetings-real-time-media-traffic.md)

Note that you can adjust the port ranges, but you can't configure the DSCP markings. 



## Related topics

- [Video: Network Planning](https://aka.ms/teams-networking)
- [Prepare your organization's network for Microsoft Teams](prepare-network.md)
- [Implement QoS in the Teams client](QoS-in-Teams-clients.md)
