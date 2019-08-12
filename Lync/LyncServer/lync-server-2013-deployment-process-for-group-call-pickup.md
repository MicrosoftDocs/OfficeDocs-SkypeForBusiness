---
title: 'Lync Server 2013: Deployment process for Group Call Pickup'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Deployment process for Group Call Pickup
ms:assetid: 082daeac-e667-4e2d-b78d-8e0901f9f0e9
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ945615(v=OCS.15)
ms:contentKeyID: 51541444
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Deployment process for Group Call Pickup in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-25_

This section provides an overview of the steps involved in deploying Group Call Pickup. You must deploy Enterprise Edition or Standard Edition with Enterprise Voice before you configure Group Call Pickup. The components required by Group Call Pickup are installed and enabled when you deploy Enterprise Voice.

### Group Call Pickup Deployment Process

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
<td><p>Enable the SEFAUtil resource kit tool in the topology</p></td>
<td><ol>
<li><p>Use the <strong>New-CsTrustedApplicationPool</strong> cmdlet to create a new trusted application pool.</p></li>
<li><p>Use the <strong>New-CsTrustedApplication</strong> cmdlet to specify the SEFAUtil tool as trusted application.</p></li>
<li><p>Run the <strong>Enable-CsTopology</strong> cmdlet to enable the topology.</p></li>
<li><p>Install the resource kit tools on a Front End Server that is in the trusted application pool created in step 1.</p></li>
<li><p>Verify that SEFAUtil is running correctly by running it to display the call forwarding settings of a user in the deployment.</p></li>
</ol></td>
<td><p>RTCUniversalServerAdmins</p></td>
<td><p><a href="lync-server-2013-deploy-the-sefautil-tool.md">Deploy the SEFAUtil tool in Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>Configure call pickup number ranges in the call park orbit table</p></td>
<td><p>Use the <strong>New-CSCallParkOrbit</strong> cmdlet to create call pickup number ranges in the call park orbit table and assign the call pickup ranges the type GroupPickup.</p>
<div>

> [!NOTE]  
> You must use Lync Server Management Shell to create, modify, remove, and view Group Call Pickup number ranges in the call park orbit table. Group Call Pickup number ranges are not available in Lync Server Control Panel.


</div>
<div>

> [!NOTE]  
> For seamless integration with existing dial plans, number ranges are typically configured as a block of virtual extensions. Assigning Direct Inward Dialing (DID) numbers as range numbers in the call park orbit table is not supported.


</div></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsVoiceAdministrator</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-configure-call-pickup-group-numbers.md">Configure call pickup group numbers in Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p>Assign a call pickup number to users, and enable Group Call Pickup for the users</p></td>
<td><p>Use the /enablegrouppickup parameter in the SEFAUtil resource kit tool to enable Group Call Pickup and assign a call pickup number for users.</p></td>
<td><p>-</p></td>
<td><p><a href="lync-server-2013-enable-group-call-pickup-for-users-and-assign-a-group-number.md">Enable Group Call Pickup for users in Lync Server 2013 and assign a group number</a></p></td>
</tr>
<tr class="even">
<td><p>Notify users of their assigned call pickup number and any other number of interest</p></td>
<td><p>Because any user can retrieve a call made to a Group Call Pickup user, users may want to monitor more than one group.</p></td>
<td><p>-</p></td>
<td><p><a href="lync-server-2013-communicate-group-call-pickup-assignment-to-users.md">Communicate Group Call Pickup assignments to users in Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p>Verify your Group Call Pickup deployment</p></td>
<td><p>Test placing and retrieving calls to make sure that your configuration works as expected.</p></td>
<td><p>-</p></td>
<td><p><a href="lync-server-2013-optional-verify-the-group-call-pickup-deployment.md">(Optional) Verify the Group Call Pickup deployment in Lync Server 2013</a></p></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

