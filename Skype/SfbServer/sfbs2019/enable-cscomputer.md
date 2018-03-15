---
title: "Enable-CsComputer"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ac014030-4cd0-4503-b70e-12ab5b0ec34b
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Enable-CsComputer
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Enables new or newly-updated services or server roles on a computer running Lync Server. This cmdlet was introduced in Lync Server 2010.
  
```
Enable-CsComputer [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] [-Report <String>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 activates any new Lync Server services or server roles that have been installed on the local computer.
  
```
Enable-CsComputer
```

### EXAMPLE 2

Example 2 also activates any new Lync Server services or server roles that have been installed on the local computer. In this case, however, the addition of the Verbose parameter ensures that a step-by-step account of the tasks being carried out by the **Enable-CsComputer** cmdlet will be reported on the screen. 
  
```
Enable-CsComputer -Verbose
```

## Detailed Description
<a name="sectionSection1"> </a>

Installing the required software does not automatically cause a computer to adopt a new service role; instead, that computer must be enabled before it actually begins to function in its new role. The **Enable-CsComputer** cmdlet provides a way for administrators to enable newly updated services or server roles on the local computer. 
  
Who can run this cmdlet: You must be a local administrator and a member of the domain in order to run the **Enable-CsComputer** cmdlet locally. 
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _GlobalCatalog_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name (FQDN) of a global catalog server in your domain. This parameter is not required if you are running the **Enable-CsComputer** cmdlet on a computer with an account in your domain.  <br/> |
| _GlobalSettingsDomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |FQDN of a domain controller where global settings are stored. If global settings are stored in the System container in Active Directory, then this parameter must point to the root domain controller. If global settings are stored in the Configuration container, then any domain controller can be used and this parameter can be omitted.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example: -Report "C:\Logs\EnableComputer.html"  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Enable-CsComputer** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

None. Instead, the **Enable-CsComputer** cmdlet enables instances of the Microsoft.Rtc.Management.Deploy.Internal.Machine object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Disable-CsComputer](disable-cscomputer.md)
  
[Get-CsComputer](get-cscomputer.md)
  
[Test-CsComputer](test-cscomputer.md)

