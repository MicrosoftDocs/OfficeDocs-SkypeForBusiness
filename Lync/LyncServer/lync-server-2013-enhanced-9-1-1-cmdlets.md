---
title: 'Lync Server 2013: Enhanced 9-1-1 cmdlets'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Enhanced 9-1-1 cmdlets
ms:assetid: e560c688-7b34-4bd7-8104-24f390644105
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg415678(v=OCS.15)
ms:contentKeyID: 48185650
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Enhanced 9-1-1 cmdlets in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-06-20_

Microsoft Lync Server 2013 ships with cmdlets that allow you to implement and manage the Enhanced 9-1-1 (E9-1-1) implementation of an Enterprise Voice solution. Use these cmdlets to map connection points to physical addresses and to configure settings required for Enterprise Voice users to successfully complete emergency calls and automatically send a location to the emergency services provider. You cannot configure E9-1-1 from the Lync Server Control Panel, you must use cmdlets.

<div>

## Enhanced 9-1-1 Cmdlets

Use the following cmdlets to configure E9-1-1.

**Enhanced 9-1-1**

  - <span></span>  
    [Get-CsEnhancedEmergencyServiceDisclaimer](https://technet.microsoft.com/en-us/library/Gg412877(v=OCS.15))

  - <span></span>  
    [Remove-CsEnhancedEmergencyServiceDisclaimer](https://technet.microsoft.com/en-us/library/Gg425810(v=OCS.15))

  - <span></span>  
    [Set-CsEnhancedEmergencyServiceDisclaimer](https://technet.microsoft.com/en-us/library/Gg398620(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Get-CsLisCivicAddress](https://technet.microsoft.com/en-us/library/Gg398459(v=OCS.15))

  - <span></span>  
    [Test-CsLisCivicAddress](https://technet.microsoft.com/en-us/library/Gg425914(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Export-CsLisConfiguration](https://technet.microsoft.com/en-us/library/Gg398539(v=OCS.15))

  - <span></span>  
    [Import-CsLisConfiguration](https://technet.microsoft.com/en-us/library/Gg398380(v=OCS.15))

  - <span></span>  
    [Debug-CsLisConfiguration](https://technet.microsoft.com/en-us/library/Gg398710(v=OCS.15))

  - <span></span>  
    [Test-CsLisConfiguration](https://technet.microsoft.com/en-us/library/Gg398497(v=OCS.15))

  - <span></span>  
    [Publish-CsLisConfiguration](https://technet.microsoft.com/en-us/library/Gg398364(v=OCS.15))

  - <span></span>  
    [Unpublish-CsLisConfiguration](unhttps://technet.microsoft.com/en-us/library/Gg398364(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Get-CsLisLocation](https://technet.microsoft.com/en-us/library/Gg412834(v=OCS.15))

  - <span></span>  
    [Remove-CsLisLocation](https://technet.microsoft.com/en-us/library/Gg425722(v=OCS.15))

  - <span></span>  
    [Set-CsLisLocation](https://technet.microsoft.com/en-us/library/Gg398757(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Get-CsLisPort](https://technet.microsoft.com/en-us/library/Gg398820(v=OCS.15))

  - <span></span>  
    [Remove-CsLisPort](https://technet.microsoft.com/en-us/library/Gg412899(v=OCS.15))

  - <span></span>  
    [Set-CsLisPort](https://technet.microsoft.com/en-us/library/Gg398700(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Get-CsLisServiceProvider](https://technet.microsoft.com/en-us/library/Gg398116(v=OCS.15))

  - <span></span>  
    [Remove-CsLisServiceProvider](https://technet.microsoft.com/en-us/library/Gg398904(v=OCS.15))

  - <span></span>  
    [Set-CsLisServiceProvider](https://technet.microsoft.com/en-us/library/Gg425911(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Get-CsLisSubnet](https://technet.microsoft.com/en-us/library/Gg398473(v=OCS.15))

  - <span></span>  
    [Remove-CsLisSubnet](https://technet.microsoft.com/en-us/library/Gg413053(v=OCS.15))

  - <span></span>  
    [Set-CsLisSubnet](https://technet.microsoft.com/en-us/library/Gg399016(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Get-CsLisSwitch](https://technet.microsoft.com/en-us/library/Gg425769(v=OCS.15))

  - <span></span>  
    [Remove-CsLisSwitch](https://technet.microsoft.com/en-us/library/Gg398352(v=OCS.15))

  - <span></span>  
    [Set-CsLisSwitch](https://technet.microsoft.com/en-us/library/Gg412823(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Get-CsLisWirelessAccessPoint](https://technet.microsoft.com/en-us/library/Gg398117(v=OCS.15))

  - <span></span>  
    [Remove-CsLisWirelessAccessPoint](https://technet.microsoft.com/en-us/library/Gg398461(v=OCS.15))

  - <span></span>  
    [Set-CsLisWirelessAccessPoint](https://technet.microsoft.com/en-us/library/Gg412723(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Get-CsLocationPolicy](https://technet.microsoft.com/en-us/library/Gg398911(v=OCS.15))

  - <span></span>  
    [Grant-CsLocationPolicy](https://technet.microsoft.com/en-us/library/Gg413049(v=OCS.15))

  - <span></span>  
    [New-CsLocationPolicy](https://technet.microsoft.com/en-us/library/Gg398231(v=OCS.15))

  - <span></span>  
    [Remove-CsLocationPolicy](https://technet.microsoft.com/en-us/library/Gg398727(v=OCS.15))

  - <span></span>  
    [Set-CsLocationPolicy](https://technet.microsoft.com/en-us/library/Gg412987(v=OCS.15))

  - <span></span>  
    [Test-CsLocationPolicy](https://technet.microsoft.com/en-us/library/Gg425962(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Get-CsNetworkSite](https://technet.microsoft.com/en-us/library/Gg398766(v=OCS.15))

  - <span></span>  
    [New-CsNetworkSite](https://technet.microsoft.com/en-us/library/Gg398365(v=OCS.15))

  - <span></span>  
    [Remove-CsNetworkSite](https://technet.microsoft.com/en-us/library/Gg398135(v=OCS.15))

  - <span></span>  
    [Set-CsNetworkSite](https://technet.microsoft.com/en-us/library/Gg398295(v=OCS.15))

</div>

<div>

## See Also


[Lync Server PowerShell Blog](http://go.microsoft.com/fwlink/p/?linkid=203150)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

