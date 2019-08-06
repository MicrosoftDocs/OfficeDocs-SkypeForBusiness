---
title: "Infrastructure qualified for Lync - IP PBXs and Gateways "
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
- Dn788945
description: "Infrastructure qualifications including PSTN gateways and IP PBX products, along with the necessary firmware combinations, that have been independently qualified for  Lync Server."
---

# IP PBXs and Gateways

## Qualified IP PBXs & Gateways

The tables that follow list the PSTN gateways and IP-PBX products along with the necessary firmware combinations that have been independently qualified for use with Lync Server.

We recommend that you visit the vendor's web site for the latest information regarding protocol, capacity, country support and documentation including a Quick Start Guide, release notes and any known issues.

### Qualified for Lync 2013

***Table 1 - Qualified IP PBXs & Gateways  for Lync 2013***

 &#x2714;= Qualified&nbsp;&nbsp;&nbsp;&nbsp;&#x2714;+S = Qualified with SRTP & TLS
<table border="1" cellpadding="5" cellspacing="" class="grid" style="border-collapse:collapse;background-color:white;" width="100%" xmlns="http://www.w3.org/1999/xhtml">
	<colgroup>
		<col width="140" />
		<col width="270" />
		<col width="344" />
		<col width="169" />
		<col width="148" />
	</colgroup>
	<thead>
		<tr bgcolor="#DEDEDE">
			<td align="center" valign="top"><strong>Vendor</strong></td>
			<td align="center" valign="top"><strong>Qualified Product</strong></td>
			<td align="center" valign="top"><strong>Software Version Tested</strong></td>
			<td align="center" colspan="2" valign="top"><strong>Supported Configuration</strong></td>
		</tr>
	</thead>
	<tbody>
		<tr align="left" valign="top">
			<td rowspan="5"><a href="http://www.audiocodes.com/microsoft">Audiocodes</a></td>
			<td>Mediant 500</td>
			<td>6.60A.236.002</td>
			<td>Basic Gateway</td>
			<td align ="center" valign="middle">&#x2714;+S</td>
		</tr>
		<tr align="left" valign="top">
			<td>Mediant 800</td>
			<td>6.60A.236.002</td>
			<td>Basic Gateway</td>
			<td align ="center" valign="middle">&#x2714;+S</td>
		</tr>
		<tr align="left" valign="top">
			<td>Mediant 1000</td>
			<td>6.60A.022.003</td>
			<td>Enhanced Gateway</td>
			<td align ="center" valign="middle">&#x2714;+S; with IPv6</td>
		</tr>
		<tr align="left" valign="top">
			<td>Mediant 2000</td>
			<td>6.60A.236.002</td>
			<td>Enhanced Gateway</td>
			<td align ="center" valign="middle">&#x2714;+S</td>
		</tr>
		<tr align="left" valign="top">
			<td>Mediant 3000</td>
			<td>6.60A.236.002</td>
			<td>Enhanced Gateway</td>
			<td align ="center" valign="middle">&#x2714;+S</td>
		</tr>
		<tr align="left" valign="top">
			<td><a href="http://bressner.com/ucfeaturebox-advanced-unified-box-communications/">Bressner</a></td>
			<td>UCFeatureBox UCFB-xxx</td>
			<td>r1.8-422960M</td>
			<td>Basic Gateway</td>
			<td align ="center" valign="middle">&#x2714;</td>
		</tr>
		<tr align="left" valign="top">
			<td rowspan="4"><a href="http://www.cisco.com/c/en/us/solutions/enterprise/interoperability-portal/networking_solutions_products_genericcontent0900aecd805bd0e4.html">Cisco</a></td>
			<td>ISR 3845</td>
			<td>15.1.4M6</td>
			<td>Basic Gateway</td>
			<td align ="center" valign="middle">&#x2714;</td>
		</tr>
		<tr align="left" valign="top">
			<td colspan="4">
				<p>Documentation: <a href="https://www.microsoft.com/en-us/download/details.aspx?id=41153">Integrating Lync 2013 and ISR 3845 Configuration Guide v1.0</a></p>
				<p>Configuration Notes:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>Disable REFER and RTCP support on both Lync Mediation Server and Cisco GW.</li>
					<li>While a specific ISR model was tested, any model in this series running the qualified firmware is supported.</li>
				</ol>
				<p>Known Limitations:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>Analog devices connected to FXS ports do not support hold/resume. To support hold/resume, the FXS port needs to be controlled by a Cisco PBX.</li>
					<li>No ringback is heard when call is forwarded from a Lync Endpoint to a PSTN Endpoint. This can be corrected by allowing 183 without SDP on the outbound dial-peers to Lync, but this will result in no ring back on regular inbound calls.</li>
				</ol>
			</td>
		</tr>
		<tr align="center" valign="middle">
			<td>ISR 3925</td>
			<td>15.3(3)M1</td>
			<td>Basic Gateway</td>
			<td>&#x2714;</td>
		</tr>
		<tr align="left" valign="top">
			<td colspan="4">
				<p>Configuration Notes:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>Disable REFER and RTCP support on both Lync Mediation Server and Cisco GW.</li>
					<li>While a specific ISR model was tested, any model in this series running the qualified firmware is supported.</li>
				</ol>
				<p>Known Limitations:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>Call Park on Lync Client fails. Lync Client drops the call as the Gateway responds with &quot;a=sendrecv&quot; to an INVITE from Lync to place the call on hold. This issue is documented under case number CSCuo44538 with Cisco Support.</li>
					<li>As the Gateway overrides the progress indicator from Lync Server, PSTN calling party does not hear IVR when the Lync called party is set to simultaneous ring an IVR number with Early Media.</li>
					<li>Call Hold and transfer on Analog Endpoints fails with the recommended dial peer configuration on the ISR.</li>
				</ol>
			</td>
		</tr>
		<tr align="left" valign="top">
			<td rowspan="2"><a href="https://www.ipecs.com/site/lgericsson/menu/157.do?scene=detail&amp;productNo=28">Ericsson-LG Enterprise</a></td>
			<td>IPECS IP-PBX</td>
			<td>IP-PBX</td>
			<td>5.5Bd</td>
			<td> </td>
		</tr>
		<tr align="left" valign="top">
			<td colspan="4">
				<p>Configuration Notes:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>Disable REFER support on Lync Mediation Server</li>
				</ol>
				<p>Known Limitations:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>DNS Load Balancing and IPv6 are not supported</li>
				</ol>
			</td>
		</tr>
		<tr align="left" valign="top">
			<td rowspan="4">Genband</td>
			<td>Experius AS</td>
			<td>10.3</td>
			<td>PBX</td>
			<td> </td>
		</tr>
		<tr>
			<td>C2100</td>
			<td>SE17</td>
			<td>PBX</td>
			<td> </td>
		</tr>
		<tr>
			<td>C20</td>
			<td>CVM17</td>
			<td>PBX</td>
			<td> </td>
		</tr>
		<tr align="left" valign="top">
			<td colspan="4">
				<p>Experius AS Notes:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>PBX is tested and is supported only with an AudioCodes Mediant 1000 Gateway v6.2</li>
					<li>When a user configures simul-ring to a PSTN IVR number, the calling party will hear ring back not early media played from the IVR</li>
					<li>PBX does not support DNS load balancing</li>
					<li>PBX does not generate OPTIONS ping</li>
				</ol>
				<p>C2100 &amp; C20 Notes:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>PBX is tested and is supported only with a Genband Quantix SBC v8.3.4.0</li>
					<li>PBX does not support DNS Load Balancing,Media Bypass,or REFER</li>
					<li>PBX does not generate OPTIONS ping</li>
				</ol>
			</td>
		</tr>
		<tr align="left" valign="top">
			<td><a href="http://www.mediagateway.de/">Ferrari electronic AG</a></td>
			<td>OfficeMaster Gate</td>
			<td>4.0-1</td>
			<td>Enhanced Gateway</td>
			<td align ="center" valign="middle">&#x2714;+S; with IPv6</td>
		</tr>
		<tr align="left" valign="top">
			<td rowspan="2"><a href="http://h17007.www1.hp.com/us/en/networking/solutions/unified-communications-and-collaboration/index.aspx#survivablebm">HP</a></td>
			<td>FlexBranch Multi-Service Router (MSR) Series</td>
			<td>Comware, version 5.2, Release 2317</td>
			<td>Enhanced Gateway</td>
			<td align ="center" valign="middle">&#x2714;+S</td>
		</tr>
		<tr align="left" valign="top">
			<td>Flexbranch MSR</td>
			<td>Comware, version 7.1</td>
			<td>Enhanced Gateway</td>
			<td align ="center" valign="middle">&#x2714;+S</td>
		</tr>
		<tr align="left" valign="top">
			<td><a href="http://www.itibia.com/product_content.php?id=7&amp;productclassid=8&amp;productid=5">Itibia Technologies</a></td>
			<td>OfficeTen IPPBX 2800</td>
			<td>1.3.1.1</td>
			<td>IP-PBX</td>
			<td align ="center" valign="middle">&#x2714;+S</td>
		</tr>
		<tr align="left" valign="top">
			<td rowspan="2"><a href="http://www.mitel.com/product-service/mitel-mivoice ">Mitel</a></td>
			<td>MiVoice MX-ONE</td>
			<td>5.0 SP3 HF2</td>
			<td>IP-PBX</td>
			<td align ="center" valign="middle">&#x2714;+S</td>
		</tr>
		<tr align="left" valign="top">
			<td>MiVoice Office 400</td>
			<td>R3.1</td>
			<td>IP-PBX</td>
			<td align ="center" valign="middle">&#x2714;+S</td>
		</tr>
		<tr align="left" valign="top">
			<td rowspan="2">Samsung</td>
			<td>Samsung Communication Manager</td>
			<td>Direct SIP</td>
			<td>4.1.0</td>
			<td> </td>
		</tr>
		<tr align="left" valign="top">
			<td colspan="4">
				<p>Configuration Notes:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>On Lync Mediation Server, Media Bypass and REFER are set to disabled. Testing found Media Bypass does not work for inbound calls and REFER is not supported.</li>
				</ol>
				<p>Known Limitations:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>DNS Load Balancing using the same FQDN for two IP addresses is not supported by the Samsung PBX.</li>
				</ol>
			</td>
		</tr>
		<tr align="left" valign="top">
			<td><a href="http://www.patton.com/partners/partner_detail.asp?i=42&amp;p=ippbx">Patton Electronics</a></td>
			<td>SmartNode SN4671</td>
			<td>6.T</td>
			<td>Basic Gateway</td>
			<td align ="center" valign="middle">&#x2714;</td>
		</tr>
		<tr align="left" valign="top">
			<td rowspan="4"><a href="http://www.sangoma.com/solutions/vega-gateways-for-microsoft-lync/">Sangoma Technologies</a></td>
			<td>Netborder Express Gateway</td>
			<td>4.4</td>
			<td>Basic Gateway</td>
			<td align ="center" valign="middle">&#x2714;</td>
		</tr>
		<tr align="left" valign="top">
			<td>Vega 400g</td>
			<td>R100S044</td>
			<td>Basic Gateway</td>
			<td align ="center" valign="middle">&#x2714;</td>
		</tr>
		<tr align="left" valign="top">
			<td>Vega 200g</td>
			<td>R100S044</td>
			<td>Basic Gateway</td>
			<td align ="center" valign="middle">&#x2714;</td>
		</tr>
		<tr align="left" valign="top">
			<td>Vega 100g</td>
			<td>R100S044</td>
			<td>Basic Gateway</td>
			<td align ="center" valign="middle">&#x2714;</td>
		</tr>
		<tr align="left" valign="top">
			<td rowspan="2"><a href="http://www.sonus.net/solutions/enterprises/microsoft-lync">Sonus</a></td>
			<td>SBC 1000/2000</td>
			<td>2.2.1, V 3.1.1v285</td>
			<td>Enhanced Gateway</td>
			<td align ="center" valign="middle">&#x2714;+S</td>
		</tr>
		<tr align="left" valign="top">
			<td>VX 1200</td>
			<td>V 4.9v55</td>
			<td>Enhanced Gateway</td>
			<td align ="center" valign="middle">&#x2714;+S</td>
		</tr>
	</tbody>
