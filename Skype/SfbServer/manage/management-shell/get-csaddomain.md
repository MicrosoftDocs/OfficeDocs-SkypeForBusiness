---
title: "Get-CsAdDomain"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 64554035-3ba5-4aa7-b5d3-91277f107275
description: "Returns information indicating whether Active Directory Domain Services has been correctly configured to allow for the installation of Skype for Business Server 2015. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsAdDomain
 
Returns information indicating whether Active Directory Domain Services has been correctly configured to allow for the installation of Skype for Business Server 2015. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsAdDomain [-Domain <Fqdn>] [-DomainController <Fqdn>] [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] [-Report <String>]

```

## Examples

### EXAMPLE 1

Example 1 returns information regarding the current status of your local Active Directory domain. If your domain settings are up-to-date, and the domain is ready to host Skype for Business Server 2015, the value LC_DOMAIN_SETTINGS_STATE_READY will be returned.
  
```
Get-CsAdDomain
```

### EXAMPLE 2

The command shown in Example 2 returns the current status of a specific domain: fabrikam.com. In a multi-domain environment, you can return information for a given domain by including the Domain parameter.
  
```
Get-CsAdDomain -Domain "fabrikam.com" 
```

### EXAMPLE 3

Example 3 retrieves the current status of your Active Directory domain and, at the same time, writes information about that status to a file named C:\Logs\DomainReport.html. This file will detail the steps taken by the **Get-CsAdDomain** cmdlet to determine the readiness status for the domain. Those steps include tasks such as verifying the existence of Active Directory groups and checking permission settings on various Active Directory containers.
  
```
Get-CsAdDomain -Report "C:\Logs\DomainReport.html"
```

## Detailed Description

Before you can install Skype for Business Server 2015 your domain must be correctly prepared, a process that includes extending the Active Directory schema to allow for the addition of attributes specific to Skype for Business Server 2015, in addition to assigning the required Access Control Entries to the universal groups used for managing and operating Skype for Business Server 2015. The **Get-CsAdDomain** cmdlet returns a single value that tells you whether or not Skype for Business Server 2015 can be installed on a domain. If the **Get-CsAdDomain** cmdlet returns the value LC_DOMAINSETTINGS_STATE_READY then you can install Skype for Business Server 2015 on that domain. If the cmdlet returns LC_DOMAINSETTINGS_STATE_NOT_READY then you will need to correctly prepare the domain before trying to install Skype for Business Server 2015.
  
The **Get-CsAdDomain** cmdlet runs as part of the Setup Wizard. If the Wizard determines that the domain is not correctly prepared, an error message is displayed and setup will stop. However, you can run the **Get-CsAdDomain** cmdlet independently of the Setup Wizard in order to verify the domain status before you try to install Skype for Business Server 2015.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Domain_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name (FQDN) of the domain to be checked; for example:  `-Domain "litwareinc.com"`. If this parameter is not specified, then the local domain will be checked.  <br/> |
| _DomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Enables administrators to specify the FQDN of the domain controller to be used when running the **Get-CsAdDomain** cmdlet. If not specified, the cmdlet will use the first available domain controller. <br/> |
| _GlobalCatalog_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |FQDN of a global catalog server in your domain. This parameter is not required if you are running the **Get-CsAdDomain** cmdlet on a computer with an account in your domain. <br/> |
| _GlobalSettingsDomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |FQDN of a domain controller where global settings are stored. If global settings are stored in the System container in Active Directory, then this parameter must point to the root domain controller. If global settings are stored in the Configuration container, then any domain controller can be used and this parameter can be omitted.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example:  `-Report "C:\Logs\DomainPrep.html"` <br/> |
   
## Input Types

None. The **Get-CsAdDomain** cmdlet does not accept pipelined input.
  
## Return Types

The **Get-CsAdDomain** cmdlet returns instances of the Microsoft.Rtc.Management.Deployment.LcDomainSettingsState object.
  
## See also

#### 

[Disable-CsAdDomain](disable-csaddomain.md)
  
[Enable-CsAdDomain](enable-csaddomain.md)

