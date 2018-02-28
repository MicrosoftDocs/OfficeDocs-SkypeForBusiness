---
title: "Disable-CsAdDomain"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 98a4982c-7d8d-460d-bff9-243373b20290
description: "Undoes the domain preparation tasks carried out by the Enable-CsAdDomain cmdlet. This cmdlet is typically used only if you are uninstalling Skype for Business Server 2015 from a domain. This cmdlet was introduced in Lync Server 2010."
---

# Disable-CsAdDomain
[]
Undoes the domain preparation tasks carried out by the **Enable-CsAdDomain** cmdlet. This cmdlet is typically used only if you are uninstalling Skype for Business Server 2015 from a domain. This cmdlet was introduced in Lync Server 2010.
  
```
Disable-CsAdDomain [-Confirm [<SwitchParameter>]] [-Domain <Fqdn>] [-DomainController <Fqdn>] [-Force <SwitchParameter>] [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 rolls back the domain preparation process in the local domain. Because the Force parameter is not included, the command will fail if the **Disable-CsAdDomain** cmdlet determines that at least one Front End Server, A/V Conferencing Server, or Web Services server is still active in the domain.
  
```
Disable-CsAdDomain
```

### EXAMPLE 2

Example 2 rolls back the domain preparation process for the domain asia.litwareinc.com.
  
```
Disable-CsAdDomain -Domain asia.litwareinc.com
```

### EXAMPLE 3

The command shown in Example 3 uses the Force parameter to force the rollback of the domain preparation process in the local domain. This means that rollback will occur even if the **Disable-CsAdDomain** cmdlet determines that at least one Front End Server, A/V Conferencing Server, or Web Services server is still active in the domain.
  
```
Disable-CsAdDomain -Force
```

## Detailed Description

When you install Skype for Business Server 2015 in a domain, that domain must be correctly prepared, a process that includes extending the Active Directory schema to allow for the addition of attributes specific to Skype for Business Server 2015 as well as assigning the required Access Control Entries to the universal groups needed for managing and operating Skype for Business Server 2015. If you later decide to uninstall Skype for Business Server 2015 (or if you encounter problems during the setup process), you might need to roll back these domain-level changes. The **Disable-CsAdDomain** cmdlet provides a way for you to undo all the domain-level modifications made by the **Enable-CsAdDomain** cmdlet.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Domain_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name (FQDN) of the domain where domain preparation should be rolled back (for example,  `-Domain asia.litwareinc.com`). If this parameter is not included, rollback will take place on the local domain.  <br/> |
| _DomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Enables administrators to specify the FQDN of the domain controller to be used when running **Disable-CsAdDomain**. If not specified, the cmdlet will use the first available domain controller. <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |If present rollback will occur even if the **Disable-CsAdDomain** cmdlet determines that at least one Front End, conferencing, or Web Services server is still active in the domain. If not present then the command will fail if a Front End, Conferencing, or Web Services server is still active in the domain. <br/> |
| _GlobalCatalog_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |FQDN of a global catalog server in your domain. This parameter is not required if you are running the **Disable-CsAdDomain** cmdlet on a computer with an account in your domain. <br/> |
| _GlobalSettingsDomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |FQDN of a domain controller where global settings are stored. If global settings are stored in the System container in Active Directory Domain Services this parameter must point to the root domain controller. If global settings are stored in the Configuration container, then any domain controller can be used and this parameter can be omitted.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example:  `-Report "C:\Logs\DisableDomain.html"` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types

None. The **Disable-CsAdDomain** cmdlet does not accept pipelined input.
  
## Return Types

None. 
  
## See also

#### 

[Enable-CsAdDomain](enable-csaddomain.md)
  
[Get-CsAdDomain](get-csaddomain.md)

