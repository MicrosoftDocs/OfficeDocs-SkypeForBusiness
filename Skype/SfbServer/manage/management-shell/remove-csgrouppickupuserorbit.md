---
title: "Remove-CsGroupPickupUserOrbit"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: dd5e815f-c91b-4b86-8f14-f895f5c3a082
description: "Use the Remove-CsGroupPickupUserOrbit cmdlet to remove the associated group pickup orbit number for an Enterprise Voice user. This effectively disables the user for group call pickup."
---

# Remove-CsGroupPickupUserOrbit
[]
Use the **Remove-CsGroupPickupUserOrbit** cmdlet to remove the associated group pickup orbit number for an Enterprise Voice user. This effectively disables the user for group call pickup.
  
```
Remove-CsGroupPickupUserOrbit -User <String> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

This example removes the group pickup orbit number and disables group pickup for a user specified by the SIP address.  _User_ is a positional parameter. The first parameter after the cmdlet is assumed to be the _User_ parameter value.
  
```
Remove-CsGroupPickupUserOrbit sip:ken.myer@contoso.com
```

## Detailed Description
<a name="DetailedDescription"> </a>

This cmdlet will throw an exception if the user does not have an assigned group pickup orbit number.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _User_ <br/> |Required  <br/> |System.String  <br/> |Specifies the user whose group pickup orbit number will be removed. Because  _User_ is a positional parameter, the `-User` syntax is not required. The first parameter after the cmdlet is assumed to be the _User_ parameter value. <br/> User identities can be specified using one of four formats: 1) the user's SIP address; 2) the user's user principal name (UPN); 3) the user's domain name and logon name, in the form domain\logon (for example, litwareinc\kenmyer); and, 4) the user's Active Directory display name (for example, Ken Myer). You can also reference a user account by using the user's Active Directory distinguished name.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error messages and completes the cmdlet operation.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

This cmdlet supports pipelined input from the **Get-CsUser** cmdlet.
  
## Return Types
<a name="ReturnTypes"> </a>

None.
  

