---
title: "Virtual Desktop Infrastructure for Lync Server 2013"
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
- dn788944
description: "Partner qualification requirements for Lync: Virtual desktop infrastructure."
---

# Virtual Desktop Infrastructure for Lync Server 2013

The Virtual Desktop Infrastructure (VDI) Partner platforms and client hardware platforms listed in the table that follows are supported in Lync Server 2013. For a given configuration to be supported, both the VDI partner platform and the client hardware platform need to be supported.

## About VDI

With the release of Lync Server 2013, Microsoft has worked closely with multiple partners to bring enterprise-grade audio and video communication support using Lync to thin clients running in a Virtual Desktop Infrastructure (VDI) environment. This functionality works through a combination of the Lync rich client running in the datacenter along with a Lync VDI plug-in running in the local client hardware. The solution is extensible and designed to work on both VDI Partner platforms such as VMware and client hardware platforms such as Dell Wyse and HP.

### Related resources

[Deploying the Lync VDI Plug-in](../../SfbServer/deploy/deploy-clients/deploy-the-lync-vdi-plug-in.md)

[Troubleshooting the Lync VDI Plug-in](/previous-versions/office/lync-server-2013/lync-server-2013-troubleshooting-the-lync-vdi-plug-in) <!-- 2013 yet to migrate -->

## VDI environments
The following table lists the VDI partners and their products that have been tested with the Lync 2013 VDI plug-in. 

<table border="1" cellpadding="0" cellspacing="0" class="grid" width="100%">
    <colgroup>
        <col width="72" />
        <col width="264" />
        <col width="240" />
        <col width="236" />
        <col />
    </colgroup>
    <thead>
        <tr bgcolor="#DEDEDE">
            <td valign="top"><strong>Vendor</strong></td>
            <td valign="top"><strong>Tested Product</strong></td>
            <td valign="top"><strong>Local Client</strong></td>
            <td valign="top"><strong>Remote Server</strong></td>
            <td valign="top"><strong>Protocol</strong></td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan="2" valign="top">Citrix</td>
            <td valign="top">XenDesktop</td>
            <td valign="top">Citrix Receiver 4.1.02</td>
            <td valign="top">XenDesktop Virtual Delivery Agent 7.1</td>
            <td valign="top">ICA</td>
        </tr>
        <tr>
            <td colspan="4" valign="top">
                <p><a href="https://www.citrix.com/products/xendesktop/overview.html" title="https://www.citrix.com/products/xendesktop/overview.html">https://www.citrix.com/products/xendesktop/overview.html</a></p>
                <p>Note: Citrix VDI solution for Lync Plugin is currently approved for use with Win7 client OS. Testing on Win8 and 8.1 is in progress. For the best experience, Microsoft recommends updating to the latest available Lync cumulative update.</p>
            </td>
        </tr>
        <tr>
            <td rowspan="2" valign="top">Microsoft</td>
            <td valign="top">Microsoft Remote Desktop Services</td>
            <td valign="top">Remote Desktop Client<em></td>
            <td valign="top">Remote Desktop Server</td>
            <td valign="top">RDP</td>
        </tr>
        <tr>
            <td colspan="4" valign="top">
                <p><a href="https://www.microsoft.com/itpro/windows">https://www.microsoft.com/itpro/windows</a></p>
                <p></em> mstsc.exe only.  The Windows 8 App &quot;Remote Desktop&quot; is not supported</p>
            </td>
        </tr>
        <tr>
            <td rowspan="2" valign="top">VMware</td>
            <td valign="top">Horizon View 5.2</td>
            <td valign="top">Horizon View Client 5.2</td>
            <td valign="top">Horizon view Agent</td>
            <td valign="top">PCOIP</td>
        </tr>
        <tr>
            <td colspan="4" valign="top">
                <p><a href="http://www.vmware.com/solutions/desktop/business-process-desktop/partners.html" title="http://www.vmware.com/solutions/desktop/business-process-desktop/partners.html">http://www.vmware.com/solutions/desktop/business-process-desktop/partners.html</a></p>
                            </td>
        </tr>
    </tbody>
</table>



## Client hardware platforms

The Lync 2013 VDI Plug-in must be installed on the local machine in combination with the VDI Partner's local client. The Plug-in uses the local machine's processing, memory, and network resources to provide an optimal media experience for the end user. 

The Lync 2013 VDI Plug-in is available in 32-bit and 64-bit versions and is supported on clients meeting following requirements.

***Supported operating systems***:

- Windows 7 Service Pack 1
- Windows 8
- Windows Embedded Standard 7

***Minimum system requirements***:

- CPU: 1.5 GHz processor
- Memory: 2 gigabytes (GB) of RAM
- Space required: 32 bit: ~700 MB, 64 bit: ~900 MB

Clients which do not meet the preceding requirements are not supported by Microsoft.

The specific VDI client terminals tested by the VDI client manufacturers and validated by Microsoft are as follows. 

|Vendor | Tested terminals |
|:---------|:---------|
|Dell Wyse|  R90L7, X90m7, Z90D7 |
|HP     |  t510, t5740e, t610 |
|      |         |



For additional information about specific thin clients, please contact the client hardware manufacturer.
