---
title: 'Lync Server 2013: Deployment checklist for Persistent Chat Server'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Deployment checklist for Persistent Chat Server
ms:assetid: b1108f8f-88a2-4660-8086-d25ba76f7239
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412851(v=OCS.15)
ms:contentKeyID: 48185155
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Deployment checklist for Persistent Chat Server in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-16_

Deployment of Lync Server 2013, Persistent Chat Server requires that you deploy it in the correct sequence and that you complete all required deployment steps.

<div>

## Deployment Sequence

You can deploy Persistent Chat Server after you deploy your initial topology, including at least one Lync Server 2013, Front End pool or one Lync Server 2013, Standard Edition server. This topic describes how to deploy Persistent Chat Server by adding it to an existing deployment.

</div>

<div>

## Deployment Process

The following table lists the basic steps to deploy Persistent Chat Server and provides links for more details.

### Persistent Chat Server Deployment Process

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Task</th>
<th>Steps</th>
<th>Required roles and group memberships</th>
<th>Related topics</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Install prerequisite hardware and software</strong></p></td>
<td><p>On hardware that meets system requirements, install the following:</p>
<ul>
<li><p>On the Persistent Chat Server Front End Servers:</p></li>
</ul>
<ul>
<li><p>An operating system that meets system requirements</p></li>
<li><p>Software prerequisites for computers running Lync Server 2013</p></li>
<li><p>SQL Server on the server that will host Persistent Chat Server database</p></li>
</ul>
<p>If Persistent Chat Server compliance is required:</p>
<ul>
<li><p>SQL Server on the server that will host Persistent Chat Server compliance database</p></li>
</ul></td>
<td><p>Any user who is a member of the local Administrators group.</p></td>
<td><p><a href="lync-server-2013-supported-hardware.md">Supported hardware for Lync Server 2013</a> in the Supportability documentation</p>
<p><a href="lync-server-2013-server-software-and-infrastructure-support.md">Server software and infrastructure support in Lync Server 2013</a> in the Supportability documentation</p>
<p><a href="lync-server-2013-determining-your-system-requirements.md">Determining your system requirements for Lync Server 2013</a></p>
<p><a href="lync-server-2013-technical-requirements-for-persistent-chat-server.md">Technical requirements for Persistent Chat Server in Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p><strong>Create the appropriate internal topology to support Persistent Chat Server (and optionally, Persistent Chat compliance)</strong></p></td>
<td><p>Run Topology Builder to add a Persistent Chat Server pool to your topology:</p>
<ul>
<li><p>Add Persistent Chat Server components to the topology</p></li>
<li><p>Create a SQL Server database for the Persistent Chat Server store (and a backup SQL Server for disaster recovery)</p></li>
<li><p>Define a new Lync File Store or use an existing Lync File Store for Persistent Chat Server files</p></li>
<li><p>Associate the Lync Server 2013 pool that can route requests to this Persistent Chat Server pool</p></li>
</ul>
<p>If Persistent Chat compliance is required:</p>
<ul>
<li><p>Add Persistent Chat Compliance Store</p></li>
<li><p>Click the Persistent Chat Server pool definition check box for enabling compliance</p></li>
<li><p>Publish the topology</p></li>
</ul>
<p>If you install Persistent Chat Server on Standard Edition, the fully qualified domain name (FQDN) of the Persistent Chat Server pool must match the Standard Edition server, and the SQL Server databases are collocated on the SQL Server Express instance on the Standard Edition server</p></td>
<td><p>To define a topology, an account that is a member of the local Users group.</p>
<p>To publish the topology, an account that is a member of the Domain Admins group and RTCUniversalServerAdmins group, and the user should also have full control permissions (read/write/modify) on the Lync File Store for Persistent Chat Server files (so that Topology Builder can configure the required DACLs).</p></td>
<td><p><a href="lync-server-2013-adding-persistent-chat-server-to-your-deployment.md">Adding Persistent Chat Server to your deployment in Lync Server 2013</a> in the Deployment documentation</p></td>
</tr>
<tr class="odd">
<td><p><strong>Deploy Persistent Chat Server</strong></p></td>
<td><p>Run the Lync Server setup on all the computers running Persistent Chat Server. The Persistent Chat Server setup is integrated into the Lync Server 2013 Deployment wizard that provides the following instructions:</p>
<ul>
<li><p>Deploy local management store</p></li>
<li><p>Install Persistent Chat Server services</p></li>
<li><p>Request and assign certificates</p></li>
<li><p>Run and start the services</p></li>
</ul></td>
<td><p>Any user who is a member of the local Administrators group.</p></td>
<td><p><a href="lync-server-2013-deploying-persistent-chat-server.md">Deploying Persistent Chat Server in Lync Server 2013</a> in the Deployment documentation</p></td>
</tr>
<tr class="even">
<td><p><strong>Create a Persistent Chat administrator</strong></p></td>
<td><p>Add users to the CsPersistentChatAdministrator security group.</p></td>
<td><p>Any user who is a member of domain administrators.</p></td>
<td><p><a href="lync-server-2013-adding-a-persistent-chat-administrator.md">Adding a Persistent Chat administrator in Lync Server 2013</a> in the Deployment documentation</p></td>
</tr>
<tr class="odd">
<td><p><strong>Configure Persistent Chat Server</strong></p></td>
<td><p>Configure users:</p>
<ul>
<li><p>User has to be enabled by policy to access Persistent Chat Server. By default, the policy is turned off for all users and can be defined at global/site/pool/user scopes.</p></li>
<li><p>Configure settings</p></li>
</ul></td>
<td><p>User must be a member of CsPersistentChatAdministrator. To change policy, user must be in CsUserAdministrator, at a minimum.</p></td>
<td><p><a href="lync-server-2013-configuring-persistent-chat-server.md">Configuring Persistent Chat Server in Lync Server 2013</a> in the Deployment documentation</p></td>
</tr>
</tbody>
</table>


<div>


> [!IMPORTANT]  
> You can deploy one or more Persistent Chat Server pools. We support multiple Persistent Chat Server pools for regulatory reasons whereby data generated in a given region is required to stay in that region. For example, if you deploy a Persistent Chat Server pool in Chicago, and another in Zurich to comply with regulations for data in Switzerland, users can connect to rooms in both the Persistent Chat Server pools, provided they have access.



</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

