---
title: 'Lync Server 2013: First steps before you start migrating users from Lync Online to Lync on-premises'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: First steps before you start migrating users from Lync Online to Lync on-premises
ms:assetid: 98245b04-ded4-4186-8da3-ba1c554b5c39
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn689118(v=OCS.15)
ms:contentKeyID: 62258123
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# First steps before you start migrating users from Lync Online to Lync on-premises in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-05-08_

Before you start moving Lync Online users to your on-premises environment, check that all of the following are true:

  - Your Lync Server on-premises environment must be fully deployed and validated. For more information, see [Deploying Lync Server 2013](lync-server-2013-deploying-lync-server.md).

  - Your Lync Online tenant must be configured for remote PowerShell Access.
    
    To do this, first install the Lync Online module for Windows PowerShell, which you can get here: [http://go.microsoft.com/fwlink/p/?LinkId=391911](http://go.microsoft.com/fwlink/p/?linkid=391911).
    
    After you install the module, you can establish a remote session by typing the following cmdlets in the Lync Server Management Shell:
    
       ```
        Import-Module LyncOnlineConnector
       ```  
    
       ```
        $cred = Get-Credential
       ``` 
    
       ```
        $CSSession = New-CsOnlineSession -Credential $cred
       ```
    
       ```
        Import-PSSession $CSSession -AllowClobber
       ```
    
    For more information about how to establish a remote PowerShell session with Lync Online, see [Connecting to Lync Online by using Windows PowerShell](https://docs.microsoft.com/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell).
  
    For more information about using the Lync Online PowerShell module, see [Using Windows PowerShell to manage Lync Online](https://docs.microsoft.com/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell).

  - Your Lync Online must be configured for Shared SIP Address Space. To do this, first start a remote Powershell session with Lync Online. Then run the following cmdlet:
    
        Set-CsTenantFederationConfiguration -SharedSipAddressSpace $True

After you’ve finished these steps, you can move on to [Migrating Lync Online users to Lync on-premises in Lync Server 2013](lync-server-2013-migrating-lync-online-users-to-lync-on-premises.md).

</div>

<span> </span>

</div>

</div>

</div>

