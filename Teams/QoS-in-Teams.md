---
title: Implement Quality of Service in Microsoft Teams
author: rmw2890
ms.author: MyAdvisor
manager: Serdars
ms.date: 12/17/2018
ms.topic: article
ms.service: msteams
ms.reviewer: rowille
description: Prepare your organization's network for Quality of Service (QoS) in Microsoft Teams.
localization_priority: Normal
search.appverid: MET150
MS.collection: Teams_ITAdmin_PracticalGuidance
appliesto:
- Microsoft Teams
---

# Implement Quality of Service (QoS) in Microsoft Teams

This article will help you prepare your organization's network for Quality of Service (QoS) in Microsoft Teams.

You can use QoS to prioritize network traffic that is sensitive to network delays over traffic that is less sensitive. A simple analogy is that QoS creates virtual “carpool lanes” in your data network so some types of data never or rarely encounter delays.
When you prioritize the traffic for real-time communications such as calls or shared meetings in Teams you can more reliably deliver a business-grade user experience. Without some form of QoS, you might see the following quality issues in voice and video:

- Jitter – media packets arriving at different rates.
- Packet loss – packets dropped, which can result in missing words or syllables.
- Delayed round trip time (RTT) – media packets taking a long time to reach their destinations.

For QoS to be truly effective, consistent QoS settings need to be applied from end to end in your organization (user PCs, network switches, and routers to the cloud), because any part of the path that fails to support your QoS priorities can degrade the quality of calls, video, and screen shares.

QoS is a mechanism you can use to prioritize certain types of network traffic that are sensitive to network delays over other traffic that is less sensitive. A simple analogy is that QoS creates virtual "carpool lanes" in your data network, so some types of data never or rarely encounter delays.

When you prioritize the traffic for real-time communications such as calls or shared meetings in Teams you can more reliably deliver a business-grade user experience. When you don't implement QoS, shared screens in meetings can freeze, video can pixellate and color shift, and voice calls can become choppy and difficult or impossible to understand. For QoS to be truly effective, consistent QoS settings need to be applied from end to end in your organization (user PCs, network switches, and routers to the cloud), because any part of the path that fails to support your QoS priorities can degrade the quality of calls, video, and screen shares.

