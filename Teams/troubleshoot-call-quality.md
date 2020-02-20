---
title: Troubleshoot call quality for Microsoft Teams
author: lolajacobsen
ms.author: lolaj
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: vkorlep, siunies, gageames
audience: admin
description: In-depth guide to troubleshooting call and meeting quality problems in Microsoft Teams.
localization_priority: Normal
search.appverid: MET150
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

#  Troubleshoot call quality for Microsoft Teams

[]: # "Lola comment: This is excerpted from sections 4.1 and 4.2 of the Lync_Server_Networking_Guide_v2.3.docx, https://www.microsoft.com/en-us/download/details.aspx?id=39084"


# 4\. Troubleshooting

This section is divided into two core parts: troubleshooting scenarios that offer guidance about how to troubleshoot each end-to-end user scenario, most of it derived from real-life experiences, and troubleshooting methodologies that offer in-depth investigation into some of the most technically challenging network issues.

We assume that you have followed the best practices advisories in the previous topics.

## 4.1 Troubleshooting Scenarios

The following troubleshooting scenarios are described in detail: a site-wide issue of Lync voice quality (a site suddenly reports poor audio quality), and an individual Lync voice quality issue.

### 4.1.1 Troubleshooting a Site-Wide Issue: Lync Voice Quality - A Site Suddenly Reports Poor Audio Quality

Troubleshoot a site that suddenly reports poor audio quality by using the following procedure:

  - Define the problem report scenario.

  - Provide an initial assessment.

  - Collect data.

  - Isolate the problem and analyze the root cause.

#### 4.1.1.1 Problem Report Scenario

This scenario specifically targets the case where a site or a group of users is experiencing audio quality issues.

#### 4.1.1.2 Initial Assessment

