---
title: 'Lync Server 2013: Enterprise Voice cmdlets'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Enterprise Voice cmdlets
ms:assetid: 7d7c6d94-3ead-4d99-95f7-c31b448ab9e2
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg415658(v=OCS.15)
ms:contentKeyID: 48184613
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Enterprise Voice cmdlets in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-03-19_

Enterprise Voice is the Microsoft implementation of Voice over IP (VoIP). The cmdlets available for managing Enterprise Voice in Microsoft Lync Server 2013 will allow you to create and modify dial plans (formerly known as location profiles), voice policies, routes, and normalization rules.

<div>

## Enterprise Voice Cmdlets

Most management tasks that apply to Enterprise Voice can be performed from the Lync Server Control Panel. These same tasks can be performed using cmdlets from the Lync Server Management Shell or from within a script, allowing you to automate certain tasks. The following is a list of cmdlets that relate directly to managing Enterprise Voice:

**[Troubleshooting Enterprise Voice cmdlets in Lync Server 2013](lync-server-2013-troubleshooting-enterprise-voice-cmdlets.md)**

  - <span></span>  
    [Get-CsVoiceConfiguration](https://technet.microsoft.com/en-us/library/Gg398815(v=OCS.15))

  - <span></span>  
    [Remove-CsVoiceConfiguration](https://technet.microsoft.com/en-us/library/Gg398804(v=OCS.15))

  - <span></span>  
    [Set-CsVoiceConfiguration](https://technet.microsoft.com/en-us/library/Gg398967(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Get-CsVoiceTestConfiguration](https://technet.microsoft.com/en-us/library/Gg412957(v=OCS.15))

  - <span></span>  
    [New-CsVoiceTestConfiguration](https://technet.microsoft.com/en-us/library/Gg398961(v=OCS.15))

  - <span></span>  
    [Remove-CsVoiceTestConfiguration](https://technet.microsoft.com/en-us/library/Gg412813(v=OCS.15))

  - <span></span>  
    [Set-CsVoiceTestConfiguration](https://technet.microsoft.com/en-us/library/Gg398614(v=OCS.15))

  - <span></span>  
    [Test-CsVoiceTestConfiguration](https://technet.microsoft.com/en-us/library/Gg398260(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Test-CsDialPlan](https://technet.microsoft.com/en-us/library/Gg399024(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Test-CsVoiceNormalizationRule](https://technet.microsoft.com/en-us/library/Gg399003(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Test-CsVoicePolicy](https://technet.microsoft.com/en-us/library/Gg398310(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Test-CsVoiceRoute](https://technet.microsoft.com/en-us/library/Gg425873(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Test-CsVoiceUser](https://technet.microsoft.com/en-us/library/Gg413013(v=OCS.15))

**[Voice normalization rules cmdlets in Lync Server 2013](lync-server-2013-voice-normalization-rules-cmdlets.md)**

  - <span></span>  
    [Get-CsVoiceNormalizationRule](https://technet.microsoft.com/en-us/library/Gg398393(v=OCS.15))

  - <span></span>  
    [New-CsVoiceNormalizationRule](https://technet.microsoft.com/en-us/library/Gg398240(v=OCS.15))

  - <span></span>  
    [Remove-CsVoiceNormalizationRule](https://technet.microsoft.com/en-us/library/Gg398501(v=OCS.15))

  - <span></span>  
    [Set-CsVoiceNormalizationRule](https://technet.microsoft.com/en-us/library/Gg398491(v=OCS.15))

  - <span></span>  
    [Test-CsVoiceNormalizationRule](https://technet.microsoft.com/en-us/library/Gg399003(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [New-CsVoiceRegex](https://technet.microsoft.com/en-us/library/Gg412751(v=OCS.15))

**[Voice policy cmdlets in Lync Server 2013](lync-server-2013-voice-policy-cmdlets.md)**

  - <span></span>  
    [Get-CsDialPlan](https://technet.microsoft.com/en-us/library/Gg413043(v=OCS.15))

  - <span></span>  
    [Grant-CsDialPlan](https://technet.microsoft.com/en-us/library/Gg398547(v=OCS.15))

  - <span></span>  
    [New-CsDialPlan](https://technet.microsoft.com/en-us/library/Gg425860(v=OCS.15))

  - <span></span>  
    [Remove-CsDialPlan](https://technet.microsoft.com/en-us/library/Gg398791(v=OCS.15))

  - <span></span>  
    [Set-CsDialPlan](https://technet.microsoft.com/en-us/library/Gg398644(v=OCS.15))

  - <span></span>  
    [Test-CsDialPlan](https://technet.microsoft.com/en-us/library/Gg399024(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Get-CsPstnUsage](https://technet.microsoft.com/en-us/library/Gg412734(v=OCS.15))

  - <span></span>  
    [Set-CsPstnUsage](https://technet.microsoft.com/en-us/library/Gg399069(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Get-CsVoicePolicy](https://technet.microsoft.com/en-us/library/Gg398101(v=OCS.15))

  - <span></span>  
    [Grant-CsVoicePolicy](https://technet.microsoft.com/en-us/library/Gg398828(v=OCS.15))

  - <span></span>  
    [New-CsVoicePolicy](https://technet.microsoft.com/en-us/library/Gg425856(v=OCS.15))

  - <span></span>  
    [Remove-CsVoicePolicy](https://technet.microsoft.com/en-us/library/Gg398309(v=OCS.15))

  - <span></span>  
    [Set-CsVoicePolicy](https://technet.microsoft.com/en-us/library/Gg399021(v=OCS.15))

  - <span></span>  
    [Test-CsVoicePolicy](https://technet.microsoft.com/en-us/library/Gg398310(v=OCS.15))

**[Voice routing cmdlets in Lync Server 2013](lync-server-2013-voice-routing-cmdlets.md)**

  - <span></span>  
    [Get-CsRoutingConfiguration](https://technet.microsoft.com/en-us/library/Gg425851(v=OCS.15))

  - <span></span>  
    [New-CsRoutingConfiguration](https://technet.microsoft.com/en-us/library/Gg399056(v=OCS.15))

  - <span></span>  
    [Remove-CsRoutingConfiguration](https://technet.microsoft.com/en-us/library/Gg398643(v=OCS.15))

  - <span></span>  
    [Set-CsRoutingConfiguration](https://technet.microsoft.com/en-us/library/Gg412811(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Get-CsVoiceRoute](https://technet.microsoft.com/en-us/library/Gg425926(v=OCS.15))

  - <span></span>  
    [New-CsVoiceRoute](https://technet.microsoft.com/en-us/library/Gg398197(v=OCS.15))

  - <span></span>  
    [Remove-CsVoiceRoute](https://technet.microsoft.com/en-us/library/Gg398468(v=OCS.15))

  - <span></span>  
    [Set-CsVoiceRoute](https://technet.microsoft.com/en-us/library/Gg412893(v=OCS.15))

  - <span></span>  
    [Test-CsVoiceRoute](https://technet.microsoft.com/en-us/library/Gg425873(v=OCS.15))

</div>

<div>

## See Also


[Advanced Enterprise Voice cmdlets in Lync Server 2013](lync-server-2013-advanced-enterprise-voice-cmdlets.md)  
[Voice application cmdlets in Lync Server 2013](lync-server-2013-voice-application-cmdlets.md)  


[Lync Server PowerShell Blog](http://go.microsoft.com/fwlink/p/?linkid=203150)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

