---
title: 'Lync Server 2013: Overview of monitoring'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Overview of monitoring
ms:assetid: 5d5eb658-7fe0-42e6-acaf-700051d0a823
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204937(v=OCS.15)
ms:contentKeyID: 48184261
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Overview of monitoring in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-05_

In Microsoft Lync Server 2013, monitoring is used to collect usage information and Quality of Experience (QoE) data about the communication sessions that your users are involved in. A session is a generic term that covers a user’s connection to a:

  - Conference

  - Conferencing modality (such as Audio/Video or Application Sharing)

  - Another user via a peer-to-peer conversation such as instant messaging or an audio call

<div>


> [!NOTE]  
> Lync Server 2013 keeps track of information about each session: who called who; which endpoints were used in the session; how long did the session last; what was the perceived quality of the session; and so on. However, Lync Server does not record and store the actual call itself. That includes instant messaging sessions as well: although Lync Server records information about instant messaging sessions, it does not maintain a record of each instant message that was sent during the session.



</div>

The call detail information collected by Lync Server can be employed for any number of uses, including:

  - **Return on Investment (ROI)**. Administrators can compare the usage data collected by Monitoring Server to similar data collected for their previous telephony system in order to show cost savings and help justify the deployment of Lync Server.

  - **Device Inventory Management**. Asset management information helps administrators identify old devices still in use that need to be replaced, as well as identify expensive devices that do not appear to be getting used at all.

  - Help Desk. Troubleshooting data enables support engineers to determine why a user’s call failed, and to do so without having to collect server or client side logs. This information can be readily accessed and understood by support personnel who do not have a deep technical knowledge of Microsoft Lync 2013 and Lync Server 2013.

  - **System Troubleshooting**. Enables administrators to detect major issues that might prevent end users from performing basic tasks like joining a conference, establishing a call, or sending an instant message.

In addition to this basic call information, the Monitoring Server also provides a mechanism that allows SIP endpoints (such as Lync 2013) to provide troubleshooting information that the server would not otherwise have access to:

  - **Media Metrics that Impact Quality**. These metrics deal with the actual transmission of the call itself; that is, they provide a sort of travel log as the call journeys across the network. These metrics (which include such things as packet loss, jitter, and round trip times) provide information on what happened to the call from the time it left your endpoint to the time it arrived at the other person's endpoint.

  - **Issues Reported to the End User**. These metrics include poor quality notifications that Lync 2013 presents to end users in cases where they are too far from a microphone, speaking too softly, have a poor network connection, or are experiencing poor quality because another program on the computer is consuming the available resources.

  - **Environment Information**. These metrics detail call quality factors such as the type of microphone and speakers being used, whether the user is connected through a VPN connection, and whether the user is on a wireless connection.

At the end of each call, SIP-compliant endpoints automatically transmit this information to the Front End server that facilitated the call. You don't have to do anything to get endpoints to transmit that information; that behavior is built into the SIP protocol. However, if you want to collect and store that information, then you need to install and enable monitoring. If you do install and enable monitoring, then call information is gathered by agents running on the Front End server and relayed to a pair of SQL Server databases.

Note that the process of installing and configuring monitoring has been simplified in Lync Server 2013. In prior versions of the software, monitoring required a separate Monitoring Server role, which typically meant a separate computer set aside for use as the Monitoring Server. In Lync Server 2013, however, the Monitoring Server role has been eliminated. Instead, the monitoring service (in the form of "unified data collection agents") has been collocated into all Front End servers. This has at least two major benefits. Collocation of the monitoring service:

  - Decreases the number of server roles required when implementing Lync Server 2013. Decrementing the Monitoring Server role also helps reduce costs by eliminating the need to maintain dedicated servers for monitoring.

  - Reduces the complexity of Lync Server 2013 setup and administration. By collocating the monitoring services on each Front End server you no longer have to install, configure, and manage the Monitoring Server role.

For more information see the topic [Deploying monitoring in Lync Server 2013](lync-server-2013-deploying-monitoring.md) in the Lync Server 2013 2013 deployment guide.

</div>

<span> </span>

</div>

</div>

</div>

