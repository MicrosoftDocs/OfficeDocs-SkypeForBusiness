---
title: 'Deployment process for integrating on-premises Unified Messaging'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Deployment process for integrating on-premises Unified Messaging and Lync Server
ms:assetid: 269a4436-f09f-415b-96ab-49a64370a385
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425737(v=OCS.15)
ms:contentKeyID: 48183664
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Deployment process for integrating on-premises Unified Messaging and Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-12-17_

If you want to integrate Exchange Unified Messaging (UM) with Lync Server 2013, you must perform the tasks described in this topic. Also be sure that you review the planning and deployment best practices described in [Guidelines for integrating on-premises Unified Messaging and Lync Server 2013](lync-server-2013-guidelines-for-integrating-on-premises-unified-messaging.md). This topic assumes that you have deployed Lync Server 2013 with a collocated Mediation Server and that you have enabled users for Lync Server 2013, but not necessarily that you have performed all deployment and configuration steps to enable Enterprise Voice, as described in [Deploying Enterprise Voice in Lync Server 2013](lync-server-2013-deploying-enterprise-voice.md) in the Deployment documentation.

<div>

## Unified Messaging Integration Process

<div>


> [!IMPORTANT]
> It is important that you coordinate with your organization’s Exchange administrators to confirm the tasks that each of you will perform to help ensure a smooth, successful integration.



