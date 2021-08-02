---
title: "Configure Skype for Business hybrid"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
audience: ITPro
f1.keywords:
- NOCSH
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
description: "Summary: Learn how to configure interoperability between your on-premises deployment and Teams."
---

# Configure Skype for Business hybrid

[!INCLUDE [sfbo-retirement](../../Hub/includes/sfbo-retirement.md)]

To configure Skype for Business hybrid, you need to:

- [Configure your on-premises Edge service to federate with Teams](#configure-your-on-premises-edge-service-to-federate-with-teams).
- [Configure your on-premises environment to trust Teams and enable shared SIP address space](#configure-your-on-premises-environment-to-enable-shared-sip-address-space-with-teams).
- [Enable shared SIP address space in your Teams organization](#enable-shared-sip-address-space-in-your-organization).

If you have Exchange on-premises, you may want to configure OAuth between your Exchange on-premises and online environments. For more information, see  [Manage server-to-server authentication in Skype for Business Server](../../SfbServer/manage/authentication/server-to-server-and-partner-applications.md) and [Plan to integrate Skype for Business and Exchange](../../SfbServer/plan-your-deployment/integrate-with-exchange/integrate-with-exchange.md#feature_support). 
  
## Configure your on-premises Edge service to federate with Teams

Federation allows users in your on-premises deployment to communicate with Teams users in your organization. To configure federation, run the following cmdlet in the Skype for Business Server Management Shell:
  
```PowerShell
Set-CSAccessEdgeConfiguration -AllowOutsideUsers $True -AllowFederatedUsers $True -EnablePartnerDiscovery $True -UseDnsSrvRouting
```

If '-EnablePartnerDiscovery' value is set to $True, Skype for Business Server will use DNS records to try and discover partner domains not listed in the AllowedDomains list. If the value is set to $False , Skype for Business Server will only federate with domains found on the AllowedDomains list. This parameter is required if you use DNS service routing.

> [!NOTE]
> For more details about enabling federation between users of your on-premises Skype for Business deployment and users of a Microsoft 365 organization, see [Configuring federation support for a Microsoft 365 customer in Skype for Business Server](../../SfbServer/manage/federation-and-external-access/federation-support/configuring-federation-support.md).


## Configure your on-premises environment to enable shared SIP address space with Teams

You must also configure your on-premises environment to trust Teams and enable shared SIP address space. This configuration means Teams can potentially host user accounts for the same set of SIP domains as your on-premises environment, and messages can be routed between users hosted on premises and online. You configuring a hosting provider with ProxyFqdn=sipfed.online.lync.com as described below.

First, check if you already have a hosting provider with ProxyFqdn=sipfed.online.lync.com. If one exists, then remove it by using the following command in the Skype for Business Server Management Shell:

```PowerShell
Get-CsHostingProvider | ?{ $_.ProxyFqdn -eq "sipfed.online.lync.com" } | Remove-CsHostingProvider
```

Then create a new hosting provider by using the New-CsHostingProvider cmdlet as follows: 

```PowerShell
New-CsHostingProvider -Identity Office365 -ProxyFqdn "sipfed.online.lync.com" -Enabled $true -EnabledSharedAddressSpace $true -HostsOCSUsers $true -VerificationLevel UseSourceVerification -IsLocal $false -AutodiscoverUrl https://webdir.online.lync.com/Autodiscover/AutodiscoverService.svc/root 
```

 ## Enable shared SIP address space in your organization
  
In addition to the change you made in your on-premises deployment, you'll need to make the corresponding change in your Teams organization to enabled shared SIP address space with your on-premises deployment.  

To enable shared SIP address space in your organization, establish a remote PowerShell session with Teams, and then run the following cmdlet:
  
```PowerShell
Set-CsTenantFederationConfiguration -SharedSipAddressSpace $true
```

> [!NOTE]
> The SharedSipAddressSpace attribute needs to remain "True" until moving to online is final, and no users remain on-premises. 
  
To establish a remote PowerShell session with Teams, you first need to install the [Teams PowerShell module](/microsoftteams/teams-powershell-install). The Teams PowerShell module replaces the Skype for Busines Online Connector module, which has been retired.
  
After you install the module, you can establish a remote session with the following cmdlets:
   ```powershell
   # When using Teams PowerShell Module

   Import-Module MicrosoftTeams
   $credential = Get-Credential
   Connect-MicrosoftTeams -Credential $credential
   ```

For more information about how to establish a remote PowerShell session with Teams, and how to use the Teams PowerShell module, see [Set up your computer for Windows PowerShell](../../SfbOnline/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell.md).
  


## See also

[New-CsHostingProvider](/powershell/module/skype/new-cshostingprovider?view=skype-ps)
