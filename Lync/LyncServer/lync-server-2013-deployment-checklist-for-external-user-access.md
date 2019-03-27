---
title: 'Lync Server 2013: Deployment checklist for external user access'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Deployment checklist for external user access
ms:assetid: 3f55f502-88a0-4315-8783-45a32a0b78ea
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425910(v=OCS.15)
ms:contentKeyID: 48183947
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Deployment checklist for external user access in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-02-04_

Before you deploy your perimeter network and implement support for external users, you must already have deployed your Microsoft Lync Server 2013 internal servers, including a Front End pool or a Standard Edition server. If you plan to deploy the optional Directors in your internal network, you should also deploy them prior to deploying Edge Servers. For details about the Director deployment process, see [Scenarios for the Director in Lync Server 2013](lync-server-2013-scenarios-for-the-director.md) in the Planning documentation.

Microsoft Lync Server 2013 includes tools to facilitate planning and deployment of both internal servers and Edge Servers. After the topology is completed, publish the resulting topology definition to your production environment. To do this, you must be a member of the **Domain Admins** group and the **RTCUniversalServerAdmins** group.

  - **Planning Tool**   Office Communications Server 2007 R2 included a Planning Tool and an Edge Planning Tool that you could use to help guide topology design. In Lync Server 2010, these two tools were combined into a single Planning Tool that has additional features and functionality, such as collecting planned user count, voice requirements, external user access types, and federation options. Additionally, you can plan your infrastructure’s network parameters, such as IP addresses, load balancer types and other perimeter network considerations.

  - **Topology Builder**   Lync Server 2013 Topology Builder helps you define your topology and components. Topology Builder is essential to deploying servers running Lync Server 2013. Topology Builder publishes the results to a Central Management store that is used to configure all of the servers running Lync Server 2013 in your organization. You cannot install Lync Server 2013 on servers without using Topology Builder.

If you designed your edge topology during your planning process, including running Topology Builder to define your edge topology, you can use those results to start your Edge Server deployment. If you did not finish building your edge topology earlier or you want to change the information you previously specified, you must finish running Topology Builder before proceeding with other deployment steps. For details about how to build your topology, see [Scenarios for external user access in Lync Server 2013](lync-server-2013-scenarios-for-external-user-access.md).

For details about the Planning Tool and Topology Builder, see [Beginning the planning process for Lync Server 2013](lync-server-2013-beginning-the-planning-process.md) in the Planning documentation.

The following table provides an overview of the Edge Server deployment process. To review the planning decisions that must be made before deploying external user access, see [Scenarios for external user access in Lync Server 2013](lync-server-2013-scenarios-for-external-user-access.md).

<div>


> [!WARNING]  
> The information in the following table focuses on a new deployment. If you have deployed Edge Servers in a Lync Server 2010, Office Communications Server 2007 R2 or Office Communications Server 2007 environment, see the <A href="migration.md">Migration</A> for details about migrating to Lync Server 2013. Migration is not supported from any version prior to Office Communications Server 2007 R2, including Office Communications Server 2007, Live Communications Server 2005, and Live Communications Server 2003.



</div>

To enhance Edge Server performance and security, and to facilitate deployment, apply the following best practices when you deploy your perimeter network and Edge Servers:

  - Deploy Edge Servers only after you have tested and verified operation of Lync Server 2013 inside your organization.

  - We recommend that you deploy Edge Servers in a workgroup rather than a domain. Doing so simplifies installation and keeps Active Directory Domain Services (AD DS) out of the perimeter network. Locating AD DS in the perimeter network can present a significant security risk.

  - Joining an Edge Server to a domain located entirely in the perimeter network is supported but not recommended. An Edge Server as part of the internal domain violates trusted network boundaries, where the Internet is least trusted, perimeter network is more trusted than the Internet, and the internal network is most trusted. An Edge server as a member of the domain is automatically a part of the most trusted network, but resides in a less trusted network (the perimeter).

<div>

## Deployment Process for Edge Servers


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Phase</th>
<th>Steps</th>
<th>Permissions</th>
<th>Documentation</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Create the appropriate edge topology and determine the appropriate components.</p></td>
<td><ul>
<li><p>Run Topology Builder to configure Edge Server settings and create and publish the topology, and then use Lync Server Management Shell to export the topology configuration file.</p></li>
</ul></td>
<td><p><strong>Domain Admins</strong> group and <strong>RTCUniversalServerAdmins</strong> or <strong>CsAdmins</strong> group</p>
<div>

> [!NOTE]  
> You can define a topology using an account that is a member of the local users group, but publishing a topology requires an account that is a member of the <STRONG>Domain Admins</STRONG> group and the <STRONG>RTCUniversalServerAdmins</STRONG> group.


</div></td>
<td><p><a href="lync-server-2013-building-an-edge-and-director-topology.md">Building an edge and Director topology in Lync Server 2013</a> in the Deployment documentation</p></td>
</tr>
<tr class="even">
<td><p>Prepare for setup.</p></td>
<td><ol>
<li><p>Ensure that system prerequisites are met.</p></li>
<li><p>Configure IP addresses (IPv4 and IPv6, if used) for both internal and public facing network interfaces on each Edge Server.</p></li>
<li><p>Configure internal and external DNS records (host A and AAAA for IPv4 and IPv6), including configuring the DNS suffix on the computer to be deployed as an Edge Server.</p></li>
<li><p>(Optional) Create and install public certificates. The time required to obtain certificates depends on which certification authority (CA) issues the certificate. If you do not perform this step at this point, you must do it during Edge Server installation. The Edge Server services cannot be started until certificates are obtained and installed.</p></li>
<li><p>Provision support for public IM connectivity, if your deployment is to support communications with Windows Live, AOL, or Yahoo! users.</p>
<div>

