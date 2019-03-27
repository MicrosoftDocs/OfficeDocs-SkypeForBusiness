---
title: 'Lync Server 2013: Modify SIP trunk configuration settings'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Modify SIP trunk configuration settings
ms:assetid: 7d68b09c-9ea0-43bd-997c-df887869d607
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ688104(v=OCS.15)
ms:contentKeyID: 49733703
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Modify SIP trunk configuration settings in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

SIP trunk configuration settings define the relationship and capabilities between a Mediation Server and the public switched telephone network (PSTN) gateway, an IP-public branch exchange (PBX), or a Session Border Controller (SBC) at the service provider. These settings do such things as specify:

  - Whether media bypass should be enabled on the trunks.

  - The conditions under which real-time transport control protocol (RTCP) packets are sent.

  - Whether or not secure real-time protocol (SRTP) encryption is required on each trunk.

When you install Microsoft Lync Server 2013, a global collection of SIP trunk configuration settings is created for you. In addition, administrators can create custom setting collections at the site scope or at the service scope (for the PSTN gateway service, only). Any of these collections can later be modified using either Lync Server Control Panel or Windows PowerShell.

When modifying SIP trunk configuration settings using Lync Server Control Panel, the following options are available to you:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>UI Setting</th>
<th>PowerShell Parameter</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Name</p></td>
<td><p>Identity</p></td>
<td><p>Unique identifier for the collection. This property is read-only; you cannot change the Identity of a collection of trunk configuration settings.</p></td>
</tr>
<tr class="even">
<td><p>Description</p></td>
<td><p>Description</p></td>
<td><p>Provides a way for administrators to store addition information about the settings (for example, the purpose of the trunk configuration).</p></td>
</tr>
<tr class="odd">
<td><p>Maximum early dialogs supported</p></td>
<td><p>MaxEarlyDialogs</p></td>
<td><p>The maximum number of forked responses a PSTN gateway, IP-PBX, or SBC at the service provider can receive to an Invite that it sent to the Mediation Server.</p></td>
</tr>
<tr class="even">
<td><p>Encryption support level</p></td>
<td><p>SRTPMode</p></td>
<td><p>Indicates the level of support for protecting media traffic between the Mediation Server and the PSTN Gateway, IP-PBX, or SBC at the service provider. For media bypass cases, this value must be compatible with the EncryptionLevel setting in the media configuration. Media configuration is set by using the <a href="https://docs.microsoft.com/powershell/module/skype/New-CsMediaConfiguration">New-CsMediaConfiguration</a> and <a href="https://docs.microsoft.com/powershell/module/skype/Set-CsMediaConfiguration">Set-CsMediaConfiguration</a> cmdlets.</p>
<p>Allowed values are:</p>
<ul>
<li><p>Required: SRTP encryption must be used.</p></li>
<li><p>Optional: SRTP will be used if the gateway supports it.</p></li>
<li><p>Not Supported: SRTP encryption is not supported and therefore will not be used.</p></li>
</ul>
<p>SRTPMode is used only if the gateway is configured to use Transport Layer Security (TLS). If the gateway is configured with Transmission Control Protocol (TCP) as the transport, SRTPMode is internally set to Not Supported.</p></td>
</tr>
<tr class="odd">
<td><p>Refer support</p></td>
<td><p>Enable3pccRefer</p>
<p>EnableReferSupport</p></td>
<td><p>If set to <strong>Enable sending refer to the gateway</strong>, indicates that the trunk supports receiving Refer requests from the Mediation Server.</p>
<p>If set to <strong>Enable refer using third-party call control</strong>, indicates that the 3pcc protocol can be used to allow transferred calls to bypass the hosted site. 3pcc is also known as &quot;third party control,&quot; and occurs when a third-party is used to connect a pair of callers (for example, an operator placing a call from person A to person B).</p></td>
</tr>
<tr class="even">
<td><p>Enable media bypass</p></td>
<td><p>EnableBypass</p></td>
<td><p>Indicates whether media bypass is enabled for this trunk. Media bypass can only be enabled if <strong>Centralized media processing</strong> is also enabled.</p></td>
</tr>
<tr class="odd">
<td><p>Centralized media processing</p></td>
<td><p>ConcentratedTopology</p></td>
<td><p>Indicates whether there is a well-known media termination point. (An example of a well-known media termination point would be a PSTN gateway where the media termination has the same IP as the signaling termination.)</p></td>
</tr>
<tr class="even">
<td><p>Enable RTP latching</p></td>
<td><p>EnableRTPLatching</p></td>
<td><p>Indicates whether or not the SIP trunks support RTP latching. RTP latching is a technology that enables RTP/RTCP connectivity through a NAT (network address translator) device or firewall.</p></td>
</tr>
<tr class="odd">
<td><p>Enable forward call history</p></td>
<td><p>ForwardCallHistory</p></td>
<td><p>Indicates whether call history information will be forwarded through the trunk.</p></td>
</tr>
<tr class="even">
<td><p>Enable forward P-Asserted-Identity data</p></td>
<td><p>ForwardPAI</p></td>
<td><p>Indicates whether the P-Asserted-Identity (PAI) header will be forwarded along with the call. The PAI header provides a way to verify the identity of the caller.</p></td>
</tr>
<tr class="odd">
<td><p>Enable outbound routing failover timer</p></td>
<td><p>EnableFastFailoverTimer</p></td>
<td><p>Indicates whether outbound calls that are not answered by the gateway within 10 seconds will be routed to the next available trunk; if there are no additional trunks then the call will automatically be dropped. In an organization with slow networks and gateway responses, that could potentially result in calls being dropped unnecessarily.</p></td>
</tr>
<tr class="even">
<td><p>Associated PSTN usages</p></td>
<td><p>PSTNUsages</p></td>
<td><p>Collection of PSTN usages assigned to the trunk.</p></td>
</tr>
<tr class="odd">
<td><p>Translated number to test</p></td>
<td><p>N/A</p></td>
<td><p>Phone number that can be used to do an ad hoc test of the trunk configuration settings.</p></td>
</tr>
<tr class="even">
<td><p>Associated translation rules</p></td>
<td><p>OutboundTranslationRulesList</p></td>
<td><p>Collection of phone number translation rules that apply to calls handled by Outbound Routing (calls routed to PBX or PSTN destinations).</p></td>
</tr>
<tr class="odd">
<td><p>Called number translation rules</p></td>
<td><p>OutboundCallingNumberTranslationRulesList</p></td>
<td><p>Collection of outbound calling number translation rules assigned to the trunk.</p></td>
</tr>
<tr class="even">
<td><p>Phone number to test</p></td>
<td><p>N/A</p></td>
<td><p>Phone number that can be used to do an ad hoc test of the translation rules.</p></td>
</tr>
<tr class="odd">
<td><p>Calling number</p></td>
<td><p>N/A</p></td>
<td><p>Indicates that the phone number to test is the phone number of the caller.</p></td>
</tr>
<tr class="even">
<td><p>Called number</p></td>
<td><p>N/A</p></td>
<td><p>Indicates that the phone number to test is the phone number of the person being called.</p></td>
</tr>
</tbody>
</table>


<div>


> [!NOTE]  
> The Lync Server CsTrunkConfiguration cmdlets support additional properties not shown in Lync Server Control Panel. For more information, see the help topic for the <A href="https://docs.microsoft.com/powershell/module/skype/Set-CsTrunkConfiguration">Set-CsTrunkConfiguration</A> cmdlet.



</div>

<div>

## To modify SIP trunk configuration settings by using Lync Server Control Panel

1.  In Lync Server Control Panel, click **Voice Routing**, and then click **Trunk Configuration**.

2.  On the **Trunk Configuration** tab, double-click the trunk configuration settings to be modified. Note that you can only edit one collection of settings at a time. If you would like to make the same changes on multiple collections, use Windows PowerShell instead.

3.  In the **Edit Trunk Configuration** dialog, make the appropriate selections and then click **OK**.

4.  The **State** property for the collection will be updated to **Uncommitted**. To commit the changes, and to delete the collection, click **Commit** and then click **Commit All**.

5.  In the **Uncommitted Voice Configuration Settings** dialog box, click **OK**.

6.  In the **Microsoft Lync Server 2013 Control Panel** dialog box click **OK**.

</div>

</div>

<span> </span>

</div>

</div>

</div>

