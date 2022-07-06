---
title: Implement Quality of Service in Microsoft Teams
ms.author: mikeplum
author: MikePlumleyMSFT
manager: Serdars
ms.topic: article
ms.service: msteams
ms.reviewer: vkorlep, siunies
audience: admin
description: Learn about how to prepare your organization's network for Quality of Service (QoS) in Microsoft Teams.
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
  - Microsoft Teams
---

# Implement Quality of Service (QoS) in Microsoft Teams

Quality of Service (QoS) in Microsoft Teams allows real-time network traffic that's sensitive to network delays (for example, voice or video streams) to "cut in line" in front of traffic that's less sensitive (like downloading a new app, where an extra second to download isn't a large deal). QoS uses Windows Group Policy Objects and Port-based Access Control Lists to identify and mark all packets in real-time streams. This helps your network to give voice, video, and screen share streams a dedicated portion of network bandwidth.

If you support a large group of users who are experiencing any of the problems described in this article, then you probably need to implement QoS. A small business with few users might not need QoS, but even there it should be helpful.

Without some form of QoS, you might see the following quality issues in voice and video:

- Jitter – media packets arriving at different rates, which can result in missing words or syllables in calls
- Packet loss – packets dropped, which can also result in lower voice quality and hard to understand speech
- Delayed round-trip time (RTT) – media packets taking a long time to reach their destinations, which result in noticeable delays between two parties in a conversation and causes people to talk over each other

The least complex way to address these issues is to increase the size of the data connections, both internally and out to the internet. Since that is often cost-prohibitive, QoS provides a way to more effectively manage the resources you have instead of adding bandwidth. To address quality issues, we recommend that you first use QoS, then add bandwidth only where necessary.

For QoS to be effective, you must apply consistent QoS settings throughout your organization. Any part of the path that fails to support your QoS priorities can degrade the quality of calls, video, and screen sharing. This includes applying settings to all user PCs or devices, network switches, routers to the internet, and the Teams service.

_Figure 1. The relationship between an organization's networks and Microsoft 365 or Office 365 services_

![Illustration of the relationship between networks and services.](media/Qos-in-Teams-Image1.png "The relationship between an organization's networks and Microsoft 365 or Office 365 services: on-premises network and devices connect with an interconnect network, which in turn connects with Microsoft 365 or Office 365 Cloud Voice and Audio Conferencing services.")

## QoS implementation checklist

At a high level, do the following to implement QoS:

1. [Make sure your network is ready](#make-sure-your-network-is-ready).

1. [Select a QoS implementation method](#select-a-qos-implementation-method).

1. [Choose initial port ranges for each media type](#choose-initial-port-ranges-for-each-media-type).

1. Implement QoS settings:
   1. On clients using a Group Policy Object (GPO) to [set client device port ranges and markings](QoS-in-Teams-clients.md).
   2. On routers (see the manufacturer documentation) or other network devices. This might include port-based Access Control Lists (ACLs) or simply defining the QoS queues and DSCP markings, or all of these.

      > [!IMPORTANT]
      > We recommend implementing these QoS policies using the client source ports and a source and destination IP address of “any.” This will catch both incoming and outgoing media traffic on the internal network.  

   3. [Set how you want to handle media traffic for Teams meetings](meeting-settings-in-teams.md#set-how-you-want-to-handle-real-time-media-traffic-for-teams-meetings).

5. [Validate your QoS implementation](#validate-your-qos-implementation) by analyzing Teams traffic on the network.

As you prepare to implement QoS, keep the following guidelines in mind:

- The shortest path to Microsoft 365 is best.
- Closing ports will only lead to quality degradation.
- Any obstacles in between, such as proxies, aren't recommended.
- Limit the number of hops:
  - Client to network edge – 3 to 5 hops
  - ISP to Microsoft network edge – 3 hops
  - Microsoft network edge to final destination – irrelevant

For information about configuring firewall ports, go to [Office 365 URLs and IP ranges](office-365-urls-ip-address-ranges.md).

## Make sure your network is ready

If you're considering a QoS implementation, you should already have determined your bandwidth requirements and other [network requirements](prepare-network.md).
  
Traffic congestion across a network will greatly impact media quality. A lack of bandwidth leads to performance degradation and a poor user experience. As Teams adoption and usage grows, use reporting, [per-user call analytics](use-call-analytics-to-troubleshoot-poor-call-quality.md), and [Call Quality Dashboard (CQD)](turning-on-and-using-call-quality-dashboard.md) to identify problems and then make adjustments using QoS and selective bandwidth additions.

### VPN considerations

QoS only works as expected when implemented on all links between callers. If you use QoS on an internal network and a user signs in from a remote location, you can only prioritize within your internal, managed network. Although remote locations can receive a managed connection by implementing a virtual private network (VPN),  a VPN inherently adds packet overhead and creates delays in real-time traffic. We  recommend that you avoid running real-time communications traffic over a VPN.

In a global organization with managed links that span continents, we strongly recommend QoS because bandwidth for those links is limited in comparison to the LAN.

## Introduction to QoS queues

To provide QoS, network devices must have a way to classify traffic and must be able to distinguish voice or video from other network traffic.

When network traffic enters a router, the traffic is placed into a queue. If a QoS policy isn't configured, there is only one queue, and all data is treated as first-in, first-out with the same priority. That means voice traffic (which is very sensitive to delays) might get stuck behind traffic where a delay of a few extra milliseconds wouldn't be a problem.

When you implement QoS, you define multiple queues using one of several congestion management features, such as Cisco’s priority queuing and [Class-Based Weighted Fair Queueing (CBWFQ)](https://www.cisco.com/en/US/docs/ios/12_0t/12_0t5/feature/guide/cbwfq.html#wp17641) and congestion avoidance features, such as [weighted random early detection (WRED)](https://en.wikipedia.org/wiki/Weighted_random_early_detection).

_Figure 2. Examples of QoS queues_

![Illustration of QoS queues and bandwidth division.](media/Qos-in-Teams-Image2.png "Total available bandwidth is divided among multiple queues—audio, video, and other traffic—that have been assigned different priorities.")

A simple analogy is that QoS creates virtual "carpool lanes" in your data network so some types of data never or rarely encounter a delay. Once you create those lanes, you can adjust their relative size and much more effectively manage the connection bandwidth you have, while still delivering business-grade experiences for your organization's users.

## Select a QoS implementation method

You could implement QoS via port-based tagging, using Access Control Lists (ACLs) on your network's routers. Port-based tagging is the most reliable method because it works in mixed Windows, Mac, and Linux environments and is the easiest to implement. Mobile clients don't provide a mechanism to mark traffic by using DSCP values, so they'll require this method.  

Using port-based tagging, your network's router examines an incoming packet, and if the packet arrived using a certain port or range of ports, it identifies it as a certain media type and puts it in the queue for that type, adding a predetermined [DSCP](https://tools.ietf.org/html/rfc2474) mark to the IP Packet header so other devices can recognize its traffic type and give it priority in their queue.

Although port-based tagging works across platforms, it only marks traffic at the WAN edge (not all the way to the client machine) and creates management overhead. Refer to the documentation provided by the router manufacturer for instructions on implementing this method.

### Insert DSCP markers

You could also implement QoS by using a Group Policy Object (GPO) to direct client devices to insert a DSCP marker in IP packet headers identifying it as particular type of traffic (for example, voice). Routers and other network devices can be configured to recognize this and put the traffic in a separate, higher-priority queue.

Although this scenario is entirely valid, it will only work for domain-joined Windows clients. Any device that isn't a domain-joined Windows client won't be enabled for DSCP tagging. Other clients, such as those running macOS, have hard-coded tags and will always tag traffic.

On the plus side, controlling the DSCP marking via GPO ensures that all domain-joined computers receive the same settings and that only an administrator can manage them. Clients that can use GPO will be tagged on the originating device, and then configured network devices can recognize the real-time stream by the DSCP code and give it an appropriate priority.

### Best practice

We recommend a combination of DSCP markings at the endpoint and port-based ACLs on routers, if possible. Using a GPO to catch the majority of clients, and also using port-based DSCP tagging will ensure that mobile, Mac, and other clients will still get QoS treatment (at least partially).

DSCP markings can be likened to postage stamps that indicate to postal workers how urgent the delivery is and how best to sort it for speedy delivery. Once you've configured your network to give priority to real-time media streams, lost packets and late packets should diminish greatly.

Once all devices in the network are using the same classifications, markings, and priorities, it's possible to reduce or eliminate delays, dropped packets, and jitter by changing the size of the port ranges assigned to the queues used for each traffic type. From the Teams perspective, the most important configuration step is the classification and marking of packets. However, for end-to-end QoS to be successful, you also need to carefully align the application's configuration with the underlying network configuration. Once QoS is fully implemented, ongoing management is a question of adjusting the port ranges assigned to each traffic type based on your organization's needs and actual usage.

## Choose initial port ranges for each media type

The DSCP value tells a correspondingly configured network what priority to give a packet or stream, whether the DSCP mark is assigned by clients or the network itself based on ACL settings. Each media workload gets its own unique DSCP value (other services might allow workloads to share a DSCP marking, Teams doesn't) and a defined and separate port range used for each media type. Other environments might have an existing QoS strategy in place, which will help you determine the priority of network workloads.

The relative size of the port ranges for different real-time streaming workloads sets the proportion of the total available bandwidth dedicated to that workload. To return to our earlier postal analogy: a letter with an "Air Mail" stamp might get taken within an hour to the nearest airport, while a small package marked "Bulk Mail" mark can wait for a day before traveling over land on a series of trucks.

_Recommended initial port ranges_

|Media traffic type| Client source port range |Protocol|DSCP value|DSCP class|
|:--- |:--- |:--- |:--- |:--- |
|Audio| 50,000–50,019|TCP/UDP|46|Expedited Forwarding (EF)|
|Video| 50,020–50,039|TCP/UDP|34|Assured Forwarding (AF41)|
|Application/Screen Sharing| 50,040–50,059|TCP/UDP|18|Assured Forwarding (AF21)|
||||||

Be aware of the following when you use these settings:

- If you plan to implement ExpressRoute in the future and haven't yet implemented QoS, we recommend that you follow the guidance so that DSCP values are the same from sender to receiver.

- All clients, including mobile clients and Teams devices, will use these port ranges and will be affected by any DSCP policy you implement that uses these source port ranges. The only clients that will continue to use dynamic ports are the browser-based clients (clients that let participants join meetings by using their browsers).

- Although the Mac client uses the same port ranges, it also uses hard-coded values for audio (EF) and video (AF41). These values aren't configurable.

- If you later need to adjust the port ranges to improve user experience, the port ranges can't overlap and should be adjacent to each other.

## Migrate QoS to Teams

If you've previously deployed Skype for Business Online, including QoS tagging and port ranges, and are now deploying. Teams, Teams will respect the existing configuration and will use the same port ranges and tagging as the Skype for Business client. In most cases, no additional configuration will be needed.

> [!NOTE]
> If you're using Application Name QoS tagging via Group Policy, you must add Teams.exe as the application name.

### Implement QoS in Teams on Windows using PowerShell

**Set QoS for audio**

```powershell
new-NetQosPolicy -Name "Teams Audio" -AppPathNameMatchCondition "Teams.exe" -IPProtocolMatchCondition Both -IPSrcPortStartMatchCondition 50000 -IPSrcPortEndMatchCondition 50019 -DSCPAction 46 -NetworkProfile All
```

**Set QoS for video**

```powershell
new-NetQosPolicy -Name "Teams Video" -AppPathNameMatchCondition "Teams.exe" -IPProtocolMatchCondition Both -IPSrcPortStartMatchCondition 50020 -IPSrcPortEndMatchCondition 50039 -DSCPAction 34 -NetworkProfile All
```

**Set QoS for sharing**

```powershell
new-NetQosPolicy -Name "Teams Sharing" -AppPathNameMatchCondition "Teams.exe" -IPProtocolMatchCondition Both -IPSrcPortStartMatchCondition 50040 -IPSrcPortEndMatchCondition 50059 -DSCPAction 18 -NetworkProfile All
```

## Managing source ports in the Teams admin center

In Teams, QoS source ports used by the different workloads should be actively managed, and adjusted as necessary. Referring to the table in [Choose initial port ranges for each media type](#choose-initial-port-ranges-for-each-media-type), the port ranges are adjustable, but the DSCP markings aren't configurable. Once you have implemented these settings, you might find that more or fewer ports are needed for a given media type. [Per-user call analytics](use-call-analytics-to-troubleshoot-poor-call-quality.md) and [Call Quality Dashboard (CQD)](turning-on-and-using-call-quality-dashboard.md) should be used in making a decision to adjust port ranges after Teams has been implemented, and periodically as needs change.

> [!NOTE]
> If you've already configured QoS based on source port ranges and DSCP markings for Skype for Business Online, the same configuration will apply to Teams and no further client or network changes to the mapping will be required, though you may have to [set the ranges used in Teams](meeting-settings-in-teams.md#set-how-you-want-to-handle-real-time-media-traffic-for-teams-meetings) to match what was configured for Skype for Business Online.

If you’ve previously deployed Skype for Business Server on-premises, you might need to re-examine your QoS policies. Adjust the policies to match port range settings you've verified provide a quality user experience for Teams.

## Validate your QoS implementation

For QoS to be effective, the DSCP value set by the GPO needs to be present at both ends of a call. By analyzing the traffic generated by the Teams client, you can verify that the DSCP value isn’t changed or stripped out when the Teams workload traffic moves through the network.

Preferably, you capture traffic at the network egress point. You can use port mirroring on a switch or router to help with this.

## Implement QoS for other devices

Read these topics for information about implementing QoS for Intune, Surface, iOS, Android, and Mac

- [QoS for Surface Hub 2S](/surface-hub/surface-hub-2s-manage-intune)

- [QoS for Surface Hub](/surface-hub/surface-hub-qos)

- [QoS for iOS, Android, and Mac](./meeting-settings-in-teams.md?WT.mc_id=TeamsAdminCenterCSH#set-how-you-want-to-handle-real-time-media-traffic-for-teams-meetings)

## Related topics

- [Video: Network Planning](https://aka.ms/teams-networking)

- [Prepare your organization's network for Microsoft Teams](prepare-network.md)

- [Implement QoS in the Teams client](QoS-in-Teams-clients.md)