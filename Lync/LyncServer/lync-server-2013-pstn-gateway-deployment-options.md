---
title: 'Lync Server 2013: PSTN gateway deployment options'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: PSTN gateway deployment options
ms:assetid: d1ab4f74-18aa-40c7-a8cf-ec806cf6e28a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398899(v=OCS.15)
ms:contentKeyID: 48185445
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# PSTN gateway deployment options in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-21_

<div>

## PSTN Gateways

Public switched telephone network (PSTN) gateways are third-party hardware components that translate signaling and media between the Enterprise Voice infrastructure and the PSTN, either directly or through connection to SIP trunks. In either topology, the gateway terminates the PSTN. The gateway is isolated in its own subnet and is connected to the enterprise network through the Mediation Server.

An enterprise with multiple sites would typically deploy one or more gateways at each site. Branch sites can connect to the PSTN either through a gateway, or through a Survivable Branch Appliance, which combines gateway and servers in a single box. If branch sites use a gateway, both a Registrar and Mediation Server are required on site, unless the WAN link is resilient. One or more Mediation Servers, which are collocated on Front End Servers, can route calls for the one or more gateways at each site. We recommend that the Registrar, Mediation Server, and gateway required on site are deployed as a Survivable Branch Appliance.

Determining the number, size, and location of PSTN gateways is perhaps the most important and expensive decision you must make when planning your Enterprise Voice infrastructure.

Here are the main questions to consider. Keep in mind that the answers to these questions are all interdependent

  - How many PSTN gateways are needed? The answer depends on the number of users, the anticipated number of simultaneous calls (traffic load), and the number of sites (each site needs one).

  - What size should the gateways be? The answer depends on the number of users at the site and on the traffic load.

  - Where should the gateways be located? The answer depends in part on the topology and in part on the geographic distribution of your organization.

You should also consider your gateway topology options (for details, see Gateway Topologies later in this topic).

<div>

## M:N Trunk Support

The Mediation Servers can route calls through multiple gateways, Session Border Controllers (SBCs) provided by Internet telephony service providers, or a combination of the two. Additionally, multiple Mediation Servers in the pool can interact with multiple gateways. The logical route defined between a Mediation Server and gateway is called a *trunk*. When an internal user places a PSTN call, outbound routing logic on the Front End pool chooses which trunk to route over out of all possible combinations that may be available for routing that particular call. With DNS load balancing, if a call fails to reach a gateway due to an issue with a particular Mediation Server in the pool, the call will be retried to an alternate Mediation Server in the pool.

For details about planning for multiple gateways, see [M:N trunk in Lync Server 2013](lync-server-2013-m-n-trunk.md).

For details about other outbound routing enhancements, see [Voice routes in Lync Server 2013](lync-server-2013-voice-routes.md).

</div>

<div>

## Gateway Topologies

When you consider the fundamental questions of gateway deployment, follow these steps:

1.  Count the sites at which you want to provide PSTN connectivity by using Enterprise Voice.

2.  Estimate the traffic at each site (number of users and average number of calls per hour per user).

3.  Deploy one or more gateways at each site to handle the anticipated traffic.

The resulting distributed gateway topology is shown in the following figure.

**Distributed gateway topology**

![Distributed Gateway Topology diagram](images/Gg398899.f0f65a0b-a462-491a-878b-4d4bf0a96f6d(OCS.15).jpg "Distributed Gateway Topology diagram")

With this topology, calls among workers at each site and between sites are all routed over your intranet. Calls to the PSTN are routed over the enterprise IP network to the gateways that are closest to the location of the destination numbers.But what if your organization supports dozens or hundreds or even thousands of sites spread across one or more continents, as many financial institutions and other large enterprises do? In such cases, deploying a separate gateway at each site is not practical.

To address this issue, many large companies prefer to deploy one or a few large telephony central sites, as shown in the following figure.

**Telephony central site topology**

![Data center gateway topology](images/Gg398899.927f4808-bf74-405a-be20-2cd9cd87af6d(OCS.15).jpg "Data center gateway topology")

In this topology, several large gateways sufficient to accommodate the anticipated user load are deployed at each central site. All calls to users in the enterprise are forwarded by the company's telephone service provider to a central site. Routing logic at the central site determines whether the call should be routed over the intranet or to the PSTN.

</div>

<div>

## Gateway Location

Gateway location may also determine the types of gateways that you choose and how they are configured. There are dozens of PSTN protocols, none of which is a worldwide standard. If all your gateways are located in a single country/region, this is not an issue, but if you locate gateways in several countries/regions, each must be configured according to the PSTN standards of that country/region. Moreover, gateways that are certified for operation in, for example, Canada, may not be certified in India, Brazil, or the European Union.

</div>

<div>

## Gateway Size and Number

The PSTN gateways that most organizations will consider deploying range in size from 2 to as many as 960 ports. (There are even larger gateways, but these are used mainly by telephone service providers.) When estimating the number of ports your organization requires, use the following guidelines:

  - Organizations with light telephony usage (one PSTN call per user per hour) should allocate one port for every 15 users. For example, if you have 20 users, you will require a gateway with two ports.

  - Organizations with moderate telephony usage (two PSTN calls per user per hour) should allocate one port for every 10 users. For example, if you have 100 users, you will require a total of 10 ports allocated among one or more gateways.

  - Organizations with heavy telephony usage (three or more PSTN calls per user per hour) should allocate one port for every five users. For example, if you have 47,000 users, you will require a total of 9,400 ports allocated among at least 10 large gateways.

  - Additional ports can be acquired as the number of users or amount of traffic in your organization increases.

For any given number of users you must support, you have the choice of deploying fewer, larger gateways, or smaller ones. As a rule, a minimum of two gateways for an organization is recommended to maintain availability if one gateway fails.

Each PSTN gateway that you deploy must have at least one corresponding Mediation Server.

</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

