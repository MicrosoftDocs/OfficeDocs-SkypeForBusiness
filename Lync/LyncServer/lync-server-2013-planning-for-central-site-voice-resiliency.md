---
title: 'Lync Server 2013: Planning for central site voice resiliency'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Planning for central site voice resiliency
ms:assetid: 52dd0c3e-cd3c-44cf-bef5-8c49ff5e4c7a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398347(v=OCS.15)
ms:contentKeyID: 48184164
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Planning for central site voice resiliency in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-10-30_

Increasingly, enterprises have multiple sites spread across the globe. Maintaining emergency services, access to help desk, and the ability to conduct critical business tasks when a central site is out of service is essential for any Enterprise Voice resiliency solution. When a central site becomes unavailable, the following conditions must be met:

  - Voice failover must be provided.

  - Users who ordinarily register with the Front End pool at the central site must be able to register with an alternative Front End pool. This can be done by creating multiple DNS SRV records, each of which resolves to a Director pool or Front End pool in each of your central sites. You can adjust the priority and weights of the SRV records so that users who are served by that central site get the corresponding Director and Front End pool ahead of those in other SRV records.

  - Calls to and from users located at other sites must be rerouted to the PSTN.

This topic describes the recommended solution for securing central site voice resiliency.

<div>

## Architecture and Topology

Planning for voice resiliency at a central site requires a basic understanding of the central role played by the Lync Server 2013 Registrar in enabling voice failover. The Lync Server Registrar is a server role that enables client registration and authentication and provides routing services. It resides along with other components on a Standard Edition server, Front End Server, Director, or Survivable Branch Appliance. A Registrar pool consists of Registrar Services running on the Front End pool and residing at the same site. The Front End pool must be load balanced. DNS load balancing is recommended, but hardware load balancing is acceptable. A Lync client discovers the Front End pool through the following discovery mechanism:

1.  DNS SRV record

2.  Autodiscovery Web Service (new in Lync Server 2013)

3.  DHCP option 120

After the Lync client connects to the Front End pool, it is directed by the load balancer to one of the Front End Servers in the pool. That Front End Server, in turn, redirects the client to a preferred Registrar in the pool.

Each user enabled for Enterprise Voice is assigned to a particular Registrar pool, which becomes that user’s primary Registrar pool. At a given site, hundreds or thousands of users typically share a single primary Registrar pool. To account for the consumption of central site resources by any branch site users that rely on the central site for presence, conferencing, or failover, we recommend that you consider each branch site user as though the user were a user registered with the central site. There are currently no limits on the number of branch site users, including users registered with a Survivable Branch Appliance.

To assure voice resiliency in the event of a central site failure, the primary Registrar pool must have a single designated backup Registrar pool located at another site. The backup can be configured by using Topology Builder resiliency settings. Assuming a resilient WAN link between the two sites, users whose primary Registrar pool is no longer available are automatically directed to the backup Registrar pool.

The following steps describe the client discovery and registration process:

1.  A client discovers Lync Server through DNS SRV records. In Lync Server 2013, DNS SRV records can be configured to return more than one FQDN to the DNS SRV query. For example, if enterprise Contoso has three central sites (North America, Europe, and Asia-Pacific) and a Director pool at each central site, DNS SRV records can point to the Director pool FQDNs in each of the three locations. As long as the Director pool in one of the locations is available, the client can connect to the first hop Lync Server.
    
    <div>
    

    > [!NOTE]  
    > Using a Director pool is optional. A Front End pool can be used instead.

    
    </div>

2.  The Director pool informs the Lync client about the user’s primary Registrar pool and backup Registrar pool.

3.  The Lync client attempts to connect to the user’s primary Registrar pool first. If the primary Registrar pool is available, the Registrar accepts the registration. If the primary Registrar pool is unavailable, the Lync client attempts to connect to the backup Registrar pool. If the backup Registrar pool is available and has determined that the user’s primary Registrar pool is unavailable (by detecting a lack of heartbeat for a specified failover interval) the backup Registrar pool accepts the user’s registration. After the backup Registrar detects that the primary Registrar is again available, the backup Registrar pool will redirect failover Lync clients to their primary pool.

The following figure shows the recommended topology for assuring central site resiliency. The two sites are connected by a resilient WAN link. If the central site becomes unavailable, users who are assigned to that pool are directed to the backup site for registration.

**Recommended topology for central site voice resiliency**

![Topology for central site voice resliency](images/Gg398347.19ea3e74-8a5c-488c-a34e-fc180ab9a50a(OCS.15).jpg "Topology for central site voice resliency")

</div>

<div>

## Requirements and Recommendations

