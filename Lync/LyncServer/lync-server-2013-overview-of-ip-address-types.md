---
title: 'Lync Server 2013: Overview of IP address types'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Overview of IP address types for Lync Server
ms:assetid: ee9a695f-5cf5-441e-94fb-6adeca50e8d8
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205363(v=OCS.15)
ms:contentKeyID: 48185759
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Overview of IP address types for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-01-29_

You have three options when configuring IP addresses in Lync Server 2013. You can configure Lync Server 2013 to support only IP version 4 (IPv4), only IP version 6 (IPv6), or a combination of both (known as a *dual stack*). There are several issues to consider with each type of configuration:

  - **IPv4 only**   IPv6 was created because the world is running out of IPv4 addresses. Ultimately, IPv6 will be fully supported worldwide, but at this time, many companies and devices that your enterprise might need to communicate with do not yet support IPv6, and may not for some time. An IPv4-only configuration will help to ensure that your Lync Server implementation can communicate with most existing devices.

  - **IPv6 only**   Conversely, a full IPv6 implementation, at this time, will exclude communication with many existing devices.

  - **Dual Stack**   Dual stack is a network where both IPv4 and IPv6 addresses are enabled. This configuration is supported in Lync Server 2013 because in most cases the transition from full-IPv4 to full-IPv6 will take several years.

The following sections outline the compatibility among these three configurations for various Lync Server features.

<div>


> [!NOTE]  
> Client or server configuration with IPv6 only is supported only for lab or validation purposes. IPv6 only configuration is not supported in the production deployment.



</div>

<div>

## Client Registration


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Client endpoint network</th>
<th>Server network</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>IPv4</p></td>
<td><p>IPv4</p></td>
</tr>
<tr class="even">
<td><p>IPv4</p></td>
<td><p>Dual stack</p></td>
</tr>
<tr class="odd">
<td><p>Dual stack</p></td>
<td><p>IPv4</p></td>
</tr>
<tr class="even">
<td><p>Dual stack</p></td>
<td><p>Dual stack</p></td>
</tr>
<tr class="odd">
<td><p>Dual stack</p></td>
<td><p>IPv6</p></td>
</tr>
<tr class="even">
<td><p>IPv6</p></td>
<td><p>Dual stack</p></td>
</tr>
<tr class="odd">
<td><p>IPv6</p></td>
<td><p>IPv6</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Peer-to-Peer Client

Peer-to-peer communications include audio, audio/video, application sharing, and file transfer. After both clients have successfully registered, the following combinations are supported.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Client endpoint 1</th>
<th>Client endpoint 2</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>IPv4</p></td>
<td><p>IPv4</p></td>
</tr>
<tr class="even">
<td><p>IPv4</p></td>
<td><p>Dual stack</p></td>
</tr>
<tr class="odd">
<td><p>Dual stack</p></td>
<td><p>Dual stack</p></td>
</tr>
<tr class="even">
<td><p>IPv6</p></td>
<td><p>Dual stack</p></td>
</tr>
<tr class="odd">
<td><p>IPv6</p></td>
<td><p>IPv6</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Conferencing

Conferencing includes audio/video, application sharing, and data collaboration (whiteboarding and file sharing).


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Client endpoint network</th>
<th>Server network</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>IPv4</p></td>
<td><p>IPv4</p></td>
</tr>
<tr class="even">
<td><p>IPv4</p></td>
<td><p>Dual stack</p></td>
</tr>
<tr class="odd">
<td><p>Dual stack</p></td>
<td><p>IPv4</p></td>
</tr>
<tr class="even">
<td><p>Dual stack</p></td>
<td><p>Dual stack</p></td>
</tr>
<tr class="odd">
<td><p>Dual stack</p></td>
<td><p>IPv6</p></td>
</tr>
<tr class="even">
<td><p>IPv6</p></td>
<td><p>Dual stack</p></td>
</tr>
<tr class="odd">
<td><p>IPv6</p></td>
<td><p>IPv6</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Mediation Server/PSTN

Lync Server 2013 does not support media bypass for public switched telephone network (PSTN) calls if the traffic is through an IPv6 interface. If media bypass is required, we recommend that the PSTN gateway is configured to IPv4.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Primary interface*</th>
<th>PSTN interface (on Mediation Server)</th>
<th>PSTN gateway setting</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>IPv4</p></td>
<td><p>Dual stack</p></td>
<td><p>IPv4</p></td>
</tr>
<tr class="even">
<td><p>Dual stack</p></td>
<td><p>Dual stack</p></td>
<td><p>IPv4</p></td>
</tr>
<tr class="odd">
<td><p>Dual stack</p></td>
<td><p>Dual stack</p></td>
<td><p>IPv6</p></td>
</tr>
</tbody>
</table>


