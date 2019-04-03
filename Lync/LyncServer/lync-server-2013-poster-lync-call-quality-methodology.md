---
title: 'Lync Server 2013: Poster: Lync Call Quality Methodology'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: 'Poster: Lync Call Quality Methodology'
ms:assetid: a069f4e5-4f80-4f0f-8657-2e07276b6b41
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn593600(v=OCS.15)
ms:contentKeyID: 61084874
ms.date: 06/24/2016
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Lync Call Quality Methodology in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2016-06-24_

This article is a companion to the [Lync Call Quality Methodology](http://go.microsoft.com/fwlink/?linkid=391841) poster, which you can download from the Download Center.

![Poster describing the CQM process](images/Dn594589.d239e04a-1c3b-4f0e-93af-88b85198615a(OCS.15).jpg "Poster describing the CQM process")

You can use this poster to learn about CQM, the Call Quality Methodology for Lync 2013 and 2010 that helps you find and eliminate issues affecting call quality and user experience for Lync implementations that include enterprise voice features. Call Quality Methodology is a new troubleshooting and service management framework that can better focus efforts to improve enterprise voice services in Lync. In this article, you can learn more about CQM, the kinds of servers and solutions that are monitored, and what to do with the collected telemetry data.

If you have questions about how to use CQM, you can submit your questions to cqmfeedback@microsoft.com.

The poster explains the following areas:

  - What is Lync CQM?

  - Prioritize: Run Trending Queries

  - PCD

  - Managed/Unmanaged

  - The Server Plant Road

  - The Last Mile Road

  - The End Points Road

  - Service Management

  - Board Game Rules

<span id="WhatIs"></span>

<div>

## What is Lync CQM?

Call Quality Methodology is a new troubleshooting and service management framework that can better focus efforts to improve enterprise voice services in Lync. When you use CQM, less effort is needed to assure call quality and user satisfaction for enterprise voice services. CQM is more fully explained in the [Call Quality Methodology](http://go.microsoft.com/fwlink/p/?linkid=615208). This article and the poster are summaries of that content.

CQM breaks down System troubleshooting into three paths or “Roads.” These are: the Server Plant Road, which looks at the servers and the links between them, the End Points Road, which looks at user devices and media used to carry calls, and the Last Mile Road, which addresses integration of traditional switched telephone network calls.

Each Road is divided into several segments relating to a specific area or topic, and at each segment definitions are made about what is an acceptable quality level, actions are taken to achieve that quality level, and a service management plan is put in place to maintain that quality level before moving on to the next topic.

The poster presents Lync CQM as a board game for three players, each of whom will go through one of the roads. Cards included with the download are used to simulate impediments to call quality that must be overcome. Hints and suggestions about targets and how to achieve them are included along the three paths, as well as prioritization guidelines for which road to pursue first in actual applications (in the game, all three roads are addressed in parallel).

How does CQM work in earlier versions of Lync? CQM is new for Lync 2013, but most of it can be adapted to be used with Lync 2010. CQM may work to a degree with Microsoft Office Communicator, but this is untested and not supported.

If you have questions about how to use CQM, you can submit your questions to cqmfeedback@microsoft.com.

</div>

<span id="Trending"></span>

<div>

## Prioritize: Run Trending Queries

The first step in CQM is to run each of the trending queries for two weeks and then analyze the results. Prioritize corrective action by the largest stream contributor, the highest poor stream ratio, and managed areas (ones you control).  If the Audio/Video Multi-point Control Unit (AV MCU) or Mediation queries show poor results, start on the Red or Server Plant road.  If the Wired or Wireless queries show poor results, start on the Blue or Last Mile road.  If the VPN or External queries show poor results, start on the Green or End Points road.

After you choose a road to start with, define a target for each area (Assert), work to meet that target (Achieve) and then implement procedures to stay on target (Maintain). You can also use this poster as a game to understand the principles behind CQM.

</div>

<span id="PCD"></span>

<div>

## PCD

The PreCall Diagnostics tool (PCD) will help you identify and diagnose problems in your perimeter network (the QoE database doesn’t collect information on your edge or perimeter network) and also to troubleshoot connections in the Last Mile. The tool is available as both a Windows 8 Modern App or a Windows Desktop App at http://apps.microsoft.com/windows/en-us/app/lync-2013-precall-diagnostics/9607fe33-2b51-403d-9615-c23f248e7c88.

</div>

<span id="ManagedUn"></span>

<div>

## Managed/Unmanaged

The Lync Server deployment and network infrastructure can usually be divided into managed and unmanaged spaces. The managed space includes your entire inside wired network and server infrastructure. The unmanaged space is the wireless infrastructure and the outside network infrastructure.

Making this distinction increases the clarity of your data and helps your organization focus on workloads that will have a measurable impact on your users’ voice and video quality. Users have a different expectation of quality if the call is placed on infrastructure that you own (managed) versus infrastructure that is partly under the control of some other entity (unmanaged). This is not to say that wireless users are left to their own devices to have excellent Lync Server experiences.

Improving voice quality in the unmanaged space requires you to have high quality in the managed space. Whether wireless (Wi-Fi) is considered managed or unmanaged space is up to your organization. The techniques to achieve a healthy environment are different in the two spaces, as are the solutions.

</div>

<span id="ServRd"></span>

<div>

## The Server Plant Road

Segment 1 of the Server Plant Road addresses the actual servers in the Lync implementation. Gather KHI data regarding both the server itself and its role in the implementation and analyze the result. If action is warranted, correct any problems found. More detail on this topic is presented in the article about [Key Health Indicators in Lync Server 2013](lync-server-2013-poster-key-health-indicators.md) that accompanies the KHI poster.

The next segment addresses media streams between the AV MCU server and mediation server. Begin by determining your targets for poor stream thresholds. Poor streams are usually PacketLossRate \> .01 or PacketLossRateMax \> .05. Another desirable target is PoorStreamsRatio \< 2%. Next, use detailed queries to find AVMCU and Mediation server pairs with poor streams, investigate the cause of poor streams, look at network equipment in the poor stream paths, remediate poor streams, and define optimal or “gold” configuration for network equipment. To maintain your achievement, implement processes and tools to manage configuration drift and to report new problem areas.

Next, examine the media streams between the Mediation server and the Public Switched Telephone Network (PSTN) gateway. Begin by determining your targets for poor stream thresholds. Poor streams are usually PacketLossRate \> .01 or PacketLossRateMax \> .05. Another desirable target is PoorStreamsRatio \< 2%. Next, use detailed queries to find Mediation server and gateway pairs with poor streams, investigate the cause of poor streams, look at network equipment in the poor stream paths, remediate poor streams, and define optimal or “gold” configuration for network equipment. To maintain your achievement, implement processes and tools to manage configuration drift and to report new problem areas.

Finally, examine the health metrics for your PSTN gateway. Identify the statistics that show health and define targets against them. No specific guidance is provided here as many possible gateways can be used. Once targets are established, remediate as needed to achieve the target; in the process you will likely define a “gold” or optimal configuration for the gateway. To maintain your achievement, implement processes and tools to manage configuration drift and to report new problem areas. Be aware that firmware and software updates may alter your configuration or lead you to change the definition of the “gold” configuration, so approach these activities with care.

</div>

<span id="LastMi"></span>

<div>

## The Last Mile Road

Of the two ways clients connect to the network, wired is expected to deliver the highest quality and correspondingly this must be your initial focus for last mile issues. Use the CQM Wired query (LastMile\_0\_Wired) and the Poor Streams ratio data it provides. We suggest defining a target PoorStreamsRatio \< 5% for sites with \> 300 streams). To achieve your targets, remediate subnets ordered from worst to best, and implement QoS.

After you optimize the quality of your wired connections, improving wireless quality becomes easier because the wireless infrastructure sits atop the wired core at each location. Poor wireless streams in a site with good wired quality must be attributed to the specific wireless components. The CQM Wireless query (LastMile\_1\_Wireless) operates on a date range and will return all internal wireless streams in your environment from Lync clients to or from either conferencing servers or mediation servers. We suggest defining a target PoorStreamsRatio \< 5% for sites with \> 300 streams). To achieve your targets, remediate subnets ordered from worst to best, and implement QoS.

