---
title: "Configure Skype for Business hybrid"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- Hybrid 
- M365-voice
- M365-collaboration
- Teams_ITAdmin_Help
- Adm_Skype4B_Online
ms.custom: 
description: "Summary: Learn how to configure interoperability between your on-premises deployment and Skype for Business Online."
---

# Configure Skype for Business hybrid

To configure Skype for Business hybrid, you need to:

- [Configure your on-premises environment to federate with Office 365.](#configure-your-on-premises-edge-service-to-federate-with-Office-365)
- [Configure your on-premises environment to trust Office 365 and enable shared SIP address space with Office 365.](#configure-your-on-premises-environment-to-share-your-SIP-address-space-with-Office-365)
- [Enable shared SIP address space in your Office 365 tenant.](#configure-server-to-server-authentication-if-required)

Note that if you have Exchange on-premises, you may want to configure OAuth between your Exchange on-premises and Skype for Business Online environments. For more information, see  [Manage server-to-server authentication in Skype for Business Server](https://docs.microsoft.com/en-us/SkypeForBusiness/manage/authentication/server-to-server-and-partner-applications) and [Plan to integrate Skype for Business and Exchange](https://docs.microsoft.com/en-us/SkypeForBusiness/plan-your-deployment/integrate-with-exchange/integrate-with-exchange#feature_support). 
  
## Configure your on-premises Edge service to federate with Office 365

Federation allows users in your on-premises deployment to communicate with Office 365 users in your organization. To configure federation, run the following cmdlet in the Skype for Business Server Management Shell:
  
```
Set-CSAccessEdgeConfiguration -AllowOutsideUsers 1 -AllowFederatedUsers 1 -EnablePartnerDiscovery 1 -UseDnsSrvRouting
```



## Configure your on-premises environment to enable shared SIP address space with Office 365

You must also configure your on-premises environment to trust Office 365 and enable shared SIP address space with Office 365. This means Office 365 can potentially host user accounts for the same set of SIP domains as your on-premises environment, and messages can be routed between users hosted on premises and online.  You do this by configuring a hosting provider with ProxyFqdn=sipfed.online.lync.com as described below.

First, check if you already have a hosting provider with ProxyFqdn=sipfed.online.lync.com. If one exists, then remove it by using the following command:

```
Get-CsHostingProvider | ?{ $_.ProxyFqdn -eq "sipfed.online.lync.com" } | Remove-CsHostingProvider
```

Then create a new hosting provider, use the New-CsHostingProvider cmdlet as follows: 

```
New-CsHostingProvider -Identity Office365 -ProxyFqdn "sipfed.online.lync.com" -Enabled $true -EnabledSharedAddressSpace $true -HostsOCSUsers $true -VerificationLevel UseSourceVerification -IsLocal $false -AutodiscoverUrl https://webdir.online.lync.com/Autodiscover/AutodiscoverService.svc/root 
```

 ## Enable shared SIP address space in your Office 365 tenant
  
In addition to the change you made in your on-premises deployment, you'll need to make the corresponding change in your Office 365 tenant to enabled shared SIP address space with your on-premises deployment.  

To enable shared SIP address space in your Office 365 tenant, establish a remote PowerShell session with Skype for Business Online, and then run the following cmdlet:
  
```
Set-CsTenantFederationConfiguration -SharedSipAddressSpace $true
```

> [!NOTE]
> The SharedSipAddressSpace attribute needs to remain "True" until moving to online is final, and no users remain on-premises. 
  
To establish a remote PowerShell session with Teams or Skype for Business Online, you first need to install the Skype for Business Online connector module for Windows PowerShell, which you can get [here](https://go.microsoft.com/fwlink/p/?LinkId=391911).
  
After you install the module, you can establish a remote session with the following cmdlets:
  
```
$cred = Get-Credential
Import-PSSession (New-CsOnlineSession -Credential $cred) -AllowClobber
```

For more information about how to establish a remote PowerShell session with Skype for Business Online, and how to use the Skype for Business Online Connector module, see [Set up your computer for Windows PowerShell](https://docs.microsoft.com/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell).
  


## See also

[New-CsHostingProvider](https://docs.microsoft.com/powershell/module/skype/new-cshostingprovider?view=skype-ps)

