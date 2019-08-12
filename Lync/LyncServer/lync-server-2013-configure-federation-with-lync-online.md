---
title: 'Lync Server 2013: Configure federation with Lync Online'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configure federation with Lync Online
ms:assetid: a10bd1d5-c003-46db-9f57-7d55d3fa08da
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205126(v=OCS.15)
ms:contentKeyID: 48184946
ms.date: 08/15/2016
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure federation of Lync Server 2013 with Lync Online

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2016-08-15_

Follow the steps in this section to configure interoperability between your on-premises deployment and Skype for Business Online.

<span id="a"></span>

<div>

## Configure Your On-Premises Edge Service for Federation with Skype for Business Online

Federation allows users in your on-premises deployment to communicate with Office 365 users in your organization. To configure federation, run the following cmdlets:

   ```
    Set-CSAccessEdgeConfiguration -AllowOutsideUsers 1 -AllowFederatedUsers 1 -UseDnsSrvRouting -EnablePartnerDiscovery $True
   ```

   ```
    New-CSHostingProvider -Identity LyncOnline -ProxyFqdn "sipfed.online.lync.com" -Enabled $true -EnabledSharedAddressSpace $true -HostsOCSUsers $true -VerificationLevel UseSourceVerification -IsLocal $false -AutodiscoverUrl https://webdir.online.lync.com/Autodiscover/AutodiscoverService.svc/root
   ```

</div>

<span id="b"></span>

<div>

## Configure Your Skype for Business Online Tenant for a Shared SIP Address Space

A Session Initiation Protocol (SIP) address is a unique identifier for each user on a network, similar to a phone number or an email address. Before you try to move Lync users from on-premises to Skype for Business Online, you’ll need to configure your Office 365 tenant to share the Shared Session Initiation Protocol (SIP) address space with your on-premises deployment. If this is not configured, you may see the following error message:

Move-CsUser : HostedMigration fault: Error=(510), Description=(This user’s tenant is not enabled for shared sip address space.)

To configure a shared SIP address space, establish a remote PowerShell session with Skype for Business Online, and then run the following cmdlet:

    Set-CsTenantFederationConfiguration -SharedSipAddressSpace $true

To establish a remote PowerShell session with Skype for Business Online, you first need to install the Skype for Business Online module for Windows PowerShell, which you can get here: [http://go.microsoft.com/fwlink/p/?LinkId=391911](http://go.microsoft.com/fwlink/p/?linkid=391911).

After you install the module, you can establish a remote session with the following cmdlets:

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

For more information about how to establish a remote PowerShell session with Skype for Business Online, see [Connecting to Skype for Business Online by using Windows PowerShell](https://docs.microsoft.com/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell).

For more information about using the Skype for Business Online PowerShell module, see [Using Windows PowerShell to manage Skype for Business Online](https://docs.microsoft.com/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell).

</div>

<div>

## See Also


[New-CsHostingProvider](https://docs.microsoft.com/powershell/module/skype/New-CsHostingProvider)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

