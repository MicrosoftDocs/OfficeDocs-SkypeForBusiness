---
title: Quality of Service (QoS) in Microsoft Teams
author: rmw2890
ms.author: MyAdvisor
manager: Serdars
ms.date: 02/16/2018
ms.topic: article
ms.service: msteams
description: Prepare your organization's network for Quality of Service (QoS) in Microsoft Teams.
localization_priority: Priority
MS.collection: Strat_MT_TeamsAdmin

---

Quality of Service (QoS) in Microsoft Teams
==========================================
This guide will help you prepare your organization's network for Quality of Service (QoS) in Teams.


Quality of Service (QoS) is a mechanism that lets you prioritize certain types of network traffic. Prioritizing the traffic for real-time communications services such as Teams is important in order to deliver a business-grade user experience. For QoS to be truly effective, a QoS-capable connection must be configured end-to-end (PC, network switches, and routers to the cloud), because any part in the path that fails to support QoS could degrade the quality of the entire call.


![Screenshot of a diagram that illustrates the relationship between an organization's networks and Office 365 services.](media/Qos-in-Teams-Image1.png)

 

In most cases, the interconnect network will be an unmanaged network, an internet connection. One option available to address end-to-end QoS is [ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/). It is our recommendation to still implement QoS on the portions of the network you have control over, namely your on-premises network. This will increase the quality of real time communication workloads throughout your deployment and will alleviate choke points in your existing deployment. 

## Objectives 

This guide will focus on how to prioritize Teams real-time communications traffic, namely voice and video. Other types of traffic can also be prioritized based on your needs.

There are multiple ways to prioritize traffic, but the most common is by using differentiated services code point (DSCP) markings. They can be applied based on port ranges but also via Group Policy objects. We will cover both in this document.

Controlling the DSCP marking via Group Policy objects (GPO) ensures that domain-joined computers receive the correct settings and that these settings can only be managed by an administrator. 

It’s important to understand that QoS only works when implemented on all links connecting caller to callee. If we use QoS on the internal network and a user signs in from a remote location, we can only prioritize within our internal, managed, network. While remote locations could receive a managed connection by implementing a VPN, it is not recommended to run real-time communications traffic over the VPN.

> [!NOTE]
> Our recommendation is to implement split tunneling for VPN connected remote users to maximize the user experience. See the document [Deploy-Guidance-VPN Split Tunnel](https://myadvisor.fasttrack.microsoft.com/CloudVoice/Downloads?SelectedIDs=5_1_0_9 ) for more information.

In a global organization with managed links spanning continents, QoS is highly recommended since the bandwidth is limited in comparisons to the local network (LAN).

## Quality of Service

In order to provide a guaranteed level of service for an application on the network, the underlying network devices must have a way to classify different types of traffic. A router, for example, must be able to distinguish between voice traffic and normal web browsing traffic, if there is an expectation that voice receives better treatment. 

Differentiated Services (DiffServ) provides a framework in which traffic is treated by network devices with priorities based on the type of services (ToS) field in the header of an IPv4/IPv6 packet. The six most significant bits of the DiffServ field is known as the Differentiated Services Code Point, or DSCP. Using this framework, traffic can be classified as a particular type of traffic (voice), and then marked (101110, or 46 in decimal), such that when network devices process these markings, the traffic can be prioritized accordingly (Expedited Forwarding, in this example).

When network traffic enters a router, the traffic is placed into a queue – if there is no QoS in place, essentially there is only one queue, and data is treated as first-in, first-out. That means voice traffic (which is very sensitive to delays) could get stuck behind traffic from online streaming services. When implementing QoS, multiple queues can be defined, with different congestion management features (such as Cisco’s Priority Queuing (PQ) and Class Based Weighted Fair Queue (CBWFQ)) and congestion avoidance features (such as Weighted Random Early Detection (WRED)).

![Screenshot of a diagram that illustrates QoS queues in Teams.](media/Qos-in-Teams-Image2.png)

Figure 1: QoS queues visualized

Once these pieces are in place, a predictable quality of service can be delivered, as the underlying managed network now understands how to classify, mark and prioritize traffic. From the Teams perspective, the most important configuration item is the classification and marking of packets – but careful planning is involved to align the application’s configuration with the underlying network configuration for end-to-end QoS to be successful.

## QoS scenarios

When implementing QoS for Teams, we’ve based our guidance on four starting scenarios:

1.	You’ve deployed or are deploying Teams and are planning on implementing QoS via Port Based Tagging. Port Based Tagging is the most reliable method since it works universally throughout all platforms and is the easiest to implement. 

2.	You’ve deployed or are deploying Teams and are planning to implement QoS via Group Policy Object tagging. This is sometimes used in combination with scenario 1. While this scenario is entirely valid and described below, it is important to understand this will only work for Domain Joined Windows Clients. Any device that is not a Windows Domain Joined Client will not be enabled for QoS\DSCP Tagging. 

3.	You have Skype for Business Online deployed including QoS Tagging and are now deploying Teams. If this is you, Teams will respect the existing configuration and will use the same port ranges and tagging as the Skype for Business client. No additional configuration should be needed. 
    > [!NOTE]
    > If you're using Application Name QoS tagging via Group Policy you should add “Teams.exe” as Application Name.
4.	You’ve deployed or are deploying Teams and want to implement QoS via port-based tagging with a custom port range.

## Recommended differentiated services code point (DSCP) markings

The first step is to classify the traffic flows (such as audio and video) by leveraging the unique, non-overlapping port ranges with a DSCP-value. The DSCP value assigned here will determine the priority of the traffic going through the network (based on the network configuration). Each workload gets its own DSCP value, although some customers might set the same value on voice and video, giving them the same priority in the network. 

What DSCP value to use depends on how a workload is prioritized. For example, business requirements could dictate that application sharing is to be treated with the same level of priority as video (and as such, marked with the same DSCP-value as video). Other environments might have an existing QoS strategy in place already. 

Table 1 below shows the required DSCP markings when utilizing Teams with ExpressRoute. This could serve as a good starting point for customers unsure what to use in their own environment. To learn more, read [ExpressRoute QoS requirements](https://docs.microsoft.com/azure/expressroute/expressroute-qos).


| Client source port|Protocol|Media category|Common DSCP value|DSCP class|
|---------|---------|---------|---------|---------|
| 50,000 – 50,019|TCP/UDP|Audio|46|Expedited Forwarding (EF)|
| 50,020 – 50,039|TCP/UDP|Video|34|Assured Forwarding (AF41)|
| 50,040 – 50,059|TCP/UDP|Application/Desktop Sharing and File Transfer|18|Class Selector (CS3)|

Table 1: DSCP markings

Here are some caveats to understand when you use the information in Table 1:

- File sharing and application sharing use the same source port range – and as such, would use the same DSCP markings when using Port Based Tagging. Because of this, it should be determined which priority is most applicable to *both* modalities (Interactive or Default).
	
- If there’s a plan to implement ExpressRoute in the future and QoS has not yet been implemented, the recommendation is to follow the guidance given above so that DSCP values are the same from sender to receiver. 
	
## Source ports used by Teams

In Teams, QoS should be configured based on the source ports used by the different workloads. Both server-side and client-side port ranges are non-configurable at this point. 

To deploy QoS, use the client source port ranges listed in Table 2, with their associated QoS DSCP markings.

| Client source port|Protocol|Media category|Common DSCP value|DSCP class|
|---------|---------|---------|---------|---------|
| 50,000 – 50,019|TCP/UDP|Audio|46|Expedited Forwarding (EF)|
| 50,020 – 50,039|TCP/UDP|Video|34|Assured Forwarding (AF41)|
| 50,040 – 50,059|TCP/UDP|Application/Desktop Sharing and File Transfer|18|Class Selector (CS3)|

Table 2: Client source port ranges

> [!NOTE]
> If you've already configured QoS based on source port ranges for Skype for Business Online, the same configuration will apply to Teams and no further changes are required. If you’ve deployed Skype for Business Server (on premises), you will need to redesign your QoS Policies.

## Setting differentiated services code point (DSCP) markings

There are multiple approaches to setting the proper DSCP markings for traffic classification.

- DSCP marking at the endpoint: This is the preferred option in general, as the endpoint itself is providing the proper markings. Currently this could be done by using a GPO, but this is only possible on domain-joined Windows clients. Mac OSX or mobile clients, for example, do not provide a mechanism to mark traffic with DSCP values.

- Port-based using ACLs on routers: This is a very common option encountered in heterogeneous environments of Windows and Mac. In this scenario, the network team marks the traffic at the ingress/egress routers (typically on the Wide Area Network (WAN)) based on the source port ranges defined for each modality. While this works across platforms, it only marks at the WAN edge – not all the way to the client machine – and incurs management overhead.
	
- A combination of DSCP markings on the client and port-based ACLs on routers.
	
If possible, we recommend a combination of both, to use a GPO to catch the majority of clients, and to also use port based DSCP tagging to ensure mobile clients, Mac and other clients will still get a (partial) QoS treatment.

Setting the DSCP value for the pre-defined source port range in the Teams client can be done using policy-based QoS within Group Policy. The following table uses the port ranges specified in the table to create a policy for each workload.

| Client traffic type|Port range start|Port range end|DSCP value|
|---------|---------|---------|--------|
| Audio|50000|50019|46|
| Video|50020|50039|34|
| Application sharing|50040|50059|18|
| File transfer|50040|50059|18|

Table 3: Port ranges by traffic type

Note: The port ranges set by Teams cannot be changed or altered. Please review this page for the latest information: https://support.microsoft.com/ kb/2409256

Once the port ranges have been determined, the next step is to configure the policy-based QoS settings within a Group Policy Object (GPO). Details for these steps can be found on [TechNet](https://technet.microsoft.com/library/jj205371(v=ocs.15).aspx). 

The new policies you have created won’t take effect until Group Policy has been refreshed on your client computers. Although Group Policy periodically refreshes on its own, you can force an immediate refresh by running the following command on each computer where Group Policy needs to be refreshed:

        gpudate.exe /force

This command can be run from any command window that is running under administrator credentials. To run a command window under administrator credentials, click **Start**, right-click **Command Prompt**, and then click **Run as administrator**.

## Verifying the DSCP markings in GPO

To verify that the values from the GPO has been set, please perform the following steps:

1.	Use gpresult to verify that the settings from the GPO has been received by the local PC. gpresult /R >gp.txt will generate a report and send it to a text file, gp.txt.

    ![Screenshot of the Administrator Command Prompt running the gpresult command.](media/Qos-in-Teams-Image3.png)

    Figure 2: Verify Applied Group Policy Objects
    > [!NOTE]
    > Alternatively, you can run gpresult /H gp.html to produce the same data in more user-friendly HTML report. 
2.	In the generated file look for the heading: Applied Group Policy Objects and verify that the names of the GPO’s created earlier is in the list of applied policies. 

3.	Open the registry editor and navigate to:

    HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\QoS\

    Verify the registry values listed in Table 3 below.
    
    | Name | Type | Data|
    |---------|---------|---------
    | Application Name|REG_SZ|Teams.exe|
    | DSCP Value|REG_SZ|46|
    | Local IP|REG_SZ|*|
    | Local IP Prefix Length|REG_SZ|*|
    | Local Port|REG_SZ|50000-50019|
    | Protocol|REG_SZ|*|
    | Remote IP|REG_SZ|*|
    | Remote Ip Prefix|REG_SZ|*|
    | Remote Port|REG_SZ|*|
    | Throttle Rate|REG_SZ|-1|
    
    Table 3: Windows registry values for QoS

4.	Verify that the Application Name is correct for the client you are using, and verify that both DSCP value and Local Port reflect the settings in the GPO.

## Validating QoS: Analyzing Teams traffic on the network

The DSCP value set by the GPO needs to be present from caller to callee in order for QoS to be affective. By looking at the traffic generated by the Teams client we can verify that the DSCP is not changed or stripped out when traversing the network. 

Preferably we would capture traffic at the network egress point. Port mirroring can be used on a switch or router to aid in capturing traffic on the network. 

### Looking at network traffic using Network Monitor

Network Monitor is a tool you can download from Microsoft to analyze network traffic. Download [Network Monitor 3.4](https://www.microsoft.com/download/4865).

Connect to PC running network monitor to the port that has been configured for port mirroring and start capturing packets. Make a call using the Skype for Business client. Make sure media is established before hanging up the call. Stop the capture create a Display Filter that matches the source IP of the PC that made the call and refine the filter by defining DSCP value 46 (hex 0xb8) as 
search criteria:

Source == "192.168.137.201" AND IPv4.DifferentiatedServicesField == 0xb8 

![Screenshot of the Display Filter dialog box in Network Monitor, showing the filters to apply.](media/Qos-in-Teams-Image4.png)


Click **Apply** to activate the filter. In the **Frame Summary** window, select the first UDP packet and look at the Frame Details:

![Screenshot of the Frame Details dialog box in Network Monitor, highlighting DSCP settings.](media/Qos-in-Teams-Image5.png)

Expand IPv4 and look at the value at the end of the DSCP line. In this example we see that the DSCP value is set to 46 which is correct since the source port used is 50019 which tells us that the workload is voice. 

Repeat the verification for each workload that has been marked by the GPO. 

> [!NOTE]
> Verify that markings are honored for peer-to-peer traffic as well. This can be done by installing Network Monitor on two clients and placing calls between the two clients. Look at the media traffic flowing between clients in the same manner as described above.

### Sample filters to use for Network Monitor or Wireshark

|Usage  |Sample filter  |
|---------|---------|
|Voice (note: muxing must be turned off)     |   udp.port==3479 AND Ipv4.DifferentiatedServicesField.DSCP==46      |
|Video     | udp.port==3480 AND Ipv4.DifferentiatedServicesField.DSCP==34        |
|Screen sharing     |  udp.port==3481 AND Ipv4.DifferentiatedServicesField.DSCP==18       |

### Filter: Media traffic from Microsoft relays (requires [Azure ExpressRoute](https://azure.microsoft.com/services/expressroute/))

ip.src in {52.114.188.0/22 52.114.220.0/22 52.114.124.0/22 52.114.60.0/22} and (udp.srcport in {3479 3480 3481} or (udp.srcport ge 50000 and udp.srcport lt 60000))

### Filter: Media traffic to Microsoft relays

ip.dst in {52.114.188.0/22 52.114.220.0/22 52.114.124.0/22 52.114.60.0/22} and (udp.dstport in {3479 3480 3481} or (udp.dstport ge 50000 and udp.dstport lt 60000))


You should see traffic to and from the Microsoft relays. You can check DSCP markings on the IP layer in Wireshark, as shown in the next section.

### Expected DSCP markings

Audio streams: 46

Video streams: 34

Data streams: 18

### Filter: DSCP condition to network

ip.dsfield.dscp in {46 34 18}



### Looking at network traffic using Wireshark

Wireshark, https://www.wireshark.org/, is a powerful tool that allows us to filter and record network data for further analysis. Connect a PC running Wireshark to the port that has been configured for port mirroring and start capturing packets. Make a call using the Teams client. Make sure media is established before hanging up the call.

Stop the packet trace and create a filter that only displays the source IP of the PC where the Teams client is installed, for example, *ip.src_host == 192.168.137.201* and looks for packages that use a source port from the range specified for voice, 50,000 – 50,019:

![Screenshot of Wireshark with filter settings.](media/Qos-in-Teams-Image6.png)
 

Mark the package and expand the Internet Protocol Version 4 (IPV4) header in the packet detail pane:

![Screenshot of Wireshark with Differentiated Services Codepoint settings highlighted.](media/Qos-in-Teams-Image7.png)
 

Verify that the value for *Differentiated Services Codepoint* match the value for the specific workload, in this case 46 (binary 101110) for voice.

Repeat the verification for each workload that has been marked by the GPO.

> [!NOTE]
> Verify that markings are honored for peer-to-peer traffic. This can be done by installing WireShark or Network Monitor on two clients and placing calls between the two clients. Look at the media traffic flowing between clients in the same manner as described above.

## Summary

Quality of Service is an important piece of the puzzle when providing business-class experiences with Teams. However, it is important to always remember that QoS is only effective on properly managed networks. As such, the deployment team must work very closely with the networking teams to ensure the proper information is passed at the network layer, ideally managed from end-to-end.

