---
title: 'Lync Server 2013: Deployment process for Call Park'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Deployment process for Call Park
ms:assetid: 2000d672-a85f-4262-9d69-0bee9ae3709a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398283(v=OCS.15)
ms:contentKeyID: 48183586
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Deployment process for Call Park in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-25_

This section provides an overview of the steps involved in deploying the Call Park application. You must deploy Enterprise Edition or Standard Edition with Enterprise Voice before you configure Call Park. The components required by Call Park are installed and enabled when you deploy Enterprise Voice.

### Call Park Deployment Process

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
<td><p>Configure the call park orbit ranges in the orbit table</p></td>
<td><p>Use Lync Server Control Panel or the <strong>New-CSCallParkOrbit</strong> cmdlet to create the orbit ranges in the call park orbit table and associate them with the Application service that hosts the Call Park application.</p>
<div>

> [!NOTE]  
> For seamless integration with existing dial plans, orbit ranges are typically configured as a block of virtual extensions. Assigning Direct Inward Dialing (DID) numbers as orbit numbers in the call park orbit table is not supported.


</div></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsVoiceAdministrator</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-create-or-modify-a-call-park-orbit-range.md">Create or modify a Call Park orbit range in Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>Configure Call Park settings</p></td>
<td><p>Use the <strong>Set-CsCpsConfiguration</strong> cmdlet to configure Call Park settings. At a minimum, we recommend that you configure the <strong>OnTimeoutURI</strong> option to configure the fallback destination to use when a parked call times out. You can also configure the following settings:</p>
<ul>
<li><p>(Optional) <strong>EnableMusicOnHold</strong> to enable or disable music on hold.</p></li>
<li><p>(Optional) <strong>MaxCallPickupAttempts</strong> to determine the number of times a parked call rings back to the answering phone before forwarding the call to the fallback Uniform Resource Identifier (URI).</p></li>
<li><p>(Optional) <strong>CallPickupTimeoutThreshold</strong> to determine the amount of time that elapses after a call has been parked before it rings back to the phone where the call was answered.</p></li>
</ul></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsVoiceAdministrator</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-configure-call-park-settings.md">Configure Call Park settings in Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p>Optionally, customize the music on hold</p></td>
<td><p>Use the <strong>Set-CsCallParkServiceMusicOnHoldFile</strong> cmdlet to customize and upload an audio file, if you don't want to use the default music on hold.</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsVoiceAdministrator</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-customize-call-park-music-on-hold.md">Customize Call Park music on hold in Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>Configure voice policy to enable Call Park for users</p></td>
<td><p>Use Lync Server Control Panel or the <strong>Set-CSVoicePolicy</strong> cmdlet with the <strong>EnableCallPark</strong> option to enable Call Park for users in voice policy.</p>
<div>

> [!NOTE]  
> By default, Call Park is disabled for all users.


</div>
<div>

> [!NOTE]  
> If you have multiple voice policies, make sure the EnableCallPark property is set for each voice policy, not just for the default policy.


</div></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsVoiceAdministrator</p>
<p>CsUserAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-enable-call-park-for-users.md">Enable Call Park for users in Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p>Verify normalization rules for Call Park</p></td>
<td><p>Call park orbits must not be normalized. Verify that your normalization rules do not include any of your orbit ranges. If necessary, create additional normalization rules to prevent orbits being normalized.</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsVoiceAdministrator</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-verify-normalization-rules-for-call-park.md">Verify normalization rules for Call Park in Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>Verify your Call Park deployment</p></td>
<td><p>Test parking and retrieving calls to make sure that your configuration works as expected.</p></td>
<td><p>-</p></td>
<td><p><a href="lync-server-2013-optional-verify-call-park-deployment.md">(Optional) Verify Call Park deployment in Lync Server 2013</a></p></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

