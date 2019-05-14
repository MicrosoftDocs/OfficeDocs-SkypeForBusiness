---
title: 'Lync Server 2013: QoE reports'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: QoE reports
ms:assetid: 49c827af-b8dd-4c6e-b0dc-b4bc6d60e9a3
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn720913(v=OCS.15)
ms:contentKeyID: 63969601
ms.date: 01/27/2015
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# QoE reports in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-05-01_

<div>

## QoE summary/trend reports

The QoE summary/trends reports are useful for finding the peak usage times of day and examining the media quality during those times to help assure that your organization's network resources are sufficient. Your organization can also use the many filters available in the report to isolate performance numbers for certain locations, client and device types, and servers.

QoE summary/trend reports consist of:

  - UC-to-UC Summary/Trend Report

  - PSTN Summary/Trend Report

  - Conference Summary/Trend Report

</div>

<div>

## QoE performance reports

QoE performance reports provide details about the three reports that concentrate on the QoE performance of Mediation Servers, A/V Conferencing Servers, and endpoint locations.

</div>

<div>

## Mediation server performance report

The Mediation Server Performance report lists the metrics achieved by one or more Mediation during the specified time period. The metrics for the unified communications (UC)-to-Mediation Server leg and the Mediation Server-to-Gateway leg of each call are reported separately. Use this report to compare the volume and performance of your organization's various Mediation Servers.

For each Mediation Server (and for each call leg), the report displays the following:

  - Number of calls

  - Packet Loss

  - Round Trip Time

  - Jitter

  - Conversational mean opinion score (MOS)

  - Sending MOS

  - Listening MOS

  - Network MOS

  - Network MOS Degradation

  - Echo Return

  - Signal Level

</div>

<div>

## A/V conferencing server performance report

The A/V Conferencing Server Performance report provides lists of metrics achieved by one or more A/V Conferencing Servers during the specified time period. This report can be used to compare the volume and performance of your organization’s various A/V Conferencing Servers. Your organization can also isolate the report to show only the experience for specific client types, such as Lync clients or PSTN clients.

For each A/V Conferencing Server, the report displays the following:

  - Number of conferences

  - Packet Loss

  - Round Trip Time

  - Jitter

  - Conversational mean opinion score (MOS)

  - Sending MOS

  - Listening MOS

  - Network MOS

  - Network MOS Degradation

  - Echo Return

  - Signal Level

</div>

<div>

## Location-based performance report

The Location-Based Performance report provides a list of network locations and for each location shows the number of calls in each pre-determined range of quality. The goal of this report is to provide insight into the media quality of the bulk of your organization’s telephone calls for various locations so that you can identify poorly performing locations, and see the different grades of media quality in your organization’s different locations.

When displaying the report, different tables of metrics appear—one table for each metric your organization decides to report on. You can choose from the following metrics for this report:

  - Conversational mean opinion score (MOS)

  - Network MOS

  - Network MOS Degradation

  - Sending MOS

  - Listening MOS

  - Packet Loss

  - Jitter

  - Latency

</div>

</div>

<span> </span>

</div>

</div>

</div>