> [!IMPORTANT]  
> <UL>
> <LI>
> <P>As of September 1st, 2012, the Microsoft Lync Public IM Connectivity User Subscription License (“PIC USL”) is no longer available for purchase for new or renewing agreements. Customers with active licenses will be able to continue to federate with Yahoo! Messenger until the service shut down date. An end of life date of June 2014 for AOL and Yahoo! has been announced. For details, see <A href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Support for public instant messenger connectivity in Lync Server 2013</A>.</P>
> <LI>
> <P>The PIC USL is a per-user per-month subscription license that is required for Lync Server or Office Communications Server to federate with Yahoo! Messenger. Microsoft’s ability to provide this service has been contingent upon support from Yahoo!, the underlying agreement for which is winding down.</P>
> <LI>
> <P>More than ever, Lync is a powerful tool for connecting across organizations and with individuals around the world. Federation with Windows Live Messenger requires no additional user/device licenses beyond the Lync Standard CAL. Skype federation will be added to this list, enabling Lync users to reach hundreds of millions of people with IM and voice.</P></LI></UL>


</div></li>
<li><p>Provision support for XMPP and federation support for Office Communications Server 2007, Office Communications Server 2007 R2, Lync Server 2010 partners, if your deployment will use these</p></li>
<li><p>Configure firewalls.</p></li>
</ol></td>
<td><p>As appropriate to your organization</p></td>
<td><p><a href="lync-server-2013-preparing-for-installation-of-servers-in-the-perimeter-network.md">Preparing for installation of servers in the perimeter network for Lync Server 2013</a> in the Deployment documentation</p></td>
</tr>
<tr class="odd">
<td><p>Set up reverse proxy.</p></td>
<td><ul>
<li><p>Set up the reverse proxy (for example, for Microsoft Forefront Threat Management Gateway 2010 or Microsoft Internet Security and Acceleration (ISA) Server with Service Pack 1) in the perimeter network, obtain the necessary public certificates, and configure the web publishing rules on the reverse proxy server.</p>
<p>Prepare the reverse proxy for Mobility services if you have planned for Mobility and are deploying the Mobility services on the Front End pool or Standard Edition server.</p></li>
</ul></td>
<td><p><strong>Administrators</strong> group or Reverse Proxy administrator</p></td>
<td><p><a href="lync-server-2013-setting-up-reverse-proxy-servers.md">Setting up reverse proxy servers for Lync Server 2013</a> in the Deployment documentation</p></td>
</tr>
<tr class="even">
<td><p>Setup a Director (optional).</p></td>
<td><ul>
<li><p>(Optional) Install and configure one or more Directors in the internal network.</p></li>
</ul></td>
<td><p><strong>Administrators</strong> group</p></td>
<td><p><a href="lync-server-2013-setting-up-the-director.md">Setting up the Director in Lync Server 2013</a> in the Deployment documentation</p></td>
</tr>
<tr class="odd">
<td><p>Set up Edge Servers.</p></td>
<td><ol>
<li><p>Install prerequisite software.</p></li>
<li><p>Transport the exported topology configuration file to each Edge Server.</p></li>
<li><p>Install the Lync Server 2013 software on each Edge Server.</p></li>
<li><p>Configure the Edge Servers.</p></li>
<li><p>Request and install certificates for each Edge Server.</p></li>
<li><p>Start the Edge Server services.</p></li>
</ol></td>
<td><p><strong>Administrators</strong> group</p></td>
<td><p><a href="lync-server-2013-setting-up-edge-servers.md">Setting up Edge Servers in Lync Server 2013</a> in the Deployment documentation</p></td>
</tr>
<tr class="even">
<td><p>Configure deployment for external user access.</p></td>
<td><ol>
<li><p>Use the Lync Server Control Panel to configure support for each of the following (as applicable):</p>
<ul>
<li><p>Media relay</p></li>
<li><p>Federation route</p></li>
<li><p>Remote user access</p></li>
<li><p>Federation with Lync Server, Office Communications Server and Live Communications Server</p></li>
<li><p>Public IM connectivity</p></li>
<li><p>XMPP federation</p></li>
<li><p>Anonymous users</p></li>
</ul></li>
<li><p>Configure user accounts for remote user access, federation, public IM connectivity, XMPP and anonymous user support (as applicable)</p></li>
</ol></td>
<td><p><strong>RTCUniversalServerAdmins</strong> group or user account that is assigned to the <strong>CSAdministrator</strong> role</p></td>
<td><p><a href="lync-server-2013-configuring-support-for-external-user-access.md">Configuring support for external user access in Lync Server 2013</a> in the Deployment documentation</p></td>
</tr>
<tr class="odd">
<td><p>Verify your Edge Server configuration.</p></td>
<td><ol>
<li><p>Verify server connectivity and replication of configuration data from internal servers.</p></li>
<li><p>Verify that external users can connect, including remote users, users in federated domains, public IM users, and anonymous users, as appropriate to your deployment.</p></li>
<li><p>Verify configuration and communication using the Lync Server Remote Connectivity Analyzer <a href="https://www.testocsconnectivity.com" class="uri">https://www.testocsconnectivity.com</a></p></li>
<li><p>Troubleshoot configuration and communication difficulties</p></li>
</ol></td>
<td><p>For verification of replication, <strong>RTCUniversalServerAdmins</strong> group or user account that is assigned to the <strong>CSAdministrator</strong> role</p>
<p>For verification of user connectivity, a user for each type of external user access that you support</p>
<p>Remote users</p></td>
<td><p><a href="lync-server-2013-verifying-your-edge-deployment.md">Verifying your edge deployment in Lync Server 2013</a> in the Deployment documentation</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

