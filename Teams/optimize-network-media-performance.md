---
title: "Optimize network and media performance for Microsoft Teams"
ms.author: lolaj
author: lolajacobsen
manager: serdars
ms.reviewer: mpottier, dougand, jastark, kojika
ms.topic: article
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-collaboration
audience: Admin
appliesto:
- Microsoft Teams
localization_priority: Priority
f1keywords: None
ms.custom:
- Optimization
description: "This topic describes the set of network performance requirements for Microsoft Teams and gives guidance for assessing and remediating any deficiencies."
---

# Optimize network and media performance for Microsoft Teams

**<font color="red">LOLA: 1) Make full pass to remove SfB, repl w/Teams. 2) Incorp stuff removed from prepare-network (appended at end of this article for now).</font>**

This article describes the set of network performance requirements for Microsoft Teams. It provides in-depth guidance for assessing and optimizing your network for best Teams performance. 

If you're just starting your Teams rollout, begin by reading [Prepare your organization's network for Teams](prepare-network.md).
  
The quality of Teams media (audio, video, and application sharing) over IP is dependent on the quality of end-to-end network connectivity. For optimal media quality in Teams, you need to have a high-quality connection between your company network and Teams. 
  
> [!TIP]
> If you need help optimizing your network performance, working with a Teams solution provider is a good option. To find a Teams partner, go to the [Teams solution provider portal](https://www.microsoft.com/solution-providers/home). 
  
## Network connectivity requirements
To see the basic network requirements for Teams, read [Prepare your organization's network for Teams](prepare-network.md).

## What affects media quality?

The biggest factors in Teams media quality (audio, video, and application sharing) are devices and network connectivity. 
  
### Devices

In a media session (audio, video, or screen sharing), devices - for example, headsets and Web cams - have a big impact on overall audio and video quality. Uncertified devices or devices with incorrect device drivers will produce lower overall sound quality for audio and lower image quality for video. Certified devices, on the other hand, help with echo cancellation, noise filtering, video resolution and reduce latency - in other words, they're your best bet for ensuring high-quality media sessions in Teams.
  
Although certified audio and video media devices aren't required, we recommend that you use devices certified for Teams for the best-possible media experience. To get the latest and up-to-date information on Teams certified devices, go to the [Teams Marketplace](https://office.com/teamsdevices).

Use the [Call Quality Dashboard (CQD)](turning-on-and-using-call-quality-dashboard.md), in the Teams admin center, to see if your devices are working correctly and to monitor audio and video media quality.

### Network

The quality of your network connections directly affects the quality of media sessions in Teams. These problems are the likeliest culprits if you're experiencing poor audio or video quality in Teams:
  
- **Latency** This is the time it takes to get an IP packet from point A to point B on the network. This network propagation delay is essentially tied to physical distance between the two points and the speed of light, including additional overhead taken by the various routers in between. Latency is measured as one-way or Round-trip Time (RTT).
    
- **Packet Loss** This is often defined as a percentage of packets that are lost in a given window of time. Packet loss directly affects audio quality—from small, individual lost packets having almost no impact, to back-to-back burst losses that cause complete audio cut-out.
    
- **Jitter** Sometimes called inter-packet arrival jitter, jitter is the average change in delay between successive packets. Teams can adapt to some levels of jitter through buffering. It's only when the jitter exceeds the buffering that a participant will notice the effects of jitter.
    
> [!NOTE]
>  Buffering for jitter will increase end-to-end latency.
  

  
### Use Quality of Service (QoS) to  prioritize media traffic

Traffic congestion across a network often degrades media quality in Teams. To allow audio and video packets to travel the network quicker and to be prioritized over other network traffic in a congested network, implement [Quality of Service (QoS)](QoS-in-Teams.md).

## How network traffic flows in Teams

**<font color="red">REVIEWERS: This seems to be duplicate of the next section. Need to combine. Can someone help me with this?</font>**

Teams combines three forms of traffic:

-   Data traffic between the Office 365 online environment and the Teams client (signaling, presence, chat, file upload and download, OneNote synchronization).
-   Peer-to-peer real-time communications traffic (audio, video, screen sharing).
-   Conferencing real-time communications traffic (audio, video, screen sharing).

This impacts the network on two levels: traffic will flow between the Teams clients directly for peer-to-peer scenarios, and traffic will flow between the Office 365 environment and the Teams clients for meeting scenarios. To ensure optimal traffic flow, traffic must be allowed to flow both between the internal network segments (for example, between sites over the WAN) as well as between the network sites and Office 365. Not opening the correct ports or actively blocking specific ports will lead to a degraded experience.

For the two defining network segments (Client to Microsoft Edge and Customer Edge to Microsoft Edge), consider the following recommendations.

|Value  |Client to Microsoft Edge  |Customer Edge to Microsoft Edge  |
|:--- |:--- |:--- |
|**Latency (one way)** \*  |< 50ms          |< 30ms         |
|**Latency (RTT or Round-trip Time)** \* |< 100ms   |< 60ms |
|**Burst packet loss**    |<10% during any 200ms interval         |<1% during any 200ms interval         |
|**Packet loss**     |<1% during any 15s interval          |<0.1% during any 15s interval         |
|**Packet inter-arrival Jitter**    |<30ms during any 15s interval         |<15ms during any 15s interval         |
|**Packet reorder**    |<0.05% out-of-order packets         |<0.01% out-of-order packets         |

\* The latency metric targets assume your company site or sites and the Microsoft edges are on the same continent.

Your company site connection to the Microsoft network edge includes first hop network access, which can be WiFi or another wireless technology.

These network performance targets assume that you have sufficient bandwidth and/or that you've [implemented QoS](QoS-in-Teams.md). In other words, the requirements apply to Teams media traffic when the network connection is under a peak load.


## How Teams media flows through your network

Teams media travels through many different devices, client apps, server software, and across different networks. The end-to-end latency of this media is the total amount of latency that is introduced across all components and network segments. The quality of the end-to-end network connection is determined by the network segment with the worst quality. This segment acts as a bottleneck for this network traffic.
  
The following diagram illustrates one-way audio flow in a conference from one Teams participant to another.
  
![ExpressRoute Call Flow.](../images/c026e8e5-ba09-42c0-9e03-60fbfda1cb02.png)
  
In this conferencing scenario, the media path consists across the following network segments:
  
1. **Connection from User 1 to the edge of the Microsoft network** This usually includes a network connection such as WiFi or Ethernet, the WAN connection from User 1 to the Internet egress point (your network Edge device), and the Internet connection from your network Edge to Microsoft network Edge.
    
2. **Connection within Microsoft network** This is between the Microsoft Edge to Skype for Business Online data center, where the A/V Conferencing servers are used.
    
3. **Connection within Microsoft Network** This is between the Skype for Business Online data center and Microsoft network Edge.
    
4. **Connection from Microsoft network edge to User 2** This includes the Internet connection from your network Edge to Microsoft network Edge, the WAN connection from User 2 to the Internet egress point (your network Edge), and the network connection such as a WiFi or an Ethernet.
    
The following diagram shows breakdown of components and network segments of a Teams PSTN call:
  
![ExpressRoute PSTN Carrier Call Flow.](../images/768a88df-c8a9-4171-a158-565a698f0193.png)
  
In a PSTN call scenario, the media path crosses the following network segments:
  
1. **Connection from a Teams caller to the edge of the Microsoft Network** This usually includes a network connection such as WiFi or Ethernet, the WAN connection from the Teams caller to the Internet egress point (your network Edge device), and the Internet connection from your network Edge to Microsoft network Edge.
    
2. **Connection within Microsoft network** This is between the Microsoft Edge to Teams data center, where a Mediation Server is used.
    
3. **Connection within Microsoft Network** This is between the Teams data center and Microsoft network Edge.
    
4. **Connection between Microsoft Network and the PSTN service provider partners** This is the connection that exists to place a PSTN call from a Teams client that is outside of the Microsoft network.
    
### Network performance requirements from Teams to Microsoft network Edge

For optimal Teams media quality, the following network performance metrics targets or thresholds are required for a connection from your company's network to the Microsoft network Edge. This segment of the network includes your internal network, this includes all WiFi and Ethernet connections, any company site-to-site traffic over a WAN connection, for example Multiprotocol Label Switching (MPLS), as well as the Internet or ExpressRoute partner connections to the Microsoft network Edge.
  
> [!CAUTION]
> **Connectivity between a Teams client on your company network to Office 365 services must meet these following network performance requirements and thresholds.**
  
|||
|:-----|:-----|
|**Metric** <br/> |**Target** <br/> |
|Latency (one way)  <br/> |< 50ms  <br/> |
|Latency (RTT or Round-trip Time)  <br/> |< 100ms  <br/> |
|Burst packet loss  <br/> |<10% during any 200ms interval  <br/> |
|Packet loss  <br/> |<1% during any 15s interval  <br/> |
|Packet inter-arrival Jitter  <br/> |<30ms during any 15s interval  <br/> |
|Packet reorder  <br/> |<0.05% out-of-order packets  <br/> |
   
 **Other performance target requirements:**
  
- The Microsoft network has over 160 Edge locations worldwide. We work with major Internet Service Providers (ISPs) worldwide through those Edge sites. The latency metric target assumes your company site or sites and the Microsoft Edges are on the same continent.
    
- Your company site or sites to the Microsoft network Edge connection include first hop network access, which can be WiFi or another wireless technology. 
    
- The network performance target assumes proper bandwidth and/or quality of service planning. In other words, This applies directly to Teams media traffic when the network connection is under a peak load.
    
### Network performance requirements from your network Edge to Microsoft network Edge

The following are the network performance targets or thresholds that are required for the connection between your network Edge and the Microsoft network Edge. This segment of the network excludes the customer's internal network or WAN, and is intended as guidance when testing your network traffic that is sent over the Internet.
  
> [!CAUTION]
> **Connectivity between your company network Edge to the Microsoft network edge must meet these following network performance requirements and thresholds.**
  
|||
|:-----|:-----|
|**Metric** <br/> |**Target** <br/> |
|Latency (one way)  <br/> |< 30ms  <br/> |
|Latency (RTT)  <br/> |< 60ms  <br/> |
|Burst packet loss  <br/> |<1% during any 200 ms interval  <br/> |
|Packet loss  <br/> |<0.1% during any 15s interval  <br/> |
|Packet inter-arrival Jitter  <br/> |<15ms during any 15s interval  <br/> |
|Packet reorder  <br/> |<0.01% out-of-order packets  <br/> |
   
 **Other performance target requirements:**
  
- The performance target requires connection between any of your company's network Edge and its nearest Microsoft network Edge, to be on the same continent.
    
- The network performance target assumes proper bandwidth and/or quality of service planning. This also applies to Teams media traffic when the network connection is under a peak load.
    
## Measuring network performance

To measure the actual network performance, especially for latency and packet loss, from any company network site to a network Edge, you can use tools such as ping, test against a set of Skype for Business media relay services running from the Microsoft Edge and data center sites. 

>[!NOTE]
> Measuring network performance through ping (ICMP) is not effective. For that reason, the anycast IP expose below will stop answering to ICMP requests starting in Jan, 2020. To measure network performace effectively, Microsoft recommends the [Network Assesment Tool](https://www.microsoft.com/download/details.aspx?id=53885).
  
For testing Internet connections to the Microsoft network, it is recommended that you test against the following VIPs of the Skype for Business media relays. The *Anycast VIP*  will resolve to an IP address of a Media Relay in a Microsoft network Edge site that is closest to the testing location.
  
||||
|:-----|:-----|:-----|
|**IP address** <br/> |**Type** <br/> |**Location** <br/> |
|13.107.8.2  <br/> |VIP  <br/> |World Wide Anycast IP  <br/> |
   
 **Here are some high level recommendations to follow for assessing network performance:**
  
- You should assess your internal network as well as the connections to Office 365.
    
- You should assess and gather data for all of your networks over a long period of time. We recommend for you to perform your testing of network performance for a minimum of a week, so that you can see usage patterns for all business days and hours. This will show you peak times.
    
- You should take multiple samples of network performance measurements. We recommend taking a measurement every 10 minutes from a company site during the entire period of time you are gathering data. For comparing the Skype for Business Online network performance requirements, take the 90th percentile measurement value from this sample data set. 
    
- You should continuously assess the network's performance. Network utilization varies over time due to usage pattern changes, new enterprise-based applications that use a large amount of bandwidth, and changes to your organizational or physical company locations. It is important for you to continuously monitor your network performance against these network performance requirements and targets/thresholds and make timely adjustments to ensure the most optimal Real-Time media quality. 
    
## Measuring Network Performance using Azure VMs
<a name="bkNetworkPerf"> </a>

Instead of testing against the Microsoft network Edge sites, there are network assessment solutions from Skype for Business customers and partners that leverage testing setup for services in the Microsoft Azure cloud. In those solutions, the network assessment tools test latency, packet loss and jitter against custom endpoints set up as a service in the Azure cloud. As a result, the test network traffic travels through one additional network segment, which is the connection within the Microsoft network between the network edges and Azure data centers that hosts the network assessment service.
  
For those network assessment solutions based on Azure hosted testing services. We recommend performing the network assessment within country and/or region. For example, for customer sites in east U.S., the assessment should be performed against a testing service instance hosted in Azure's east US data center region. 
  
Below are the latency (RTT) targets for the Azure service based network assessment setup. The one-way latency targets will be half of the corresponding RTT targets. The packet loss and jitter goals stays the same as those defined for Skype Media Relay based testing.
  
|||||
|:-----|:-----|:-----|:-----|
|**Customer region** <br/> |**Azure region** <br/> |**Your network Edge - Azure Round-trip Time (RTT)** <br/> |**Your Site - Azure Round-trip Time (RTT)** <br/> |
|Central US  <br/> |Central US  <br/> |99  <br/> |139  <br/> |
|East US  <br/> |East US  <br/> |86  <br/> |126  <br/> |
|North Central US  <br/> |North Central US  <br/> |97  <br/> |137  <br/> |
|South Central US  <br/> |South Central US  <br/> |94  <br/> |134  <br/> |
|West US  <br/> |West US  <br/> |94  <br/> |134  <br/> |
|Hawaii US  <br/> |West US  <br/> |116  <br/> |156  <br/> |
|Canada Central  <br/> |Canada Central  <br/> |138  <br/> |178  <br/> |
|Canada East  <br/> |Canada East  <br/> |131  <br/> |171  <br/> |
|North Europe  <br/> |North Europe  <br/> |99  <br/> |139  <br/> |
|West Europe  <br/> |West Europe  <br/> |95  <br/> |135  <br/> |
|East Asia  <br/> |East Asia  <br/> |118  <br/> |158  <br/> |
|Southeast Asia  <br/> |Southeast Asia  <br/> |97  <br/> |137  <br/> |
|Japan East  <br/> |Japan East  <br/> |111  <br/> |151  <br/> |
|Japan West  <br/> |Japan West  <br/> |118  <br/> |158  <br/> |
|Brazil South  <br/> |Brazil South  <br/> |70  <br/> |110  <br/> |
|Australia East  <br/> |Australia East  <br/> |124  <br/> |164  <br/> |
|Australia Southeast  <br/> |Australia Southeast  <br/> |124  <br/> |164  <br/> |
|Central India  <br/> |Central India  <br/> |103  <br/> |143  <br/> |
|South India  <br/> |South India  <br/> |103  <br/> |143  <br/> |
|West India  <br/> |West India  <br/> |103  <br/> |143  <br/> |
|China East  <br/> |China East  <br/> |120  <br/> |160  <br/> |
|China North  <br/> |China North  <br/> |120  <br/> |160  <br/> |
   
#### Voice quality SLA

**<font color="red">REVIEWERS: The SfBO version of this article included a voice quality SLA. AFAICT, we don't have one for Teams - correct?  I commented out the SfBO SLA info.</font>**
<!--
The [Skype for Business Online Voice Quality SLA](http://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&amp;DocumentTypeId=37) applies to any eligible call placed by any Skype for Business Online voice service user within the correct license and subscription that enables that user to make any type of VoIP or PSTN call. A voice quality SLA should include that all of the following conditions are addressed:
  
- Calls from Microsoft certified IP Phones.
    
- Wired Ethernet connections.
    
- Voice quality issues due to Microsoft Network problems.
    
> [!NOTE]
> The voice quality SLA excludes those calls where the low call quality is caused by problems in non-Microsoft networks including ExpressRoute partner and other networks. 
--> 

## Related topics


**<font color="red">=============Below here: stuff I cut from prepare-network. ==========</font>**
## Test the network

After you're done optimizing your network, test it to see if your optimizations worked. Did your changes give you the network-performance improvements you were looking for?

Best practice: Take baseline readings once in a while, when your network is working well. This gives you something to compare against when you're having problems. Similarly, if you do a major update to your network, take another baseline.

Download the [Skype for Business Network Assessment Tool](https://www.microsoft.com/download/details.aspx?id=53885) to test whether your network is ready for Teams. This tool tests whether all the correct ports are open, and it can identify network impairments.

After you download and install the tool, you'll find it in C:\Program Files (x86)\Microsoft Skype for Business Network Assessment Tool. A detailed guide for how to use the tool, Usage.docx, is included in that directory.

### Test for opened ports

To test for opened ports, open a Command prompt window and navigate to the Network Assessment Tool directory by entering **cd C:\Program Files (x86)\Microsoft Skype for Business Network Assessment Tool**. At the command prompt, start the test for opened ports by entering **networkassessmenttool.exe /connectivitycheck**.

After running the checks, the tool will either display the message “Verifications Completed Successfully” or report on the ports that were blocked. It also generates a file named Connectivity_results.txt, which contains the output from the tool and stores it in the %userprofile%\\appdata\\local\\microsoft skype for business network assessment tool\\ directory.

Best practice: Run the connectivity checks on a regular basis to ensure that ports are open and functioning correctly.

### Test for network impairments

Network impairments affect Teams performance, so you'll want to find and remediate them. The most common network impairments are delay (latency), packet loss, and jitter.

- **Latency:** This is the time it takes to get an IP packet from point A to point B on the network. This network propagation delay is essentially tied to physical distance between the two points and the speed of light, including additional overhead taken by the various routers in between. Latency is measured as one-way or round-trip time.

- **Packet loss**: This is often defined as a percentage of packets that are lost in a given window of time. Packet loss directly affects audio quality—from small, individual lost packets having almost no impact to back-to-back burst losses that cause audio to cut out completely.

- **Inter-packet arrival jitter, or simply jitter:** This is the average change in delay between successive packets. Most modern VoIP software, including Skype for Business, can adapt to some levels of jitter through buffering. It's only when the jitter exceeds the buffering that a participant will notice the effects of jitter.

The maximum values for these impairments are described in [Media quality and network connectivity performance](/SkypeForBusiness/optimizing-your-network/media-quality-and-network-connectivity-performance). When testing for these impairments, we distinguish between two separate segments:

- The *edge segment* is the segment in which your router lives. This is the closest logical network segment connected to the internet at each of your locations. In most cases, this is the connection point of the router, or possibly a perimeter network (also known as *DMZ*, *demilitarized zone*, and *screened subnet*). No further traffic that affects devices other than the router should occur between this segment and the internet.

- The *client segment* is the logical network segment in which your clients reside.

You should test both segments by using the Network Assessment Tool. To test the segment, navigate to the directory and enter **networkassessmenttool.exe** at the command prompt. The results are written to a file named Results.tsv, and you can compare them to the [requirements](/SkypeForBusiness/optimizing-your-network/media-quality-and-network-connectivity-performance) for each segment.

For best Teams performance, both segments should meet the requirements. Best practice: Run the tool multiple times for one hour straight to get a good indication of your network’s performance.


## Bandwidth requirements

Microsoft Teams is designed to give the best audio, video and content sharing experience regardless of your network conditions. That said, when bandwidth is insufficient, Teams prioritizes audio quality over video quality.

Where bandwidth isn't limited, Teams optimizes media quality, including up to 1080p video resolution, up to 30fps for video and 15fps for content, and high-fidelity audio. Here are the bandwidth requirements for Teams:

[!INCLUDE [Bandwidth requirements](includes/bandwidth-requirements.md)]

**<font color="red">REVIEWERS: The following table was commented out of the article. It's in more depth than the bandwidth-requirements article included above. Keep or kill?</font>**

|Activity  |Download Bandwidth  |Upload Bandwidth  |Traffic Flow |
|---------|---------|---------|---------|
|**Peer to peer Audio Call**     |0.1 Mb         |0.1Mb         |Client <> Client         |
|**Peer to peer Video Call (full screen)**     |4 Mb         |4Mb         |Client <> Client          |
|**Peer to peer Desktop Sharing (1920*1080 resolution)**     |4 Mb         |4 Mb         |Client <> Client          |
|**2 Participant Meeting**     |4 Mb         |4 Mb         |Client <> Office 365         |
|**3 participant meeting**     |8 Mb         |6.5 Mb         |Client <> Office 365           |
|**4 participant meeting**     |5.5 Mb         |4 Mb         |Client <> Office 365           |
|**5 participant+ meeting**     |6 Mb         |1.5 Mb         |Client <> Office 365           |

## Firewall and proxy requirements

TCP ports 80 and 443 are used to connect to web-based content such as SharePoint Online, Exchange Online, and Teams Chat services. Plug-ins and connectors also connect over these TCP ports. The four UDP ports (3478 through 3481) are used for media such as audio and video, to ensure they flow correctly.

If your organization requires that you specify the exact IP address ranges and domains to which these ports should be opened, you can restrict the target IP ranges and domains for these ports. For a list of exact ports, protocols, and IP ranges, see [Office 365 URLs and IP address ranges](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges). If you choose to restrict the target IP address ranges and domains, you must ensure that you keep the list of ports and ranges up to date because they might change. It’s also a good practice to test whether all ports are opened by running the [Skype for Business Network Assessment Tool](https://www.microsoft.com/download/details.aspx?id=53885) on a regular basis. 

If you use one, we recommend that you bypass the proxy server for all Teams services. Although using a proxy might work, it’s likely that quality will be reduced due to media using TCP instead of UDP. For more information about proxy servers and bypassing them, see [Office 365 URLs and IP address ranges](office-365-urls-ip-address-ranges.md).

**<font color="red">============REMOVED from article: Do we need Cloud Connector Edition for Teams?=====**</font>

### Online deployment with Cloud Connector Edition

Skype for Business Online Cloud Connector Edition is a hybrid offering that consists of a set of packaged Virtual Machines (VMs) that implement on-premises PSTN connectivity. By deploying a minimal Skype for Business Server topology in a virtualized environment, you will be able to send and receive calls with landlines and mobile phones through the existing on-premises PSTN voice infrastructure.
  
If you decide to deploy Azure ExpressRoute and Cloud Connector Edition, we recommend for you to set up at least one Express Route connection for each continent between each continent's main site to it's closest [ExpressRoute peering location](https://azure.microsoft.com/documentation/articles/expressroute-locations/). Depending on cost vs benefit, for each continent you can choose to deploy additional ExpressRoute connections from sites where network performance targets aren't being met.
  
If you have an on-premises Skype for Business deployment, you must follow the [Planning Guide for Skype for Business Cloud Connector Edition](https://technet.microsoft.com/library/mt605227.aspx). Specifically, the Access Edge and A/V Edge services should be assigned public IP addresses and reachable from Office 365 data centers.
  
In the following example, Contoso is a European accounting firm with presence in a few major European countries and cities. When they sign up for Skype for Business Online for all their collaboration needs, they decided to put a Cloud Connector for each country they have a physical location to continue to use their PSTN infrastructure and carrier contracts that already exist. Based on their testing from all their sites and Microsoft network Edge, they determined that a single ExpressRoute connection in London will help meet the Skype for Business client connection network performance targets described in [Network Performance requirements from a Skype for Business client to Microsoft network Edge](media-quality-and-network-connectivity-performance.md#bkSfBClienttoEdge).
  
![ExpressRoute Cloud Connector One.](../images/ebdc96e5-b22a-4bf2-b668-062460b4b890.png)
  
Below is another deployment option for Contoso. In this case, they decided to set up an ExpressRoute connection at each site where a Cloud Connector is deployed. 
  
![ExpressRoute Cloud Connector Two.](../images/06d967a9-64f5-4d7d-98ed-3f3add1b7c2b.png)