</table>
<br/><br/>

### Qualified for Lync 2010

***Table 2 - Qualified IP PBXs & Gateways for Lync 2010***<br/><br/>
 &#x2714;= Qualified&nbsp;&nbsp;&nbsp;&nbsp;&#x2714;+S = Qualified with SRTP & TLS
<table border="1" cellpadding="5" cellspacing="" class="grid" style="border-collapse:collapse;background-color:white;" width="100%" xmlns="http://www.w3.org/1999/xhtml">
	<colgroup>
		<col width="140" />
		<col width="270" />
		<col width="450" />
		<col />
		<col />
	</colgroup>
	<thead>
		<tr bgcolor="#DEDEDE">
			<td align="center" valign="top"><strong>Vendor</strong></td>
			<td align="center" valign="top"><strong>Qualified Product</strong></td>
			<td align="center" valign="top"><strong>Software Version Tested</strong></td>
			<td align="center" colspan="2" valign="top"><strong>Supported Configuration</strong></td>
		</tr>
	</thead>
	<tbody>
		<tr align="left" valign="top">
			<td rowspan="3"><a href="http://www.aastra.com/microsoft-uc-integration.htm">Aastra</a></td>
			<td>MX-One</td>
			<td>4.1 SP3</td>
			<td>IP-PBX</td>
			<td align ="center" valign="middle">&#x2714;+S </td>
		</tr>
		<tr>
			<td colspan="4" style="display:none;"> </td>
		</tr>
		<tr align="left" valign="top">
			<td colspan="4">
				<p>Configuration Notes:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>On Lync Mediation Server, Enable Media Bypass and RTCP, but Disable REFER. Testing determined that REFER does not function.</li>
					<li>MX-One does not support sending DTMF as a part of early media.</li>
				</ol>
			</td>
		</tr>
		<tr align="left" valign="top">
			<td rowspan="4"><a href="http://www.audiocodes.com/microsoft">Audiocodes</a></td>
			<td>Mediant 800 MSBG</td>
			<td>6.00AL.019.007</td>
			<td>Enhanced Gateway</td>
			<td align ="center" valign="middle">&#x2714;+S </td>
		</tr>
		<tr align="left" valign="top">
			<td>Mediant 1000</td>
			<td>6.00A.033.005</td>
			<td>Enhanced Gateway</td>
			<td align ="center" valign="middle">&#x2714;+S </td>
		</tr>
		<tr align="left" valign="top">
			<td>Mediant 2000</td>
			<td>6.00A.033.005</td>
			<td>Enhanced Gateway</td>
			<td align ="center" valign="middle">&#x2714;+S </td>
		</tr>
		<tr align="left" valign="top">
			<td>Mediant 3000</td>
			<td>6.00A.033.005</td>
			<td>Enhanced Gateway</td>
			<td align ="center" valign="middle">&#x2714;+S</td>
		</tr>
		<tr align="left" valign="top">
			<td rowspan="5"><a href="http://www.cisco.com/c/en/us/solutions/enterprise/interoperability-portal/networking_solutions_products_genericcontent0900aecd805bd0e4.html">Cisco</a></td>
			<td>ISR 29xx / 39xx</td>
			<td>15.1(3)T</td>
			<td>Basic Gateway</td>
			<td align ="center" valign="middle">&#x2714;</td>
		</tr>
		<tr align="left" valign="top">
			<td>ISR 2811</td>
			<td>12.4(24)T</td>
			<td>Basic Gateway</td>
			<td align ="center" valign="middle">&#x2714;</td>
		</tr>
		<tr align="left" valign="top">
			<td>ISR 3845</td>
			<td>12.4(15)T3</td>
			<td>Basic Gateway</td>
			<td align ="center" valign="middle">&#x2714;</td>
		</tr>
		<tr>
			<td colspan="4" style="line-height:0;font-size:0;display:none;"> </td>
		</tr>
		<tr align="left" valign="top">
			<td colspan="4">
				<p>Configuration Notes:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>Disable REFER on both Lync Mediation Server and Cisco GW.</li>
					<li>On Lync Mediation Server, disable TLS and SRTP.  Secure connectivity is not supported. </li>
				</ol>
				<p>Known Limitations:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>Analog devices connected to FXS ports do not support hold/resume. To support hold/resume, the FXS port needs to be controlled by a Cisco PBX.</li>
				</ol>
			</td>
		</tr>
		<tr align="left" valign="top">
			<td rowspan="3"><a href="http://www.dialogic.com/Solutions/Unified-Communications/UC-Connectivity/Microsoft-Lync.aspx">Dialogic</a></td>
			<td>DMG1000</td>
			<td>6.0 SU7</td>
			<td>Enhanced Gateway</td>
			<td align ="center" valign="middle">&#x2714;+S </td>
		</tr>
		<tr align="left" valign="top">
			<td>DMG2000</td>
			<td>6.0 SU7</td>
			<td>Enhanced Gateway</td>
			<td align ="center" valign="middle">&#x2714;+S </td>
		</tr>
		<tr align="left" valign="top">
			<td>DMG4000</td>
			<td>SU4, SIPcontrol 2.5, DIVA System Release 9.5 Win</td>
			<td>Basic Gateway</td>
			<td align ="center" valign="middle">&#x2714;+S </td>
		</tr>
		<tr align="left" valign="top">
			<td><a href="http://www.mediagateway.de/">Ferrari Electronic AG</a></td>
			<td>OfficeMaster Gate</td>
			<td>3, 3.3</td>
			<td>Enhanced Gateway</td>
			<td align ="center" valign="middle">&#x2714;+S </td>
		</tr>
		<tr align="left" valign="top">
			<td rowspan="4"><a href="http://www.genband.com/">Genband</a></td>
			<td>A2</td>
			<td>8.0 SP1</td>
			<td>IP-PBX</td>
		<td align ="center" valign="middle">&#x2714;</td>
		</tr>
		<tr align="left" valign="top">
			<td>C20</td>
			<td>CVM14</td>
			<td>IP-PBX</td>
			<td align ="center" valign="middle">&#x2714;</td>
		</tr>
		<tr>
			<td colspan="4" style="line-height:0;font-size:0;display:none;"> </td>
		</tr>
		<tr align="left" valign="top">
			<td colspan="4">
				<p>Configuration Notes:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>Disable REFER, TLS and SRTP on Mediation Server. They are not supported by Genband.</li>
				</ol>
				<p>Known Limitations:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>Media Bypass is not supported.</li>
					<li>DNS load balancing is not supported by the Genband C20, but load-balancing to multiple provisioned IP addresses is supported.</li>
				</ol>
			</td>
		</tr>
		<tr align="left" valign="top">
			<td rowspan="6"><a href="http://enterprise.huawei.com/en/">Huawei</a></td>
			<td>AR1220</td>
			<td>V200R001C01</td>
			<td>IP-PBX </td>
			<td align ="center" valign="middle">&#x2714;</td>
		</tr>
		<tr>
			<td colspan="4" style="line-height:0;font-size:0;display:none;"> </td>
		</tr>
		<tr align="left" valign="top">
			<td colspan="4">
				<p>Configuration Notes:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>Disable REFER, TLS and SRTP on Medaition Server. They are not supported by Huawei.</li>
				</ol>
				<p>Known Limitations:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>DNS load balancing is not supported by Huawei.</li>
					<li>Mediation Server Failover is not suppored by Huawei.</li>
				</ol>
			</td>
		</tr>
		<tr>
			<td>eSpace <a href="http://enterprise.huawei.com/en/products/coll-communication/union-comuni/ip_telephony/1en_u1910.htm">U1910</a>, <a href="http://enterprise.huawei.com/en/products/coll-communication/union-comuni/ip_telephony/1en_u1930.htm">U1930</a>, <a href="http://enterprise.huawei.com/en/products/coll-communication/union-comuni/ip_telephony/1en_u1980.htm">U1980</a></td>
			<td>V100R001</td>
			<td>IP-PBX </td>
			<td align ="center" valign="middle">&#x2714;+S </td>
		</tr>
		<tr>
			<td colspan="4" style="line-height:0;font-size:0;display:none;"> </td>
		</tr>
		<tr align="left" valign="top">
			<td colspan="4">
				<p>Configuration Notes:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>Disable REFER on Mediation Server. It is not supported by Huawei.</li>
				</ol>
			</td>
		</tr>
		<tr align="left" valign="top">
			<td rowspan="3"><a href="http://www.innovaphone.com/en/">Innovaphone</a></td>
			<td>IP3010</td>
			<td>v.9.00 [90773]</td>
			<td>IP-PBX </td>
		<td align ="center" valign="middle">&#x2714;+S</td>
		</tr>
		<tr>
			<td colspan="4" style="line-height:0;font-size:0;display:none;"> </td>
		</tr>
		<tr align="left" valign="top">
			<td colspan="4">
				<p>Configuration Notes:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>Media Bypass, TLS and SRTP are supported.</li>
					<li>Disable REFER on Lync Mediation Server. Attended Transfer functions correctly only when REFER is disabled.</li>
					<li>Disable RTCP on Lync Mediation Server for active calls and calls on hold. The session timer should be enabled.</li>
				</ol>
				<p>Known Limitations:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>While the IP-PBX supports Comfort Noise negotiation, it does not generate CN packets itself.</li>
				</ol>
			</td>
		</tr>
		<tr align="left" valign="top">
			<td><a href="http://www.inin.com/solutions/pages/microsoft-integrations.aspx">Interactive Intelligence</a></td>
			<td>Customer Interaction Center</td>
			<td>4.0 SU1</td>
			<td>IP-PBX</td>
			<td align ="center" valign="middle">&#x2714;</td>
		</tr>
		<tr align="left" valign="top">
			<td><a href="http://www.media5corp.com/en/">Media5</a></td>
			<td>Mediatrix 3000</td>
			<td>2.0.1v116</td>
			<td>Enhanced Gateway</td>
			<td align ="center" valign="middle">&#x2714;+S</td>
		</tr>
		<tr align="left" valign="top">
			<td rowspan="3"><a href="http://www.mitel.com/search/node/DocController">Mitel</a></td>
			<td>3300</td>
			<td>4.2.1.6</td>
			<td>IP-PBX</td>
			<td align ="center" valign="middle">&#x2714;</td>
		</tr>
		<tr>
			<td colspan="4" style="line-height:0;font-size:0;display:none;"> </td>
		</tr>
		<tr align="left" valign="top">
			<td colspan="4">
				<p>Configuration Notes:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>On Lync Mediation Server, Enable Media Bypass and Disable REFER and RTCP. Testing determined that Mitel does not support REFER and RTCP.</li>
				</ol>
				<p>Known Limitations:</p>
				<ol style="margin-left:20px;margin-top:-12px;">
					<li>When a Mitel user calls a Lync user, there is no ring back tone provided for the Mitel user. Mitel is investigating adding RFC 3960 support in the future.</li>
					<li>Mitel does not support comfort noise. As a result, comfort noise is not played on Microsoft Lync.</li>
				</ol>
			</td>
		</tr>
		<tr align="left" valign="top">
			<td><a href="http://www.patton.com/partners/partner_detail.asp?i=42&amp;p=ippbx">Patton Electronics</a></td>
			<td>SmartNode SN4671</td>
			<td>R6.T 2012-04-23</td>
			<td>Basic Gateway</td>
			<td align ="center" valign="middle">&#x2714;</td>
		</tr>
		<tr align="left" valign="top">
			<td><a href="http://www.sangoma.com/solutions/netborder-software-for-ms-lync/">Sangoma</a></td>
			<td>NetBorder Express</td>
			<td>6.0.42.4</td>
			<td>Basic Gateway</td>
			<td align ="center" valign="middle">&#x2714;+S </td>
		</tr>
		<tr align="left" valign="top">
			<td rowspan="6"><a href="http://www.sonus.net/solutions/enterprises/microsoft-lync">Sonus</a></td>
			<td>SBC 1000</td>
			<td>2.0.1v118</td>
			<td>Enhanced Gateway</td>
		<td align ="center" valign="middle">&#x2714;+S</td>
		</tr>
		<tr align="left" valign="top">
			<td>SBC 2000</td>
			<td>1.0.2v221</td>
			<td>Enhanced Gateway</td>
			<td align ="center" valign="middle">&#x2714;+S</td>
		</tr>
		<tr align="left" valign="top">
			<td>Tenor DX</td>
			<td>P108-09-18</td>
			<td>Basic Gateway</td>
			<td align ="center" valign="middle">&#x2714;</td>
		</tr>
		<tr align="left" valign="top">
			<td>UX1000</td>
			<td>2.0.1v118</td>
			<td>Enhanced Gateway</td>
			<td align ="center" valign="middle">&#x2714;+S </td>
		</tr>
		<tr align="left" valign="top">
			<td>UX2000</td>
			<td>1.0.2v221 patch 1<br />2.0.1v118</td>
			<td>Enhanced Gateway</td>
			<td align ="center" valign="middle">&#x2714;+S </td>
		</tr>
		<tr align="left" valign="top">
			<td>VX900<br />VX1200<br />VX1800</td>
			<td>4.7.2v69</td>
			<td>Enhanced Gateway</td>
			<td align ="center" valign="middle">&#x2714;+S </td>
		</tr>
	</tbody>
</table>


For more information on Direct SIP configurations, please see [PSTN Connectivity Components](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/enterprise-voice-solution/pstn-connectivity).