---
title: "Remove-CsTrustedApplicationComputer"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c9c0604b-a94e-42b9-9db3-bc3dbe686e41
description: "Removes a trusted application computer. This cmdlet was introduced in Lync Server 2010."
---

# Remove-CsTrustedApplicationComputer
[]
Removes a trusted application computer. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsTrustedApplicationComputer -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

This example removes the computer with the FQDN Trust1.litwareinc.com.
  
```
Remove-CsTrustedApplicationComputer -Identity Trust1.litwareinc.com
```

### EXAMPLE 2

This example removes all trusted computers that have FQDNs beginning with the string Trust. The example begins by calling the **Get-CsTrustedApplicationComputer** cmdlet, passing the Filter parameter the value Trust*. This will retrieve all trusted application computers with an FQDN beginning with Trust and ending with any set of characters. That collection of computers is then piped to the **Remove-CsTrustedApplicationComputer** cmdlet, which removes each item (each computer) in the collection. Keep in mind that this won't remove the computers from a pool if removing those computers would result in an empty pool.
  
```
Get-CsTrustedApplicationComputer -Filter Trust* | Remove-CsTrustedApplicationComputer
```

## Detailed Description

It is recommended that the computers that are running trusted applications within a Skype for Business Server 2015 deployment be added to a separate pool that is only for trusted applications. However, you can add trusted application computers to an existing pool that is also used for other purposes. Use this cmdlet to remove a trusted application computer.
  
When you use this cmdlet to remove a trusted application computer, it will be removed not only from the list of trusted application computers but from the list of computers available on Skype for Business Server 2015. In other words, if you call the **Get-CsTrustedApplicationComputer** cmdlet or the **Get-CsComputer** cmdlet the computer will no longer be listed. You cannot remove a trusted application computer if it's the only computer on the pool. If you want to remove the only computer on a pool you must remove the entire pool (which can be done by calling the **Remove-CsTrustedApplicationPool** cmdlet).
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |The fully qualified domain name (FQDN) of the computer to remove.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.Xds.DisplayComputer object. Accepts pipelined input of trusted application computer objects.
  
## Return Types

This cmdlet does not return a value. It removes an object of type Microsoft.Rtc.Management.Xds.DisplayComputer.
  
## See also

#### 

[New-CsTrustedApplicationComputer](new-cstrustedapplicationcomputer.md)
  
[Get-CsTrustedApplicationComputer](get-cstrustedapplicationcomputer.md)
  
[Remove-CsTrustedApplicationPool](remove-cstrustedapplicationpool.md)
  
[Get-CsTrustedApplicationPool](get-cstrustedapplicationpool.md)

