---
title: 'Configuring SIP federation, XMPP federation and public instant messaging'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configuring SIP federation, XMPP federation and public instant messaging
ms:assetid: a6d04f0b-5cb8-4084-a3a2-d501938971f9
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205134(v=OCS.15)
ms:contentKeyID: 48184998
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring SIP federation, XMPP federation and public instant messaging in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-10-07_

Federation, public instant messaging connectivity and Extensible Messaging and Presence Protocol (XMPP) define a different class of external users – Federated users. Users of a federated Lync Server deployment or XMPP deployment have access to a limited set of services and are authenticated by the external deployment. Remote users are members of your Lync Server deployment and have access to all services offered by your deployment.

<div>


> [!NOTE]
> An end of life date of June 2014 for AOL and Yahoo! has been announced. For details, see <A href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Support for public instant messenger connectivity in Lync Server 2013</A>.



</div>

Public instant messaging connectivity is a special type of federation that allows a Lync Server client to access configured public Instant Messaging partners using the Lync 2013. The current public instant messaging connectivity partners are:

  - <span></span>  
    America Online

  - <span></span>  
    Windows Live

  - <span></span>  
    Yahoo\!

A public instant messaging connectivity configuration allows Lync users access to public instant messaging connectivity users by:

  - IM and Presence

  - Visibility of public instant messaging connectivity contacts in Lync client

  - Person to person IM conversations with contacts

  - Audio and video calls with Windows Live users

Lync Server federation defines an agreement between your Lync Server deployment and other Office Communications Server 2007 R2 or Lync Server deployments. A Lync Server federated configuration allows Lync users access to federated users by:

  - IM and Presence

  - Creation of federated contacts in the Lync client

XMPP federation defines an external deployment based on the eXtensible Messaging and Presence Protocol. An XMPP configuration allows Lync users access to allowed XMPP domain users by:

  - IM and Presence – person to person only

  - Creation of XMPP federated contacts in the Lync client

<div>


> [!IMPORTANT]
> The XMPP capability of Lync Server 2013 is tested and supported by Microsoft for instant messaging federation with Google Talk. For any other XMPP systems contact the third-party vendor to verify that they support federation with Lync Server 2013, and for any deployment or troubleshooting recommendations.



</div>

<div>

## Edge Server External Federation, Public Instant Messaging Connectivity and XMPP Users Deployment Process


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
<td><p>Determine the options to add to the existing Edge deployment</p></td>
<td><p>Run Topology Builder to edit Edge Server settings and create and publish the topology. Your existing Edge topology will replicate changes from the Central Management store to the Edge Server.</p></td>
<td><p>Domain Admins group and RTCUniversalServerAdmins group</p>



> [!NOTE]
> You can edit a topology using an account that is a member of the local users group, but publishing a topology requires an account that is a member of the Domain Admins group and the RTCUniversalServerAdmins group

</td>
<td><p><a href="lync-server-2013-building-an-edge-and-director-topology.md">Building an edge and Director topology in Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>Prepare for setup</p></td>
<td><ol>
<li><p>Ensure that system prerequisites are met.</p></li>
<li><p>Configure internal and external DNS records, to support public instant messaging connectivity, Lync Federation and XMPP Federation</p></li>
<li><p>Configure ports and protocols at the firewall to support the types of federation that you are deploying</p></li>
<li><p>Obtain and install public certificates. The time required to obtain certificates depends on which certification authority (CA) issues the certificate. This step is optional at this point in the deployment. If you do not perform this step at this point, you must do it during Edge Server configuration. The Edge Server service cannot be started until certificates are obtained</p></li>
</ol></td>
<td><p>As appropriate to your organization, as these roles are typically split amongst numerous work groups</p></td>
<td><p><a href="lync-server-2013-planning-for-sip-xmpp-federation-and-public-instant-messaging.md">Planning for SIP, XMPP federation, and public instant messaging in Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p>Set up Edge Servers for Federation Scenarios</p></td>
<td><ol>
<li><p>Transport the exported topology configuration file to each Edge Server or allow replication to complete</p></li>
<li><p>Re-Run the Deployment Wizard to install supporting components for Federation</p></li>
<li><p>Configure the Edge Servers</p></li>
<li><p>Request and install certificates for each Edge Server</p></li>
<li><p>Restart the Edge Server services</p></li>
</ol></td>
<td><p>Administrators group</p></td>
<td><p><a href="lync-server-2013-setting-up-lync-federation.md">Setting up Lync federation in Lync Server 2013</a></p>
<p><a href="lync-server-2013-setting-up-public-instant-messaging-connectivity.md">Setting up public instant messaging connectivity in Lync Server 2013</a></p>
<p><a href="lync-server-2013-setting-up-xmpp-federation.md">Setting up XMPP federation in Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>Configure support for external user access.</p></td>
<td><ol>
<li><p>Use the Lync Server Control Panel External User Access</p></li>
<li><p>Configure External Access Policy to enable Communications with federated users or public users</p></li>
<li><p>Configure SIP Federated Domains to Allow or Block domains</p></li>
<li><p>Enable SIP Federated Providers for public instant messaging connectivity providers</p></li>
<li><p>Configure XMPP Federated Partners per XMPP domain</p></li>
</ol></td>
<td><p>RTCUniversalServerAdmins group or user account that is assigned to the CSAdministrator role</p></td>
<td><p><a href="lync-server-2013-configuring-support-for-external-user-access.md">Configuring support for external user access in Lync Server 2013</a></p>
<p><a href="lync-server-2013-configure-media-encryption-for-public-providers.md">Configure media encryption for public providers in Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p>Verify your Edge Server configuration</p></td>
<td><p>Verify server connectivity and replication of configuration data from internal servers</p></td>
<td><p>For verification of replication, RTCUniversalServerAdmins group or user account that is assigned to the CSAdministrator roleFor verification of user connectivity, a user for each type of Federated user</p></td>
<td><p><a href="lync-server-2013-verifying-your-edge-deployment.md">Verifying your edge deployment in Lync Server 2013</a></p>
<p><a href="lync-server-2013-example-xmpp-configuration-–-xmpp-federation-with-google-talk.md">Example XMPP configuration in Lync Server 2013 – XMPP federation with Google Talk</a></p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

