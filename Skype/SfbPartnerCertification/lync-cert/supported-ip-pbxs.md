---
title: "Partner qualification for Lync - IP PBXs"
ms.author: jambirk
author: jambirk
manager: serdars
ms.reviewer: dougand
ms.topic: article
ms.tgt.pltfrm: lync
ms.service: skype-for-business-online-admin
ms.collection: Lync
audience: Admin
appliesto:
- Lync
- Skype for Business
localization_priority: Normal
f1keywords: None
ms.custom:
- Lync Certification
- dn788945
description: "Partner qualification requirements for Lync."
---

# Supported IP PBXs

IP PBXs listed in the table that follows are supported by Microsoft, although they have not gone through the formal UCOIP qualification process nor was the testing requested by the vendor.

Sufficient internal testing has been performed by Microsoft such that specific configurations are supported by Microsoft (where applicable with known limitations). These configurations utilize the commercially available production SIP trunk interface of the IP-PBX vendor but may not be supported by the IP-PBX vendor. In addition, IP-PBX vendor-provided complete documentation for installation and set-up, release notes, or documented support processes may not be available. Wherever possible, Microsoft will endeavor to provide documentation for installation and set-up.

## Supported for Lync 2013
***Table 1 - Supported for Lync 2013***

<table border="1" cellpadding="5" cellspacing="" class="grid" style="border-collapse:collapse;background-color:white;" width="100%" xmlns="http://www.w3.org/1999/xhtml">
	<colgroup>
		<col width="74" />
		<col width="364" />
		<col width="254" />
		<col />
	</colgroup>
	<thead>
		<tr bgcolor="#DEDEDE">
			<td align="center" valign="top"><strong>IP-PBX Vendor</strong></td>
			<td align="center" valign="top"><strong>Tested Product</strong></td>
			<td align="center" valign="top"><strong>Supported Configuration</strong></td>
			<td align="center" valign="top"><strong>Software Version Tested</strong></td>
		</tr>
	</thead>
	<tbody>
		<tr align="left" valign="top">
			<td rowspan="6">Avaya</td>
			<td>Aura Session Manager 6.1</td>
			<td>Direct SIP</td>
			<td>6.1.2.0.612004 (Service Pack 2)</td>
		</tr>
		<tr>
			<td colspan="3" style="display:none;"> </td>
		</tr>
		<tr align="left" valign="top">
			<td colspan="3">
				<p>Documentation: <a href="https://www.microsoft.com/en-us/download/details.aspx?id=41152">Lync 2013 and Avaya Aura 6.1 Integration Guide v1.3</a></p>
				<p>Configuration Notes:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>REFER can be set to enabled and RTCP set to Disabled.</li>
					<li>TLS and SRTP were not tested.</li>
					<li>Disable &quot;ForwardCallHistory&quot; on the trunk Call forwarding on Lync client fails at PRI when History-Info is turned on.</li>
				</ol>
				<p>Known Limitations:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>Due to a the issue documented in <a href="https://support.microsoft.com/kb/2904439">KB 2904439</a>, call hold fails with media bypass enabled.</li>
					<li>Comfort noise generation is not supported. As a result, comfort noise is not played on Lync.</li>
				</ol>
			</td>
		</tr>
		<tr align="left" valign="top">
			<td>Aura Session Manager 6.3</td>
			<td>Direct SIP</td>
			<td>6.3.2.0.632023</td>
		</tr>
		<tr>
			<td colspan="3" style="display:none;"> </td>
		</tr>
		<tr align="left" valign="top">
			<td colspan="3">
                <p>Configuration Notes<em>:</p>
				<ol>
					<li>Media Bypass, RTCP, REFER, Centralized Media Processing and ForwardCallHistory were set to Disabled.</li>
                    <li>Session Timer were set to Enabled.<br /></em>Information was received from Avaya.</li>
				</ol>
				<p>Known Limitations:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>With Media bypass enabled in Lync, for an incoming call to Lync client that has simultaneous ring to a number with early media enabled, caller will hear ring back instead of the early media.</li>
					<li>Avaya Aura communication manager does not send disconnect to PSTN via ISDN trunk while receiving SIP 603 response from Mediation server for incoming call to Lync client. Caller will hear overflow tone and call will not disconnect until caller drops the call.</li>
				</ol>
			</td>
		</tr>
		<tr align="left" valign="top">
			<td rowspan="6">Cisco</td>
			<td>Cisco Unified Communications Manager</td>
			<td>Direct SIP</td>
			<td>UCM 8.6.2.20000-2</td>
		</tr>
		<tr>
			<td colspan="3" style="display:none;"> </td>
		</tr>
		<tr align="left" valign="top">
			<td colspan="3">
				<p>Configuration Notes:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>On the Cisco IP-PBX, configure MTP to enabled and PRACK to disabled (the default for PRACK).</li>
					<li>In order to manage call hold appropriately in bypass scenarios, the following update is needed for the Lync client: <a href="https://support.microsoft.com/kb/3020377">https://support.microsoft.com/kb/3020377</a></li>
					<li>On Lync Mediation Server, Media Bypass, REFER and Session Timer are set to enabled. RTCP is set to disabled.</li>
				</ol>
				<p>Known Limitations:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>Comfort noise generation is not supported. As a result, comfort noise is not played on Microsoft Lync.</li>
					<li>When a Lync user configures call forward or simul-ring to a PSTN IVR number, the calling party will not hear early media played from the IVR.</li>
					<li>Cisco UCM does not originate or pass through ‘History-Info’ and ‘Referred-by’ nor convert it to ‘Diversion’ header. As a result, calls being forwarded or transferred to a PSTN user or calls that simultaneously ring a PSTN user, may fail with Service Providers that expect history information (transferring party info). Service Providers not looking for the transferring party details in history or diversion headers may pass the call through, however this may cause billing challenges for these kinds of calls.</li>
				</ol>
			</td>
		</tr>
		<tr align="left" valign="top">
			<td>Cisco Unified Communications Manager</td>
			<td>Direct SIP</td>
			<td>UCM 7.0.1.11000-2</td>
		</tr>
		<tr>
			<td colspan="3" style="display:none;"> </td>
		</tr>
		<tr align="left" valign="top">
			<td colspan="3">
				<p>Configuration Notes:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>On the Cisco IP-PBX, configure MTP to enabled and PRACK to disabled (the default for PRACK).</li>
                    <li>On Lync Mediation Server, Media Bypass is set to enabled. RTCP and REFER are set to disabled, as Cisco doesn&#39;t send RTCP messages and REFER is not supported by this IP-PBX without a Referred-By header.</li>
				</ol>
				<p>Known Limitations:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>When a Lync user transfers a PBX call to another PBX user, the local PBX phone will still show connected to the first Lync user.</li>
					<li>Comfort noise generation is not supported. As a result, comfort noise is not played on Microsoft Lync.</li>
					<li>When a Lync user configures call forward or simul-ring to a PSTN IVR number, the calling party will not hear early media played from the IVR.</li>
                    <li>CUCM will not send OPTIONS, impacting failover scenarios as the IP-PBX cannot determine Lync&#39;s state until a call is offered.</li>
				</ol>
			</td>
		</tr>
		<tr align="left" valign="top">
			<td>Seimens</td>
			<td>OpenScape Voice</td>
			<td> </td>
			<td>v6.00.01</td>
		</tr>
	</tbody>
