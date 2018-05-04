---
title: "Configure federation with Skype for Business Online"
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 5/4/2018
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Priority
ms.collection:
ms.custom: 
description: "Summary: Learn how to configure interoperability between your on-premises deployment and Skype for Business Online."
---

# Configure federation with Skype for Business Online
 
**Summary:** Learn how to configure interoperability between your on-premises deployment and Skype for Business Online.
  
Follow the steps in this section to configure interoperability between your on-premises deployment and Skype for Business Online.
  
## Configure your on-premises Edge service for federation with Skype for Business Online

Federation allows users in your on-premises deployment to communicate with Office 365 users in your organization. To configure federation, run the following cmdlets in the Skype for Business Server Management Shell:
  
```
Set-CSAccessEdgeConfiguration -AllowOutsideUsers 1 -AllowFederatedUsers 1 -EnablePartnerDiscovery 1 -UseDnsSrvRouting
```

```
New-CSHostingProvider -Identity SkypeforBusinessOnline -ProxyFqdn "sipfed.online.lync.com" -Enabled $true -EnabledSharedAddressSpace $true -HostsOCSUsers $true -VerificationLevel UseSourceVerification -IsLocal $false -AutodiscoverUrl https://webdir.online.lync.com/Autodiscover/AutodiscoverService.svc/root
```

## Configure your Skype for Business Online tenant for a shared SIP address space

A Session Initiation Protocol (SIP) address is a unique identifier for each user on a network, similar to a phone number or an email address. Before you try to move users from on-premises to Skype for Business Online, you'll need to configure your Office 365 tenant to share the Shared Session Initiation Protocol (SIP) address space with your on-premises deployment. If this is not configured, you may see the following error message:
  
Move-CsUser : HostedMigration fault: Error=(510), Description=(This user's tenant is not enabled for shared sip address space.)
  
To configure a shared SIP address space, establish a remote PowerShell session with Skype for Business Online, and then run the following cmdlet:
  
```
Set-CsTenantFederationConfiguration -SharedSipAddressSpace $true
```

> [!NOTE]
> The SharedSipAddressSpace attribute needs to remain "True" until moving to online is final, and no users remain on-premises. 
  
To establish a remote PowerShell session with Skype for Business Online, you first need to install the Skype for Business Online connector module for Windows PowerShell, which you can get here: [https://go.microsoft.com/fwlink/p/?LinkId=391911](https://go.microsoft.com/fwlink/p/?LinkId=391911).
  
After you install the module, you can establish a remote session with the following cmdlets:
  
```
Import-Module SkypeOnlineConnector
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

For more information about how to establish a remote PowerShell session with Skype for Business Online, see [Connecting to Lync Online By Using Windows PowerShell](http://technet.microsoft.com/library/6167dad9-9628-4fdb-bed1-bdb3f7108e64.aspx).
  
For more information about using the Skype for Business Online connector PowerShell module, see [Using Windows PowerShell to Manage Lync Online](http://technet.microsoft.com/library/9ef2d853-10fb-4e02-a552-dcf6818d7153.aspx).
  
## See also

#### 

[New-CsHostingProvider](https://docs.microsoft.com/powershell/module/skype/new-cshostingprovider?view=skype-ps)