</div>


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
<th>Required groups and roles</th>
<th>Deployment documentation</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Deploy one of the following:</p>
<ul>
<li><p>Microsoft Exchange Server 2007 Service Pack 1 (SP2) or latest service pack</p></li>
<li><p>Microsoft Exchange Server 2010 or latest service pack</p></li>
<li><p>Microsoft Exchange Server 2013</p></li>
</ul></td>
<td><p>If you are using Microsoft Exchange Server 2013, install the following Exchange Server roles in either the same forest or a different forest as Lync Server 2013:</p>
<ul>
<li><p>Client Access</p></li>
<li><p>Mailbox</p></li>
</ul>
<p>If Microsoft Exchange Server 2013 and Exchange Unified Messaging (UM) are installed in different forests, configure each Exchange forest to trust the Lync Server 2013 forest.</p>
<p>If you are using Exchange 2010, install the following Exchange Server roles in either the same forest or a different forest as Lync Server 2013:</p>
<ul>
<li><p>Unified Messaging</p></li>
<li><p>Hub Transport</p></li>
<li><p>Client Access</p></li>
<li><p>Mailbox</p></li>
</ul>
<p>If Lync Server 2013 and Exchange Unified Messaging (UM) are installed in different forests, configure each Exchange forest to trust the Lync Server 2013 forest.</p></td>
<td><p>Enterprise administrators (if this is the first Exchange Server in the organization)</p>
<p>-OR-</p>
<p>Exchange Organization administrator (if this is not the first Exchange Server in the organization)</p></td>
<td><p>See the appropriate documentation for your version of Exchange Server:</p>
<dl>
<dt><span></span></dt>
<dd><p>Exchange Server 2007 deployment documentation at <a href="http://go.microsoft.com/fwlink/p/?linkid=268694">http://go.microsoft.com/fwlink/p/?LinkId=268694</a>.</p>
</dd>
<dt><span></span></dt>
<dd><p>Exchange Server 2010 or latest service pack deployment documentation at <a href="http://go.microsoft.com/fwlink/p/?linkid=268695">http://go.microsoft.com/fwlink/p/?LinkId=268695</a>.</p>
</dd>
<dt><span></span></dt>
<dd><p>Microsoft Exchange Server 2013 Planning and Deployment at <a href="http://go.microsoft.com/fwlink/p/?linkid=266569">http://go.microsoft.com/fwlink/p/?LinkId=266569</a>.</p>
</dd>
</dl></td>
</tr>
<tr class="even">
<td><p>Install certificates.</p></td>
<td><p>Download and install certificates for each Exchange UM server from a trusted root certificate authority (CA). The certificates are required for mutual Transport Level Security (MTLS) between the servers running Exchange UM and Lync Server 2013.</p></td>
<td><p>Administrators</p></td>
<td><p><a href="lync-server-2013-configure-certificates-on-the-server-running-microsoft-exchange-server-unified-messaging.md">Configure certificates on the server running Microsoft Exchange Server Unified Messaging</a></p></td>
</tr>
<tr class="odd">
<td><p>Create and configure a new Exchange UM SIP dial plan.</p></td>
<td><p>On the Exchange UM server, create a SIP dial plan based on your organization’s specific deployment requirements.</p></td>
<td><p>Exchange Organization administrator</p></td>
<td><p>For Exchange 2007 SP1 or latest service pack, see &quot;How to Create a Unified Messaging SIP URI Dial Plan&quot; at <a href="http://go.microsoft.com/fwlink/p/?linkid=268632">http://go.microsoft.com/fwlink/p/?linkId=268632</a>.</p>
<p>For Exchange 2010 or latest service pack, see &quot;Create a UM Dial Plan&quot; at <a href="http://go.microsoft.com/fwlink/p/?linkid=268674">http://go.microsoft.com/fwlink/p/?linkId=268674</a>.</p>
<p>For Exchange 2013, see Unified Messaging at <a href="http://go.microsoft.com/fwlink/p/?linkid=266579">http://go.microsoft.com/fwlink/p/?LinkId=266579</a>.</p></td>
</tr>
<tr class="even">
<td><p>Configure security settings for the Exchange UM SIP dial plan.</p></td>
<td><p>To encrypt Enterprise Voice traffic, configure the security settings on the Exchange UM SIP dial plan as <strong>SIP Secured</strong> or <strong>Secured</strong>. This is an especially important step if you have deployed or plan to deploy Lync Phone Edition devices in your environment. For Lync Phone Edition devices to function in an environment with Exchange UM integration, Lync Server encryption settings must align with the Exchange UM dial plan security settings. For details, refer to the Deployment documentation.</p></td>
<td><p>Exchange Organization administrator</p></td>
<td><p><a href="lync-server-2013-configure-unified-messaging-on-microsoft-exchange.md">Configure Unified Messaging on Microsoft Exchange for Lync Server 2013</a></p>
<p>For Exchange 2007 SP1 or latest service pack, see also:</p>
<p>&quot;How to Configure Security on a Unified Messaging Dial Plan&quot; at <a href="http://go.microsoft.com/fwlink/p/?linkid=268696">http://go.microsoft.com/fwlink/p/?LinkId=268696</a>.</p>
<p>For Exchange 2010 or latest service pack, see also:</p>
<p>&quot;Configure VoIP Security on a UM Dial Plan&quot; <a href="http://go.microsoft.com/fwlink/p/?linkid=268697">http://go.microsoft.com/fwlink/p/?LinkId=268697</a>.</p>
<p>For Exchange 2013, see Unified Messaging at <a href="http://go.microsoft.com/fwlink/p/?linkid=266579">http://go.microsoft.com/fwlink/p/?LinkId=266579</a>.</p></td>
</tr>
<tr class="odd">
<td><p>Add Unified Messaging servers to the Exchange UM SIP dial plan.</p></td>
<td><p>To enable a newly installed Unified Messaging server to answer and process incoming calls, you must add the Unified Messaging server to a UM dial plan. In this case, add the server to the Exchange UM SIP dial plan.</p></td>
<td><p>Administrators</p>
<p>Exchange Server administrators</p></td>
<td><p>For Exchange 2007 SP1 or latest service pack, see &quot;How to Add Unified Messaging Server to a Dial Plan&quot; at <a href="http://go.microsoft.com/fwlink/p/?linkid=268681">http://go.microsoft.com/fwlink/p/?linkId=268681</a>.</p>
<p>For Exchange 2010 or latest service pack, see &quot;View or Configure the Properties of a UM Server&quot; at <a href="http://go.microsoft.com/fwlink/p/?linkid=268682">http://go.microsoft.com/fwlink/p/?linkId=268682</a>.</p>
<p>For Exchange 2013, see Unified Messaging at <a href="http://go.microsoft.com/fwlink/p/?linkid=266579">http://go.microsoft.com/fwlink/p/?LinkId=266579</a>.</p></td>
</tr>
<tr class="even">
<td><p>Configure mailboxes with SIP addresses.</p></td>
<td><p>Assign SIP addresses to the mailboxes of Enterprise Voice users who will be using Exchange UM features.</p></td>
<td><p>Lync Server 2013 administrator</p>
<p>Exchange Recipient administrator</p></td>
<td><p>For Exchange 2007 SP1 or latest service pack, see &quot;How to Add, Remove, or Modify a SIP Address for a UM-Enabled User&quot; at <a href="http://go.microsoft.com/fwlink/p/?linkid=268698">http://go.microsoft.com/fwlink/p/?LinkId=268698</a>.</p>
<p>For Exchange 2010 or latest service pack, see &quot;Modify a SIP Address for a UM-Enabled User&quot; at <a href="http://go.microsoft.com/fwlink/p/?linkid=268699">http://go.microsoft.com/fwlink/p/?LinkId=268699</a>.</p>
<p>For Exchange 2013, see Unified Messaging at <a href="http://go.microsoft.com/fwlink/p/?linkid=266579">http://go.microsoft.com/fwlink/p/?LinkId=266579</a>.</p></td>
</tr>
<tr class="odd">
<td><p>Run the exchucutil.ps1 script.</p></td>
<td><p>On the server running Exchange UM services, open the Exchange Management Shell and run the exchucutil.ps1 script, which does the following:</p>
<ul>
<li><p>Grants Lync Server 2013 permission to read Exchange UM Active Directory Domain Services objects, specifically, the SIP dial plans created in the previous task.</p></li>
<li><p>Creates a Unified Messaging IP gateway object in Active Directory for each Lync Server 2013 Enterprise Edition pool or Standard Edition server that hosts users who are enabled for Enterprise Voice.</p></li>
<li><p>Creates an Exchange UM hunt group for each gateway. The hunt group pilot identifier will be the name of the dial plan that is associated with the corresponding gateway. These need to be mapped 1:1 if there is more than one dial plan.</p></li>
</ul></td>
<td><p>Exchange Organization administrator</p>
<p>Exchange Recipient administrator</p></td>
<td><p><a href="lync-server-2013-configure-unified-messaging-on-microsoft-exchange.md">Configure Unified Messaging on Microsoft Exchange for Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>Configure Lync Server 2013 dial plans.</p></td>
<td><p>If you are integrating with Exchange 2007 SP1 or latest service pack, or Exchange 2010, create a new Enterprise Voice dial plan with a name that matches the Exchange UM dial plan fully qualified domain name (FQDN).</p>



