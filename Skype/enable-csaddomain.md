---
title: Enable-CsAdDomain
ms.prod: SKYPEFORBUSINESS
ms.assetid: a39768de-51ae-45e8-b6b7-441b5da0b3b2
---


# Enable-CsAdDomain
[]
Modifies the security settings on the universal groups created during forest preparation. These modifications provide the permissions needed to host and manage users enabled for Skype for Business Server 2015 within the domain. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Enable-CsAdDomain [-Confirm [<SwitchParameter>]] [-CrossForest <SwitchParameter>] [-Domain <Fqdn>] [-DomainController <Fqdn>] [-Force <SwitchParameter>] [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] [-Report <String>] [-SkipPrepareCheck <$true | $false>] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

The command shown in Example 1 prepares the local domain for the installation of Skype for Business Server 2015.
  
    
    

```

Enable-CsAdDomain
```


### EXAMPLE 2

Example 2 prepares the domain asia.litwareinc.com for the installation of Skype for Business Server 2015.
  
    
    

```
Enable-CsAdDomain -Domain asia.litwareinc.com
```


## Detailed Description

Before you can install Skype for Business Server 2015 in a domain, that domain must be correctly prepared, a process that includes extending the Active Directory schema to allow for the addition of attributes specific to Skype for Business Server 2015 as well as assigning the required Access Control Entries to the universal groups needed for managing and operating Skype for Business Server 2015. Domain preparation is typically carried out through the Skype for Business Server 2015 Setup Wizard. However, administrators can also perform domain preparation by running the **Enable-CsAdDomain** cmdlet.
  
    
    
After the **Enable-CsAdDomain** cmdlet finishes running, you can use the **Get-CsAdDomain** cmdlet to verify that the domain is ready for the next step in the installation process.
  
    
    

> [!NOTE]
> If you receive the following error, "Cannot find the object 'CrossRef' in Active Directory" while running tasks to prepare a child domain of a single-forest environment with multiple domains, you may have to manually add the RTCComponentUniversalServices group from the parent domain to the Windows Authorization Access group in the child domain. 
  
    
    

This cmdlet carries out tasks similar to those carried out by the following Microsoft Office Communications Server 2007 R2 command:
  
    
    



```
Lcscmd.exe /domain /action:DomainPrep

```


## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _CrossForest_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |If present, indicates that domain preparation is taking place in a domain in a different forest. This parameter is not required if the domain being enabled is in the same forest as the computer where the command is being run.  <br/> |
| _Domain_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name (FQDN) of the domain where domain preparation is to take place (for example, -Domain asia.litwareinc.com). If this parameter is not included, domain preparation will take place on the local domain.  <br/> |
| _DomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Enables administrators to specify the FQDN of the domain controller to be used when running the **Enable-CsAdDomain** cmdlet. If not specified, the cmdlet will use the first available domain controller. <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _GlobalCatalog_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |FQDN of a global catalog server in your domain. This parameter is not required if you are running the **Enable-CsAdDomain** cmdlet on a computer with an account in your domain. <br/> |
| _GlobalSettingsDomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |FQDN of a domain controller where global settings are stored. If global settings are stored in the System container in Active Directory Domain Services, then this parameter must point to the root domain controller. If global settings are stored in the Configuration container then any domain controller can be used and this parameter can be omitted.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example:  `-Report "C:\\Logs\\DomainPrep.html"` <br/> |
| _SkipPrepareCheck_ <br/> |Optional  <br/> |System.Boolean  <br/> |If set to True ($True), then the **Enable-CsAdDomain** cmdlet will skip its initial preparation check. <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   

## Input Types

None. The **Enable-CsAdDomain** cmdlet does not accept pipelined input.
  
    
    

## Return Types

None. 
  
    
    

## See also


#### 


  
    
    
 [Disable-CsAdDomain](disable-csaddomain.md)
  
    
    
 [Get-CsAdDomain](get-csaddomain.md)
