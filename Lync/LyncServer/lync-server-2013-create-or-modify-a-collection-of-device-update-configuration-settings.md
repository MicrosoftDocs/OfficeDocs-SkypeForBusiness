---
title: 'Create or modify a collection of Device Update configuration settings'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Create or modify a collection of Device Update configuration settings
ms:assetid: 3e8ce95f-a8c8-417c-b1f7-0f759a567aff
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ994029(v=OCS.15)
ms:contentKeyID: 51803938
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Create or modify a collection of Device Update configuration settings in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-23_

Device update configuration settings can be created (at the site scope only) by using Windows PowerShell and the **New-CsDeviceUpdateConfiguration** cmdlet and modified by using the **Set-CsDeviceUpdateConfiguration** cmdlet. These cmdlets can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell.

<div>


> [!NOTE]
> For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at <A href="http://go.microsoft.com/fwlink/p/?linkid=255876">http://go.microsoft.com/fwlink/p/?linkId=255876</A>.



</div>

<div>


<div>

## To create device update configuration settings that use the default values

  - This command creates a new set of device update configuration settings for the Redmond site:
    
        New-CsDeviceUpdateConfiguration -Identity "site:Redmond"
    
    Because no parameters other than the mandatory Identity parameter were specified in the preceding command, the new collection of configuration settings will use the default values for all its properties.

</div>

<div>

## To change a single property value when creating device update configuration settings

  - To create settings that use different property values, simply include the appropriate parameter and parameter value. For example, to create a collection of device update configuration settings that, by default, deletes old log files every 21 days, use a command like this one:
    
        New-CsDeviceUpdateConfiguration -Identity "site:Redmond" -LogCleanupInterval "21.00:00:00"

</div>

<div>

## To change multiple property values when creating device update configuration settings

  - Multiple property values can be modified by including multiple parameters. For example, this command sets the log cleanup interval to 21 days and the log flush interval to 30 minutes:
    
        New-CsDeviceUpdateConfiguration -Identity "site:Redmond" -LogCleanupInterval "21.00:00:00" -LogFlushInterval "00:30:00"

</div>

For details about modifying existing device configuration settings, see the Help topic for the [Set-CsDeviceUpdateConfiguration](https://technet.microsoft.com/en-us/library/Gg398320(v=OCS.15)) cmdlet. For details about creating collections of configuration settings, see the Help topic for the [New-CsDeviceUpdateConfiguration](https://technet.microsoft.com/en-us/library/Gg425761(v=OCS.15)) cmdlet.

</div>

</div>

<span> </span>

</div>

</div>

</div>