</table>
<br />


## Supported in Lync 2010

<strong><em>Table 2 - IP PBXs supported in Lync 2010</em></strong>
<table border="1" cellpadding="5" cellspacing="" class="grid" style="border-collapse:collapse;background-color:white;" width="100%" xmlns="http://www.w3.org/1999/xhtml">
	<thead>
		<tr bgcolor="#DEDEDE">
			<td align="center" valign="top"><strong>IP-PBX Vendor</strong></td>
			<td align="center" valign="top"><strong>Tested Product</strong></td>
			<td align="center" valign="top"><strong>Supported Configuration</strong></td>
			<td align="center" valign="top"><strong>Software Version Tested</strong></td>
		</tr>
	</thead>
	<tbody>
		<tr align="left" valign="top">
			<td rowspan="3">Alcatel-Lucent</td>
			<td>OmniPCX Enterprise OXE</td>
			<td>Direct SIP</td>
			<td>R9.1</td>
		</tr>
		<tr>
			<td colspan="3" style="display:none;"> </td>
		</tr>
		<tr align="left" valign="top">
			<td colspan="3">
				<p>Configuration Notes:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>On Lync Mediation Server, Media Bypass, RTCP and REFER are set to disabled. Testing found Media Bypass does not work for inbound calls, REFER is not supported and Alcatel does not send RTCP messages.</li>
				</ol>
				<p>Known Limitations:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>When Lync user initiates a call to PBX or PSTN endpoint and subsequently places the call on hold, they will receive the error &quot;call could not be put on hold&quot; with the Lync client muted. Afterwards, the Lync client cannot be unmuted.</li>
                    <li>When a Lync user performs a Blind transfer of a PBX or PSTN call to another PBX, PSTN or Lync number, if the transfer target doesn&#39;t answer, the call cannot be recovered to the original call. If the transfer completes, the local PBX phone will still show connected to the first Lync user</li>
					<li>When an call is ringing to a Lync user, the caller (either on an Alcatel station or a PSTN line routed through the PBX) will not get a ring-back tone.</li>
					<li>Comfort noise generation is not supported. As a result, comfort noise is not played on Microsoft Lync.</li>
					<li>When a Lync user declines a PSTN call routed from some PSTN trunk configurations, the PSTN caller does not get disconnected, and instead will start to hear Ring-Back.</li>
					<li>Because Alcatel sends a 502 message for a T1 line out of service or disconnected instead of a 503, failover to an alternate route will not function.</li>
				</ol>
			</td>
		</tr>
		<tr align="left" valign="top">
			<td rowspan="6">Avaya</td>
			<td>Aura Session Manager</td>
			<td>Direct SIP</td>
			<td>6.0.1</td>
		</tr>
		<tr>
			<td colspan="3" style="display:none;"> </td>
		</tr>
		<tr align="left" valign="top">
			<td colspan="3">
				<p>Configuration Notes:</p>
				<div style="margin-left:20px;margin-top:-12px;">
					<ol>
						<li>On Lync Mediation Server, Media Bypass and REFER are set to disabled. Testing found Media Bypass does not work for inbound calls and REFER is not supported.</li>
						<li>TLS and SRTP are not supported by Avaya and as a result need to be set to disabled on Mediation Server.</li>
					</ol>
				</div>
				<p>Known Limitations:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>Avaya does not support using an FQDN in the connection field.</li>
					<li>Comfort noise generation is not supported. As a result, comfort noise is not played on Lync.</li>
					<li>Testing found when calls routed to Avaya Audix voice mail may hear partial audio followed by disconnection.</li>
				</ol>
			</td>
		</tr>
		<tr align="left" valign="top">
			<td>Communications Manager SIP Enablement Services</td>
			<td>Direct SIP</td>
			<td>4.0<br />5.1<br />5.2.1</td>
		</tr>
		<tr>
			<td colspan="3" style="display:none;"> </td>
		</tr>
		<tr align="left" valign="top">
			<td colspan="3">
				<p>Documentation: <a href="https://www.microsoft.com/en-us/download/details.aspx?displaylang=en&amp;id=2187">Integrating Microsoft Lync Server 2010 and Avaya Communications Manager S8300</a></p>
				<p>Configuration Notes:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>On the Avaya IP-PBX, the configuration requires setting &quot;Alternate Route Timer(sec)&quot; value from default of 10 sec to 30 sec. The configuration should show &quot;Alternate Route Timer(sec): 30&quot; in the corresponding SIP signaling group.</li>
					<li>On Lync Mediation Server, Media Bypass and REFER are set to disabled. Testing found Media Bypass does not work for inbound calls and REFER is not supported.</li>
				</ol>
				<p>Known Limitations:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>When a Lync user transfers a PBX call to another PBX user, the local PBX phone will still show connected to the first Lync user.</li>
					<li>When a call is ringing to a Lync user, the caller (either on an Avaya station or a PSTN line routed through the PBX) will not get a ring-back tone. This issue has been resolved by Avaya with the 5.2.1 SP1 software release.</li>
					<li>Monitoring reports will not contain information regarding jitter and packet loss.</li>
					<li>Comfort noise generation is not supported. As a result, comfort noise is not played on Lync.</li>
					<li>ISDN Failover is not supported from a Lync perspective. If the Avaya PBX is being used for PSTN connectivity and multiple T1s are being utilized, a Lync client will not retry a call based on a T1 being unavailable. It may be possible to configure the PBX to not assign outbound calls from Lync to an unavailable T1, but this configuration was not tested.</li>
				</ol>
			</td>
		</tr>
		<tr align="left" valign="top">
			<td rowspan="10">Cisco</td>
			<td colspan="3">Documentation: <a href="https://www.microsoft.com/en-us/download/details.aspx?id=26800">Integrating Microsoft Lync Server 2010 and Cisco Unified Communications Manager</a></td>
		</tr>
		<tr align="left" valign="top">
            <td>Cisco Unified Communications Manager<br />Cisco Unified Session Manager<em></td>
			<td>Direct SIP</td>
			<td>UCM 8.5.1.12900-7</td>
		</tr>
		<tr>
			<td colspan="3" style="display:none;"> </td>
		</tr>
		<tr align="left" valign="top">
			<td colspan="3">
				<p>Configuration Notes:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>On the Cisco IP-PBX, configure MTP to enabled and PRACK to enabled.</li>
                    <li>On Lync Mediation Server, Media Bypass is set to enabled. RTCP is set to disabled, as Cisco doesn&#39;t send RTCP messages. REFER should be set to enabled, as REFER is supported by this IP-PBX.</li>
				</ol>
				<p>Known Limitations:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>Comfort noise generation is not supported. As a result, comfort noise is not played on Microsoft Lync. When a Lync user configures call forward or simul-ring to a PSTN IVR number, the calling party will not hear early media played from the IVR.</li>
				</ol>
                <p></em> <b>Note:</b> Cisco states that Unified Session Manager is based on the same SIP capability as Unified Communications Manager. As such, it is supported with the same capabilities as the qualified version of Unified Communications Manager.</p>
			</td>
		</tr>
		<tr align="left" valign="top">
			<td>Cisco Unified Communications Manager</td>
			<td>Direct SIP</td>
			<td>UCM 8.0.3.21900-8</td>
		</tr>
		<tr>
			<td colspan="3" style="display:none;"> </td>
		</tr>
		<tr align="left" valign="top">
			<td colspan="3">
				<p>Configuration Notes:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>On the Cisco IP-PBX, configure MTP to enabled and PRACK to disabled (the default for PRACK). The PRACK message sent by CUCM 4 is malformed by missing the MAXFORWARDS header.</li>
                    <li>On Lync Mediation Server, Media Bypass is set to enabled. RTCP and REFER are set to disabled, as Cisco doesn&#39;t send RTCP messages and REFER is not supported by this IP-PBX.</li>
				</ol>
				<p>Known Limitations:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>Comfort noise generation is not supported. As a result, comfort noise is not played on Microsoft Lync.</li>
					<li>When a Lync user configures call forward or simul-ring to a PSTN IVR number, the calling party will not hear early media played from the IVR.</li>
				</ol>
			</td>
		</tr>
		<tr align="left" valign="top">
			<td>Cisco Unified Communications Manager</td>
			<td>Direct SIP</td>
			<td>UCM 4.2 2000-4-4a<br />UCM 6.1.3.2000-1<br />UCM 7.1.3.10000-11</td>
		</tr>
		<tr>
			<td colspan="3" style="display:none;"> </td>
		</tr>
		<tr align="left" valign="top">
			<td colspan="3">
				<p>Configuration Notes:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>On the Cisco IP-PBX, configure MTP to enabled and PRACK to disabled (the default for PRACK). The PRACK message sent by CUCM 4 is malformed by missing the MAXFORWARDS header.</li>
                    <li>On Lync Mediation Server, Media Bypass is set to enabled. RTCP and REFER are set to disabled, as Cisco doesn&#39;t send RTCP messages and REFER is not supported by this IP-PBX.</li>
				</ol>
				<p>Known Limitations:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>When a Lync user transfers a PBX call to another PBX user, the local PBX phone will still show connected to the first Lync user.</li>
					<li>Comfort noise generation is not supported. As a result, comfort noise is not played on Microsoft Lync.</li>
					<li>When a Lync user configures call forward or simul-ring to a PSTN IVR number, the calling party will not hear early media played from the IVR.</li>
				</ol>
			</td>
		</tr>
	</tbody>
</table>

For more information on Direct SIP Configurations with Lync Server, please see: [PSTN Connectivity Components](../../SfbServer/plan-your-deployment/enterprise-voice-solution/pstn-connectivity.md).
