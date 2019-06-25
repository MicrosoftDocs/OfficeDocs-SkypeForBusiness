---
title: "ExpressRoute and QoS in Skype for Business Online"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: mpottier, dougand
ms.topic: article
ms.assetid: 20c654da-30ee-4e4f-a764-8b7d8844431d
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
search.appverid: MET150
ms.collection: Adm_Skype4B_Online
audience: Admin
appliesto:
- Skype for Business 
- Microsoft Teams
localization_priority: Normal
f1keywords: None
ms.custom:
- Optimization
description: "Learn about using Azure ExpressRoute to have a network with bandwidth requirements and Quality of Service capability for a business class user experience. "
---

# ExpressRoute and QoS in Skype for Business Online

Connect to Office 365 over a dedicated network connection using Azure ExpressRoute for Office 365 and Skype for Business Online. Your dedicated connection for your Skype for Business apps will give you reliable and predictable performance as well as privacy away from the public internet. You can now buy a better network connection to Office 365 and Skype for Business Online that adds predictability, business class reliability and comes with an uptime SLA.
  
> [!NOTE]
> A new version of the bandwidth calculator is available: [Skype for Business, Bandwidth Calculator](https://go.microsoft.com/fwlink/?LinkId=715766). However, the directions in this document use the Lync 2010 and 2013 Bandwidth Calculator. 
  
## Skype for Business Online and ExpressRoute

Working with a Microsoft's ExpressRoute partner, you can connect a variety of Office 365 applications including Skype for Business Online in the cloud over a dedicated connection. However, the real-time voice and video communications capabilities for Skype for Business require network services that are specifically configured to support these Office 365 real-time workloads. This includes a network that has sufficient bandwidth to carry the required volume of traffic and be capable of supporting Quality of Service (QoS) to deliver a business class experience for your users.
  
This document is designed to help you, administrators and network designers understand the special challenges needed to support real-time communications, the tools provided by Microsoft to assist you in designing a network capable of supporting those requirements, and to walk you through the design process using a case study. 
  
The first part of this document walks you through a case study to help you with the network design using the [Lync 2010 and 2013 Bandwidth Calculator](https://go.microsoft.com/fwlink/?LinkId=690282) to estimate the network requirements for a large, multi-site Skype for Business ExpressRoute deployment. The second part of this document gives you with the fundamental concepts of Quality of Service (QoS), a deep-dive on the specific technical details for supporting Skype for Business real-time communications, and the specific types of network services that are needed.
  
All of the information here will give you the technical details and understanding for QoS and ExpressRoute, an understanding of the specific challenges you'll be facing, and give you a working knowledge of the tools and techniques that will allow you to successfully deploy an ExpressRoute across your Skype for Business network. 
  
## Getting started

When you are getting ready for ExpressRoute for Skype for Business, it's a good idea to look at the different ExpressRoute connection models and the various choice of partners and locations and read how to purchase and provision ExpressRoute within your business. Here are some resources to get you started: 
  
- [Azure ExpressRoute]( https://go.microsoft.com/fwlink/?LinkId=690283)
    
- [ExpressRoute Pricing](https://go.microsoft.com/fwlink/?LinkId=690284)
    
- [ExpressRoute documentation](https://go.microsoft.com/fwlink/?LinkId=690285)
    
## Part 1: Case study - ExpressRoute for Dewey Law, LLC.

This case study for Dewey Law, LLC. will show you how to setup a network, order network access services, and determine the bandwidth requirements to support ExpressRoute for Skype for Business Online.
  
 **Background** Dewy Law LLC. is a large national law firm with 790 attorneys and a total of 5,580 employees spread across 78 locations. The firm has a headquarters in New York, three regional offices in Chicago, San Francisco and Dallas, along with 24 large and 50 small branch offices scattered around the country. The firm handles large, complex cases with the workload typically spread among two or more of the offices. Having this network design results in considerable network traffic between the offices.
  
Dewy Law LLC. is a relatively young firm and the attorneys and other staff members are very comfortable with technology and greatly depend on it for their daily work. 
  
 **Distribution of users by locations and positions**
  
||**Headquarters (NY)**|**Regional offices (3)**|**Large branch offices (24)**|**Small branch offices (50)**|
|:-----|:-----|:-----|:-----|:-----|
|Executive  <br/> |20  <br/> |10  <br/> |1  <br/> |1  <br/> |
|Partners  <br/> |150  <br/> |50  <br/> |10  <br/> |5  <br/> |
|Associates  <br/> |300  <br/> |100  <br/> |20  <br/> |10  <br/> |
|Paralegal  <br/> |400  <br/> |125  <br/> |30  <br/> |15  <br/> |
|Executive admins  <br/> |100  <br/> |35  <br/> |6  <br/> |3  <br/> |
|IT and general Administrative  <br/> |100  <br/> |25  <br/> |3  <br/> |2  <br/> |
|Total per site  <br/> |1,070  <br/> |345  <br/> |70  <br/> |36  <br/> |
|Total per site class  <br/> |1,070  <br/> |1,035  <br/> |1,680  <br/> |1,800  <br/> |
   
### Setting up the network

To deliver consistent and high quality real-time services for Dewey Law LLC., there are a couple basics requirements that must be met:
  
- They want to provide voice services during power failure so their network distribution switches and routers must provide power over Ethernet (PoE) IEEE 802.3af or 802.3at.
    
- The networking switches and routers must also use uninterrupted power sources (UPS) so they can continue operating during a power failure.
    
    They have a Wi-Fi connections to their LAN offices, so we highly recommend they use a certified Skype for Business Wi-Fi infrastructure partner from [Skype for Business Solutions](https://go.microsoft.com/fwlink/?LinkId=690281).
    
    > [!TIP]
    >  802.11n and 802.11ac wireless access points are recommended.
  
- And most importantly, all of the LAN networks in all offices must be set up to provide Quality of Service (QoS). This includes PCs, laptops and any networking hardware such as switches and routers.
    
Now that you have the basics covered, to deliver business grade voice services for Dewey Law LLC., we recommend using Multi-Protocol Label Switching (MPLS) IP service from a network service partner that will connect to the Azure ExpressRoute service. MPLS provides an IP service with performance guarantees for delay, jitter and packet loss. However, if MPLS isn't available, Ethernet connected to one of our ExpressRoute data exchange partners can also be used.
  
MPLS providers offer several class of service levels but each use different terms to identify them. You will have to work closely with your provider to ensure they understand the data that you have input into the [Lync 2010 and 2013 Bandwidth Calculator](https://go.microsoft.com/fwlink/?LinkID=690282) and the options available and are recommended for the different Office 365 real-time workload applications.
  
There are two options for how data from Skype for Business applications can be mapped to the appropriate MPLS classes of service:
  
- Endpoint Marking of traffic using DiffServ Control Point (DSCP)
    
- Network Access Control List (ACL) based
    
To implement Endpoint Marking, you must configure all domain joined Windows machines for Dewey Law LLC. to mark each packet with the appropriate DiffServ Control Point (DSCP) marking and then implement QoS on all network switches and routers across all of their office sites to make sure the QoS markings are maintained and aren't removed. DSCP markings on network packets tell the service provider how that network packet is prioritized. **There is more information on DSCP in the QoS section in Part 2.**
  
For network ACL-based assignment, the DSCP priority markings are implemented at an upstream router and are based on the UDP source port. The recommended port ranges for each application are listed in Section 2.6.1.1 of [Network Planning, Monitoring, and Troubleshooting with Lync Server](https://go.microsoft.com/fwlink/?LinkId=690286). It is important that you coordinate this with Dewey Law LLC's overall QoS implementation and design and be aware of different QoS policies and the potential for packet marking mismatches.
  
Each ExpressRoute network service provider will have a class of service (QoS) that is appropriate for real-time voice and video. This COS is called 'Expedited Forwarding' (EF) for voice and 'Assured Forwarding' (AF) for video. You must be very careful in sizing the amount of bandwidth you purchase for voice EF traffic. The reason is that the voice class of service is very unforgiving in the event you send more voice traffic than the class of service is provisioned for.
  
> [!TIP]
>  Any traffic that is sent on the voice class of service in excess of the service provider's commitment is immediately discarded which will direct effect voice quality.
  
When looking at the overall design for Dewey Law LLC. it is extremely important that you accurately determine the amount of network bandwidth that they need to support the voice traffic across their network and be marking each voice packet (and only voice packets) with the DSCP setting for voice (i.e. DSCP EF 46).
  
To implement QoS across their enterprise network, the endpoints or routers must mark each packet with the appropriate Layer 3 priority indicator (i.e., DSCP). Along the entire network path, each switch and router must have the QoS option turned on. Having even only one network switch or router that doesn't have QoS turned on, the QoS markings on voice or video packets passing through that switch or router could be stripped off. This effectively disables QoS in all downstream switches and routers which decreases the value of having ExpressRoute.
  
This also requires that the association of the Layer 3 and Layer 2 QoS priorities be defined at each point. The Layer 2 priority mechanisms are defined in IEEE 802.1p for wired networks and 802.11e/WMM for Wi-Fi networks. More importantly, the network router facing the network service provider's MPLS network must maintain the DSCP settings on all outbound packets so that they will maintain the appropriate MPLS class of service. 
  
> [!TIP]
>  For the specific details regarding QoS set-up, refer to Section 2.6 [Network Planning, Monitoring, and Troubleshooting with Lync Server]( https://go.microsoft.com/fwlink/?LinkId=760669). You can also see [Plan network requirements for Skype for Business 2015](https://go.microsoft.com/fwlink/?LinkId=690287) for more network planning requirements.
  
### Ordering Network Access Services

Once you have the QoS network prerequisites and mechanisms in place to support ExpressRoute, the next step is to place an order for the ExpressRoute network access services. When ordering ExpressRoute access services for Dewey Law LLC from the Microsoft network services provider partner, you will need to provide two things:
  
- The total amount of bandwidth required to connect each site to ExpressRoute and Office 365.
    
- The total bandwidth required for each class of service that is required to support Skype for Business apps that are being used at Dewey Law LLC. The class of service bandwidth requirement is driven by the volume of traffic you expect from each of the various Skype for Business applications like voice, video, IM, presence, and screen sharing.
    
### Determining Bandwidth Requirements for Skype for Business Applications

For Dewey Law LLC., once you have determined the total bandwidth required you now need to know how that total amount of bandwidth should be divided among the various classes of service. For example, how much bandwidth for each Skype for Business application.
  
To determine those requirements at each of the Dewey Law LLC. sites, you will use the [Lync 2010 and 2013 Bandwidth Calculator](https://go.microsoft.com/fwlink/?LinkID=690282). This calculator is an Excel-based tool that allows you to specify the expected use of the various Skype for Business applications including voice, video, conferencing, and screen sharing. The calculator will automatically generate an estimate of the bandwidth and CoS requirements for each site on their network. When you download the Lync 2010 and 2013 Bandwidth Calculator, a user's guide will also be downloaded which will give you details on using it. 
  
To help you with the spreadsheet, the various cells in the spreadsheet are color-coded:
  
- **Green** These are general data input areas.
    
- **Yellow** These are advanced data input areas. You can change these, but do so carefully.
    
- **Red** These are read-only areas and are locked input values and can't be changed.
    
- **Gray** These are display-only areas. They are the results or data that is from the general input areas.
    
The design process for Dewey Law LLC. begins by characterizing their users into different 'Personas.' For each persona you define, you can specify their expected use of the various Skype for Business applications ('None', 'Low', 'Medium', 'High', or one of three defined 'Custom' settings). Those selections are found in the 'Persona' worksheet. The specific usage for each choice ('Low', 'Medium', or 'High') is provided, but the defaults for each choice can be changed. By identifying the number of users for each persona that is located at each site, the calculator can compute the total bandwidth required for each location.
  
You can also specify the audio and video codecs that are used, whether forward error correction is used and also other system parameters that will affect the bandwidth requirements. You can use the default settings in the Lync 2010 and 2013 Bandwidth Calculator or select different codecs and other system parameters. For Dewey Law LLC's site design, the default settings can be used. However, to change from any of the default settings there is a pull-down menu with all of the available choices. The bandwidths that are used for each choice are included in the 'Codecs' worksheet. When you change any setting, the change in bandwidth and class of service (CoS) mix at each site is updated. Having this capability allows you to test different potential configurations for them and see the impact the changes will have on bandwidth requirements for them.
  
We have defined three personas for Dewey Law LLC., 'Executive/Partner', 'Associate/Paralegal' and 'IT admins'. The table below shows how we have set the usage profiles for the various Skype for Business apps for each persona.
  
 **Personas and usage profiles ('Persona' Worksheet- Columns A through P)**
  
|**Persona**|**IM/Presence**|**P2P audio**|**P2P video**|**Conferencing audio**|**Conferencing video**|**Desktop sharing**|**Audio Conferencing**|**Lync 2010 RTV_Type**|**Remote Users**|**Lync 2013 stereo audio**|**Lync 2013 video quality**|**Lync 2013 users behavior for P2P video window**|**Lync 2013 Multi-view usage**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|Executive/ Partner  <br/> |High  <br/> |Medium  <br/> |Low  <br/> |Medium  <br/> |Medium  <br/> |None  <br/> |Medium  <br/> |CIF  <br/> |0%  <br/> |0%  <br/> |Best  <br/> |Typical  <br/> |Typical  <br/> |
|Associate/ Paralegal  <br/> |High  <br/> |Medium  <br/> |Low  <br/> |Medium  <br/> |High  <br/> |High  <br/> |Medium  <br/> |CIF  <br/> |0%  <br/> |0%  <br/> |Medium  <br/> |Typical  <br/> |Typical  <br/> |
|IT admins  <br/> |High  <br/> |Medium  <br/> |None  <br/> |Low  <br/> |None  <br/> |None  <br/> |Medium  <br/> |CIF  <br/> |0%  <br/> |0%  <br/> |Medium  <br/> |Typical  <br/> |Typical  <br/> |
   
You will need to enter the information in the **Distribution of users by locations and positions** table above in the 'Sites' worksheet of the Lync 2010 and 2013 Bandwidth Calculator. As the number of users in the regional offices is identical, they are defined for one 'Site' and specified that there were three instances of it. The same was done for the large and small branches where there were 24 and 50 users in sites respectively.
  
After specifying the settings for each persona, you need to enter the number of users in each persona at each site in the 'Sites' worksheet. The total users for all sites is updated automatically. Since there aren't users at the Office 365 location, they should all be entered in the 'Branches' rows of the worksheet. The Lync 2010 and 2013 Bandwidth Calculator then populates the 'Best Effort Class', 'Data Traffic Class' and 'Real-time traffic class' columns in the 'WAN BW per QoS traffic class' table. This is shown in the data in the table below.
  
> [!TIP]
>  The full spreadsheet also includes the maximum number of simultaneous sessions for each application, but we deleted those columns to save space.
  
 **Personas by site - ('Sites' Worksheet- Columns A, D, I and AI through AX)**
  
|**Site Name**|**Total Users in Site**|**Total Sites Like This**|**User Profile 1**|**User's of Profile 1**|**User Profile 2**|**User's of Profile 2**|**User Profile 3**|**User's of Profile 3**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|Headquarters  <br/> |1070  <br/> |1  <br/> |Executive/Partner  <br/> |170  <br/> |Associate/Paralegal  <br/> |700  <br/> |IT admins  <br/> |200  <br/> |
|Regional offices  <br/> |345  <br/> |3  <br/> |Executive/Partner  <br/> |60  <br/> |Associate/Paralegal  <br/> |225  <br/> |IT admin  <br/> |60  <br/> |
|Large branch offices  <br/> |70  <br/> |24  <br/> |Executive/Partner  <br/> |11  <br/> |Associate/Paralegal  <br/> |50  <br/> |IT admin  <br/> |9  <br/> |
|Small branch offices  <br/> |36  <br/> |50  <br/> |Executive/Partner  <br/> |6  <br/> |Associate/Paralegal  <br/> |25  <br/> |IT admin  <br/> |1  <br/> |
   
 **Bandwidth required per application by site in Kbps ('Sites Worksheet'- Columns A and BQ through LF)**
  
|**Site**|**Peak SIP / IM bandwidth**|**Peak Intersite Peer Audio bandwidth**|**Peak Intersite Peer Video bandwidth**|**Peak Audio Conferencing bandwidth**|**Peak Video Conferencing bandwidth**|**Peak WAN Share bandwidth**|**Peak WAN bandwidth for PSTN Calls**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|Headquarters  <br/> |1070  <br/> |525.30  <br/> |560.00  <br/> |739.50  <br/> |2640.00  <br/> |4224.00  <br/> |2688.30  <br/> |
|Regional Offices  <br/> |345  <br/> |185.40  <br/> |560.00  <br/> |255.00  <br/> |1320.00  <br/> |1536.00  <br/> |896.10  <br/> |
|Large Branches  <br/> |70  <br/> |92.70  <br/> |560.00  <br/> |102.00  <br/> |600.00  <br/> |384.00  <br/> |216.30  <br/> |
|Small Branches  <br/> |36  <br/> |119.40  <br/> |560.00  <br/> |76.50  <br/> |600.00  <br/> |384.00  <br/> |123.60  <br/> |
   
Probably the most important columns in the spreadsheet are those that describe the WAN bandwidth by QoS class. This is shown in the table below. This data summarizes the information you will need to provide to the network service provider to order the access connection at each of your sites. When calculating total bandwidth, please remember to multiply the bandwidth for each type of branch sites by the number of sites of the same type. To connect with your ExpressRoute network services partner, you can see [Azure ExpressRoute]( https://go.microsoft.com/fwlink/?LinkId=690283).
  
It is very important that you don't exceed the bandwidth in the voice or 'Expedited Forwarding' (EF) class of service. A random set of packets will be discarded so rather than reducing the quality of a single call or group of calls, all of the calls in progress can be impacted. It is also important that only voice be marked with the DSCP for EF (i.e. DSCP = 46) or the voice queue could overflow when of non-voice traffic is added.
  
> [!TIP]
>  Again, while the EF class of service offers the best performance guarantee, if you exceed the defined bandwidth, any additional packets will immediately be discarded.
  
 **Aggregate bandwidth per site by QoS traffic class - ('Sites' Worksheet- Columns A and ML through MR)**
  
|**Site Name**|**Best effort class (DSCP 0)**|**Data traffic class (DSCP custom)**|**Real-time traffic class (DSCP 34, AF41)**|**Priority traffic class (DSCP 46, EF)**|
|:-----|:-----|:-----|:-----|:-----|
|Headquarters  <br/> |0.00  <br/> |5764.80  <br/> |3200.00  <br/> |3953.10  <br/> |
|Regional Offices  <br/> |0.00  <br/> |2033.60  <br/> |1880.00  <br/> |1336.50  <br/> |
|Large Branches  <br/> |0.00  <br/> |486.40  <br/> |1160.00  <br/> |411.00  <br/> |
|Small Branches  <br/> |0.00  <br/> |438.40  <br/> |1160.00  <br/> |319.50  <br/> |
   
### Putting your plan into action

We can calculate the total bandwidth that will traverse the WAN and the amount of bandwidth that will traverse ExpressRoute, using the bandwidth estimates from the **Per application Per site** table above. The portion of traffic that traverses ExpressRoute excludes the inter-site peer bandwidth.

 
|**Site**|**Peak SIP / IM bandwidth**|**Peak Audio Conferencing bandwidth**|**Peak Video Conferencing bandwidth**|**Peak WAN Share bandwidth**|**Peak WAN bandwidth for PSTN Calls**|**Total ExpressRoute<br/>traffic per site class<br/>(i.e., total<br/>time # of sites)**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|**Headquarters** <br/> |1,070  <br/> |739.50  <br/> |2640.00  <br/> |4224.00  <br/> |2688.30  <br/> |11361.80  <br/> |
|**Regional Offices** <br/> |345  <br/> |255.00  <br/> |1320.00  <br/> |1536.00  <br/> |896.10  <br/> |8704.20  <br/> |
|**Large Branches** <br/> |70  <br/> |102.00  <br/> |600.00  <br/> |384.00  <br/> |216.30  <br/> |32935.20  <br/> |
|**Small Branches** <br/> |36  <br/> |76.50  <br/> |600.00  <br/> |384.00  <br/> |123.60  <br/> |61005.00  <br/> |
   
This means that Skype for Business Online traffic which will traverse the express route will be approximately 114 Mbps, so Dewey will need at least the 200 Mbps subscription for ExpressRoute. Multiple ExpressRoute circuits may be purchased at different ExpressRoute peering locations. This could be recommended if Dewey's sites are in different geographical regions, or to provide resiliency in the event that connection to the ExpressRoute circuit fails. If you purchase ExpressRoute circuits in multiple Azure regions, the ExpressRoute premium add-on will be required to receive global connectivity over ExpressRoute.
  
Now that you have the total amount of required bandwidth, and class of service (CoS) bandwidth numbers you can place your orders with the selected network service provider(s). Don't forget to include estimates for traffic for other applications and services. We offer network planning guidance for other Office 365 services, including bandwidth calculators for Exchange and OneDrive. Bandwidth subscription for network service provider will be higher because intra-site traffic will need to be added back in. The Lync 2010 and 2013 Bandwidth Calculator provides only an estimate of the expected traffic, therefore it is recommended to confirm the network's ability to support that volume of traffic conducting a stress test. 
  
> [!TIP]
> Stress testing your network is a highly recommended when you are performing a network pre-assessment. 
  
A stress test involves building and configuring the infrastructure and then running it with the expected volume of simulated traffic while monitoring the performance. Your traffic estimates might be inaccurate in some areas, but at least you can be sure it can support the volume of traffic the Lync 2010 and 2013 Bandwidth Calculator predicted. It is recommended that you run the stress test for a minimum of a few days, but running it for longer periods of time can help you refine the numbers. However, extending the stress test period must be weighed against the cost of the network services you are paying for that aren't carrying real user network traffic. Microsoft has certified a number of vendors as part of its IT Pro Tools program to provide network management and operations tools including network pre-assessment stress tools. Skype for Business also provides a System Integrators (SI) that can take the certified IT Pro Tools and that can do the network assessment for you. You can see more at [Skype for Business Solutions: IT Pro Tools](https://go.microsoft.com/fwlink/?LinkID=690307).
  
Stress testing provides some reassurance that the network can support the traffic volume that will be needed, but in reality the Lync 2010 and 2013 Bandwidth Calculator data can be off for any number of reasons. You should also consider continuing to monitor your sites networks by doing an ongoing network assessment once it is deployed to ensure the bandwidth is sufficient and that the QoS mechanisms are operating properly. It is important to continue monitoring the network performance as more and more real users are brought on line.
  
## Part 2: ExpressRoute Skype for Business QoS

Microsoft's ExpressRoute service provides a dedicated connection to the Azure cloud, but Office 365 Real Time Workloads' communication services will require network services with sufficient bandwidth to carry the volume of traffic and are capable of supporting Quality of Service (QoS) to deliver a business grade user experience. A QoS capable connection must be configured end-to-end (PC, network switches and routers to the cloud) as any part in the path that fails to support QoS could degrade the quality of the entire call.
  
The purpose of this section is to help you understand the challenges when supporting real-time traffic in an IP network and configuring and supporting a successful ExpressRoute deployment of Office 365 Real Time Workloads using a Microsoft's ExpressRoute Exchange Provider or Network Service Provider partner.
  
QoS is accepted from your networks exclusively over ExpressRoute network circuits and is used within the Microsoft network for Skype for Business traffic. Today, portions of some outbound connections from Microsoft have missing DSCP values for Skype for Business. Until outbound traffic is fully marked with DSCP values, you are encouraged to follow the guidelines for adding QoS markings to traffic at your network boundary as described in the **Implementing QoS using Network Access Control List (ACL)** section of this article.
  
### The Real Time problem

Delivering business quality voice and video services places special demands on an IP network. Real-time traffic uses the Real-time Transport Protocol (RTP) that is carried using User Datagram Protocol (UDP). Unlike Transmission Control Protocol (TCP) that numbers and tests each message for errors and includes other mechanisms to detect and retransmit lost or errored messages, UDP doesn't provide for this type reliability. If messages are corrupted by errors or are lost due to buffer overflows, they are lost. UDP was chosen for use with RTP because the nature of real-time traffic is that even if the lost messages were resent, they would arrive far too late to have any positive impact to the flow of voice message.
  
Knowing the impact of lost voice packets, designers came up with two approaches to improve the performance of voice and video over IP:
  
- Make the voice coding/decoding more resilient when packets are lost. This can be done by either using forward error correction (FEC) to correct a percentage of the encountered errors which is a capability found in Office 365 Real Time Transport, or by designing voice decoding systems that attempt to mask the effect of lost packets which is a characteristic of Microsoft codecs. 
    
- Use transport services that use quality of service mechanisms to guarantee the network's performance with respect to delay, packet loss and jitter and the variation in delay between packets.
    
Resilient voice coding only addresses the problem of packet loss, so it's important that a network used to carry real-time voice and video have mechanisms that minimize delay and jitter. Even with resilient coding, if too many packets are lost, the receiving station won't have enough information to reconstruct a recognizable version of the voice signal. The percentage of lost packets that would result in a noticeable degradation in voice quality which varies depending on the voice encoding technique that is used. In all cases however, losing strings of successive packets is very problematic.
  
Minimizing delay is important because excessive delay can impact the flow of the conversation and create an annoyance for speakers. Best practices tell us that end-to-end delay for voice (what we refer to as 'mouth-to-ear' delay) must be kept below 150 milliseconds (msecs). one-way, not 'round trip' delay. Of course the delay will increase on longer transmission links like those that go across oceans, given the propagation delay or the time it takes for the signal to physically travel over the cable.
  
When the delay goes higher than 150 msecs. one-way, it has a strange effect on the speaker. Psychologically, a clock goes off in the speaker's brain that makes them think that the recipient hasn't heard them and they repeat the last thing they said. This collides with the delayed response coming from the far end. If you have ever spoken over a satellite channel you will recognize this effect. Over a satellite channel the one-way delay is roughly 250 msecs., which is far beyond the allowable delay.
  
 **Recommended network parameters for business grade voice**
  
|**Parameter**|**Recommended value**|
|:-----|:-----|
|Inter arrival packet jitter (average)  <br/> |≤ 5ms  <br/> |
|Inter arrival packet jitter (maximum)  <br/> |≤ 40ms  <br/> |
|Packet loss rate (average)  <br/> |0% approaching  <br/> |
|Network latency one way  <br/> |≤ 100ms (should include checks on delay versus geographic distance)  <br/> |
   
### ExpressRoute as part of a business grade voice network

ExpressRoute offers a dedicated connection via a Network Service Provider (NSP) or an Exchange Provider (EXP) in one of 3 connection options: 
  
- Cloud Exchange Colocation
    
- Point-to-Point Ethernet connection
    
- Any-to-Any (IPVPN) connection
    
This provides benefits of high availability (99.9% uptime SLA), and dependable routing that is secure (no internet transit), unaffected by variations in Internet traffic, and respects Quality of Service markings for prioritizing traffic (QoS is explained below). ExpressRoute, along with a well-planned WAN can provide you with a business grade voice network.
  
You may use ExpressRoute for data transit from offices or datacenters (if hybrid topology) that are connected to the circuit. Data for offsite users (For example, from home offices, or traveling, etc.) won't leverage the ExpressRoute circuit unless users are VPN connected and need not be included in bandwidth estimations for sizing the ExpressRoute circuit. If you are a multi-national customer, you may purchase ExpressRoute circuits in each region and use BGP community tags to inform routing rules so that traffic is directed to the preferred ExpressRoute circuit (typically the nearest one for each site), while the other circuits offer redundancy in the event of an outage affecting a single circuit. 
  
### If ExpressRoute isn't an option

It may not be feasible to connect all sites to ExpressRoute, either due to costs, inability to meet ExpressRoute prerequisites, or limitations of your current NSP. If you who can't use ExpressRoute you are still recommended to follow the guidance below for marking QoS within your network, and to plan the contracts with your NSP to ensure sufficient bandwidth and support for traffic prioritization based on QoS.
  
Additionally, if you have offices in multiple regions, but don't have ExpressRoute circuits in all regions should use the region BGP community tags when configuring routing for traffic to/from satellite offices so that unnecessary long haul transit can be avoided. For example, consider a company that has a Skype for Business Online organization hosted in United states, but with branch offices in Europe, and the company only has a single ExpressRoute circuit in Silicon Valley. Most of the Skype for Business Online traffic will be routed to a datacenter where the organization is hosted (For example, conference calls with other users within the company), using the ExpressRoute circuit may be preferred for most traffic. However, if a user in Europe were to join a conference call hosted by another company whose organization is located in Europe, the destination for media in that call would be the European datacenter where second company is located. Routing the traffic through the ExpressRoute circuit in Silicon Valley would be a less direct route than would be possible via the Internet. In such a case, you may want to configure routers within your network (For example, at the European offices) to inspect the community tags when making routing rules, and routing via Internet rather than Silicon Valley ExpressRoute circuit for traffic that has European region tags.
  
### Basic concepts of Quality of Service (QoS)/Class of Service (CoS)

In IP, Quality of Service (QoS) describes any mechanism that is used to provide priority handling for some packets over others. According to the International Telecommunications Union (ITU) definition, QoS comprises all quality aspects of a connection including delay, loss, signal-to-noise ratio, crosstalk, echo, interrupts, frequency response, loudness levels, and so on. What we refer to as QoS in packet networks is more correctly termed Class of Service (CoS) that focuses on improving performance for delay, jitter and packet loss, but we will continue to use the QoS term as it is more commonly used.
  
Providing QoS in an IP network calls for two primary components:
  
- The reservation of a defined amount of bandwidth on each link for real-time traffic; if that bandwidth isn't needed for real-time traffic at any time, it can be used for other traffic. The general guidance is that no more than 30% of the capacity of any link should be assigned for voice traffic.
    
- Marking the packets with a priority indicator in the header that tells the switches and routers in the path the priority of the packet that should be assigned.
    
When a packet is received at a switch or router, it is moved to an output queue for the next leg or hop. There are different output queues for the different priority levels. A switch or router uses an algorithm that services the high priority queue more frequently than the lower priority queues.
  
The challenge is that there are different QoS techniques that are implemented at Layer 2 (i.e. the Ethernet or Wi-Fi layer) and Layer 3 (i.e. the IP layer). Those different QoS implementations may have to be configured in each switch and router in the network, as well as the interface between your network and the network service provider's network.
  
There are two options for how data from the various Skype for Business applications can be mapped to the appropriate classes of service:
  
- End point marking of the traffic using Differentiated Services Control Point (DSCP) 
    
- Network Access Control List (ACL)-based
    
### End Point Traffic Marking- Differentiated Services Control Point (DSCP)

Differentiated Services (DiffServ) is referred to as a "coarse grained" mechanism for classifying and managing network traffic and providing QoS in IP networks. Routers and other devices that implement Layer 3 functions use the DiffServ Control Point (DSCP) to define the packet's priority. QoS is implemented by inserting a 6-bit DSCP value in the Differentiated Services field (formerly the "Type of Service" field) in the IP header; 6-bits allows for 64 different priority levels. The priority levels are typically defined as shown here.
  
 **Recommended DSCP settings**
  
|**Traffic Class**|**Treatment (DSCP Marking)**|**Skype for Business workloads**|
|:-----|:-----|:-----|
|**Voice** <br/> |EF (46)  <br/> |Skype for Business and Lync voice  <br/> |
|**Interactive** <br/> |AF41 (34)  <br/> |Video  <br/> |
||AF21 (18)  <br/> |Application sharing  <br/> |
|**Default** <br/> |AF11 (10)  <br/> |File transfer  <br/> |
||CS0 (0)  <br/> |Anything else  <br/> |
   
 **IP Version 4 header**
  
![IPv4 header](../images/c8a6a714-2784-4328-8297-2e62706f302d.png)
  
### Layer 2 QoS: IEEE 802.1p/Wi-Fi Multi-Media (IEEE 802.11e)

While DSCP is the standard mechanism for implementing QoS at Layer 3, there are different Layer 2 QoS mechanisms for wired (i.e. Ethernet) and wireless (i.e. Wi-Fi networks). The QoS mechanism for wired networks is defined in IEEE 802.1p standard; the WLAN QoS mechanism is defined in IEEE 802.11e, what the Wi-Fi Alliance identifies as "Wi-Fi Multi-Media Certified" (WMM Certified).
  
The IEEE 802.1p uses a 3-bit Priority Code Point (PCP) to identify the message's priority; the PCP is part of a 32-bit field in the Ethernet Header that also carries the VLAN identifier. The definitions for the PCP values are included below.
  
 **IEEE 802.1p PCP values**
  
|**PCP Value**|**Priority**|**Acronym**|**Traffic types**|
|:-----|:-----|:-----|:-----|
|7  <br/> |7  <br/> |NC  <br/> |Network Control  <br/> |
|6  <br/> |6  <br/> |IC  <br/> |Internetwork Control  <br/> |
|5  <br/> |5  <br/> |VO  <br/> |Voice  <br/> |
|4  <br/> |4  <br/> |VI  <br/> |Video  <br/> |
|3  <br/> |3  <br/> |CA  <br/> |Critical Applications  <br/> |
|2  <br/> |2  <br/> |EE  <br/> |Excellent Effort  <br/> |
|0  <br/> |1  <br/> |BE  <br/> |Best Effort  <br/> |
|1  <br/> |0  <br/> |BK  <br/> |Background  <br/> |
   
Where IEEE 802.1p is implemented in much the same way as DSCP with traffic sorted into different priority queues for each priority level, but the shared media nature of WLANs calls for a different approach. While the access point and the client will maintain separate output queues for the different priority levels, there are also differences in how the frames are sent out on the radio channel.
  
In a Wi-Fi network, all clients associated with an access point share a single, half-duplex channel (i.e. only one client station or the access point can send at a time). To minimize the potential of collisions on the radio channel, before sending a frame the station waits for the channel to be idle for a defined period of time called an "Inter-Frame Spacing", if the channel is busy when a station goes to send, it backs off a random time period. Once the frame is sent, if the sender does not receive an acknowledgment message from the recipient, it assumes a collision or other failure has occurred and it steps back a random interval before attempting to access the radio channel to resend. The back-off interval is random to reduce the probability the same two stations will collide again.
  
To prioritize access to the radio channel, IEEE 802.11e/WMM defines different pre-transmission waiting intervals called "Arbitrated Inter-Frame Spacings" (AFIS) and different back-off ranges for the different traffic classes; four priority levels called 'Access Categories' are defined.
  
Priority is given by assigning shorter AFIS values to the higher priority frames. So if one station is waiting to send a voice frame and another is waiting to send a data frame, the voice frame will always be sent first. Technically, voice and video frames are assigned the same AFIS value, but the range of back-off intervals for video frames is higher. So while a voice and video frame may collide on the first attempt, the voice frame will always be retransmitted sooner. The correlation between IEEE 802.1p and IEEE 802.11e is shown below:
  
 **IEEE 802.11e/Wi-Fi Multi-Media (WMM) to 802.1P mapping**
  
|**WMM access category**|**WMM description**|**802.1P PCP value**|**802.1P designation**|
|:-----|:-----|:-----|:-----|
|1 (AC_VO)  <br/> |Voice  <br/> |7 (111)  <br/> |NC  <br/> |
|6 (110)  <br/> |VO  <br/> |
|2 (AC_VI)  <br/> |Video  <br/> |5 (101)  <br/> |VI  <br/> |
|4 (100)  <br/> |CL  <br/> |
|3 (AC_BE)  <br/> |Best Effort Data  <br/> |3 (011)  <br/> |EE  <br/> |
|0 (000)  <br/> |BE  <br/> |
|4 (AC_BK)  <br/> |Background Data  <br/> |1 (001)  <br/> |BK  <br/> |
|2 (010)  <br/> |---  <br/> |
   
The recommended association of Layer 3 to Layer 2 priorities is shown here:
  
 **Recommended Layer 3 to Layer 2 priority associations**
  
||**Layer 3 markings**|**Layer 2 (PCP Value)**|**Wi-Fi (Access Category)**|
|:-----|:-----|:-----|:-----|
|Network Control  <br/> |Per Hop Behavior (PHB) - Class Selector (CS) 6  <br/> |6  <br/> |1 (AC_VO)  <br/> |
|DSCP Value -48  <br/> |
|Voice  <br/> |Per Hop Behavior (PHB) -Expedited Forwarding (EF)  <br/> |5  <br/> |1 (AC_VO)  <br/> |
|DSCP Value - 46  <br/> |
|Video Conferencing  <br/> |Per Hop Behavior (PHB) - Assured Forwarding (AF) 41  <br/> |4  <br/> |2 (AC_VI)  <br/> |
|DSCP Value - 34  <br/> |
|Call Signaling  <br/> |Per Hop Behavior (PHB) - Class Selector (CS) 3  <br/> |3  <br/> |2 (AC_VI)  <br/> |
|DSCP Value - 24  <br/> |
|Low Latency Data  <br/> |Per Hop Behavior (PHB) -Assured Forwarding (AF) 21  <br/> |2  <br/> |3 (AC_BE)  <br/> |
|DSCP Value -18  <br/> |
|High Throughput Data  <br/> |Per Hop Behavior (PHB) - Assured Forwarding (AF) 11  <br/> |1  <br/> |3 (AC_BE)  <br/> |
|DSCP Value - 10  <br/> |
|Best Effort  <br/> |Per Hop Behavior (PHB) - 0  <br/> |0  <br/> |4 (AC_BK)  <br/> |
|DSCP Value - 0  <br/> |
   
It is important to note that there is a mismatch in the priority coding for IEEE 802.1p and WMM. The 802.1p the PCP value for voice is 5, however, in the standard equivalence mapping to WMM, PCP 5 is translated to Access Category 2, the WMM access category for video (AC_VI). If possible you should override that mapping so that PCP 5 translates to Access Category 1, or simply avoid using voice and video on the same Wi-Fi network until the Wi-Fi Alliance addresses this issue. For additional information on Wi-Fi, see [Wi-Fi Catalog Items]( https://go.microsoft.com/fwlink/?LinkId=690322).
  
### Implementing QoS using Network Access Control List (ACL)

The alternative method of implementing QoS in an ExpressRoute configuration is to use Network Access Control List (ACL). In that approach, rather than having the end points insert the appropriate DSCP marking in the header of each packet, the marking can be done by an upstream router, based on the UDP source port. All of the switches and routers must still be configured to support QoS to ensure the DSCP settings are maintained. More importantly, the router connected to the service provider's network must maintain the DSCP in the header of each packet, as that DSCP setting is essentially your instruction to the network service provider for how that packet should be treated.
  
The recommended port ranges for each Skype for Business application are listed in Section 2.6.1.1 of the [Network Planning, Monitoring, and Troubleshooting with Lync Server](https://go.microsoft.com/fwlink/?LinkId=690286) guide. It is important that this be coordinated with the organization's overall approach to QoS and you should be on the lookout for different QoS policies and potential packet remarking mismatches.
  
While the main reason QoS and MPLS network services are used is to ensure a good user experience for real-time voice and video, those same capabilities can also be applied to data applications. Rather than treating all applications equally, MPLS networks can allow organizations to give priority to some data applications over others. With MPLS, real-time applications like credit card transactions or screen sharing can be given priority over less time sensitive traffic like email.
  
### Understanding the types of IP Network Services- Basic IP and MPLS

The original IP packet forwarding operated on the principle of "best effort." That meant that the routers forwarding those IP packets would do their best to deliver them to their destinations, but there was absolutely no guarantee with regard to when or if they would arrive at their destinations. That is how basic Internet services, including your home Internet connection, work today. The idea was that if reliability was required for a particular application, it would be provided at a higher level in the protocol stack. The reliable delivery mechanism is the Transmission Control Protocol (TCP). The User Datagram Protocol (UDP), which is used for real-time voice and video, is the unreliable (i.e. "best effort") delivery mechanism. 
  
Multi-Protocol Label Switching (MPLS) was developed as a means for network service providers to offer an IP service with performance guarantees for delay, jitter and packet loss. To deliver on those performance guarantees, MPLS takes some of the unpredictability out of traditional IP. First, rather than having each packet find its way router-to-router to its destination (the result of which could be that each packet takes a different route from the source to the destination), MPLS routes all of the packets on a "virtual circuit" connection with a fixed route called a Label Switched Path (LSP). If one of the links in that path fails, all of the LSPs using that link are quickly rerouted.
  
When a packet is sent into the MPLS network the network service provider's edge router appends an additional header to the packet that includes a label that is used to forward it over the appropriate LSP. The label is stripped off by the edge router at the other end of the MPLS network.
  
Beside simplifying the forwarding process, the other advantage MPLS provides is that the network management system will know what connections are being carried on every link in the network. By controlling the way traffic is routed through the network, the operator can guarantee the QoS each path will provide. So unlike the best effort performance of traditional or basic IP, MPLS operators can provide an IP service with predictable performance. That LSP also makes MPLS inherently more secure than traditional Internet services. So with basic IP service we can hope that the network will perform well enough to provide good quality voice and use techniques like FEC and more resilient voice coding to improve the odds, but by using MPLS, we can be sure of it.
  
MPLS providers offer several class of service gradients that unfortunately uses different terms to identify them. You will have to work closely with your provider to ensure they understand the outputs from the [Lync 2010 and 2013 Bandwidth Calculator](https://go.microsoft.com/fwlink/?LinkID=690282) and the recommended options for different Office 365 Real Time Workloads applications.
  
## Conclusion

Skype for Business enhances the way business communications are conducted. Rather than having a telephone connected to a PBX, a stand-alone video conferencing system, a separate platform for email, an outside service for audio conferencing and some vehicle for IM and presence, Skype for Business can bring all of these capabilities together in a single user interface.
  
Consistently delivering business grade real-time voice and video services requires an end-to-end network infrastructure that is capable of providing QoS. That would include both LAN and the WAN services. Microsoft provides tools like the [Lync 2010 and 2013 Bandwidth Calculator](https://go.microsoft.com/fwlink/?LinkID=690282) to estimate the network capacity you will require for the various services. Also, there are partners in the IT Pro Tools program [Skype for Business Solutions: IT Pro Tools](https://go.microsoft.com/fwlink/?LinkID=690307) that offer tools to pre-assess the network infrastructure and support monitoring, reporting and troubleshooting. Without a correctly sized and configured network infrastructure, you run the risk of having an ExpressRoute Skype of Business deployment that will not meet your user's expectations for quality and consistency.
  
Effective business tools must perform reliably, consistently, and deliver a user experience that encourages user adoption. From a networking standpoint that means having a network infrastructure, both local and wide area, fixed and mobile, that can allow that to happen. Planning, designing, implementing and maintaining that infrastructure isn't always an easy feat. The hardware, tools and network services to accomplish that are available today, but it is the responsibility of IT Pro to see that they are designed, implemented and maintained in a way that ensures the users get a set of communications and collaboration services that allow them to work efficiently and effectively and that the organization can reap the full benefit of what this technology has to offer. 
  
## Related topics

[ExpressRoute documentation](https://go.microsoft.com/fwlink/?LinkId=690285)

  
 