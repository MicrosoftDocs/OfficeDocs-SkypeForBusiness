---
title: Quality of Service in Microsoft Teams - Microsoft Teams
author: rmw2890
ms.author: MyAdvisor
manager: Serdars
ms.date: 04/23/2018
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

# Quality of Service (QoS) in Microsoft Teams

This article will help you prepare your organization's network for Quality of Service (QoS) in Microsoft Teams.
QoS is a mechanism you use to prioritize certain types of network traffic. Prioritizing the traffic for real-time communications services such as Teams is important to deliver a business-grade user experience. For QoS to be truly effective, you must configure a QoS-capable connection from end to end (PC, network switches, and routers to the cloud), because any part of the path that fails to support QoS can degrade the quality of the entire call.

![The relationship between an organization's networks and Office 365 services: on-premises network and devices connect with an interconnect network, which in turn connects with Office 365 Cloud Voice and Audio Conferencing services.](media/Qos-in-Teams-Image1.png "The relationship between an organization's networks and Office 365 services: on-premises network and devices connect with an interconnect network, which in turn connects with Office 365 Cloud Voice and Audio Conferencing services.")

_Figure 1. The relationship between an organization’s networks and Office 365 services_


In most cases, the interconnect network will be an unmanaged network internet connection. One option available to address end-to-end QoS is [Azure ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/). We still recommend that you implement QoS on the portions of the network you have control over, namely your on-premises network. This will increase the quality of real-time communication workloads throughout your deployment and alleviate chokepoints in your existing deployment. 


## Prioritize Teams network traffic for QoS 

This article focuses on how to prioritize Teams real-time communications traffic—namely, voice and video. You can also prioritize other types of traffic, based on your needs.

There are multiple ways to prioritize traffic, but the most common is by using differentiated services code point (DSCP) markings. They can be applied (“tagged”) based on port ranges and also via Group Policy objects. We’ll cover both in this article. We recommend that you use tagging based on port ranges because it will work for all devices, not just those joined to the domain.

Controlling the DSCP marking via Group Policy objects ensures that domain-joined computers receive the correct settings and that only an administrator can manage them.

It’s important to understand that QoS only works when implemented on all links that connect caller to callee. If you use QoS on the internal network and a user signs in from a remote location, you can only prioritize within your internal, managed network. Although remote locations can receive a managed connection by implementing a virtual private network (VPN), we  recommend that you avoid running real-time communications traffic over the VPN.

> [!NOTE]
> We recommend that you implement split tunneling for VPN-connected remote users to maximize the quality of the user experience. Download the document [Deploy-Guidance-VPN Split Tunnel](https://myadvisor.fasttrack.microsoft.com/CloudVoice/Downloads?SelectedIDs=5_1_0_9 ) from MyAdvisor for more information.

In a global organization with managed links that span continents, QoS is highly recommended because bandwidth for those links is limited in comparison to the LAN.

## QoS queues

To provide a guaranteed level of service for an application on the network, the underlying network devices must have a way to classify different types of traffic. If your organization wants to give voice traffic priority over other traffic, a router (for example) must be able to distinguish between voice traffic and normal web-browsing traffic. 

Differentiated services (DiffServ) provides a framework in which traffic is given different priority by network devices based on the type of services (ToS) field in the header of an IPv4/IPv6 packet. The six most significant bits of the DiffServ field are the differentiated services code point, or DSCP. Using this framework, traffic can be classified as a particular type of traffic (for example, voice), and then marked (101110, or 46 in decimal for voice traffic), so that when network devices process these markings, the traffic can be prioritized accordingly (Expedited Forwarding, in this example).

When network traffic enters a router, the traffic is placed into a queue—if there is no QoS in place, essentially there is only one queue, and data is treated as first-in, first-out. That means voice traffic (which is very sensitive to delays) might get stuck behind traffic from online streaming services. When implementing QoS, you can define multiple queues by using different congestion management features (such as Cisco’s priority queuing and class-based weighted fair queue [CBWFQ]) and congestion avoidance features (such as weighted random early detection [WRED]).

![Total available bandwidth is divided among multiple queues—audio, video, and other traffic—that have been assigned different priorities.](media/Qos-in-Teams-Image2.png "Total available bandwidth is divided among multiple queues—audio, video, and other traffic—that have been assigned different priorities.")

_Figure 2. QoS queues visualized_

After these pieces are in place, it’s possible to deliver predictable QoS because the underlying managed network now understands how to classify, mark, and prioritize traffic. From the Teams perspective, the most important configuration step is the classification and marking of packets, but for end-to-end QoS to be successful you also need to carefully align the application’s configuration with the underlying network configuration.

## Teams QoS scenarios

The guidance for implementing QoS for Teams is based on four scenarios:

*  **Scenario 1:** You’ve deployed, or are deploying, Teams and are planning on implementing QoS via port-based tagging. Port-based tagging is the most reliable method, because it works universally throughout all platforms and is the easiest to implement.  

*  **Scenario 2:** You’ve deployed, or are deploying, Teams and are planning to implement QoS via Group Policy Object tagging. This is sometimes used in combination with scenario 1. Although this scenario is entirely valid, it’s important to understand it will only work for domain-joined Windows clients. Any device that isn’t a domain-joined Windows client won’t be enabled for DSCP tagging.

*  **Scenario 3:** You’ve deployed Skype for Business Online, including QoS tagging, and are now deploying Teams. If this is you, Teams will respect the existing configuration and will use the same port ranges and tagging as the Skype for Business client. In most cases, no additional configuration will be needed. 

    > [!NOTE]
    > If you're using Application Name QoS tagging via Group Policy, you must add Teams.exe as the application name.

*  **Scenario 4:** You’ve deployed, or are deploying, Teams and want to implement QoS via port-based tagging by using a custom port range.

## Recommended DSCP markings

The first step is to classify the traffic flows (such as audio and video) by assigning DSCP values to the unique, non-overlapping port ranges. The DSCP value assigned here will determine the priority of the traffic going through the network, based on network configuration. Each workload gets its own DSCP value, though not necessarily a unique value—some customers might set the same value for voice and video workloads, giving them the same priority in the network.  

The DSCP value to use depends on how you want to prioritize the workload. For example, business requirements might dictate that you give application sharing the same priority as video (and therefore mark it with the same DSCP value as video). Other environments might have an existing QoS strategy in place, which will help you determine the priority of network workloads. 

Table 1 shows the DSCP markings required when using Teams with ExpressRoute. These markings might serve as a good starting point for customers who are unsure what to use in their own environments. To learn more, read [ExpressRoute QoS requirements](https://docs.microsoft.com/azure/expressroute/expressroute-qos).


_Table 1. DSCP markings_

| Client source port range |Protocol|Media category|DSCP value|DSCP class|
|---------|---------|---------|---------|---------|
| 50,000–50,019|TCP/UDP|Audio|46|Expedited Forwarding (EF)|
| 50,020–50,039|TCP/UDP|Video|34|Assured Forwarding (AF41)|
| 50,040–50,059|TCP/UDP|Application/Desktop Sharing|18|Assured Forwarding (AF21)|

Here are some caveats to understand when you use the information in Table 1:

-  If you plan to implement ExpressRoute in the future and haven’t yet implemented QoS, we recommend that you follow the guidance in Table 1 so that DSCP values are the same from sender to receiver. 

-  All clients, including mobile clients and Teams devices, will use these port ranges and will be affected by any DSCP policy you implement that uses these source port ranges. The only clients that will continue to use dynamic ports are the browser-based clients (that is, those clients that let participants join meetings by using their browsers).

-  Although the Mac client does use the same port ranges, the Mac client also uses hard-coded values for audio (EF) and video (AF41). These values are not configurable.


## Source ports used by Teams

In Teams, QoS should be configured based on the source ports used by the different workloads. Neither server-side nor client-side port ranges are currently configurable. 

Note the client source port ranges listed in Table 2, and use their associated QoS DSCP markings.

_Table 2. Client source port ranges_

| Client source port range |Protocol|Media category|DSCP value|DSCP class|
|---------|---------|---------|---------|---------|
| 50,000–50,019|TCP/UDP|Audio|46|Expedited Forwarding (EF)|
| 50,020–50,039|TCP/UDP|Video|34|Assured Forwarding (AF41)|
| 50,040–50,059|TCP/UDP|Application/Desktop Sharing|18|Assured Forwarding (AF21)|

The recommended method of implementing these QoS policies is to use the client source ports with a source and destination IP address of “any.” This will catch both incoming and outgoing media traffic on the internal network. 

> [!NOTE]
> If you've already configured QoS based on source port ranges for Skype for Business Online, the same configuration will apply to Teams and no further changes will be required. If you’ve deployed Skype for Business Server on-premises, you’ll need to redesign your QoS policies.

## Setting DSCP markings

There are multiple approaches to setting the proper DSCP markings for traffic classification:

-  **DSCP marking at the endpoint:** This is generally the preferred option, because the endpoint itself provides the proper markings. Currently this can be done by using a Group Policy object, but it can only be used on domain-joined Windows clients. Mobile clients don’t provide a mechanism to mark traffic by using DSCP values. Although you can’t configure non&ndash;domain-joined Windows clients to tag traffic, clients such as Mac OS have hard-coded tags and will always tag traffic as described above.

-  **Port-based DSCP tagging by using access control lists (ACLs) on routers:** This is a very common option encountered in heterogeneous Windows and Mac environments. In this scenario, the network team marks the traffic at the ingress/egress routers (typically located on the WAN) based on the source port ranges defined for each modality. Although this works across platforms, it only marks traffic at the WAN edge—not all the way to the client machine—and therefore incurs management overhead.

-  **A combination of DSCP markings at the endpoint and port-based ACLs on routers:** We recommend this combination, if possible in your environment. Use a Group Policy object to catch the majority of clients, and also use port-based DSCP tagging to ensure that mobile, Mac, and other clients will still get QoS treatment (at least partially).

You can use policy-based QoS within Group Policy to set the DSCP value for the predefined source port range in the Teams client. Use the port ranges specified in Table 3 to create a policy for each workload.

_Table 3. Port ranges by traffic type_

| Client traffic type|Port range start|Port range end|DSCP value|
|---------|---------|---------|--------|
| Audio|50000|50019|46|
| Video|50020|50039|34|
| Application sharing|50040|50059|18|

> [!NOTE]
> The port ranges set by Teams can't be changed. Review [this support article](https://support.microsoft.com/kb/2409256) for the latest information. 

After you’ve identified the port ranges, the next step is to configure the policy-based QoS settings within a Group Policy object. More information about these steps can be found in [this TechNet article](https://technet.microsoft.com/library/jj205371(v=ocs.15).aspx). 

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

   ![Screenshot of the console window running the gpresult command.](media/Qos-in-Teams-Image3.png "Screenshot of the console window running the gpresult command.")

3. In the generated file, look for the heading **Applied Group Policy Objects** and verify that the names of the Group Policy objects created earlier are in the list of applied policies. 

4. Open the Registry Editor, and go to:

   HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\QoS\

   Verify the values for the registry entries listed in Table 3.

   _Table 3. Values for Windows registry entries for QoS_


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

The DSCP value set by the Group Policy object needs to be present from caller to callee in order for QoS to be effective. By looking at the traffic generated by the Teams client, you can verify that the DSCP value isn’t changed or stripped out when the Teams workload traffic traverses the network. 

Preferably, you capture traffic at the network egress point. You can use port mirroring on a switch or router to help with this.

### Use Network Monitor to verify DSCP values

Network Monitor is a tool you can [download from Microsoft](https://www.microsoft.com/download/4865) to analyze network traffic.

1.  On the PC running Network Monitor, connect to the port that has been configured for port mirroring and start capturing packets. 

2.  Make a call by using the Skype for Business client. Make sure media has been established before hanging up the call. 

3.  Stop the capture.

4. In the **Display Filter** field, use the source IP address of the PC that made the call, and refine the filter by defining DSCP value 46 (hex 0xb8) as search criteria, as shown in the following example:

    Source == "192.168.137.201" AND IPv4.DifferentiatedServicesField == 0xb8 

    ![Screenshot of the Display Filter dialog box in Network Monitor, showing the filters to apply.](media/Qos-in-Teams-Image4.png "Screenshot of the Display Filter dialog box in Network Monitor, showing the filters to apply.")

5.  Select **Apply** to activate the filter.

6.  In the **Frame Summary** window, select the first UDP packet.

7.  In the **Frame Details** window, expand the IPv4 list item and note the value at the end of the line that begins with **DSCP**. 

    ![Screenshot of the Frame Details dialog box in Network Monitor, highlighting DSCP settings.](media/Qos-in-Teams-Image5.png "Screenshot of the Frame Details dialog box in Network Monitor, highlighting DSCP settings.")

In this example, the DSCP value is set to 46. This is correct, because the source port used is 50019, which indicates that this is a voice workload. 

Repeat the verification for each workload that has been marked by the GPO. 
