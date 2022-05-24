---
title: "Infrastructure qualified for Lync - IP PBXs and Gateways "
ms.author: serdars
author: msdmaguire
manager: serdars
ms.reviewer: dougand
ms.topic: article
ms.tgt.pltfrm: lync
ms.service: skype-for-business-online
ms.collection: Lync
audience: Admin
appliesto:
- Lync
- Skype for Business
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.custom:
- Lync Certification
- Dn788945
description: "Infrastructure qualifications including PSTN gateways and IP PBX products, along with the necessary firmware combinations, that have been independently qualified for  Lync Server."
---

# IP PBXs and Gateways

## Qualified IP PBXs & Gateways

The following PSTN gateways, IP-PBX products, and relevant firmware combinations have been independently qualified for use with Lync Server.

We recommend that you visit the vendor's web site for the latest information.

### Qualified for Lync 2013

***Table 1 - Qualified IP PBXs & Gateways  for Lync 2013***

 &#x2714;= Qualified&nbsp;&nbsp;&nbsp;&nbsp;&#x2714;+S = Qualified with SRTP & TLS
<table>
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
            <td rowspan="5"><a href="https://www.audiocodes.com/microsoft">Audiocodes</a></td>
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
            <td align ="center" valign="middle">&#x2714;+S; with IPv6</td>
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
            <td rowspan="4"><a href="https://www.cisco.com/c/en/us/solutions/enterprise/interoperability-portal/networking_solutions_products_genericcontent0900aecd805bd0e4.html">Cisco</a></td>
            <td>ISR 3845</td>
            <td>15.1.4M6</td>
            <td>Basic Gateway</td>
            <td align ="center" valign="middle">&#x2714;</td>
        </tr>
        <tr align="left" valign="top">
            <td colspan="4">
                <p>Documentation: <a href="https://www.microsoft.com/download/details.aspx?id=41153">Integrating Lync 2013 and ISR 3845 Configuration Guide v1.0</a></p>
                <p>Configuration Notes:</p>
                <ol>
                    <li>Disable REFER and RTCP support on both Lync Mediation Server and Cisco GW.</li>
                    <li>While a specific ISR model was tested, any model in this series running the qualified firmware is supported.</li>
                </ol>
                <p>Known Limitations:</p>
                <ol>
                    <li>Analog devices connected to FXS ports don't support hold/resume. To support hold/resume, the FXS port needs to be controlled by a Cisco PBX.</li>
                    <li>No ringback is heard when call is forwarded from a Lync Endpoint to a PSTN Endpoint. This issue can be corrected by allowing 183 without SDP on the outbound dial-peers to Lync, but this will result in no ring back on regular inbound calls.</li>
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
                <ol>
                    <li>Disable REFER and RTCP support on both Lync Mediation Server and Cisco GW.</li>
                    <li>While a specific ISR model was tested, any model in this series running the qualified firmware is supported.</li>
                </ol>
                <p>Known Limitations:</p>
                <ol>
                    <li>Call Park on Lync Client fails. Lync Client drops the call as the Gateway responds with "a=sendrecv" to an INVITE from Lync to place the call on hold. This issue is documented under case number CSCuo44538 with Cisco Support.</li>
                    <li>As the Gateway overrides the progress indicator from Lync Server, PSTN calling party doesn't hear IVR when the Lync called party is set to simultaneous ring an IVR number with Early Media.</li>
                    <li>Call Hold and transfer on Analog Endpoints fails with the recommended dial peer configuration on the ISR.</li>
                </ol>
            </td>
        </tr>
        <tr align="left" valign="top">
            <td rowspan="2"><a href=" https://ipecs.com/site/lgericsson/menu/">Ericsson-LG Enterprise</a></td>
            <td>IPECS IP-PBX</td>
            <td>IP-PBX</td>
            <td>5.5Bd</td>
            <td> </td>
        </tr>
        <tr align="left" valign="top">
            <td colspan="4">
                <p>Configuration Notes:</p>
                <ol>
                    <li>Disable REFER support on Lync Mediation Server</li>
                </ol>
                <p>Known Limitations:</p>
                <ol>
                    <li>DNS Load Balancing and IPv6 aren't supported</li>
                </ol>
            </td>
        </tr>
        <tr align="left" valign="top">
            <td rowspan="4">Genband</td>
            <td>Experius AS</td>
            <td>10.3</td>
            <td>PBX</td>
            <td> </td>
        </tr>
        <tr>
            <td>C2100</td>
            <td>SE17</td>
            <td>PBX</td>
            <td> </td>
        </tr>
        <tr>
            <td>C20</td>
            <td>CVM17</td>
            <td>PBX</td>
            <td> </td>
        </tr>
        <tr align="left" valign="top">
            <td colspan="4">
                <p>Experius AS Notes:</p>
                <ol>
                    <li>PBX is tested and is supported only with an AudioCodes Mediant 1000 Gateway v6.2</li>
                    <li>When a user configures simul-ring to a PSTN IVR number, the calling party will hear ring back not early media played from the IVR</li>
                    <li>PBX does'ot support DNS load balancing</li>
                    <li>PBX doesn't generate OPTIONS ping</li>
                </ol>
                <p>C2100 &amp; C20 Notes:</p>
                <ol>
                    <li>PBX is tested and is supported only with a Genband Quantix SBC v8.3.4.0</li>
                    <li>PBX doesn't support DNS Load Balancing, Media Bypass, or REFER</li>
                    <li>PBX doesn't generate OPTIONS ping</li>
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
            <td> </td>
        </tr>
        <tr align="left" valign="top">
            <td colspan="4">
                <p>Configuration Notes:</p>
                <ol>
                    <li>On Lync Mediation Server, Media Bypass and REFER are set to disabled. Testing found Media Bypass doesn't work for inbound calls and REFER isn't supported.</li>
                </ol>
                <p>Known Limitations:</p>
                <ol>
                    <li>DNS Load Balancing using the same FQDN for two IP addresses isn't supported by the Samsung PBX.</li>
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
            <td rowspan="4"><a href="https://www.sangoma.com/">Sangoma Technologies</a></td>
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
            <td rowspan="2">Sonus</td>
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

For more information on Direct SIP configurations, see [PSTN Connectivity Components](../../SfbServer/plan-your-deployment/enterprise-voice-solution/pstn-connectivity.md).
