---
title: Enable-CsAdForest
ms.prod: SKYPEFORBUSINESS
ms.assetid: 2381fca7-294b-486d-919d-e8626cef6fea
---


# Enable-CsAdForest
[]
Makes the Active Directory modifications required before you can install Skype for Business Server 2015. This includes making global changes to the Configuration or System containers; creating universal groups; and creating property sets and display specifiers that are specific to Skype for Business Server 2015. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Enable-CsAdForest [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] [-GroupDomain <Fqdn>] [-GroupDomainController <Fqdn>] [-Report <String>] [-RootDomainController <Fqdn>] [-SkipPrepareCheck <$true | $false>] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

This command prepares the Active Directory forest for the installation of Skype for Business Server 2015. Because the GroupDomain parameter is not used, the universal security groups generated when you run the **Enable-CsAdForest** cmdlet will be created in the local domain.
  
    
    

```

Enable-CsAdForest
```


### EXAMPLE 2

This command prepares the Active Directory forest for the installation of Skype for Business Server 2015. The GroupDomain parameter is used to ensure that the universal security groups created by running the **Enable-CsAdForest** cmdlet will be created in the northamerica.litwareinc.com domain.
  
    
    

```
Enable-CsAdForest -GroupDomain northamerica.litwareinc.com
```


## Detailed Description

Before you can install Skype for Business Server 2015, you must make a number of forest-level changes to Active Directory Domain Services. This includes creating display specifiers and objects specific to Skype for Business Server 2015, creating the universal security groups that are needed to manage Skype for Business Server 2015, and granting global settings object access rights to these groups. Forest preparation is typically carried out through the Skype for Business Server 2015 Setup Wizard. However, enterprise administrators can also perform forest preparation at any time by running the **Enable-CsAdForest** cmdlet.
  
    
    
After the **Enable-CsAdForest** cmdlet finishes running, you can use the **Get-CsAdForest** cmdlet to verify that the forest is ready for the next step in the installation process.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _GlobalCatalog_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |FQDN of a global catalog server in your domain. This parameter is not required if you are running the **Enable-CsAdForest** cmdlet on a computer with an account in your domain. <br/> |
| _GlobalSettingsDomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |FQDN of a domain controller where global settings are stored. If global settings are stored in the System container in Active Directory, then this parameter must point to the root domain controller. If global settings are stored in the Configuration container, then any domain controller can be used and this parameter can be omitted.  <br/> |
| _GroupDomain_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name (FQDN) of the domain where the new universal security groups should be created. If this parameter is not included, then the groups will be created in the local domain.  <br/> |
| _GroupDomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |FQDN of a domain controller where universal group information is stored.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example:  `-Report "C:\\Logs\\ForestPrep.html"` <br/> |
| _RootDomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |FQDN of the root domain controller, used to create trust paths for clients that need to access resources in domains other than their own.  <br/> |
| _SkipPrepareCheck_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True ($True), causes Enable-CsAdForest to run without first doing its initial preparation checks.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   

## Input Types

None.
  
    
    

## Return Types

None.
  
    
    