> [!NOTE]
> You will need to do this for each UM Dial plan.


<p>If you are integrating with Exchange 2010 SP1, ensure that suitable global/site-level or pool-level Enterprise Voice dial plans have been configured.</p>



> [!NOTE]
> If you are integrating with Exchange 2010 SP1, the Lync Server dial plan and Exchange UM SIP dial plan names do not need to match.

</td>
<td><p>RTCUniversalServerAdmins</p></td>
<td><p><a href="lync-server-2013-configuring-dial-plans.md">Configuring dial plans in Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p>Run the Exchange UM Integration tool.</p></td>
<td><p>On the Lync Server 2013, run <strong>ocsumutil.exe</strong>, which:</p>
<ul>
<li><p>Creates Subscriber Access and Auto Attendant contact objects.</p></li>
<li><p>Validates that there is an Enterprise Voice dial plan with a name that matches the Exchange UM dial plan FQDN. If you are running Exchange 2010 SP1 or later, the dial plan names do not need to match, and you can ignore the tool’s warning about this.</p></li>
</ul>
<p>This tool works by scanning the Active Directory for Exchange UM settings and allowing the Lync Server 2013 administrator to view, create, and edit contact objects.</p></td>
<td><p>RTCUniversalServerAdmins <em>and</em> RTCUniversalUserAdmins</p>



> [!IMPORTANT]
> To run ocsumutil.exe successfully, the user must belong to both of these groups.





> [!NOTE]
> To create Contact objects, the user who runs ocsumutil.exe must have the correct permission to the Active Directory organizational unit (OU) where the new contact objects are stored. This permission can be granted by running the <STRONG>Grant-CsOUPermission</STRONG> cmdlet. For details, see the Lync Server Management Shell documentation.

</td>
<td><p><a href="lync-server-2013-configure-lync-server-2013-to-work-with-unified-messaging-on-microsoft-exchange-server.md">Configure Lync Server 2013 to work with Unified Messaging on Microsoft Exchange Server</a></p></td>
</tr>
<tr class="even">
<td><p>If necessary, perform other Enterprise Voice configuration steps.</p></td>
<td><p>If you have not already configured Enterprise Voice settings on your servers or users, do one or more of the following:</p>
<ul>
<li><p>Deploy and configure</p>
<p>Public switched telephone network (PSTN) gateways and Mediation Servers</p></li>
<li><p>Define voice policies, PSTN usage records, and outbound call routes.</p></li>
<li><p>Enable users for Enterprise Voice.</p></li>
<li><p>Optionally, configure specific users with dial plans.</p></li>
</ul>
<p>Other configuration steps may be required depending on the Enterprise Voice features that you enable.</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>RTCUniversalUserAdmins</p></td>
<td><p>See topics in the following sections:</p>
<ul>
<li><p><a href="lync-server-2013-configuring-voice-policies-pstn-usage-records-and-voice-routes.md">Configuring voice policies, PSTN usage records, and voice routes in Lync Server 2013</a></p></li>
<li><p><a href="lync-server-2013-deploying-enterprise-voice.md">Deploying Enterprise Voice in Lync Server 2013</a></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Enable Enterprise Voice users for Exchange UM.</p></td>
<td><p>On the Exchange UM server, ensure that a Unified Messaging mailbox policy has been created and that each user has a unique extension number assignment, and then enable the user for Unified Messaging.</p></td>
<td><p>Exchange Recipient administrator</p></td>
<td><p>For Exchange 2007 SP1 or latest service pack, see &quot;How to Enable a User for Unified Messaging&quot; at <a href="http://go.microsoft.com/fwlink/p/?linkid=268700">http://go.microsoft.com/fwlink/p/?LinkId=268700</a>.</p>
<p>For Exchange 2010 or latest service pack, see &quot;Enable a User for Unified Messaging&quot; at <a href="http://go.microsoft.com/fwlink/p/?linkid=268701">http://go.microsoft.com/fwlink/p/?LinkId=268701</a>.</p>
<p>For Exchange 2013, see Unified Messaging at <a href="http://go.microsoft.com/fwlink/p/?linkid=266579">http://go.microsoft.com/fwlink/p/?LinkId=266579</a>.</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

