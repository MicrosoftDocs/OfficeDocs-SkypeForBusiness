---
title: 'Lync Server 2013: Configuring media port range settings'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configuring media port range settings
ms:assetid: 2c4b7c0b-0dce-48f4-a489-336d6e526f7c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204770(v=OCS.15)
ms:contentKeyID: 48183723
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring media port range settings in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-18_

Media port range settings can significantly impact client performance and should be configured. You can configure these settings by using Lync Server Management Shell.

### Media Port Range Settings

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Setting</th>
<th>Description</th>
<th>Lync Server Management Shell cmdlet</th>
<th>Cmdlet parameters</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Portrange\Enabled</p></td>
<td><p>Specifies whether the port ranges sent by the server should be used by the client for media and signaling. Used in conjunction with the subvalues MinMediaPort and MaxMediaPort.</p></td>
<td><p><strong>CsConferencingConfiguration</strong></p></td>
<td><p>ClientMediaPortRangeEnabled</p></td>
</tr>
<tr class="even">
<td><p>Portrange\MinMediaPort</p></td>
<td><p>Specifies the starting port number to use for media. Combines with MaxMediaPort to specify the range of ports. The recommended minimum range is 40 ports.</p></td>
<td><p><strong>CsConferencingConfiguration</strong></p></td>
<td><p>ClientMediaPort (represents the starting port number to use for client media)</p></td>
</tr>
<tr class="odd">
<td><p>Portrange\MaxMediaPort</p></td>
<td><p>Specifies the highest port number to use for media. Combines with MinMediaPort to specify the range of ports. The recommended minimum range is 40 ports.</p></td>
<td><p><strong>CsConferencingConfiguration</strong></p></td>
<td><p>ClientMediaPortRange (indicates the total number of ports available for client media; default is 40)</p></td>
</tr>
</tbody>
</table>


<div>

## To Configure Media Port Range Settings

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

2.  Run the following cmdlet:
    
        Get-CsConferencingConfiguration
    
    This cmdlet returns the conferencing configuration settings.

3.  Run the following cmdlet with the parameters and values you want to change (for details about the parameters for this cmdlet, see the Lync Server Management Shell documentation):
    
        Set-CsConferencingConfiguration
    
    <div>
    

    > [!NOTE]  
    > You can create additional sets of conferencing configuration settings for specific sites. Use the <STRONG>New- CsConferencingConfiguration</STRONG> cmdlet with a site identity. When you create new conferencing configuration settings for sites, the site settings take precedence over the global settings. For details, see the Lync Server Management Shell documentation.

    
    </div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

