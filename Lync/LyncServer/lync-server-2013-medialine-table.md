---
title: 'Lync Server 2013: MediaLine table'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: MediaLine table
ms:assetid: 414b1d63-ae97-4c27-bac0-c9ad0f808ff0
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425920(v=OCS.15)
ms:contentKeyID: 48183956
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# MediaLine table in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-02-21_

Each record represents one media line. (One audio session usually contains one audio media line. One audio and video (A/V) session usually contains one audio media line and one video media line, although the session might contain two video media lines if a conferencing device is used or if Gallery View is used.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Column</strong></th>
<th><strong>Data Type</strong></th>
<th><strong>Key/Index</strong></th>
<th><strong>Details</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>ConferenceDateTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>Primary</p></td>
<td><p>Referenced from the <a href="lync-server-2013-session-table.md">Session table in Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Primary</p></td>
<td><p>Referenced from the <a href="lync-server-2013-session-table.md">Session table in Lync Server 2013</a>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MediaLineLabel</strong></p></td>
<td><p>tinyint</p></td>
<td><p>Primary</p></td>
<td><p>0 is main audio, 1 is main video, and 2 is panoramic video, 3 is Application/Desktop Sharing. This label must be unique within a single session.</p></td>
</tr>
<tr class="even">
<td><p><strong>ConnectivityIce</strong></p></td>
<td><p>tinyint</p></td>
<td><p> </p></td>
<td><p>This column is present but not used in Microsoft Lync Server 2013. Information about the connectivity used for a media line is captured in the CallerConnectivityICE and CalleeConnectivityICE columns.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CallerIceWarningFlags</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Information about Interactive Connectivity Establishment (ICE) process described in bits flags. For details, refer to the <em>Quality of Experience Monitoring Server Protocol Specification</em>, available for download.</p></td>
</tr>
<tr class="even">
<td><p><strong>CalleeIceWarningFlags</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Same as CallerIceWarningFlags, but on the callee side. For details, refer to the <em>Quality of Experience Monitoring Server Protocol Specification</em>, available for download.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Security</strong></p></td>
<td><p>tinyint</p></td>
<td><p> </p></td>
<td><p>The security profile in use. 0 is NONE, 1 is SRTP, 2 is V1.</p></td>
</tr>
<tr class="even">
<td><p><strong>Transport</strong></p></td>
<td><p>tinyint</p></td>
<td><p> </p></td>
<td><p>0 is UDP, 1 is TCP.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CallerIPAddr</strong></p></td>
<td><p>int</p></td>
<td><p>Foreign</p></td>
<td><p>IP Address of the caller. See the <a href="lync-server-2013-ipaddress-table.md">IPAddress table in Lync Server 2013</a> for more information.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallerPort</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Port used by the caller.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CallerSubnet</strong></p></td>
<td><p>int</p></td>
<td><p> Foreign</p></td>
<td><p>The subnet of the caller. See the <a href="lync-server-2013-ipaddress-table.md">IPAddress table in Lync Server 2013</a> for more information.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallerInside</strong></p></td>
<td><p>bit</p></td>
<td><p> </p></td>
<td><p>1 means caller is inside the enterprise network, 0 means the caller is outside the network.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CallerMacAddress</strong></p></td>
<td><p>int</p></td>
<td><p>Foreign</p></td>
<td><p>Caller’s mac address, referenced from <a href="lync-server-2013-macaddress-table.md">MacAddress table in Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallerRelayIPAddr</strong></p></td>
<td><p>int</p></td>
<td><p>Foreign</p></td>
<td><p>IP Address of the Lync Server A/V Edge service used by the caller. See the <a href="lync-server-2013-ipaddress-table.md">IPAddress table in Lync Server 2013</a> for more information.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CallerRelayPort</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Port used on the A/V Edge service by the caller.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallerCaptureDev</strong></p></td>
<td><p>int</p></td>
<td><p>Foreign</p></td>
<td><p>Capture device used by the caller. Referenced from the <a href="lync-server-2013-device-table.md">Device table in Lync Server 2013</a>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CallerRenderDev</strong></p></td>
<td><p>int</p></td>
<td><p>Foreign</p></td>
<td><p>Render device used by caller. Referenced from the <a href="lync-server-2013-device-table.md">Device table in Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallerCaptureDevDriver</strong></p></td>
<td><p>int</p></td>
<td><p>Foreign</p></td>
<td><p>Driver for the caller’s capture device, referenced from the <a href="lync-server-2013-devicedriver-table.md">DeviceDriver table in Lync Server 2013</a>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CallerRenderDevDriver</strong></p></td>
<td><p>int</p></td>
<td><p>Foreign</p></td>
<td><p>Driver for the caller’s render device, referenced from the <a href="lync-server-2013-devicedriver-table.md">DeviceDriver table in Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallerNetworkConnectionType</strong></p></td>
<td><p>tinyint</p></td>
<td><p>Foreign</p></td>
<td><p>Indicates how the caller connected to the network. Values are obtained from the <a href="lync-server-2013-networkconnectiondetail-table.md">NetworkConnectionDetail table in Lync Server 2013</a>. Typical values are 0 for a wired connection’ 1 for a WiFi connection; and 3 for an Ethernet connection.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CallerBssid</strong></p></td>
<td><p>int</p></td>
<td><p>Foreign</p></td>
<td><p>Caller’s BSSID if wireless is used. Referenced from <a href="lync-server-2013-macaddress-table.md">MacAddress table in Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallerVPN</strong></p></td>
<td><p>bit</p></td>
<td></td>
<td><p>The caller's link. 1 is virtual private network (VPN), 0 is non-VPN.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CallerLinkSpeed</strong></p></td>
<td><p>decimal(18,0)</p></td>
<td></td>
<td><p>The network link speed, in bps, for the caller's endpoint.</p></td>
</tr>
<tr class="even">
<td><p><strong>CalleeIPAddr</strong></p></td>
<td><p>int</p></td>
<td><p>Foreign</p></td>
<td><p>IP Address of the call receiver. See the <a href="lync-server-2013-ipaddress-table.md">IPAddress table in Lync Server 2013</a> for more information.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CalleePort</strong></p></td>
<td><p>bit</p></td>
<td></td>
<td><p>Port used by the call receiver.</p></td>
</tr>
<tr class="even">
<td><p><strong>CalleeSubnet</strong></p></td>
<td><p>int</p></td>
<td><p>Foreign</p></td>
<td><p>Subnet of callee. See the <a href="lync-server-2013-ipaddress-table.md">IPAddress table in Lync Server 2013</a> for more information.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CalleeInside</strong></p></td>
<td><p>bit</p></td>
<td><p> </p></td>
<td><p>1 means call receiver is inside the enterprise network, 0 means the call receiver is outside the network.</p></td>
</tr>
<tr class="even">
<td><p><strong>CalleeMacAddress</strong></p></td>
<td><p>int</p></td>
<td><p>Foreign</p></td>
<td><p>Callee Mac address. Referenced from the <a href="lync-server-2013-macaddress-table.md">MacAddress table in Lync Server 2013</a>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CalleeRelayIPAddr</strong></p></td>
<td><p>int</p></td>
<td><p>Foreign</p></td>
<td><p>IP Address of the A/V Edge service used by the call receiver. See the <a href="lync-server-2013-ipaddress-table.md">IPAddress table in Lync Server 2013</a> for more information.</p></td>
</tr>
<tr class="even">
<td><p><strong>CalleeRelayPort</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Port used on the A/V Edge Service by the call receiver.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CalleeCaptureDev</strong></p></td>
<td><p>int</p></td>
<td><p>foreign</p></td>
<td><p>Capture device used by the call receiver. Referenced from the <a href="lync-server-2013-device-table.md">Device table in Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>CalleeRenderDev</strong></p></td>
<td><p>int</p></td>
<td><p>Foreign</p></td>
<td><p>Render device used by the call receiver. Referenced from the <a href="lync-server-2013-device-table.md">Device table in Lync Server 2013</a>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CalleeCaptureDevDriver</strong></p></td>
<td><p>int</p></td>
<td><p>Foreign</p></td>
<td><p>Driver for the call receiver’s capture device. Referenced from <a href="lync-server-2013-devicedriver-table.md">DeviceDriver table in Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>CalleeRenderDevDriver</strong></p></td>
<td><p>varchar(256)</p></td>
<td><p>Foreign</p></td>
<td><p>Driver for the call receiver’s render device. Referenced from <a href="lync-server-2013-devicedriver-table.md">DeviceDriver table in Lync Server 2013</a>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CalleeNetworkConnectionType</strong></p></td>
<td><p>tinyint</p></td>
<td><p>Foreign</p></td>
<td><p>Indicates how the callee connected to the network. Values are obtained from the <a href="lync-server-2013-networkconnectiondetail-table.md">NetworkConnectionDetail table in Lync Server 2013</a>. Typical values are 0 for a wired connection’ 1 for a WiFi connection; and 3 for an Ethernet connection.</p></td>
</tr>
<tr class="even">
<td><p><strong>CalleeBssid</strong></p></td>
<td><p>int</p></td>
<td><p>Foreign</p></td>
<td><p>Callee’s BSSID if wireless is used. Referenced from <a href="lync-server-2013-macaddress-table.md">MacAddress table in Lync Server 2013</a>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CalleeVPN</strong></p></td>
<td><p>bit</p></td>
<td><p> </p></td>
<td><p>The call receiver’s link; 1 is virtual private network (VPN), 0 is non-VPN.</p></td>
</tr>
<tr class="even">
<td><p><strong>CalleeLinkSpeed</strong></p></td>
<td><p>decimal(18,0)</p></td>
<td><p> </p></td>
<td><p>The network link speed, in bps, for the call receiver’s endpoint.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ConversationalMOS</strong></p></td>
<td><p>decimal(3,2)</p></td>
<td><p> </p></td>
<td><p>Narrowband Conversational MOS of the audio sessions (based on both audio streams).</p></td>
</tr>
<tr class="even">
<td><p><strong>AppliedBandwidthLimit</strong></p></td>
<td><p>int</p></td>
<td></td>
<td><p>This is the actual bandwidth applied to the given send side stream given various policy settings (TURN, API, SDP, Policy Server, and so on). This is not to be confused with the effective bandwidth because there can be a lower effective bandwidth based on the bandwidth estimate. This is basically the maximum bandwidth the send stream can take barring limits imposed by the bandwidth estimate.</p></td>
</tr>
<tr class="odd">
<td><p><strong>AppliedBandwidthSourceKey</strong></p></td>
<td><p>smallint</p></td>
<td></td>
<td><p>This is the source of the bandwidth cap being imposed. It describes where the bandwidth limit is coming from (“Policy Server”, “TURN Server”, “Modality”, and so on). Referenced from the <a href="lync-server-2013-appliedbandwidthsource-table.md">AppliedBandwidthSource table in Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>Caller</strong></p></td>
<td><p>bit</p></td>
<td><p> </p></td>
<td><p>Indicates whether metrics from the caller were received; 1 is yes, a null value is no.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Callee</strong></p></td>
<td><p>bit</p></td>
<td><p> </p></td>
<td><p>Indicates whether metrics from the call receiver were received; 1 is yes, a null value is no.</p></td>
</tr>
<tr class="even">
<td><p><strong>MidCallReport</strong></p></td>
<td><p>bit</p></td>
<td></td>
<td><p>Indicates whether the report is for a portion of the session or for the complete session.</p>
<p>This column was introduced in Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ClassifiedPoorCall</strong></p></td>
<td><p>bit</p></td>
<td></td>
<td><p>Indicates whether a call was classified as a poor call (value of 1) or as a good call (0).</p>
<p>This column was introduced in Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallerConnectivityICE</strong></p></td>
<td><p>tinyInt</p></td>
<td></td>
<td><p>Indicates whether the caller connected to the network using the ICE protocol (Internet Connectivity Establishment).</p>
<p>This column was introduced in Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CalleeConnectivityICE</strong></p></td>
<td><p>tinyint</p></td>
<td></td>
<td><p>Indicates whether the caller connected to the network using the ICE protocol (Internet Connectivity Establishment).</p>
<p>This column was introduced in Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallerReflexiveLocalIPAddr</strong></p></td>
<td><p>int</p></td>
<td><p>Foreign</p></td>
<td><p>Reflexive IP address of the user who placed the call. In organizations that use NAT (network address translation), the reflexive IP address is the IP address of the proxy server.</p>
<p>This column was introduced in Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CallerWiFiDriverDevicesDesc</strong></p></td>
<td><p>int</p></td>
<td><p>Foreign</p></td>
<td><p>Device description for the WiFi driver employed by the user who placed the call.</p>
<p>This column was introduced in Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallerWiFiDriverVersion</strong></p></td>
<td><p>int</p></td>
<td><p>Foreign</p></td>
<td><p>Version number for the WiFi driver employed by the user who placed the call.</p>
<p>This column was introduced in Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CalleReflexiveLocalIPAddr</strong></p></td>
<td><p>int</p></td>
<td><p>Foreign</p></td>
<td><p>Reflexive IP address of the user who received the call. In organizations that use NAT (network address translation), the reflexive IP address is the IP address of the proxy server.</p>
<p>This column was introduced in Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>CalleeWiFiDriverDevicesDesc</strong></p></td>
<td><p>int</p></td>
<td><p>Foreign</p></td>
<td><p>Device description for the WiFi driver employed by the user who received the call.</p>
<p>This column was introduced in Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CalleeWiFiDriverVersion</strong></p></td>
<td><p>int</p></td>
<td><p>Foreign</p></td>
<td><p>Version number for the WiFi driver employed by the user who received the call.</p>
<p>This column was introduced in Microsoft Lync Server 2013.</p></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