</div>

<span id="EndPt"></span>

<div>

## The End Points Road

Begin inquiries into the End Points Road with the headsets and other devices known to produce acceptable quality when used with Lync. We suggest a target AvgSendListen MOS \> 3.6 for implementations with over 100 streams.) Achieve the target by identifying problematic devices and fix or replace them.

Next, examine the device or PC processing the audio for end user calls. A suggested target quality metric is an AudioMicGlitchRate \<= 1. As you identify optimal system configurations for the user systems, define a “golden” PC configuration including driver versions.

Now examine the network path an audio stream takes from a Lync endpoint system, which can cause poor audio quality. If audio travels over a VPN connection you might see latency issues. If an internal Lync client cannot establish a direct media stream to another internal Lync client for a two-party or peer-to-peer call, it will fall back to a path that relays through a Lync Edge server, again leading to latency issues as well as increased potential for loss and jitter. We suggest you define a quality metric of 0% Media over VPN. As you remediate to achieve the target you set, identify problem subnets and investigate firewall rules, packet shapers, and other relevant network equipment configuration.

IP Packets can use either Transmission Control Protocol (TCP) or User Datagram Protocol (UDP). TCP is optimal for data streams. UDP is connectionless and is more efficient for media since TCP recovery mechanisms cannot address loss in real time media. Lync always prefers UDP, but will revert to TCP if a UDP session cannot be established. Media sessions over TCP will exhibit poorer quality than over UDP. We recommend a quality definition of 0% connections over TCP. As you remediate to achieve the target you set, identify problem subnets and investigate firewall rules, packet shapers, and other relevant network equipment configuration.

