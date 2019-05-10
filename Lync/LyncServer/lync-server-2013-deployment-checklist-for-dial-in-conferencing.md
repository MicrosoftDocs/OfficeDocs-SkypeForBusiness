---
title: Lync Server 2013 deployment checklist for dial-in conferencing
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Deployment checklist for dial-in conferencing
ms:assetid: 9c8d3ebe-0d70-4a61-9bd0-522286cddd9a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412726(v=OCS.15)
ms:contentKeyID: 48184987
ms.date: 10/03/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Deployment checklist for dial-in conferencing in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-10-03_

The components required for dial-in conferencing are deployed when you deploy the conferencing workload. Before you can configure dial-in conferencing, you need to deploy either Enterprise Voice or a Mediation Server and a public switched telephone network (PSTN) gateway.

All the steps in the following table must be performed before users can dial in from the PSTN to join an audio/video conference.

<div>


> [!NOTE]  
> If you are migrating from Office Communications Server 2007 R2, you must apply the latest updates to your Office Communications Server 2007 R2 environment before deploying dial-in conferencing.



</div>

### Dial-in Conferencing Deployment Process

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
<th>Deployment documentation</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Create a topology that includes the Conferencing workload, including a Mediation Server and PSTN gateway, and deploy the Front End pool or Standard Edition server</strong></p></td>
<td><ol>
<li><p>Run Topology Builder to configure your topology. While configuring the topology, select the dial-in conferencing option.</p></li>
<li><p>Publish the topology and deploy the Front End pool or Standard Edition server.</p></li>
<li><p>If necessary, create a stand-alone Mediation Server and associate it with a PSTN gateway.</p>
<div>

> [!NOTE]  
> This step is required only if you do not deploy Enterprise Voice and do not collocate the Mediation Server with the Enterprise EditionFront End Server or Standard Edition server. If you deploy Enterprise Voice, you install and configure Mediation Servers and PSTN gateways as part of the Enterprise Voice deployment. If you collocate the Mediation Server, you install and configure the Mediation Server as part of the Front End pool or Standard Edition server deployment.


</div></li>
</ol></td>
<td><p>Domain Admins</p>
<p>RTCUniversalServerAdmins</p>
<p>Administrator</p></td>
<td><ul>
<li><p><a href="lync-server-2013-deploying-lync-server.md">Deploying Lync Server 2013</a></p></li>
<li><p>To create a stand-alone Mediation Server pool: <a href="lync-server-2013-deploying-mediation-servers-and-defining-peers.md">Deploying Mediation Servers and defining peers in Lync Server 2013</a></p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Configure dial plans</strong></p></td>
<td><p>A dial plan is a set of phone number normalization rules that translate phone numbers dialed from a specific location to a single standard (E.164) format for purposes of phone authorization and call routing. The same phone number dialed from different locations can, based on the respective dial plans, resolve to different E.164 numbers, as appropriate to each location. If you deploy Enterprise Voice, you set up dial plans as part of that deployment, and you need to make sure that the dial plans also accommodate dial-in conferencing. If you do not deploy Enterprise Voice, you need to set up dial plans for dial-in conferencing.</p>
<p>Use the Lync Server 2013 Control Panel or Lync Server Management Shell to set up dial plans as follows:</p>
<ol>
<li><p>Create one or more dial plans for routing dial-in access phone numbers.</p></li>
<li><p>Assign a default dial plan to each pool. Set the <strong>Dial-in conferencing region</strong> to the geographic location to which the dial plan applies. The region associates the dial plan with dial-in access numbers.</p></li>
</ol></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsVoiceAdministrator</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-configure-dial-plans-for-dial-in-conferencing.md">Configure dial plans for dial-in conferencing in Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p><strong>Make sure that dial plans are assigned regions</strong></p></td>
<td><p>Run the <strong>Get-CsDialPlan</strong> and <strong>Set-CsDialPlan</strong> cmdlets to make sure that all dial plans have a region assigned.</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsVoiceAdministrator</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-make-sure-dial-plans-have-assigned-regions.md">Make sure dial plans Lync Server 2013 have assigned regions</a></p></td>
</tr>
<tr class="even">
<td><p><strong>(Optional) Verify or modify user personal identification number (PIN) requirements</strong></p></td>
<td><p>Use Lync Server 2013 Control Panel or Lync Server Management Shell to view or modify the Conferencing <strong>PIN Policy</strong>. You can specify minimum PIN length, maximum number of logon attempts, PIN expiration, and whether common patterns are allowable.</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-optional-verify-pin-policy-settings.md">(Optional) Verify PIN policy settings in Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p><strong>Configure conferencing policy to support dial-in conferencing</strong></p></td>
<td><p>Use Lync Server 2013 Control Panel or Lync Server Management Shell to configure <strong>Conferencing Policy</strong> settings. Specify whether:</p>
<ul>
<li><p>PSTN conference dial-in is enabled.</p></li>
<li><p>Users can invite anonymous participants.</p></li>
<li><p>Unauthenticated users can join a conference by using dial-out phoning. With dial-out phoning, the conference server calls the user, and the user answers the phone to join the conference.</p></li>
</ul></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-configure-conferencing-policy-for-dial-in.md">Configure conferencing policy for dial-in in Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p><strong>Configure dial-in access numbers</strong></p></td>
<td><p>Use Lync Server 2013 Control Panel or Lync Server Management Shell to set up dial-in access numbers that users call to dial in to a conference, and specify the regions that associate the access number with the appropriate dial plans. The first three access numbers for the region specified by the organizer's dial plan are included in the conference invitation. All access numbers are available on the Dial-in Conferencing Settings page.</p>
<div>