\* The primary interface is the interface that communicates with the Lync Server components.

</div>

<div>

## Remote User Peer-to-Peer Communications

Peer-to-peer communications with remote users include instant messaging, audio/video, application sharing, and file transfer.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Remote user network</th>
<th>Edge server (External edge)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>IPv4</p></td>
<td><p>IPv4</p></td>
</tr>
<tr class="even">
<td><p>Dual stack</p></td>
<td><p>IPv4</p></td>
</tr>
<tr class="odd">
<td><p>Dual stack</p></td>
<td><p>Dual stack</p></td>
</tr>
<tr class="even">
<td><p>IPv6</p></td>
<td><p>Dual stack</p></td>
</tr>
<tr class="odd">
<td><p>IPv6</p></td>
<td><p>IPv6</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Front End Pool and Edge Pool Configuration

The following table shows the support matrix between the Front End Server pool and the internal Edge Server pool.

### Front End Pool and Edge Pool (Internal Edge) Matrix

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<tbody>
<tr class="odd">
<td></td>
<td><p><strong>Edge Pool: IPv4</strong></p></td>
<td><p><strong>Edge Pool: Dual Stack</strong></p></td>
<td><p><strong>Edge Pool: IPv6</strong></p></td>
</tr>
<tr class="even">
<td><p><strong>Front End Pool: IPv4</strong></p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>No</p></td>
</tr>
<tr class="odd">
<td><p><strong>Front End Pool: Dual Stack</strong></p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>No</p></td>
</tr>
<tr class="even">
<td><p><strong>Front End Pool: IPv6</strong></p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>Yes*</p></td>
</tr>
</tbody>
</table>


\* Use this combination only in a lab environment.

The following table is a matrix of the supported combinations of internal and external edge interfaces.

### Edge Pool (Internal Edge) and Edge pool (External Edge) Matrix

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<tbody>
<tr class="odd">
<td></td>
<td><p><strong>Edge Pool (External Edge) : IPv4</strong></p></td>
<td><p><strong>Edge Pool (External Edge): Dual Stack</strong></p></td>
<td><p><strong>Edge Pool (External Edge): IPv6</strong></p></td>
</tr>
<tr class="even">
<td><p><strong>Edge Pool (Internal Edge): IPv4</strong></p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>No</p></td>
</tr>
<tr class="odd">
<td><p><strong>Edge Pool (Internal Edge): Dual Stack</strong></p></td>
<td><p>No</p></td>
<td><p>Yes</p></td>
<td><p>No</p></td>
</tr>
<tr class="even">
<td><p><strong>Edge Pool (Internal Edge): IPv6</strong></p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>Yes*</p></td>
</tr>
</tbody>
</table>


\* Use this combination only in a lab environment.

</div>

<div>

## Advanced Enterprise Voice Support for IPv6

Deployments that include call admission control (CAC), Enhanced 9-1-1 (E9-1-1), or media bypass must be configured as IPv4 only or as a dual-stacked implementation.

<div>


> [!NOTE]  
> In a dual-stacked deployment, even if a Lync client connects to a Lync Server by using IPv6, Lync will make a best effort to map an appropriate IPv4 address to support E9-1-1.



</div>

Location Information service with IPv6 addresses is not supported.

Exchange Unified Messaging (UM) does not support IPv6. For Exchange UM, be sure that DNS resolution does not return an IPv6 address. Using IPv6 may cause failure when calls are sent to voice mail.

</div>

<div>

## Other Lync Server 2013 Feature Support for IPv6

In addition to the features and components mentioned previously, Lync Server 2013 supports IPv6 for the following features:

  - **Persistent Chat**
    
    You configure IPv6 for Persistent Chat by using Topology Builder. For details about configuring Persistent Chat, see the Deploying Persistent Chat Server documentation.

  - **Quality of Experience (QoE) and call detail recording (CDR) reports**
    
    Monitoring reports include the IP address as it is stored in the Monitoring Server database, whether of type IPv4 or IPv6.

</div>

</div>

<span> </span>

</div>

</div>

</div>

