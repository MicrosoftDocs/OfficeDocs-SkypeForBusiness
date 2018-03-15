---
title: "New-CsTrustedApplicationComputer"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 5c44a596-7fca-49d3-a7cf-e22656698a28
description: "Adds a computer that hosts trusted applications to an existing pool. This cmdlet was introduced in Lync Server 2010."
---

# New-CsTrustedApplicationComputer
 
Adds a computer that hosts trusted applications to an existing pool. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsTrustedApplicationComputer -Identity <XdsGlobalRelativeIdentity> -Pool <String> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

This example adds a new computer with the FQDN Trust1.litwareinc.com to the pool TrustPool.litwareinc.com. We use the Identity parameter to specify the FQDN of the new computer, and the Pool parameter to specify the FQDN of the pool. The pool must exist and must be a trusted application pool. (Note: To create a trusted application pool, call the **New-CsTrustedApplicationPool** cmdlet.)
  
```
New-CsTrustedApplicationComputer -Identity Trust1.litwareinc.com -Pool TrustPool.litwareinc.com
```

## Detailed Description

We recommend that the computers that are running trusted applications within a Skype for Business Server 2015 deployment be added to a separate pool that is only for trusted applications. However, you can add trusted application computers to an existing pool that is also used for other purposes. By default, when you create a pool, a computer with the same fully qualified domain name (FQDN) as the pool is also created. Use this cmdlet to create a new computer and add it to a pool.
  
The trusted application pool must already exist in order for this cmdlet to succeed. In addition, you can't add an additional trusted application computer to a pool that contains service roles other than the ExternalServer role. For example, if the pool also supports Registrar or CentralMgmt roles, the pool can contain only one trusted application computer. In addition, if you did not specify a computer FQDN for the default computer when you created the pool (by calling the **New-CsTrustedApplicationPool** ) cmdlet, the computer will have the same FQDN as the pool and you cannot add another computer.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |The FQDN of the computer that hosts the trusted application.  <br/> |
| _Pool_ <br/> |Required  <br/> |System.String  <br/> |The FQDN of the pool hosting the trusted application computer. You can find available pools by running the **Get-CsTrustedApplicationPool** cmdlet. <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None.
  
## Return Types

Creates an object of type Microsoft.Rtc.Management.Xds.DisplayComputer.
  
## See also

#### 

[Remove-CsTrustedApplicationComputer](remove-cstrustedapplicationcomputer.md)
  
[Get-CsTrustedApplicationComputer](get-cstrustedapplicationcomputer.md)
  
[New-CsTrustedApplicationPool](new-cstrustedapplicationpool.md)
  
[Get-CsTrustedApplicationPool](get-cstrustedapplicationpool.md)