The first step is to assess the issue from the initial report. If all you have in terms of a description of the issue is “audio is poor at a site,” you can still use the process of elimination to try to isolate the issue. [Lync Audio Quality Model](#appendix-a.-lync-audio-quality-model) describes the different types of audio quality issues and their causes, such as environmental, device, codec, and network-related causes. Assuming that the audio quality problem is localized to a site, you can probably eliminate all potential causes, except network issues. There’s always the slight possibility of a non-network issue—for example a software update—but the likelihood is low. The most efficient approach is to start your investigation with the highest probable potential cause.

[Lync Audio Quality Model](#appendix-a.-lync-audio-quality-model) describes how network issues include not only actual network issues, but also client endpoint and server performance issues.

#### 4.1.1.3 Data Collection

The next step is to collect the data needed to confirm network issues as the likely cause. Specifically, check to see if user reports about specific issues are available from the help desk.

[Lync Audio Quality Model](#appendix-a.-lync-audio-quality-model) describes how audio quality issues can be classified into rigorous categories, which helps the troubleshooting process. Assuming that the help desk team follows the taxonomy described in [Lync Audio Quality Model](#appendix-a.-lync-audio-quality-model), you can review the user reports to determine if there are network issues. Look for reports of distortions, fast or slow speech, or audio cutouts.

If users report noise, echo, low quality audio, or other issues, consult these articles for troubleshooting guidance: "Lync Troubleshooting: Your audio device may cause an echo" at <http://go.microsoft.com/fwlink/p/?LinkId=301452> and "Lync Troubleshooting: Your Microphone Is Capturing Too Much Noise" at <http://go.microsoft.com/fwlink/p/?LinkId=301456>.

DON’T LINK OUT TO THE ABOVE PLACES – INSTEAD, ADD THIS TO THE ARTICLE:

## Symptoms

When you are on a Lync call or in a Lync conference, a message appears stating that your microphone is capturing too much noise.

## Resolution

  - Your computer’s fan or spinning hard drive is too close to the microphone.

  - You may be sitting near a fan or air conditioning unit that is producing static noise.

  - If are using a noise-canceling microphone, make sure it is positioned close to the mouth, approximately 2 centimeters or less than 1 inch away from the mouth. This filters out unwanted background noise, so it is important that you position it correctly to avoid audio issues.

  - When you are using the speaker on your phone make sure that the phone is placed on a flat surface. Also, make sure that there is no obstruction between the phone and your mouth.

  - If there is physical damage to the device, try using a different device.

  - Make sure that the device you are using is optimized for Lync 2010. For a list of optimized devices, see [Phones and Devices Qualified for Microsoft Lync ![Jump](c:\\Users\\lolaj\\OfficeDocs-SkypeForBusiness-pr\\Teams/media/image1.png) ](http://technet.microsoft.com/en-us/lync/gg278164.aspx).

If users complain about call setup failures or call drops, there’s still a chance that network issues are present. However, you should expect distortion issues, as well.

Next, review specific scenarios from user reports. For example, did the poor quality occur in peer-to-peer (P2P) calls, conference calls, PC-to-phone (PC2Phone) calls, or in all of these call types? This investigative inquiry can help you determine if there are specific entities that need investigation.

Lastly, be sure to check the when the issue occurred—just recently, or over a period time. This will clue you in to whether you’re looking for a sudden change in the system or a gradual degradation.

Studying the user reports will help you determine if you’re on the right track in chasing down your initial assessment. Assuming that you followed the guidelines in the "Lync 2013 Technical Documentation" at <http://go.microsoft.com/fwlink/p/?LinkID=254806>, including the Deployment Guide and Operations Guide, you’ll be able to gather additional empirical data, as well.

If the audio quality issue is localized to a site, review the Wired and Wireless Subnets Report in [Subnet Reports](#Subnet_Reports), which can be very useful. If [trending reports](#Trending_Data_Retention) are available, you may see an increase in the number of poor calls for the site. The issue may be in the wired or wireless networks, so check both sets of reports.

If a Mediation Server is deployed to the site, check the call quality between the Mediation Server and the AVMCU. Because these are both managed server endpoints, there should be little, if any, packet loss and jitter. If you find a sharp inflection in any of these reports, you may discover corroborative data matching the user reports.

If users complain about PC2Phone quality, you’ll need to check the [MS-GW Reports](#Mediation_Server_IP_PSTN_Gateway_Report) for any sudden changes in packet loss and jitter.

If the trend reports don’t show anything out of the ordinary, you’ll need to find the right signature for the issue. For example, if the report site does not match the user report site, you’ll need additional filtering. Acquiring individual user aliases is important, so that you can compare the users’ QoE metrics to those of the rest of the population. In one case study, a buggy network adapter driver in a certain model of laptops caused network issues for laptop users. Because the same model of laptop was ordered for a group of users, the issue initially appeared to be a site-based issue.

#### 4.1.1.4 Problem Isolation and Root Cause Analysis

If [QoE Reports](#Lync_QoE_Reporting) are able to capture the inflection in the quality metrics from a before-the-issue to an after-issue-resolution period, the subnet IP can be passed to the networking team to investigate further. For details about how to fix common network issues that affect Lync audio quality, see [Troubleshooting a Network Segment](#troubleshooting-a-network-segment).

### 4.1.2 Troubleshooting an Individual Lync Voice Quality Issue

Troubleshoot an individual Lync voice quality issue by using the following procedure:

  - [Define the problem report scenario](#problem-report-scenario-1).

  - [Provide an initial assessment](#initial-assessment-1).

  - [Collect data](#data-collection-1).

  - [Reproduce the scenario and analyze the root cause](#problem-isolation-and-root-cause-analysis-1).

#### 4.1.2.1 Problem Report Scenario

In the typical help desk scenario, a user reports an audio quality issue that they recently experienced. If the user mentions that several individuals are experiencing similar issues at a certain location, see [Troubleshooting a Sitewide Issue: Lync Voice Quality - A Site Suddenly Reports Poor Audio Quality](#troubleshooting-a-site-wide-issue-lync-voice-quality---a-site-suddenly-reports-poor-audio-quality) for useful guidance.

#### 4.1.2.2 Initial Assessment

Because most users don’t know the cause of their audio quality issue, it’s generally up to the frontline support engineer at the help desk to ask clarifying questions to classify the type of issue. Often, carefully directed questioning is all that’s required to determine the type of issue. After you’ve determined the type of issue, you can apply the appropriate troubleshooting methodology. All Lync audio quality issues fall into the following categories:

  - **Distortion (metallic-sounding, fast speech, slow speech)**

> Certain types of distortions, such as those that are described "metallic-sounding," contain "twangs,"—speech that accelerates and/or slows down—that are caused by network impairment. If the network degrades beyond a certain threshold, the audio healer operates at extreme recovery modes and creates certain types of distortions in the process. If you determine that the user is experiencing these distortions, the next step is to collect information about the call scenario and the appropriate network metrics.

  - **Distortion (other)**

> These distortions can include "metallic-sounding audio," "low quality voice," "fuzzy sounding speech," or some similar variation. Generally, these distortions are caused by poor quality audio at by the source—that is, the audio quality is already poor before it is transmitted over VoIP. In these cases, the causes can be device-related (a low-quality and/or inappropriate device for the situation—unidirectional microphone used as a conferencing device, bad device drivers, or DSP software), environmental (noisy location), or PSTN (poor cell phone reception or IP-PSTN GW misconfiguration). By reproducing the scenario and patterns, and asking clarifying questions, you’ll get closer to the cause.

  - **Speech cut-out**

> Speech cut-outs can be caused by severe network impairment, devices, or environmental causes. To determine if network issues are the cause, ask if the distortions are of the metallic-sounding type or the fast speech and/or slow speech type. Also find out if a new device has recently been added. Lastly, inquire about environmental or user error issues—for example, noise, or poor placement of a microphone.

  - **Glitch (pops, clicks)**

> Glitches—brief, minor malfunctions, sometimes with noise effects—are almost always due to device issues. Device issues can also include host PC, issues because CPU processing delays can cause pops and clicks.

  - **Noise**

> Noise issues can be caused by device issues or environmental conditions. The Lync client contains noise suppression features, and can remove a significant amount of background noise. However, excessive noise can lead to distortion and some noise leaks. Certain types of artificial noise, such as clicks or unusual machine noise, are not filtered. PSTN endpoints do not have the Lync noise removal processes in place and can send noisy audio into a Lync conversation.

  - **Volume issues (low or varying)**

> Low volume audio or varying volume levels are caused by the sender side of the conversation. If the sender is using Lync, examine the device. USB audio devices designed for VoIP are typically precalibrated. Built-in sound devices or sound cards may require additional configuration changes to be suitable for VoIP. Loud bursts of audio sent by the sender or PSTN caller, followed by low-volume speech, can cause the receiving Lync client to lower the volume for a short duration.

  - **Echo**

> Echo issues are typically caused by bad devices and/or PC hardware or drivers, or can originate from external sources, such as PSTN endpoints. Echoes can also be caused by a user moving a speakerphone, or by multiple users with speakerphones joined into the same conference from the same room. Investigating the call scenario can help you determine the cause.

  - **No audio or one-way audio**

> Network issues can cause an audio blackout or one-way audio, if an intermediate network device, such as a proxy server or firewall, blocks packets. This may occur after the initial connection is set up. Device issues and device misconfiguration issues are also common causes. For example, the user may think they are using a particular device, but another device may be the actively configured one.

The following table summarizes the issue types and potential causes. Be aware that multiple causes can exist. Be sure to check all potential causes.

Lync Audio Issue Types and Potential Causes

| Issue Type                                               | Network | Device | Environmental | PSTN | User Error |
| -------------------------------------------------------- | ------- | ------ | ------------- | ---- | ---------- |
| Distortion (metallic-sounding, fast speech, slow speech) | Y       |        |               |      |            |
| Distortion (other)                                       |         | Y      | Y             | Y    |            |
| Speech cut-out                                           | Y       | Y      | Y             |      | Y          |
| Glitch (pops, clicks)                                    |         | Y      |               |      |            |
| Noise                                                    |         | Y      | Y             | Y    |            |
| Volume issues (low or varying)                           |         | Y      | Y             | Y    | Y          |
| Echo                                                     |         | Y      | Y             | Y    | Y          |
| No audio or one-way audio                                | Y       | Y      |               |      | Y          |

#### 4.1.2.3 Data Collection

For each potential cause, use its unique own set of logs, metrics, or line of questioning to collect data. The specific data items can include:

  - **Network**

<!-- end list -->

  - QoE metrics from the Call Details Report
    
      - > NMOS degradation, packet loss, jitter, and burst loss metrics for the direction of interest

  - VQReport XML binary large object (blob) from UCCAPI logs

  - Precall diagnostics tool metrics log

  - Scenario questions:
    
      - > Were you calling from a Wi-Fi network?
    
      - > Were you calling from outside the corporate network?
    
      - > Were you calling from a VPN?
    
      - > If it was a P2P call, what was the other person’s network connection?
    
    <!-- end list -->
    
      - **Device**

  - QoE metrics from the Call Details Report
    
      - > SendListenMOS for send-side device metrics
    
      - > Noise level and SNR metrics for send and receive side

  - VQReport XML blob from UCCAPI logs, if the device in question is from the local user

  - Obtain a recording of the audio that shows the type of distortion or noise experienced by the user

  - Scenario questions:
    
      - > Does it only reproduce with this device if you were the one causing the issue?
    
      - > Does it only reproduce with a specific caller if you were the one hearing the issue?
    
    <!-- end list -->
    
      - **Environmental**

  - QoE metrics from the Call Details Report
    
      - > Noise level and SNR metrics

  - Scenario questions:
    
      - > Was it noisy when you made the call?
    
      - > What device was used for the conference room?
    
      - > How far away were you from the microphone?
    
      - > Were there multiple calls using speakerphone devices from the same room joined in the same conference?

#### 4.1.2.4 Problem Isolation and Root Cause Analysis

Use the collected data to eliminate as many potential causes as possible. After a potential cause has been determined, the next step is to find the root cause. Potential causes are grouped into the categories of network, device, and environmental. Within each category, there can be multiple issues that qualify as root causes. See the following topics for troubleshooting steps for each category:

  - **Network**  
    [Troubleshooting a Network Segment](#troubleshooting-a-network-segment) or [Troubleshooting External Network Issues](#Tshooting_External_Network_Issues), depending on whether the issue is internal or external to the corporate firewall.

  - **Device  
    **[Troubleshooting Device Issues](#troubleshooting-device-issues)

  - **Environmental  
    **[Troubleshooting Environmental Issues](#troubleshooting-environmental-issues)

## 4.2 Troubleshooting Methodologies

Troubleshooting methodologies are common procedures used to find the root cause of symptoms discovered by any of the frequently used methods—help desk user reports, monitoring alerts, or other ad hoc sources. The following methodologies are scoped so that they apply to many escalation paths, yet contain enough details to help discover the root cause.

For example, the [Troubleshooting a Network Segment](#troubleshooting-a-network-segment) helps you troubleshoot network impairment issues in a specific segment of the network, rather in than the entire network. If this methodology attempted to cover all network issues, there would be too many starting points, making the subject unwieldy. If it only covered specific entities in the network, you’d need to know in advance which entities were relevant to your investigation.

### 4.2.1 Troubleshooting a Network Segment

Because all voice quality troubleshooting cases can be associated with the network path involved, the network path is the optimal level at which to begin troubleshooting. For example, if the case involves a user report of a single call, you can find the call path in QoE by examining the caller and callee endpoint information, such as the IP addresses and subnet IPs, to determine the network path. If the case originates from a [Subnet Report](#Subnet_Reports) alert, the subnet IP is known, and you can look at the call paths from the subnet to known good servers, as well as calls within the subnet itself.

At this point, you should already have QoE, PING protocol, and other network measurements that indicate either packet loss or jitter exist on the network segment of interest. If not, refer to [Subnet Reports](#Subnet_Reports) or [Troubleshooting a Sitewide Issue: Lync Voice Quality - A Site suddenly Reports Poor Audio Quality](#troubleshooting-a-site-wide-issue-lync-voice-quality---a-site-suddenly-reports-poor-audio-quality), depending on how you encountered the original issue escalation.

Begin your investigation from the network segment involving two Lync endpoints. This means that you may be looking at two client endpoints, two server endpoints, or one client endpoint and one server endpoint. The following table shows what types of issue categories can exist, depending on the mix of endpoints straddling the network segment.

Network Issue Category Mix

| Network Issue Categories     | Client-Client | Client-Server | Server-Server |
| ---------------------------- | ------------- | ------------- | ------------- |
| Network router configuration | Yes           | Yes           | Yes           |
| Network hardware Issues      | Yes           | Yes           | Yes           |
| Wi-Fi quality                | Yes           | Yes           |               |
| Other client network quality | Yes           | Yes           |               |
| Client endpoint performance  | Yes           | Yes           |               |
| Server endpoint performance  |               | Yes           | Yes           |

Network issues may not be exclusively network-related. Endpoint performance can also be a factor, because any process that delays a packet or causes a packet to drop will appear as a network issue in the QoE Reports.

One way to isolate the network issue categories is to use QoE to reduce the length of the network segment. For example, if you see poor-quality calls between a client Wi-Fi subnet and a server subnet, you should get a [QoE Report](#Lync_QoE_Reporting) for call quality from the client-wired subnet to the same server subnet. Additionally, get a QoE Report that shows call quality between servers in the same server subnet. The smaller the network segment into which you can isolate the issue, the fewer devices you’ll need to check.

The following sections describe some of the root causes that cause network issues for Lync Server.

#### 4.2.1.1 Network Router Configuration

Network router configuration issues can consist of:

  - *Use of Differentiated Services Code Point (*DSCP)

  - Rate limiting

  - Speed sensing mismatch (Full/Auto)

  - Nagle algorithm (TCP only)

  - Load balancer configuration

  - HTTP proxies

  - Bandwidth

  - WAN/ISP

##### 4.2.1.1.1 Quality of Service (QoS)

Lync Server supports Quality of Service (QoS) by marking traffic at each endpoint that terminates media, with the exception of the Media Relay Edge Servers. The Lync Server deployment must first be configured to enable DSCP marking, and the network devices and switches must also trust the marked packets sent by the Lync Server endpoints, and must propagate the packets with the markings intact. Each network device can have its own configuration setting to enable/disable DCSP. There can also be access control lists (ACLs) in place that affect the final effective setting. Incorrect DSCP settings are often the biggest source of packet loss or jitter that affects Lync Server media traffic.

The following tables show examples of QoS commands that can enable QoS for VLAN-based and port-based methods.

VLAN-based QoS

| Task                                   | Command                                                  |
| -------------------------------------- | -------------------------------------------------------- |
| Enable QoS                             | mls qos                                                  |
| Create access list to match packets    | ip access-list extended VOICE, permit IP any             |
| Create class map                       | class-map match-all VOICE, match access-group name VOICE |
| Create policy map                      | policy-map VOICE, class VOICE, trust dscp                |
| Enable VLAN-based QoS on the interface | interface range GX/1-48, mls qos vlan-based              |
| Apply Service Policy to all VLANs      | int vlan X, service-policy input VOICE                   |

Port-based QoS

| Task                                  | Command            |
| ------------------------------------- | ------------------ |
| Enable QoS                            | mls qos            |
| Apply port-based QoS to the interface | mls qos trust dscp |

With the VLAN-based method, there are multiple settings to enable QoS. Configuration drift issues are more likely to occur because of the larger scope of potential misconfigurations, as compared to the port-based method.

For instructions about how to detect if DCSP traffic is being received, see "Voice Rx: Validating QoS on Lync Endpoints" at <http://go.microsoft.com/fwlink/p/?LinkId=301460>*.*

The following tables show issues that can cause QoS settings to fail, and suggested solutions.

Potential QoS Settings Failures

| Issue                                                                                                                                                                                                                                                                                                                                                                                | Resolution                                         |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------- |
| A wireless router firmware bug caused DSCP bits on packets to be remarked from 46 to 38, effectively erasing the expedited flags.                                                                                                                                                                                                                                                    | Apply the firmware fix.                            |
| CMPLS carrier providing WAN backbone is remarking packets and erasing Expedited Forwarding (EF) flag.                                                                                                                                                                                                                                                                                | Inform carrier of issue and request policy change. |
| VLAN-based QoS policy prone to errors, due to the requirement of multiple disparate settings to align, which affects DSCP. For example, the network interface on the media server must have the correct VLAN ID set, and the next hop switch needs to associate the VLAN ID with the expedited DCSP policy. A change in either setting can cause DSCP to (silently) not get applied. | Switch to port-based QoS policy.                   |

##### 4.2.1.1.2 Rate Limiting

Rate limiting is the specification of an upper bound of the network pipe for a specific Class of Service traffic. It is often used to prevent prioritized traffic from blocking unprioritized traffic. For example, if voice is prioritized at Expedited Forwarding (EF), it’s possible that no other traffic will get through, if the amount of voice traffic is high. Network administrators may set rate limiting policies to cap the amount of EF traffic at a fixed amount—for example, 20 percent of the total bandwidth. If the EF traffic exceeds the 20 percent limit, you can instruct the router to discard the additional packets, or forward them at the normal priority. If voice packets are discarded, voice quality will be negatively affected.

In practice, blocking rarely occurs in deployments with no rate limiting at all. If you want rate limiting as a form of protection against blocking normal traffic, you should configure it so that any packets above the rate limit cap are forwarded at the normal priority level, rather than being dropped by the router.

##### 4.2.1.1.3 Speed Sensing Mismatch (Full/Auto)

Network adapter speed and duplex mismatch is another issue that can cause packet loss and jitter on a network segment. It can seem counterintuitive that the Auto setting on a network adapter driver or switch port does not work against another interface set to Full. Both interfaces must be set to the same setting in order for packets to flow reliably. In many cases, network performance degradation caused by mismatched settings go unnoticed until real-time media is carried over this link. So far, this issue is known to affect only 100 Mbps network links.

##### 4.2.1.1.4 Nagle Algorithm (TCP only)

Although Lync Server supports transmitting audio/video (A/V) over the TCP transport, having the Nagle algorithm enabled in network gear can introduce jitter. The Nagle algorithm is designed to optimize the network for throughput. It buffers TCP segments until a certain amount of data is accumulated, and sends the segments in a batch. Because TCP is a stream protocol, merging the TCP frames results in less overhead, because it has headers at each protocol layer. Real-time A/V works best if the packets are sent as soon as they arrive on the network. The Nagle algorithm can cause choppy A/V, or even dropouts.

If your organization wants to use the Nagle algorithm to boost TCP throughput of other services, you should configure it so that Lync Server A/V traffic is not affected. You can do this by separating the traffic paths of the Lync Server A/V traffic from the rest of your organization’s traffic.

##### 4.2.1.1.5 Load Balancer Configuration

Certain Lync Server components, such as the Media Relay Edge (MRE) servers, require hardware load balancers (HLBs) to distribute loads across multiple instances of the server. There are a number of ways that the HLBs can be misconfigured, including:

  - Load directed unevenly across the MRE servers.

  - Load directed unevenly on a particular interface that is not monitored (internal versus external).

  - Media Relay IP addresses (MRE) directly reachable by external clients.

  - MRE external IP addresses directly reachable by internal clients.

  - HLB configured to route traffic to an MRE that is not in service or is undergoing maintenance.

  - Load balancing algorithms – round robin versus least connections.

  - Connection stickiness and affinity.

##### 4.2.1.1.6 HTTP Proxies

HTTP proxies can affect Lync Server audio/visual (A/V) traffic carried over TCP/TLS. Lync Server uses “pseudo-tls” where the TLS encryption key is null. Some HTTP proxy servers—specifically, those of the deep-packet-inspecting or stateful variants—attempt to analyze TLS traffic patterns in order to purge tunneled traffic or traffic with weak encryption keys. Some variants even serve as arbiters to examine every step of the TLS handshaking protocol and block any anomalies. All of these security features can adversely affect Lync Server A/V traffic because, after all, Lync Server A/V is designed to tunnel through traditional HTTP proxy servers.

Occasionally, the deep-packet-inspecting proxy server can prevent the TLS connection from completing. At other times, the connection may be set up, and then dismantled by the proxy server—a few seconds, or even a few minutes, later.

One popular brand of an HTTP proxy server known to cause issues is Blue Coat Systems Inc. It is a freeware server and is therefore widely used by many organizations. If you determine the HTTP proxy server to be the cause of the issue, turn off all deep packet inspection features, or exempt Lync Media Servers from inspection by specifying the media servers’ AP addresses in the exemption list.

##### 4.2.1.1.7 Bandwidth

When IT administrators diagnose network issues that can affect audio/visual (A/V) traffic, bandwidth is often a primary consideration. Fortunately, confirming that sufficient bandwidth is available for Lync Server is a straightforward process. The total concurrent A/V bandwidth usage across the day can be calculated by using [QoE data](#Lync_QoE_Reporting). The Lync Bandwidth Calculator can present the projected bandwidth usage, based on user models. For details, see "Lync 2010 and 2013 Bandwidth Calculator" at <http://go.microsoft.com/fwlink/p/?LinkId=301391>. There are also various third-party solutions for monitoring traffic usage by workload across a particular link.

##### 4.2.1.1.8 WAN/ISP

If Lync Server A/V traffic is carried over a leased network segment, the physical medium will be under the control of a third party. Isolating network performance issues requires the cooperation of the network provider.

#### 4.2.1.2 Network Hardware Issues

Network hardware issues consist of:

  - Bad patch cable

  - Cable loop/***b**ridge **p**rotocol **d**ata **u**nit (*BPDU) guard feature

  - Router CPU spikes

##### 4.2.1.2.1 Bad Patch Cable

Physical defects in the network cabling infrastructure can cause network performance degradation. Simply pulling out the cable and replacing it can disrupt existing traffic.

##### 4.2.1.2.2 Cable Loop/BPDU Guard Protection

A physical cabling loop can cause routing loops. When a switch detects such loops, it can either shut down the port or issue a device-wide reset. Shutting down the port provides immediate feedback to the user, but can also cause network outage. If your organization decides against shutting down the port, the device then attempts a device-wide reset to try to resolve the issue. The reset is very fast, but it can cause packet drops on all traffic across the device. Because hardware resets can’t correct physical issues, the device will continue to rest one every few minutes, causing packet loss each time. Some network devices report this condition by flagging it through the BPDU guard feature.

##### 4.2.1.2.3 Router CPU Spikes

Network router devices can experience dynamic load factors, such as CPU spikes, that cause packet loss or jitter. Finding the root cause of this depends on the specific device.

#### 4.2.1.3 Wi-Fi Quality

Wi-Fi quality issues consist of:

  - Interference

  - AP density

  - Roaming

  - Wi-Fi network adapter and driver

For a complete explanation of the issues and guidelines for deploying Wi-Fi in an organization, see "Delivering Lync 2013 Real-Time Communications over Wi-Fi" at <http://go.microsoft.com/fwlink/p/?LinkId=299371>.

##### 4.2.1.3.1 Interference

Radio interference is probably the biggest source of network performance degradation in Wi-Fi networks. Interference can come from a variety of sources, including:

  - Static structures, such as walls, pillars, and furniture

  - Human movement

  - Other radio frequency sources

  - Poor antenna placement/design

##### 4.2.1.3.2 Access Point Density

Radio wave signal strength is inversely proportional to the distance between the transmitter and the receiver. To overcome any interference, the Wi-Fi access point should be as close to the Lync Server endpoint as possible. Increasing access point density helps to shorten the distance between the Lync Server endpoint and the nearest access point.

##### 4.2.1.3.3 Roaming

Mobile Lync clients can also experience network performance degradation when a user moves around and the Wi-Fi connection is handed off from one AP to another. At this point, all traffic can be dropped.

##### 4.2.1.3.4 Wi-Fi Network Adapter and Driver

Buggy network adapters and drivers can degrade network performance. Some network adapters and drivers also perform scanning periodically to update the Wi-Fi access point list. This scanning can interrupt other ongoing traffic, such as a Lync Server call.

#### 4.2.1.4 Other Client Network Quality Issues

Other client network quality issues include:

  - Mobile Broadband

  - IPSec

  - VPN

  - Forced TCP connection

  - ISP/Internet

##### 4.2.1.4.1 Mobile Broadband

Many of the issues affecting Wi-Fi connections also affect mobile broadband connections.

##### 4.2.1.4.2 IPSec

IPSec requires key exchanges between the two endpoints at either end of the IP conversation. Usually, the key exchange occurs between two endpoints communicating for the first time. Subsequently, the keys are cached and reused if traffic between the two endpoints keeps the IPSec tunnel active. If the keys expire, a new round of key exchanges must occur. Some implementations of IPSec can let a few unencrypted packets go through, but none during the key exchange phase. After the key exchange phase, packets are allowed to flow again. However, some packets could be lost. This loss can cause call failures or audio dropouts.

##### 4.2.1.4.3 Virtual Private Network (VPN)

A major aspect of virtual private networks (VPNs) are that they are equated with any private packet encapsulation technology. Most VPN solutions are designed for TCP and optimized for throughput, rather than for real-time delivery of media traffic. As such, rate limits or server performance can affect Lync Server performance.

##### 4.2.1.4.4 Forced TCP Connection

Although Lync Server supports sending media over Transmission Control Protocol (TCP) connections, it is not an optimal solution. Small network performance degradations can cause noticeable issues for real-time traffic carried over TCP. One major reason is that the TCP protocol is lossless, meaning the TCP stack will retransmit the missing segments. During the retransmission, all subsequent data is queued. After the retransmission, the receiving endpoint will have experienced several times the RTT of delay. Buffering is often used to combat this issue, but it comes at the expense of providing a two-way, full duplex experience.

##### 4.2.1.4.5 ISP/Internet

Residential Internet connections often have minimal service level agreements (SLAs) and support to troubleshoot user network issues. Typically, almost all Lync Server audio/visual (A/V) performance degradation is caused by external Internet users. Because these connections are unmanaged, the best mitigation is to offer the users tools such as the Transport Reliability IP Probe (TRIPP) and Microsoft Pre Call Diagnostic Tool to test their “last hop” connection quality. For details, see "Lync Online - Transport Reliability IP Probe (TRIPP Tool)" at <http://go.microsoft.com/fwlink/p/?LinkId=304032>, and "Microsoft Pre Call Diagnostic Tool" at <http://go.microsoft.com/fwlink/p/?LinkId=304035>.

#### 4.2.1.5 Client Endpoint Performance

Packet loss and jitter are not always caused by network entities beyond the client and server endpoints. Sometimes, the client endpoint itself is the source of the network impairment. Packets are transmitted by the client endpoint based on a timer and picked from the receive queue by live threads. If the sender or receiver process is blocked, the packet loss and jitter will be just as real. Because Lync Server runs at the highest-priority thread level, only driver issues or other high-priority processes can interfere with normal processing functions in Lync Server.

Client endpoint performance issues consist of:

  - Power-saving mode

  - USB hub/cable

  - Drivers/deferred procedure calls (DPC) storm

##### 4.2.1.5.1 Power-Saving Mode

If the client endpoint is on battery power, the operating system can throttle the CPU share for Lync Server processing functions and affect its ability to send or receive packets in a timely manner.

##### 4.2.1.5.2 USB Hub/Cable

Low-quality USB hubs or cables can trigger deferred procedure calls (DPC) storms that preempt Lync Server processes from operating smoothly. Poorly shielded USB cables (even if the cables are inside a laptop or a PC case) can cause USB drivers to require more frequent servicing than usual.

##### 4.2.1.5.3 Drivers/DPC Storm

As previously described, low-quality drivers can preempt Lync Server processes, due to their privileged execution status in the operating system. The privileged code execution can come in the form of deferred procedure calls (DPCs). On client operating systems, use the DPC/second counters in the task manager to see if poor audio is associated with an increase in DPCs.

#### 4.2.1.6 Server Endpoint Performance

Server endpoint performance issues include:

  - Antivirus/port scanning software

  - Performance counter collection and logging

  - Network adapter configuration

  - Concurrent call load

  - Virtualization

##### 4.2.1.6.1 Antivirus/Port Scanning Software

Some corporate security policies require the installation of client endpoint security software on all corporate PCs, including those running Lync Server applications. This endpoint security software may have network firewall components that also actively scan traffic. Because Lync Media Servers, such as the AVMCU, and Edge Servers, such as the Media Relay Edge Servers, can process large volumes of packet traffic to support A/V/AppSharing modalities, any additional processing of network packets by port scanning software processes can affect the performance of the host computers, and therefore affect Lync Server performance. The performance impact occurs in the form of packet loss or higher jitter.

##### 4.2.1.6.2 Performance Counter Collection and Logging

Performance counter collection is an important part of monitoring the health and state of Lync servers. Collecting too many counters and collecting them at high frequencies can displace Lync Server processes from their CPU access, due to the high thread priority of the performance counter collection process. Because several Lync Server services can run on the same host computer and some counters run per CPU instance, the combination of application-specific counters and CPU cores can create large numbers of unique counters that need collection.

##### 4.2.1.6.3 Network Adapter Configuration

Network adapter configuration issues include:

  - Network adapter teaming/driver

  - TCP offloading

  - CPU affinity

**Network Adapter Teaming/Driver**

Although Lync Server deployment guidelines recommend against the use of network adapter teaming, some organizations may choose to follow their own guidelines around high-availability. Network adapter teaming bugs have been found in a few occasions. These bugs may affect only real-time traffic, such as audio/video/application sharing. Because most organizations do not run the host and network hardware through any benchmarks, latent issues in the hardware and drivers can remain undetected until the system is put into full production and real load is placed on the system.

**TCP Offloading**

TCP offloading is another feature that can affect real-time traffic under load.

**CPU Affinity**

Some network adapter drivers use only one CPU core on a multicore server to process network traffic. This can cause performance degradations if Lync Server uses the core to process media.

##### 4.2.1.6.4 Concurrent Call Load

Most Lync Server 2013 Media Quality Diagnostic Reports at <http://go.microsoft.com/fwlink/p/?LinkId=304027> (or Lync Server 2010 Media Quality Diagnostic Reports at <http://go.microsoft.com/fwlink/p/?LinkId=304029>) show the number of calls per day or maybe per hour. If there are too many concurrent calls at any one time, the server performance may be impaired to the point of degrading packet performance. There are performance counters and SCOM alerts to warn of this scenario. However, monitoring peak concurrent call load at the most detailed, customized level can provide early alerts on usage trends. QoE can provide this data through custom reports.

##### 4.2.1.6.5 Virtualization

While Lync Server supports virtualization technologies, packet performance should be monitored to avoid any issues with untested hardware and software interaction.

### 4.2.2 Troubleshooting Device Issues

Getting an issue statement from the user is the best way to start troubleshooting a device issue. For example, knowing that the user is experiencing distortion can help isolate your search for the root cause. Learning the troubleshooting steps that the user has already taken can also help you find the root cause. For example, if the user tried swapping one USB headset for another and the same issue persists, the issue is probably with the PC USB subsystem or the BIOS firmware.

The following sections describe the known causes of device issues and remedies.

#### 4.2.2.1 Built-in Sound Cards

Built-in sound devices in laptops and sound cards in PCs exist within a broad category of hardware. They’re often designed for general multimedia use, which may conflict with VoIP communication use scenarios. Laptop devices also have particular physical constraints, which makes them a poor substitute for open-air speaker phones or conferencing devices. Analog speakers and headsets can be used with sound cards to improve audio capture fidelity. However, the user must be aware of how the volume settings work to help ensure the best audio experience.

##### 4.2.2.1.1 Microphone Boost

Many sounds cards have a separate microphone boost setting that you must modify from the default setting to help ensure that human speech volumes are captured. Too low a setting for the microphone boost can make speech unintelligible, even if the volume settings are at the maximum level. Too high a setting can cause clipping (a sound distortion generated when the **audio** signal is too large to be represented), which can lead to echo issues. By using the tuning wizard in the Lync client, you can monitor microphone levels while modifying the boost setting. The following figure shows an example of the microphone boost setting from the **Microphone Properties** dialog box in the **Sound Device** settings.

![](c:\\Users\\lolaj\\OfficeDocs-SkypeForBusiness-pr\\Teams/media/image2.png)

Lync Microphone Properties Dialog Box

##### 4.2.2.1.2 Digital Signal Processing (DSP)

Some sound cards offer digital signal processing (DSP) features to improve music or game audio sound. These features alter the audio signal played by Lync and can cause echo issues. Disabling these features fixes the issue.

##### 4.2.2.2.3 Noise

In many laptops, built-in sound devices are often the least optimized components. Some sound devices are found to have obvious issues when marketed. The following figure shows noise in the left channel of the sound device, but not in the right channel. Using noise removal processes after the audio is captured can help, to some degree, but there still may be distortion.

![](c:\\Users\\lolaj\\OfficeDocs-SkypeForBusiness-pr\\Teams/media/image3.png)

Noise in Sound Device: Left Channel versus Right Channel

#### 4.2.2.2 USB Devices

USB devices combine the sound card, microphone, and speakers into one device. This gives the manufacturer more control over the device’s functionality, and tailors it for specific scenarios, such as communications or conferencing. However, USB devices can have electrical or USB host issues.

In addition to requiring glitch-free and noise-free playback and capture performance from the USB subsystem, Lync Server requires the subsystem to provide accurate timing for the audio samples. The Call Details Report contains microphone and speaker glitch rates. If rates are in the thousands range, there is an issue in the USB subsystem.

Determining which component in the USB subsystem is causing issues requires a scientific method of investigation, and different components to swap and test. Issues can affect entire classes of devices or laptops, or individual devices and laptops.

##### 4.2.2.2.1 USB Host Device Driver

The USB host device driver is one component of the USB subsystem that can cause poor capture or render suboptimal performance. For this reason, we recommend updating to the latest driver version as a troubleshooting step. At this level of troubleshooting, you can only determine the root cause if a change eliminates the problem so it’s easier to try many changes to see if any of them work.

##### 4.2.2.2.2 USB Hubs and Cabling

Inexpensive, low-quality USB hubs and cables can cause many USB device-related issues. Removing hubs, including laptop docking stations and swapping cables, are useful troubleshooting steps. Internal cabling in PCs can also be defective.

##### 4.2.2.2.3 PC BIOS

PC BIOS settings and firmware have been known to cause issues with USB audio devices. Troubleshooting the issue to this component level often occurs in large organizations with many models of similar laptops, where patterns emerge over many occurrences and user reports.

#### 4.2.2.3 Other Device Issues

Physical characteristics of audio devices can also affect voice quality. These characteristics include the devices’ physical and electrical properties, and design features. Because the characteristics are often associated with a specific make and model of a particular device, from a troubleshooting perspective, swapping devices can eliminate issues or rule them out.

##### 4.2.2.3.1 Harmonics

All materials have natural harmonic resonance frequencies. If the frequency is within normal speech frequencies, the device can vibrate and generate distortions. If the issue is inherent in the device, replace the device.

##### 4.2.2.3.2 Acoustic Isolation

Acoustic isolation minimizes the amount of feedback between the speaker or earpiece and the microphone. Poor isolation results in greater quantities of echo leaking into the microphone. While Lync has built-in software echo cancellation, requiring the software to remove the echo always results in distortion. The amount of distortion is proportional to the amount of echo that needs to be cancelled. Also, leaked acoustic signal can be band-limited because of harmonics, and can cause the echo canceller to leak the echo in its entirety.

##### 4.2.2.3.3 Electrical Isolation

Many devices have common electrical connections between the microphone and speaker. Solid-state components separate the incoming and outgoing signals. However, strong signals in the incoming signals can lead to signal leakage in the outgoing signals (and vice versa), causing echo and distortion.

### 4.2.3 Troubleshooting Environmental Issues

Environmental issues can affect how the audio is captured at the source. For example, simply having the user move to a quieter location may resolve poor audio quality. This section examines some of the environmental causes of low-quality audio.

#### 4.2.3.1 Noise

Lync has a noise canceller that removes common background noise, which goes unnoticed by the receiver. However, moderate amounts of noise can lead to distortion, and excessive noise can lead to distortion, audio cutouts, and volume fluctuations. Additionally, artificial sources of noise, such as computer-generated sounds can evade the noise canceller profiles.

##### 4.2.3.1.1 Heating, Ventilating, and Air Conditioning (HVAC) Noise

Heating, ventilating, and air-conditioning (HVAC) noise is often cancelled. However, this is also the type of noise that users don’t generally notice, and so they may not mention it when asked if there were noise sources in the room.

##### 4.2.3.1.2 Laptop Fan/Hard Drive

Laptops often pack microphones close to other mechanical components that generate noise, such as fans and hard drives. These sounds often don’t fit the noise profile in the noise canceller and may be excessively loud to the receiver. Using headsets with built-in sound cards on laptops can eliminate this issue.

##### 4.2.3.1.3 Typing

Typing sounds are also cancelled by the noise canceller. However, if the user who is typing is also talking, the noise canceller will not suppress the audio. Typing sounds are often recognized by the receiver as such, and so this issue is often not often reported to help desk.

#### 4.2.3.2 Microphone Positioning and Audio Device Selection

Microphone positioning and the appropriate choice of an audio device is often overlooked as a cause of audio quality issues. For example, a unidirectional microphone should be aimed toward the speaker’s mouth, and is therefore not suitable for multiple speakers in a conference setting.

Omnidirectional microphones must have adequate noise cancellation and echo removal features. Typically, built-in sound devices do not perform well as conference devices. The Audio Test service feature in the Lync client is a powerful tool, enabling users to test how their audio sounds to remote participants before the actual call is made. This helps to ensure that there aren't any major network issues or other issues that could affect call quality.

### 4.2.4 Troubleshooting IP-PSTN Gateways

#### 4.2.4.1 Comfort Noise

Comfort noise is artificial noise played by an audio device in a call. It fills in the gaps when the other party in the call is not sending packets due to silence suppression. To enhance the comfort noise generation, endpoints support sending a comfort noise packet at the end of a talk spurt. The packet marks the start of silence suppression, and it provides information about the type of comfort noise to be generated. This enhancement helps ensure that comfort noise is generated at the appropriate volume level, and it removes distortions caused by transitions between speech and comfort noise. The comfort noise packet is described in detail in IETF RFC 3389.

Make sure that the configuration of Comfort Noise is the same across all devices in the environment. Misconfiguration can lead to incorrect reporting of packet loss.

#### 4.2.4.2. Voice Activity Detection/Silence Suppression (VAD/SS) 

Voice Activity Detection/Silence Suppression detects the presence or absence of speech from the user’s microphone, and stops packets from being sent over the network if the user is not talking (in tandem with the AGC which ensures there is no clipping of the audio). VAD/SS works to ensure no “empty” packet is sent, which reduces the total number of packets sent during a call and optimizes transmission bandwidth, making it is available for other calls. The primary function of the Voice Activity Detection component is to categorize the captured audio as speech content or not. The Silence Suppression module uses this information to filter the silence packets out.

Make sure that the configurations of Voice Activity Detection and Silence Suppression are the same across all devices in the environment. Misconfiguration can lead to incorrect reporting of packet loss.

# Appendix A. Lync Audio Quality Model

Understanding the Lync Audio Quality Model will help anyone involved in deploying, monitoring, or troubleshooting Lync Server. An Audio Quality model can explain what factors can modify audio and in what ways, and, more importantly, what factors cannot modify audio. The following sections describe the basics of sound, digital representation and transmission of voice, the various signal processing stages, and finally, the issues that can occur in each stage.

## A.1 Lync Audio Pipeline

The audio pipeline consists of discrete stages from which audio signals are captured and transmitted from one Lync Server endpoint to another, where the audio is received and rendered.

The pipeline consists of the following stages:

  - Analog audio source

  - Analog audio capture

  - Analog-to-digital conversion (ADC)

  - Digital signal packet capture

  - Digital signal preprocessing

  - Encoding

  - Protocol encapsulation

  - Encryption

  - Transmission

  - Reception

  - Decryption

  - Decoding

  - Reassembly and buffering

  - Healing

  - Post processing

  - Playback

  - Digital-to-analog conversion

  - Analog audio render

As the audio signal gets transformed and moved along the audio pipeline, the signal can be subjected to certain forms of distortion or attenuation, but can also be immune to others. Understanding which types of distortions are possible at each stage can greatly improve the speed by which issues are isolated and diagnosed.

The following topics describe each of these stages, how the audio can be modified, and what effects the various stages have on the subjective quality of audio.

### A.1.1 Analog Audio Source

Analog audio, or sound, is a series of sound pressure waves. In a telephony call scenario, sound is generated by the speaker as well as by sources, such as other speakers in the room, air conditioning units, CPU fans, cars rolling by, and so on. The term *signal* refers to the desired audio in any given context, and the term *noise* refers to everything else that coexists with the signal. Generally, unless the speaker is in a sound chamber, sounds in typical environments are often a mix of signal and noise. The term *signal-to-noise, or* SNR, refers to the amount of desired sound relative to unwanted noise. If the SNR is low, it’s hard to distinguish the preferred audio from the noise. For example, if a person is calling from a crowded trading floor with many other people talking at the same time in close proximity, it’s hard to distinguish and comprehend the speaker’s words. However, if the speaker is in a noisy server room with loud fan noise, the speech may be decipherable, and signal processing elements may be able to clean up the signal to a certain degree.

Basically, the source audio should have as high an SNR as possible to help ensure good conversation quality.

### A.1.2 Analog Audio Capture

Sound waves are captured when they strike the surface of the microphone membrane, which, in turn, vibrates with the pressure of the individual waves. The vibration is picked up by an electric coil that converts the waves to an analog voltage. The voltage is then transmitted to the analog-to-digital conversion (ADC) described in the next stage. During this stage, the design and placement of the capture device, usually a microphone, can affect the quality of the captured audio. The following characteristics can influence the captured audio:

  - Microphone type: Omnidirectional vs. unidirectional

  - Microphone placement relative to noise sources

  - Microphone placement and orientation relative to the speaker

  - Microphone frequency response

  - Wind or breath shielding

  - Microphone and surrounding material harmonics

  - Acoustic signal isolation between the microphone and speaker

  - Electrical noise shielding

  - Electrical signal isolation between microphone and speaker

The audio tuning wizard in the Lync client enables users to test their audio device, and it can also be used to diagnose microphone and source issues.

### A.1.3 Analog-to-Digital Conversion (ADC)

The analog-to-digital conversion (ADC) process, also called *sampling*, converts the analog voltage from the microphone to a digital or binary representation of the waveform. There are two parameters in the ADC process that affect the quality of the digitized signal—sampling rate and bit depth. The sampling rate should be twice that of the highest frequency that needs to be preserved. For human speech, that sound frequency is 4 kHz, so an 8 kHz sampling rate is sufficient. This is the rate that traditional telephony has used for decades. Lync Server provides *wideband* audio and samples at 16 kHz, and therefore can capture even more frequencies, resulting in a more natural sounding conversation. The second parameter is the bit depth. Generally, 16 bits is enough to adequately represent each sampled value. Even CD audio uses only 16 bits per sample. If the sampling rate or bit depth is too low, the speech quality is significantly impaired. The audio sounds like it’s coming through a walkie-talkie or a CB radio.

Additionally, after the audio has been digitized, many distortions that can affect the signal in the analog form have no effect on the digital form. For example, you won’t hear any other noise, such as car noise, introduced into the signal after this point.

### A.1.4 Digital Signal Packet Capture

After the audio is digitized, it must still be copied into the Lync client’s memory buffers. Lync must determine how often to read the data from the sound device, and how much of the data to read at one time. Reading too frequently results in excess CPU usage, but lower latency; reading not often enough results in high latency. The delay from which an audio sample is available to be read to when it is actually read is called the *framing delay*. Generally, this delay is 10-20ms, because most codecs operate at 20ms frame sizes. If, for some reason, the data is not available when Lync Server attempts to read it, a glitch might occur. A glitch occurs when Lync Server presents a frame of zeros to the next stage in the pipeline, and the zeros cause a discontinuity in the audio waveform. Physically, the rendering device may be pulled hard from its last location to the center and a sharp sound, or a click or a pop, is heard.

### A.1.5 Digital Signal Preprocessing (DSP)

Digital Signal Pre-processing (DSP) can be applied to the audio waveform before encoding. Certain processing is most optimal at the sender side because other metadata is available to help in the processing. These processes can include:

  - Noise reduction

  - Typing suppression

  - Acoustic echo cancellation

  - Automatic gain control

  - Silence suppression
    
    Some of these processes can introduce distortions if the source audio requires significant correction. For example, in the earlier scenario where a speaker is in a noisy server room, the noise reduction process may remove much of the noise but cause some distortion in return. Compared to the noisy audio, almost all users prefer the cleaned but distorted audio. However, the listener in a call may not be aware of what the alternative unprocessed audio would sound like had a noise suppression algorithm not been run. Therefore the listener may judge the call based on the distortion and not the underlying conditions of the call. Lync Server addresses this awareness issue by letting the speaker know that they are in a noisy environment. The speaker must still volunteer that bit of information to the caller at the other end. Troubleshooting distortion issues generally involve looking at the call metrics in the Quality of Experience (QoE), or listening to samples of source audio, if available.

### A.1.6 Encoding

Encoding the audio before sending it is done only for conserving bandwidth. Uncompressed audio sampled at 16 kHz with 16 bits per sample has a bit rate of 256kbps. That can be compressed to about 1/8 of size by using a good encoder. The choice of the encoder depends on the available bandwidth, available CPU, and capabilities of receiving endpoint. There are a few things to keep in mind in determining if codecs are causing voice quality escalations.

  - Users making calls with one codec and then another may experience a difference in quality and think that the system is unstable. In fact, the specific call scenarios dictate the codec choice.

  - Call admission control (CAC) may be in effect, so that even Lync-Lync calls get routed through the public switched telephone network (PSTN) without warning to the user, and so the user experiences the lower quality GW CODEC unexpectedly.

  - Complex call routes result in transcoding or multiple encoding stages with losses at each stage.

  - Unexpected low bandwidth situations where a lower bit rate codec is selected.

### A.1.7 Encryption

The encoded audio packet is encoded for privacy reasons. Lync Server uses secure real-time transport protocol (SRTP), an encryption scheme that helps to ensure against packet loss. There should be no quality degradation associated with SRTP, other than packets that can be discarded if the sender and receiver have bugs in their implementation of the encryption process.

### A.1.8 Protocol Encapsulation

Lastly, the encrypted audio is placed in a protocol suitable for real-time transmission. Lync Server uses real-time transport protocol (RTP) and *real-time transport control protocol (*RTCP) to frame the packets. The RTP protocol contains several advanced features to facilitate the transmission and recovery of audio and video. First, the sequence number in each packet helps the receiver know immediately if a packet is received out of order, or lost. The marker bit tells the receiver when a *talkspurt*—a continuous segment of speech between silent intervals where only background noise can be heard—starts.

The RTCP channel transmits metrics about the call, and this channel the basis for much of the network-related metrics seen on QoE reports.

### A.1.9 Transmission

The transmission stage involves many devices and individual steps. It is also the most significant stage for this guide’s intended audience, the network administrator. Most of this guide focuses on ways to prevent issues in the transmission of audio and video, so the issues that can affect packets in transit are not described here. Rather, this section addresses the three ways in which packet transit performance can be degraded—jitter, loss, and delay.

#### A.1.9.1 Jitter

Jitter is the change in delay from packet to packet. The expected delay is equal to the packetization time, or *p-time*. For example, if 20ms of data is sent at a time, a packet of data is sent every 20ms. Any deviation from the 20ms mark is considered jitter. A jitter value of 5ms means, on average, that the packet was early or late 5ms from the expected arrival time.

Jitter can cause poor audio performance because the receiving endpoint attempts to minimize delay by playing the audio as soon as it is received. If a packet is delayed, the endpoint can either play a frame of zeros and glitch, or stretch out the previous frame to buy more time. Smart endpoints like Lync Server will also use an adaptive jitter buffer so that the first time a large glitch is experienced, the buffer grows to accommodate any additional jitter. If no jitter is experienced for some time, the buffer slowly shrinks. This means sustained high jitter is better than sporadic high jitter.

For Transmission Control Protocol (TCP)-based audio sessions, jitter is also the only impairment because losses are removed by retransmission.

#### A.1.9.2 Loss

Packet loss results directly in the receiver attempting to recover from the loss by using advanced corrective, or *healing*, algorithms. Single packet losses can be healed with minimal distortion. Back-to-back packet losses may cause distortion. Larger bursts of loss result in speech cutout. Of course, the actual speech content plays a big role in how the listener perceives the healed audio. For example, lost packets containing silence will not be missed, but lost packets containing important syllables will be missed much more.

Forward error correction algorithms provide redundancy to help recover the lost packets. However, redundancy comes at the expense of added bandwidth. Forward error correction (FEC) distance generally does not go greater than one, so back-to-back packet losses are still hard to recover from. You’ll have a high packet loss rate and very little noticeable call quality degradation if the losses are uniform, or if FEC is enabled. In practice, losses are not uniform, so a high loss rate generally translates to poor audio experience.

In this guide, we discuss two different thresholds that are used in QoE reports. A loss threshold of 10 percent is at a high enough mark so that, most likely, the callers have a poor experience. This type of reporting is used for gauging the amount of user listening dissatisfaction. A threshold of 1 percent packet loss, on the other hand, is used to discover infrastructure issues between well-connected endpoints on managed networks.

#### A.1.9.3 Delay

Delay is often measured by using the round-trip delay calculation via the RTCP channel. Delay should be directly correlated to the distance between the callers; therefore, absolute thresholds are not useful for determining whether an issue exists. Although delay figures in the users’ perception of overall quality, issues caused by loss and jitter generally supersede those caused by delay.

In some cases, long delays can cause Line Echo Cancellers to fail when PSTN endpoints are involved in calls.

### A.1.10 Reception

As packets arrive on the receiving endpoint, they must be read by the Lync client or server process in a timely manner. If the Lync Server transport threads that are running in user context (as opposed to kernel) are blocked or delayed, the appearance of jitter, loss, or delay may exist in the end-to-end metrics, such as QoE network metrics.

### A.1.11 Decryption

Decrypting the packets is the counterpart of encrypting them. The only issue that can occur at this stage is the system fails to decrypt the packets, which results in packets being discarded. The result is no audio or audio loss midway through the call.

### A.1.12 Decoding

The decoding stage is the counterpart of the encoding stage. Similar to the decryption stage, if the wrong codec is in use, it can result in audio loss. In addition, bugs in the encoder or decoder can cause math errors, which sound like glitches or other unnatural, machine-made noises. For example, the G.711 bit flip is a common coding mistake in G.711 implementations, which produces a distinctive distortion.

### A.1.13 Reassembly, Buffering, and Healing

After decoding, the audio is in uncompressed digital form. The audio is stored in a large buffer and may contain spaces for missing packets. If the missing packets arrive in time, they can be inserted into the holes with no detrimental effect on quality. If they arrive too late, the algorithmic healer extrapolates the missing data by using the surrounding data. The healing process can produce metallic sounding artifacts, if pushed to extremes. Such artifacts are sure indications that network impairments exist. These are also the only types of artifacts introduced by this processing stage.

### A.1.15 Post processing

Before sending the healed audio to the sound device to play back, the audio is run through digital signal processing (DSP) again to improve the audio one last time. Generally, this involves applying gain algorithms because the audio could have come from non-Lync sources that don’t have the benefit of automatic gain control (AGC) at the source.

### A.1.16 Playback

Lastly, the audio samples are written to the sound device’s render buffer at prescribed intervals. There is a chance that the Lync client can be interrupted by system events or bad drivers so that glitches are created. Glitches on the render side can be diagnosed by examining a Microsoft Network Monitor or Wireshark capture to determine if the audio arriving on the local endpoint is glitch-free. There are also speaker glitch counters in QoE for each client endpoint.

### A.1.17 Digital-to-Analog Conversion (DAC)

The digital-to-analog conversion (DAC) stage is straightforward and does not have any potential to degrade the audio. We mention it here for complete coverage of the stages.

### A.1.18 Analog Audio Render

The render stage can distort the audio if the speaker device is low quality. However, most of these issues can be easily discovered by the user because they affect all audio coming out of the device. The audio tuning wizard in the Lync client enables users to test their audio device, and can be used to diagnose speaker issues.


## Related topics

[Improve and monitor call quality for Teams](monitor-call-quality-qos.md)

[Set up per-user call analytics](set-up-call-analytics.md)

[Use Call Analytics to troubleshoot poor call quality](use-call-analytics-to-troubleshoot-poor-call-quality.md)

[Set up Call Quality Dashboard (CPD)](turning-on-and-using-call-quality-dashboard.md)

[Use CQD to manage call and meeting quality](quality-of-experience-review-guide.md)