![The relationship between an organization's networks and Office 365 services: on-premises network and devices connect with an interconnect network, which in turn connects with Office 365 Cloud Voice and Audio Conferencing services.](media/Qos-in-Teams-Image1.png) 

In most cases, the interconnect network will be an unmanaged network internet connection. 

One option available to address end-to-end QoS is [Azure ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/). We still recommend that you implement QoS on your on-premises network. This will increase the quality of real-time communication workloads throughout your deployment and alleviate chokepoints. 

In most cases, the network connecting your enterprise to the cloud will be an unmanaged network internet connection where you won't be able to reliably set QoS. One option available to allow truly end-to-end QoS is [Azure ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/). We still recommend that you implement QoS on the portions of the end-to-end network you have control over, namely your on-premises network. This will increase the quality of real-time communication workloads throughout your deployment and alleviate chokepoints in your existing deployment.

## Prioritize Teams network traffic for QoS 

This article focuses on how to prioritize Teams real-time communications traffic—namely, voice and video. You can also prioritize other types of traffic, based on your needs.

There are several ways to prioritize traffic, but the most common is by using differentiated services code point (DSCP) markings. They can be applied (“tagged”) based on port ranges or via Group Policy objects. We’ll cover both in this article. We recommend that you use tagging based on port ranges because it will work for all devices, not just those joined to the domain.

Controlling the DSCP marking via Group Policy objects ensures that domain-joined computers receive the correct settings and that only an administrator can manage them.

It’s important to understand that QoS only works when implemented on all links that connect caller to another. If you use QoS on the internal network and a user signs in from a remote location, you can only prioritize within your internal, managed network. Although remote locations can receive a managed connection by implementing a virtual private network (VPN), we  recommend that you avoid running real-time communications traffic over the VPN.

> [!NOTE]
> We recommend that you implement split tunneling for VPN-connected remote users to maximize the quality of the user experience. Download the document [Deploy-Guidance-VPN Split Tunnel](https://myadvisor.fasttrack.microsoft.com/CloudVoice/Downloads?SelectedIDs=5_1_0_9 ) from MyAdvisor for more information.

In a global organization with managed links that span continents, we strongly recommend QoS because bandwidth for those links is limited in comparison to the LAN.

## QoS queues

To provide QoS, network devices must have a way to classify traffic and must be able to distinguish voice or video from other network traffic. 

Differentiated services (DiffServ) uses the type of services (ToS) field in the header of an IPv4/IPv6 packet to set priority for network devices. The six most significant bits of the DiffServ field are the differentiated services code point, or DSCP. Using this, traffic can be classified as a particular type (for example, voice), and then marked (101110, or 46 in decimal for voice traffic), so that when network devices process these markings, the traffic can be prioritized accordingly (expedited forwarding, in this example).

When network traffic enters a router, the traffic is placed into a queue. If there is no QoS in place, there is only one queue, and data is treated as first-in, first-out. That means voice traffic (which is very sensitive to delays) might get stuck behind traffic from online streaming services. When you implement QoS, you can define multiple queues by using different congestion management features (such as Cisco’s priority queuing and class-based weighted fair queue [CBWFQ]) and congestion avoidance features (such as weighted random early detection [WRED]).

![Total available bandwidth is divided among multiple queues—audio, video, and other traffic—that have been assigned different priorities.](media/Qos-in-Teams-Image2.png "Total available bandwidth is divided among multiple queues—audio, video, and other traffic—that have been assigned different priorities.")

_Figure 2. Examples of QoS queues_

After these pieces are in place, it’s possible to deliver predictable QoS because the network now understands how to classify, mark, and prioritize traffic. From the Teams perspective, the most important configuration step is the classification and marking of packets, but for end-to-end QoS to be successful you also need to carefully align the application’s configuration with the underlying network configuration.

## Teams QoS scenarios

The guidance for implementing QoS for Teams is based on four scenarios:

*  **Scenario 1:** You’ve deployed or are deploying Teams and plan to implement QoS via port-based tagging. Port-based tagging is the most reliable method because it works universally on all platforms and is the easiest to implement.  

*  **Scenario 2:** You’ve deployed or are deploying Teams and plan to implement QoS via Group Policy object tagging. This is sometimes used in combination with scenario 1. Although this scenario is entirely valid, it will only work for domain-joined Windows clients. Any device that isn’t a domain-joined Windows client won’t be enabled for DSCP tagging.

*  **Scenario 3:** You’ve deployed Skype for Business Online, including QoS tagging, and are now deploying Teams. If this is you, Teams will respect the existing configuration and will use the same port ranges and tagging as the Skype for Business client. In most cases, no additional configuration will be needed. 

    > [!NOTE]
    > If you're using Application Name QoS tagging via Group Policy, you must add Teams.exe as the application name.

*  **Scenario 4:** You’ve deployed or are deploying Teams and want to implement QoS via port-based tagging by using a custom port range.

## Implement QoS

At a very high level, implementing QoS requires these steps:

1. Determine your route and bandwidth requirements.

2. Use DSCP markings and port ranges to classify traffic.

3. Configure the policy-based QoS settings within a Group Policy object.

4. Verify the port ranges in the Group Policy object.

5. Validate QoS by analyzing Teams traffic on the network.

As you prepare to implement QoS, keep the following guidelines in mind:

- The shortest path to Office 365 is best.

- Closing ports will only lead to quality degradation.

- Any obstacles in-between, such as proxies, are not recommended.

- Limit the number of hops:

    - Client to network edge – 3 to 5 hops.
    - ISP to Microsoft network edge – 3 hops
    - Microsoft network edge to final destination – irrelevant 

For information about configuring firewall ports, go to [Office 365 URLs and IP ranges](office-365-urls-ip-address-ranges.md).

## Determine bandwidth requirements

Before you configure QoS for Microsoft Teams, it’s important to prepare your network for Microsoft Teams and determine your bandwidth requirements. Providing QoS in your network requires the reservation of a defined amount of bandwidth on each link for real-time traffic. (If that bandwidth isn’t required for real-time traffic at any time, it can be used for other traffic.)

Traffic congestion across a network will greatly impact media quality. A lack of bandwidth leads to performance degradation and a poor user experience, so consider bandwidth planning as a starting point for Teams deployment. As Teams adoption and usage grows, use reporting to make necessary adjustments. 

The Network Planner available on FastTrack is helpful when you are determining bandwidth requirements.

### Requirements for a connection from your network to Microsoft network edge

For the best media quality, the network performance targets or thresholds shown in Table 1 are required for a connection from your organization’s network to the Microsoft network edge.

> [!IMPORTANT]
> Connectivity between a Teams client on your company network to Office 365 services must meet the following network performance requirements.

_Table 1. Network performance metrics - client to Office 365 services_

| Metric | Target |
|--------|--------|
| Latency (one way) | < 50 milliseconds |
| Latency (round trip time (RTT) | < 100 milliseconds |
| Burst packet loss | < 10% during any 200 millisecond interval |
| Packet loss | < 1% during any 15 second interval |
| Packet inter-arrival jitter | < 30 milliseconds during any 15 second interval |
| Packet reorder | < 0.05% out of order packets |

The latency metric target assumes your company site or sites and the Microsoft edges are on the same continent.

Your company site to the Microsoft network edge connection includes first hop network access, which can be WiFi or another wireless technology.

The network performance target assumes proper bandwidth and/or QoS planning. In other words, the requirements apply directly to Teams real-time media traffic when the network connection is under a peak load.

### Requirements for a connection from your network edge to Microsoft network edge

Table 2 shows the network performance targets or thresholds that are required for the connection between your network edge and the Microsoft network edge. This excludes your organization’s internal network or WAN, and is intended as a guide when you test network traffic that is sent over the internet or through an ExpressRoute partner network.

> [!IMPORTANT]
> Connectivity between your company's network edge to the Microsoft network edges must meet the following network performance requirements.

_Table 2. Network performance metrics - edge to edge_

| Metric | Target |
|--------|--------|
| Latency (one way) | < 30 milliseconds |
| Latency (round trip time (RTT) | < 60 milliseconds |
| Burst packet loss | < 1% during any 200 millisecond interval |
| Packet loss | < 0.1% during any 15 second interval |
| Packet inter-arrival jitter | < 15 milliseconds during any 15 second interval |
| Packet reorder | < 0.01% out of order packets |


## Recommended DSCP markings

When you're ready to configure QoS, your first step is to classify the traffic flows (such as audio and video) by assigning DSCP values to the unique, non-overlapping port ranges. The DSCP value assigned here will determine the priority of the traffic going through the network, based on network configuration. Each workload gets its own DSCP value, though not necessarily a unique value—you might want to set the same value for voice and video workloads, giving them the same priority in the network.  

The DSCP value to use depends on how you want to prioritize the workload. For example, business requirements might dictate that you give application sharing the same priority as video (and therefore mark it with the same DSCP value as video). Other environments might have an existing QoS strategy in place, which will help you determine the priority of network workloads. 

Table 3 shows the DSCP markings required for Teams with ExpressRoute. These markings might serve as a good starting point for customers who are unsure what to use in their own environments. To learn more, read [ExpressRoute QoS requirements](https://docs.microsoft.com/azure/expressroute/expressroute-qos).

_Table 3. DSCP markings_

| Client source port range |Protocol|Media category|DSCP value|DSCP class|
|---------|---------|---------|---------|---------|
| 50,000–50,019|TCP/UDP|Audio|46|Expedited Forwarding (EF)|
| 50,020–50,039|TCP/UDP|Video|34|Assured Forwarding (AF41)|
| 50,040–50,059|TCP/UDP|Application/Desktop Sharing|18|Assured Forwarding (AF21)|

Be aware of the following when you use the information in Table 3:

-  If you plan to implement ExpressRoute in the future and haven’t yet implemented QoS, we recommend that you follow the guidance in Table 3 so that DSCP values are the same from sender to receiver. 

-  All clients, including mobile clients and Teams devices, will use these port ranges and will be affected by any DSCP policy you implement that uses these source port ranges. The only clients that will continue to use dynamic ports are the browser-based clients (that is, those clients that let participants join meetings by using their browsers).

-  Although the Mac client uses the same port ranges, it also uses hard-coded values for audio (EF) and video (AF41). These values are not configurable.


## Source ports used by Teams

In Teams, QoS should be configured based on the source ports used by the different workloads. Currently, neither server-side nor client-side port ranges are configurable. 

The client source port ranges listed in Table 3 also apply to Teams and use their associated QoS DSCP markings.

The recommended method of implementing these QoS policies is to use the client source ports with a source and destination IP address of “any.” This will catch both incoming and outgoing media traffic on the internal network. 

> [!NOTE]
> If you've already configured QoS based on source port ranges for Skype for Business Online, the same configuration will apply to Teams and no further changes will be required. If you’ve deployed Skype for Business Server on-premises, you’ll need to re-examine your QoS policies and adjust them if necessary.

## Set DSCP markings

There are multiple approaches to setting the proper DSCP markings for traffic classification:

-  **DSCP marking at the endpoint:** This is generally the preferred option, because the endpoint itself provides the proper markings. Currently this can be done by using a Group Policy object, but it can only be used on domain-joined Windows clients. Mobile clients don’t provide a mechanism to mark traffic by using DSCP values. Although you can’t configure non&ndash;domain-joined Windows clients to tag traffic, clients such as Mac OS have hard-coded tags and will always tag traffic as described above.

-  **Port-based DSCP tagging by using access control lists (ACLs) on routers:** This is a very common option encountered in heterogeneous Windows and Mac environments. In this scenario, the network team marks the traffic at the ingress/egress routers (typically located on the WAN) based on the source port ranges defined for each modality. Although this works across platforms, it only marks traffic at the WAN edge—not all the way to the client machine—and therefore incurs management overhead.

-  **A combination of DSCP markings at the endpoint and port-based ACLs on routers:** We recommend this combination, if possible in your environment. Use a Group Policy object to catch the majority of clients, and also use port-based DSCP tagging to ensure that mobile, Mac, and other clients will still get QoS treatment (at least partially).

You can use policy-based QoS within Group Policy to set the DSCP value for the predefined source port range in the Teams client. Use the port ranges specified in Table 3 to create a policy for each workload.

After you’ve identified the port ranges, the next step is to configure the policy-based QoS settings within a Group Policy object. You can find more information about these steps in [Configuring port ranges and a Quality of Service policy for your clients on Skype for Business Server](https://docs.microsoft.com/SkypeForBusiness/manage/network-management/qos/configuring-port-ranges-for-your-skype-clients#configure-quality-of-service-policies-for-clients-running-on-windows-10).

To create a QoS audio policy for Windows 10 computers, first log on to a computer on which Group Policy Management has been installed. Open Group Policy Management (click Start, point to Administrative Tools, and then click Group Policy Management), and then complete the following steps:

1. In Group Policy Management, locate the container where the new policy should be created. For example, if all your client computers are located in an OU named **Clients**, the new policy should be created in the Client OU.

2. Right-click the appropriate container, and then click **Create a GPO in this domain, and Link it here**.

3. In the **New GPO** dialog box, type a name for the new Group Policy object in the **Name** box, and then click **OK**.

4. Right-click the newly created policy, and then click **Edit**.

5. In the Group Policy Management Editor, expand **Computer Configuration**, expand **Windows Settings**, right-click **Policy-based QoS**, and then click **Create new policy**.

6. In the **Policy-based QoS** dialog box, on the opening page, type a name for the new policy in the **Name** box. Select **Specify DSCP Value** and set the value to **46**. Leave **Specify Outbound Throttle Rate** unselected, and then click **Next**.

7. On the next page, make sure that **All applications** is selected, and then click **Next**. This setting instructs the network to look for all packets with a DSCP marking of 46, not just packets created by a specific application.

8. On the third page, make sure that both **Any source IP address** and **Any destination IP address** are selected, and then click **Next**. These two settings ensure that packets will be managed regardless of which computer (IP address) sent the packets and which computer (IP address) will receive the packets.

9. On page four, select **TCP and UDP** from the **Select the protocol this QoS policy applies to** drop-down list. TCP (Transmission Control Protocol) and UDP (User Datagram Protocol) are the two networking protocols most commonly used.

10. Under the heading **Specify the source port number**, select **From this source port or range**. In the accompanying text box, type the port range reserved for audio transmissions. For example, if you reserved ports 50000 through ports 50019 for audio traffic, enter the port range using this format: **50000:50019**. Click **Finish**.

The new policies you’ve created won’t take effect until Group Policy has been refreshed on your client computers. Although Group Policy periodically refreshes on its own, you can force an immediate refresh.

### Force Group Policy refresh

1. On each computer for which you want to refresh Group Policy, open a command console. Ensure that the command console is set to run as administrator.

2. At the command prompt, enter
   ```
    gpupdate.exe /force
   ```

## Verify DSCP markings in the Group Policy object

To verify that the values from the Group Policy object have been set, perform the following steps.

1. Open a command console. Ensure that the command console is set to run as administrator.

2. At the command prompt, enter 
   ```
   gpresult /R > gp.txt
   ```

   This will generate a report and send it to a text file named gp.txt. Alternatively, you can enter the following command to produce the same data in a more readable HTML report named gp.html:
   ```
   gpresult /H >gp.html
   ```


3. In the generated file, look for the heading **Applied Group Policy Objects** and verify that the names of the Group Policy objects created earlier are in the list of applied policies. 

4. Open the Registry Editor, and go to:

   HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\QoS\

   Verify the values for the registry entries listed in Table 4.

   _Table 4. Values for Windows registry entries for QoS_


   |          Name          |  Type  |    Data     |
   |------------------------|--------|-------------|
   |    Application Name    | REG_SZ |  Teams.exe  |
   |       DSCP Value       | REG_SZ |     46      |
   |        Local IP        | REG_SZ |     \*      |
   | Local IP Prefix Length | REG_SZ |     \*      |
   |       Local Port       | REG_SZ | 50000-50019 |
   |        Protocol        | REG_SZ |     \*      |
   |       Remote IP        | REG_SZ |     \*      |
   |    Remote IP Prefix    | REG_SZ |     \*      |
   |      Remote Port       | REG_SZ |     \*      |
   |     Throttle Rate      | REG_SZ |     -1      |


5. Verify that the value for the Application Name entry is correct for the client you’re using, and verify that both the DSCP Value and Local Port entries reflect the settings in the Group Policy object.

## Validate QoS by analyzing Teams traffic on the network

For QoS to be effective, the DSCP value set by the Group Policy object needs to be present at both ends of a call. By looking at the traffic generated by the Teams client, you can verify that the DSCP value isn’t changed or stripped out when the Teams workload traffic traverses moves through the network.

Preferably, you capture traffic at the network egress point. You can use port mirroring on a switch or router to help with this.

### Use Network Monitor to verify DSCP values

Network Monitor is a tool you can [download from Microsoft](https://www.microsoft.com/download/4865) to analyze network traffic.

1. On the PC running Network Monitor, connect to the port that has been configured for port mirroring and start capturing packets. 

2. Make a call by using the Teams client. Make sure media has been established before hanging up the call. 

3. Stop the capture.

4. In the **Display Filter** field, use the source IP address of the PC that made the call, and refine the filter by defining DSCP value 46 (hex 0xb8) as search criteria, as shown in the following example:

    Source == "192.168.137.201" AND IPv4.DifferentiatedServicesField == 0xb8 

    ![Screenshot of the Display Filter dialog box in Network Monitor, showing the filters to apply.](media/Qos-in-Teams-Image4.png "Screenshot of the Display Filter dialog box in Network Monitor, showing the filters to apply.")

5. Select **Apply** to activate the filter.

6. In the **Frame Summary** window, select the first UDP packet.

7. In the **Frame Details** window, expand the IPv4 list item and note the value at the end of the line that begins with **DSCP**. 

    ![Screenshot of the Frame Details dialog box in Network Monitor, highlighting DSCP settings.](media/Qos-in-Teams-Image5.png "Screenshot of the Frame Details dialog box in Network Monitor, highlighting DSCP settings.")

In this example, the DSCP value is set to 46. This is correct, because the source port used is 50019, which indicates that this is a voice workload. 

Repeat the verification for each workload that has been marked by the GPO. 

## More information

[Prepare your organization's network for Microsoft Teams](prepare-network.md)

[ExpressRout QoS requirements](https://docs.microsoft.com/azure/expressroute/expressroute-qos)