</div>

<span id="ServMgt"></span>

<div>

## Service Management

Service management is the end state of CQM, and the destination for all three roads. To maintain high levels of call quality, monitor these areas:

1.  **Users** - Remediation activities should show a measurable increase in user satisfaction. You can measure this by problem tickets or other feedback mechanisms. You can also publish quality metrics.

2.  **Process** - define daily, weekly and monthly processes to operationalize CQM. Monitoring rhythm starts at a higher frequency while you are remediating (daily) and moves to a lower frequency (monthly) as you stabilize.

3.  **Tools** - identify tools to both measure and remediate. You may find it useful to automate running the CQM queries to support your processes. Remediation may require additional tools for example to enforce standardized configurations on network elements or troubleshooting loss in poor streams.

</div>

<span id="BoardGm"></span>

<div>

## Board Game Rules

You can use this poster either as a reference to a CQM implementation or as a game to practice the concepts. To play, you will need one six-sided die and the cards provided. A downloadable version of the cards is available to print on standard Avery 5871 business cards.

The game is for 3 players. There are three paths the players can use to achieve the desired quality and reach the center Service Management state: Server Plant, End Point, and Last Mile. Each path has stops along the way where you Assert quality targets, Achieve goals, and Maintain an aspect of your system. Place the cards in the indicated area above, and then draw 5 cards. Review the cards you’ve drawn and place them on the relevant board segment. Each player moves through the cards on their path step by step, asserting quality targets, achieving those targets, and maintaining the service levels. The game is completed when all players reach the center Service Management state. More detailed rules are provided with the game card download.

To **Assert** a quality target, review the parameters applicable to that target, and state out loud what you will and won’t choose to accept. We have recommended beginning points, but you must make the final call. The exception is KHI data, where the standards established by Microsoft should be used. See the accompanying KHI poster.

To **Achieve** in the game, use the cards provided in place of KHI data and system queries. If at the start of the game you did not draw a card relating to a given aspect, you can continue past it. If there is a relevant card, roll the die. If you rolled under the number indicated on the card, you have succeeded. If you roll at or over the indicated number, you must draw another card from the deck. If the card indicates two or more players need to roll, they must all roll successfully.

To **Maintain** in the game, state out loud the service management plan regarding that aspect of the Lync environment.

</div>

<div>

## See Also


[Lync Server Networking Guide](http://go.microsoft.com/fwlink/p/?linkid=390677)  
[Key Health Indicators: The Foundation for Maintaining Healthy Lync Servers](http://go.microsoft.com/fwlink/?linkid=391838)  
[Lync Call Quality Methodology](http://go.microsoft.com/fwlink/?linkid=391841)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