> [!NOTE]  
> After you create dial-in access numbers, you can use the <STRONG>Set-CsDialInConferencingAccessNumber</STRONG> cmdlet to modify the display name of the Active Directory contact objects so that users can more easily identify the correct access number.


</div></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-configure-dial-in-conferencing-access-numbers.md">Configure dial-in conferencing access numbers in Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p><strong>(Optional) Verify dial-in conferencing settings</strong></p></td>
<td><p>Use the <strong>Get-CsDialinConferencingAccessNumber</strong> cmdlet to search for dial plans that have a dial-in conferencing region that is not used by any access number and for access numbers that have no region assigned.</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p>
<p>CsViewOnlyAdministrator</p>
<p>CsHelpDesk</p></td>
<td><p><a href="lync-server-2013-optional-verify-dial-in-conferencing-settings.md">(Optional) Verify dial-in conferencing settings in Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p><strong>(Optional) Modify key mapping of DTMF commands</strong></p></td>
<td><p>Use the <strong>Set-CsDialinConferencingDtmfConfiguration</strong> cmdlet to modify the keys used for dual-tone multifrequency (DTMF) commands, which participants can use to control conference settings (such as mute and unmute or lock and unlock).</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-optional-modify-key-mapping-for-dtmf-commands.md">(Optional) Modify key mapping for DTMF commands in Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p><strong>(Optional) Modify conference join and leave announcement behavior</strong></p></td>
<td><p>Use the <strong>Set-CsDialinConferencingConfiguration</strong> to change how announcements work when participants join and leave conferences.</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-optional-enable-and-disable-conference-join-and-leave-announcements.md">(Optional) Enable and disable conference join and leave announcements in Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p><strong>(Optional) Verify dial-in conferencing</strong></p></td>
<td><p>Use the <strong>Test-CsDialInConferencing</strong> cmdlet to test that the access numbers for the specified pool work correctly.</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-optional-verify-dial-in-conferencing.md">(Optional) Verify dial-in conferencing in Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p><strong>Deploy the Online Meeting Add-in for Lync 2013</strong></p></td>
<td><p>Deploy the Online Meeting Add-in for Lync 2013 so that users can schedule conferences that support dial-in conferencing. The Online Meeting Add-in for Lync 2013 is installed automatically when you install Lync 2013.</p></td>
<td><p>Administrators</p></td>
<td><p><a href="lync-server-2013-deploy-the-online-meeting-add-in-for-lync-2013.md">Deploy the Online Meeting Add-in for Lync 2013</a></p></td>
</tr>
<tr class="even">
<td><p><strong>Configure user account settings</strong></p></td>
<td><p>Use Lync Server 2013 Control Panel or Lync Server Management Shell to configure the telephony <strong>Line URI</strong> as a unique, normalized phone number (for example, tel:+14255550200).</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsAdministrator</p>
<p>CsUserAdministrator</p></td>
<td><p><a href="lync-server-2013-configure-user-account-settings.md">Configure user account settings in Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p>(Recommended) Configure conference directories</p></td>
<td><p>Use the <strong>New-CsConferenceDirectory</strong> cmdlet to create one conference directory for every 999 users in the pool.</p></td>
<td><p>RTCUniversalServerAdmins</p></td>
<td><p><a href="lync-server-2013-dial-in-conferencing-requirements.md">Dial-in conferencing requirements in Lync Server 2013</a> <a href="recommended-create-conference-directories.md">(Recommended) Create Conference Directories</a></p></td>
</tr>
<tr class="even">
<td><p><strong>(Optional) Welcome users to dial-in conferencing and set the initial PIN</strong></p></td>
<td><p>Use the <strong>Set-CsPinSendCAWelcomeMail</strong> script to set users' initial PINs and send a welcome email that contains the initial PIN and a link to the Dial-in Conferencing Settings page.</p></td>
<td><p>RTCUniversalServerAdmins</p></td>
<td><p><a href="lync-server-2013-optional-welcome-users-to-dial-in-conferencing.md">(Optional) Welcome users to dial-in conferencing in Lync Server 2013</a></p></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

