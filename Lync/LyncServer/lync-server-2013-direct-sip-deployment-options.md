---
title: 'Lync Server 2013: Direct SIP deployment options'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Direct SIP deployment options
ms:assetid: 84691944-03f2-4a89-9f2b-1ab3d7f388cc
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398672(v=OCS.15)
ms:contentKeyID: 48184692
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Direct SIP deployment options in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-21_

This topic provides example topologies for deploying direct SIP connections.

<div id="sectionSection0" class="section">

<span id="BKMK_CommunicationsServerStand_Alone"></span>

<div>

## Lync Server Stand-Alone

If your organization uses one of the deployments described in this section, you can use Lync Server 2013 as the sole telephony solution for part or all of an organization. This section describes the following deployments in detail:

  - **Incremental deployment:** This option assumes that you have an existing private branch exchange (PBX) infrastructure and you intend to introduce Enterprise Voice incrementally to smaller groups or teams within your organization.

  - **Lync Server VoIP-only deployment:** this option assumes that you are considering deploying Enterprise Voice at a site that does not have a traditional telephony infrastructure.

<div>

## Incremental Deployment

In incremental deployment, Lync Server 2013 is the sole telephony solution for individual teams or departments, while the rest of the users in an organization continue to use a PBX. This incremental deployment strategy provides one way to introduce IP telephony into your enterprise through controlled pilot programs. Workgroups whose communication needs are best served by Microsoft Unified Communications are moved to Enterprise Voice, while other users remain on the existing PBX. Additional workgroups can be migrated to Enterprise Voice, as needed.

The incremental option is recommended if you have clearly defined user groups that have communication requirements in common and that lend themselves to centralized management. This option is also effective if you have teams or departments that are spread over wide geographic areas, where the savings in long-distance charges can be significant. In fact, this option is useful for creating virtual teams whose members may be scattered across the globe. You can create, modify, or disband such teams in rapid response to shifting business requirements.

The following figure shows the generic topology for deployment of Enterprise Voice behind a PBX. This is the recommended topology for incremental deployment.

**Incremental deployment option**

![Departmental Migration Option diagram](images/Gg398672.e951ecf4-7cd2-425a-9106-76977492d682(OCS.15).jpg "Departmental Migration Option diagram")

<div>


> [!NOTE]  
> If you are connecting your Lync Server deployment to a certified Direct SIP partner, a public switched telephone network (PSTN) gateway between the Mediation Server and the PBX is not required. For a list of certified Direct SIP partners, see the Microsoft Unified Communications Open Interoperability Program website at <A href="http://go.microsoft.com/fwlink/p/?linkid=203309">http://go.microsoft.com/fwlink/p/?linkId=203309</A>.



</div>

<div>


> [!NOTE]  
> The media path shown in this figure has media bypass enabled (the recommended configuration). If you opt to disable media bypass, the media path is routed through the Mediation Server.



</div>

In this topology, selected departments or workgroups are enabled for Enterprise Voice. A PSTN gateway links the Voice over Internet Protocol (VoIP)-enabled workgroup to the PBX. Users who are enabled for Enterprise Voice, including remote workers, communicate across the IP network. Calls by Enterprise Voice users to the PSTN and to coworkers who are not enabled for Enterprise Voice are routed to the appropriate PSTN gateway. Calls from colleagues who are still on the PBX system, or from callers on the PSTN, are routed to the PSTN gateway, which forwards the calls to Lync Server for routing.

There are two recommended configurations for connecting Enterprise Voice to an existing PBX infrastructure for interoperability: Enterprise Voice behind the PBX and Enterprise Voice in front of the PBX.

<div>

## Enterprise Voice Behind the PBX

When Enterprise Voice is deployed behind the PBX, all calls from the PSTN arrive at the PBX, which routes calls to Enterprise Voice users to a PSTN gateway, and calls to PBX users to the PBX.

</div>

<div>

## Enterprise Voice in Front of the PBX

When Enterprise Voice is deployed in front of the PBX, all calls arrive at the PSTN gateway, which routes calls for Enterprise Voice users to Lync Server and calls for PBX users to the PBX. Calls to the PSTN from both Enterprise Voice and PBX users are routed over the IP network to the most cost-efficient PSTN gateway. The following table shows the advantages and disadvantages of this configuration.

### Advantages and Disadvantages of Deploying Enterprise Voice in Front of PBX

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Advantages</th>
<th>Disadvantages</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>PBX still serves users not enabled for Enterprise Voice.</p></td>
<td><p>Existing gateways may not support the features or capacity that you want.</p></td>
</tr>
<tr class="even">
<td><p>PBX handles all earlier devices.</p></td>
<td><p>Requires a trunk from gateway to the PBX and from the gateway to the Mediation Server. You may need more trunks from the service provider.</p></td>
</tr>
<tr class="odd">
<td><p>Enterprise Voice users keep the same phone numbers.</p></td>
<td><p> </p></td>
</tr>
</tbody>
</table>


</div>

</div>

<div>

## Lync Server VoIP-Only Deployment

Enterprise Voice provides new businesses, and also new office sites for existing businesses, with the opportunity to implement a full-featured VoIP solution without having to worry about PBX integration or incurring the substantial deployment and maintenance costs of an IP-PBX infrastructure. This solution supports both on-site and remote workers.

In this deployment, all calls are routed over the IP network. Calls to the PSTN are routed to the appropriate PSTN gateway. Lync 2013 or Lync Phone Edition serves as a softphone. Remote call control is unavailable and unnecessary because there are no PBX phones for users to control. Voice mail and auto-attendant services are available through the optional deployment of Exchange Unified Messaging (UM).

<div>


> [!NOTE]  
> In addition to the network infrastructure that is required to support Lync Server 2013, a VoIP-only deployment can use a small, qualified gateway to support fax machines and analog devices.



</div>

The following figure shows a typical topology for a VoIP-only deployment.

**VoIP-only deployment option**

![Greenfidle deployment option](images/Gg398672.820dc5fe-0e20-431b-ae4e-fefdf2221d3b(OCS.15).jpg "Greenfidle deployment option")

<div>


> [!NOTE]  
> The media path shown in this figure has media bypass enabled (the recommended configuration). If you opt to disable media bypass, the media path is routed through the Mediation Server.



</div>

</div>

</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

