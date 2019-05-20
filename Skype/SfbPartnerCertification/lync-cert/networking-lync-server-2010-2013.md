---
title: "Partner qualification for Lync"
ms.author: v-lanac
author: lanachin
manager: serdars
ms.reviewer: dougand
ms.topic: article
ms.tgt.pltfrm: lync
ms.service: skype-for-business
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

# Networking for Lync Server 2010 and 2013

The tables that follows shows the network infrastructure solutions that have been tested by these partners and reviewed by Microsoft to meet Lync Server 2010 requirements. We recommend that you visit the partner’s web site for the latest information regarding product specifications, capacity, country support and documentation including release notes and known issues. 

Additional information on networking with Microsoft Lync Server 2010, including Planning, QoS, Call Admission Control and Security can be found on the [Lync Server Network Infrastructure Roadmap](infra-roadmap.md). 

For more information on optimizing Wi-Fi networks with Microsoft Lync, please see the white paper [Network Planning, Monitoring, and Troubleshooting with Lync Server](https://www.microsoft.com/en-us/download/details.aspx?id=39084).

Please contact the listed partner for more information on these products.

## WiFi

<table border="1" cellpadding="5" cellspacing="" class="grid" style="border-collapse:collapse;background-color:white;" width="100%" xmlns="http://www.w3.org/1999/xhtml">
	<colgroup>
		<col width="138" />
		<col width="510" />
		<col width="242" />
	</colgroup>
	<tr bgcolor="#DEDEDE">
		<td><strong>Vendor</strong></td>
		<td><strong>Qualified Device</strong></td>
		<td><strong>Controller Used</strong></td>
		<td><strong>Firmware Version Tested</strong></td>
	</tr>
	<tr align="left" valign="top">
		<td><a href="http://www.aerohive.com/products/overview/access-points.html">Aerohive Networks</a></td>
		<td>AP350 &amp; AP330 Access Points</td>
		<td> </td>
		<td>HiveOS 6.4r1</td>
	</tr>
	<tr align="left" valign="top">
		<td rowspan="3"><a href="http://www.arubanetworks.com/solutions/lync">Aruba Networks, Inc.</a></td>
		<td>Aruba Mobility Controller and Aruba AP 204/205, AP 214/215, AP 224/225, AP 274/275 802.11ac Access Points</td>
		<td>3600</td>
		<td>AOS 6.4.2.0</td>
	</tr>
	<tr align="left" valign="top">
		<td>Aruba Mobility Controller and Dual-Radio 802.11n Aruba Access Points</td>
		<td> </td>
		<td>AOS 6.1.3.2</td>
	</tr>
	<tr align="left" valign="top">
		<td>Virtual controller for Aruba Instant. IAP 224/225, IAP 274/275 802.11ac Instant Access Points. Dual-Radio 802.11n Instant Access Points</td>
		<td> </td>
		<td>4.0.0.7</td>
	</tr>
	<tr align="left" bgcolor="#F8F8F8" valign="top">
		<td rowspan="4"><a href="http://www.cisco.com/c/dam/en/us/products/collateral/wireless/lync.pdf">Cisco Systems</a></td>
		<td>Cisco Wireless LAN Controllers, Cisco Aironet 802.11n Access Points</td>
		<td>AIR-CT5508-K9</td>
		<td>SW 7.6</td>
	</tr>
	<tr align="left" bgcolor="#F8F8F8" valign="top">
		<td>AP 2700, AP 3700, AP 1570</td>
		<td>5500/7500/8500/WiSM2</td>
		<td>AireOS 8.0.100.0</td>
	</tr>
	<tr align="left" bgcolor="#F8F8F8" valign="top">
		<td>AP 2700, AP 3700, AP 1570</td>
		<td>3650/3850/5760</td>
		<td>IOS-XE 03.07.00E</td>
	</tr>
	<tr align="left" bgcolor="#F8F8F8" valign="top">
		<td>AP 1700, AP 3700</td>
		<td>5508</td>
		<td>IOS-XE: 03.07.00E / AireOS 8.0.100.0</td>
	</tr>
	<tr align="left" valign="top">
		<td rowspan="3"><a href="http://www.dell.com/us/business/p/powerconnect-w-series?~ck=anav">Dell, Inc.</a></td>
		<td>Dell Networking W-Series Mobility Controller and W-AP204/205, W-AP214/215, W-AP224/225, W-AP274/275 802.11ac Access Points.</td>
		<td>W-3600</td>
		<td>AOS 6.4.2.0 and higher</td>
	</tr>
	<tr align="left" valign="top">
		<td>Dell Networking W-Series Mobility Controller and Dual-Radio 802.11n Access Points.</td>
		<td>W-3600</td>
		<td>AOS 6.1.3.2 and higher</td>
	</tr>
	<tr align="left" valign="top">
		<td>Virtual controller for Dell Networking W-Series Instant. W-IAP224/225, W-IAP274/275 802.11ac Instant Access Points. Dual-Radio 802.11n Instant Access Points.</td>
		<td>n/a</td>
		<td>4.0.0.7 and higher</td>
	</tr>
	<tr align="left" bgcolor="#F8F8F8" valign="top">
		<td rowspan="2"><a href="http://www.extremenetworks.com/product/microsoft-lync-solutions">Extreme Networks</a></td>
		<td>IdentiFi Wireless Appliances and IdentiFi 802.11n Access Points</td>
		<td>IdentiFi V2110 Virtual Controller on Vmware</td>
		<td>9.01.01.0228</td>
	</tr>
	<tr align="left" bgcolor="#F8F8F8" valign="top">
		<td>WS-AP3825e, WS-AP3825i, WS-AP3865 802.11ac Access Points</td>
		<td>IdentiFi V2110 Virtual Controller on Vmware</td>
		<td>09.12.01.0067</td>
	</tr>
	<tr align="left" valign="top">
		<td rowspan="2"><a href="https://support.hpe.com/hpesc/public/home/signin">HP</a>
<!-- this link no longer works 
<a href="http://h17007.www1.hp.com/us/en/networking/solutions/allianceone/lync.aspx#.U6LD2HlOVaQ">HP, H3C</a> -->
        </td>
		<td>MSM720/MSM760/MSM765 zl/MSM775 zl Wireless LAN Controllers<br />and<br />MSM430/MSM460/MSM466/MSM466-R and HP 425 Access Points</td>
		<td>MSM720</td>
		<td>6.0.1.1</td>
	</tr>
	<tr align="left" valign="top">
		<td>HP 560, HP 425, MSM430/MSM460/MSM466/MSM466-R</td>
		<td>HP 830 8G</td>
		<td>3507P26</td>
	</tr>
	<tr align="left" bgcolor="#F8F8F8" valign="top">
		<td><a href="https://www.juniper.net/us/en/partners/technology-alliances/unified-communications/">Juniper Networks</a></td>
		<td>Wireless LAN Controllers, WLA532 Wireless LAN APs</td>
		<td>WLC880R</td>
		<td>MSS 8.0</td>
	</tr>
	<tr align="left" valign="top">
		<td><a href="http://www.merunetworks.com/products/technology/microsoft-lync/index.html">Meru Networks</a></td>
		<td>AP-322, AP-832, AP-822 802.11ac Access Points and MC-4200 Controller</td>
		<td>MC-4200</td>
		<td>6.1.2</td>
	</tr>
	<tr align="left" bgcolor="#F8F8F8" valign="top">
		<td><a href="https://atgsupportcentral.motorolasolutions.com/content/emb/docs/manuals/Lync_AP_Test_Results.pdf">Motorola Solutions</a></td>
		<td>Motorola Wireless LAN Controllers and 802.11n Access Points</td>
		<td>NX9510</td>
		<td>WiNG 5.5.0.0</td>
	</tr>
	<tr align="left" valign="top">
		<td><a href="http://a030f85c1e25003d7609-b98377aee968aad08453374eb1df3398.r40.cf2.rackcdn.com/other/bpcg-lync-ruckus.pdf">Ruckus</a></td>
		<td>ZoneFlex R500, R600, T300 802.11ac Access Points</td>
		<td>Zone Director 1200, 3000, 5000</td>
		<td>9.9.0/0 build 118</td>
	</tr>
	<tr align="left" bgcolor="#F8F8F8" valign="top">
		<td><a href="http://a030f85c1e25003d7609-b98377aee968aad08453374eb1df3398.r40.cf2.rackcdn.com/other/bpcg-lync-ruckus.pdf">Ruckus Wireless</a></td>
		<td>Ruckus Wireless LAN Controllers and 802.11n Access Points</td>
		<td>SCG-200</td>
		<td>SCG 2.5</td>
	</tr>
</table>

## Wired

<table border="1" cellpadding="5" cellspacing="" class="grid" style="border-collapse:collapse;background-color:white;" width="100%" xmlns="http://www.w3.org/1999/xhtml">
	<colgroup>
		<col width="138" />
		<col width="684" />
	</colgroup>
	<tr bgcolor="#DEDEDE">
		<td><strong>Vendor</strong></td>
		<td><strong>Qualification</strong></td>
	</tr>
	<tr align="left" valign="top">
		<td><a href="http://www.arubanetworks.com/solutions/lync">Aruba Networks</a></td>
		<td>S1500, S2500, and S3500 Mobility Access Switches</td>
	</tr>
	<tr align="left" valign="top">
		<td><a href="http://www.brocade.com/downloads/documents/deployment_guides/Brcd_MS_Lync_Server.pdf">Brocade</a></td>
		<td>Brocade MLX, SX, ICX, VDX, 5120</td>
	</tr>
	<tr align="left" bgcolor="#F8F8F8" valign="top">
		<td rowspan="2"><a href="http://www.dell.com/learn/us/en/04/campaigns/networking?c=us%26l=en%26s=bsd">Dell, Inc.</a></td>
		<td>
			<p>Dell Networking OS9.5 and higher with Dell Networking Switch Models:</p>
			<p>S4810, S6000, S5000, S4820T, Z9500, Z9000, M I/0 aggregator, MXL 10/40 GbE</p>
		</td>
	</tr>
	<tr align="left" bgcolor="#F8F8F8" valign="top">
		<td>
			<p>Dell Networking OS6.1.0.1 and higher with Dell Networking Switch Models:</p>
			<p>N4064, N4064F, N4032, N4032F, N3048P, N3048, N3024P, N3024, N3024F, N2048P, N2048, N2024P, N2024, 8164, 8164F, 8132, 8132F</p>
		</td>
	</tr>
	<tr align="left" valign="top">
		<td><a href="http://www.extremenetworks.com/partners/tsp/convergence/microsoft-lync">Extreme Networks</a></td>
		<td>ExtremeXOS 15.3.14</td>
	</tr>
	<tr align="left" bgcolor="#F8F8F8" valign="top">
		<td><a href="https://support.hpe.com/hpesc/public/home/signin">HP</a></td>
		<td>HP 2610, 2910al, 3500yl, 5400zl, 8200zl</td>
	</tr>
	<tr align="left" valign="top">
		<td><a href="http://www.juniper.net/us/en/dm/microsoft-lync/">Juniper Networks</a></td>
		<td>Juniper 10.2R2.11</td>
	</tr>
</table>

