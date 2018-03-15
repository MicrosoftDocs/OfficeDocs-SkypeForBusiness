---
title: "Configure federation of Lync Server 2013 with Lync Online"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection:
- Ent_O365_Hybrid
- Ent_O365_Hybrid_Top
ms.assetid: a10bd1d5-c003-46db-9f57-7d55d3fa08da
description: "Follow the steps in this section to configure interoperability between your on-premises deployment and Skype for Business Online."
---

# Configure federation of Lync Server 2013 with Lync Online
[]
Follow the steps in this section to configure interoperability between your on-premises deployment and Skype for Business Online.
  
## Configure Your On-Premises Edge Service for Federation with Skype for Business Online
<a name="a"> </a>

Federation allows users in your on-premises deployment to communicate with Office 365 users in your organization. To configure federation, run the following cmdlets:
  
```
Set-CSAccessEdgeConfiguration -AllowOutsideUsers 1 -AllowFederatedUsers 1 -UseDnsSrvRouting -EnablePartnerDiscovery $True
```

```
New-CSHostingProvider -Identity LyncOnline -ProxyFqdn "sipfed.online.lync.com" -Enabled $true -EnabledSharedAddressSpace $true -HostsOCSUsers $true -VerificationLevel UseSourceVerification -IsLocal $false -AutodiscoverUrl https://webdir.online.lync.com/Autodiscover/AutodiscoverService.svc/root
```

## Configure Your Skype for Business Online Tenant for a Shared SIP Address Space
<a name="b"> </a>

A Session Initiation Protocol (SIP) address is a unique identifier for each user on a network, similar to a phone number or an email address. Before you try to move Lync users from on-premises to Skype for Business Online, you'll need to configure your Office 365 tenant to share the Shared Session Initiation Protocol (SIP) address space with your on-premises deployment. If this is not configured, you may see the following error message:
  
Move-CsUser : HostedMigration fault: Error=(510), Description=(This user's tenant is not enabled for shared sip address space.)
  
To configure a shared SIP address space, establish a remote PowerShell session with Skype for Business Online, and then run the following cmdlet:
  
```
Set-CsTenantFederationConfiguration -SharedSipAddressSpace $true
```

To establish a remote PowerShell session with Skype for Business Online, you first need to install the Skype for Business Online module for Windows PowerShell, which you can get here: [https://go.microsoft.com/fwlink/p/?LinkId=391911](https://go.microsoft.com/fwlink/p/?LinkId=391911).
  
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

For more information about how to establish a remote PowerShell session with Skype for Business Online, see [Connecting to Skype for Business Online by using Windows PowerShell](connecting-to-skype-for-business-online-by-using-windows-powershell.md).
  
For more information about using the Skype for Business Online PowerShell module, see [Using Windows PowerShell to manage Skype for Business Online](using-windows-powershell-to-manage-skype-for-business-online.md).
  
## See also
<a name="b"> </a>

#### 

[New-CsHostingProvider](new-cshostingprovider.md)

