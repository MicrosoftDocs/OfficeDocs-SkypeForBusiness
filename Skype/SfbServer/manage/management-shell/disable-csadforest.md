---
title: "Disable-CsAdForest"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 06a6117c-27da-400f-8db9-eb28fe353aae
description: "Undoes the forest preparation tasks carried out by the Enable-CsAdForest cmdlet. This cmdlet is typically used only if you are uninstalling Skype for Business Server 2015. This cmdlet was introduced in Lync Server 2010."
---

# Disable-CsAdForest
[]
Undoes the forest preparation tasks carried out by the **Enable-CsAdForest** cmdlet. This cmdlet is typically used only if you are uninstalling Skype for Business Server 2015. This cmdlet was introduced in Lync Server 2010.
  
```
Disable-CsAdForest [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] [-GroupDomain <Fqdn>] [-GroupDomainController <Fqdn>] [-Report <String>] [-RootDomainController <Fqdn>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 rolls back the forest preparation tasks carried out by the **Enable-CsAdForest** cmdlet. Because the Force parameter is not included, the command will fail if the **Disable-CsAdForest** cmdlet detects that at least one of the domains in the forest is still prepared for Skype for Business Server 2015. In that case, you will need to rolls back the domain preparation by running the **Disable-CsAdDomain** cmdlet.
  
```
Disable-CsAdForest
```

### EXAMPLE 2

In Example 2, forest preparation is rolled back even if the **Disable-CsAdForest** cmdlet detects that at least one of the domains in the forest is still prepared for Skype for Business Server 2015. Rollback is forced by including the Force parameter.
  
```
Disable-CsAdForest -Force
```

## Detailed Description

When you install Skype for Business Server 2015, you make a number of forest-level changes to Active Directory Domain Services. These changes (which can be carried out by using the **Enable-CsAdForest** cmdlet) include creating objects and display specifiers that are specific to Skype for Business Server 2015, creating universal security groups needed to manage Skype for Business Server 2015, and granting global settings object access administrative rights and permissions to these groups. If you later decide to uninstall Skype for Business Server 2015 (or if you encounter issues during the setup process) you might need to roll back these forest-level changes. The **Disable-CsAdForest** cmdlet provides a way for you to undo all the forest-level modifications made by the **Enable-CsAdForest** cmdlet.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |If present, forces the rollback of the forest preparation steps even if the **Disable-CsAdForest** cmdlet detects that at least one of the domains in the forest is still prepared for Skype for Business Server 2015. If not present, the command will fail if the **Disable-CsAdForest** cmdlet detects that at least one of the domains in the forest is still prepared for. <br/> |
| _GlobalCatalog_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |FQDN of a global catalog server in your domain. This parameter is not required if you are running the **Disable-CsComputer** cmdlet on a computer with an account in your domain. <br/> |
| _GlobalSettingsDomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |FQDN of a domain controller where global settings are stored. If global settings are stored in the System container in Active Directory Domain Services, then this parameter must point to the root domain controller. If global settings are stored in the Configuration container, then any domain controller can be used and this parameter can be omitted.  <br/> |
| _GroupDomain_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name (FQDN) of the domain where the Skype for Business Server 2015 universal groups were created (for example, -GroupDomain asia.litwareinc.com). If this parameter is not included, the **Disable-CsAdForest** cmdlet will look for the universal groups in the local domain. <br/> |
| _GroupDomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |FQDN of a domain controller where universal group information is stored.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example:  `-Report "C:\Logs\DisableForest.html"` <br/> |
| _RootDomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |FQDN of the root domain controller, used to create trust paths for clients that need to access resources in domains other than their own.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types

None.
  
## Return Types

None.
  