The following requirements and recommendations for implementing central site voice resiliency are appropriate for most organizations:

  - The sites in which the primary and backup Registrar pools reside should be connected by a resilient WAN link.

  - Each central site must contain a Registrar pool consisting of one or more Registrars.

  - Each Registrar pool must be load-balanced by using DNS load balancing, hardware load balancing, or both. For detailed information about planning your load balancing configuration, see [Load balancing requirements for Lync Server 2013](lync-server-2013-load-balancing-requirements.md).

  - Each user must be assigned to a primary Registrar pool by using either the Lync Server Management Shell **set-CsUser** cmdlet or the Lync Server Control Panel.

  - The primary Registrar pool must have a single backup Registrar pool located in a different central site.

  - The primary Registrar pool must be configured to fail over to the backup Registrar pool. By default, the primary Registrar is set to fail over to the backup Registrar pool after an interval of 300 seconds. You can change this interval by using the Lync Server 2013 Topology Builder.

  - Configure a failover route, as described in the “[Configuring a failover route in Lync Server 2013](lync-server-2013-configuring-a-failover-route.md)” topic in the Planning documentation. When configuring the route, specify a gateway that is located at a different site from the gateway specified in the primary route.

  - If the central site contained your primary management server and the site is likely to be down for an extended period, you will need to reinstall your management tools at the backup site; otherwise, you won’t be able to change any management settings.

</div>

<div>

## Dependencies

Lync Server depends on the following infrastructure and software components to assure voice resiliency:


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Component</strong></p></td>
<td><p><strong>Functional</strong></p></td>
</tr>
<tr class="even">
<td><p>DNS</p></td>
<td><p>Resolving SRV records and A records for server-server and server-client connectivity</p></td>
</tr>
<tr class="odd">
<td><p>Exchange and Exchange Web Services (EWS)</p></td>
<td><p>Contact storage; calendar data</p></td>
</tr>
<tr class="even">
<td><p>Exchange Unified Messaging and Exchange Web Services</p></td>
<td><p>Call logs, voice mail list, voice mail</p></td>
</tr>
<tr class="odd">
<td><p>DHCP Options 120</p></td>
<td><p>If DNS SRV is unavailable, the client will attempt to use DHCP Option 120 to discover the Registrar. For this to work, either a DHCP server must be configured or Lync Server 2013 DHCP must be enabled. For details, see Hardware and Software Requirements for Branch-Site Resiliency in <a href="lync-server-2013-branch-site-resiliency-requirements.md">Branch-site resiliency requirements for Lync Server 2013</a> section.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Survivable Voice Features

If the preceding requirements and recommendations have been implemented, the following voice features will be provided by the backup Registrar pool:

  - Outbound PSTN calls

  - Inbound PSTN calls, if the telephony service provider supports the ability to fail over to a backup site

  - Enterprise calls between users at both the same site and between two different sites

  - Basic call handling, including call hold, retrieval, and transfer

  - Two-party instant messaging and sharing audio and video between users at the same site

  - Call forwarding, simultaneous ringing of endpoints, call delegation, and team call services, but only if both parties to call delegation, or all team members, are configured at the same site.

  - Existing phones and clients continue to work.

  - Call detail recording (CDR)

  - Authentication and authorization

Depending on how they are configured, the following voice features may or may not work when a primary central site is out of service:

  - Voice mail deposit and retrieval
    
    If you want to make Exchange UM available when the primary central site is out of service, you must do one of the following:
    
      - Change DNS SRV records so that the Exchange UM servers at the central site point to backup Exchange UM servers at another site.
    
      - Configure each user’s Exchange UM dial plan to include Exchange UM servers at both the central site and the backup site, but designate the backup Exchange UM servers as disabled. If the primary site becomes unavailable, the Exchange administrator has to mark the Exchange UM servers at the backup site as enabled.
    
    If neither of the preceding solutions is possible, then Exchange UM will not be available in the event the central site becomes unavailable.

  - Conferencing of all types
    
    A user who has failed over to a backup site can join a conference that is created or hosted by an organizer whose pool is available but cannot create or host a conference on his or her own primary pool, which is no longer available. Similarly, others users cannot join conferences that are hosted on the affected user’s primary pool.

The following voice features do not work when a primary central site is out of service:

  - Conference Auto-Attendant

  - Presence and DND-based routing

  - Updating call forwarding settings

  - Response Group service and Call Park

  - Provisioning new phones and clients

  - Address Book Web Search

</div>

<div>

## See Also


[Planning for branch-site voice resiliency in Lync Server 2013](lync-server-2013-planning-for-branch-site-voice-resiliency.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

