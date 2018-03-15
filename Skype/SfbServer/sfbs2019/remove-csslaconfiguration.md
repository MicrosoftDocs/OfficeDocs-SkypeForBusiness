---
title: "Remove-CsSlaConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 4/12/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 54196776-6b43-43de-b5a9-6c31f347048b
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsSlaConfiguration
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Use the **Remove-CsSlaConfiguration** cmdlet to remove the Shared Line Appearance (SLA) configuration for a shared number. A shared number in SLA is an Enterprise Voice user that is capable of receiving multiple calls at a time and forwarding them to its delegates, who answer the call. 
  
```
Remove-CsSlaConfiguration -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-PassThru <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

 This example removes the SLA configuration for a user with the Identity of "sip:emergency@contosohealth.com". 
  
```
Remove-CsSlaConfiguration -Identity sip:emergency@contosohealth.com

```

### Example 2

 This example removes the SLA configuration using just the id of the shared number user. 
  
```
Remove-CsSlaConfiguration -Identity emergency

```

## Detailed Description
<a name="DetailedDescription"> </a>

 SLA is a feature in Skype for Business (SfB) for handling multiple calls on a specific number called a shared number. SLA can configure any enterprise voice enabled SfB user as a shared number with multiple lines to respond to multiple calls. The calls are not actually received on the shared number, instead they are forwarded to users that act as delegates for the shared number. Any one of the delegates can pick up the call while the rest of the delegates get a notification on their phone about who picked up the call and which line has become busy as a result. Both the number of lines and the delegates are configurable for a shared number in SLA. In addition, advanced options such as BusyOption (what happens in a situation when all lines are busy) and MissedCallOption (the case in which none of the delegates pick up a call) can also be configured for a shared number. 
  
The **Remove-CsSlaConfiguration** cmdlet provides a way to remove the Shared Line Appearance (SLA) configuration for a shared number. 
  
> [!NOTE]
> Logging in with the account created for the SLA number is not supported. Using the SLA number account with any device or Desktop Client can result in unpredictable behavior. It is not necessary to use that account for the Shared Line Appearance feature to function. 
  
By default, members of the RTCUniversalServerAdmins group are authorized to run the **Remove-CsSlaConfiguration** cmdlet. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
```
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsSlaConfiguration"}
```

## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |Indicates the identity of the Enterprise Voice user whose shared number information will be removed.  <br/> UNRESOLVED_TOKENBLOCK_VAL(PS_PD_User_Updated_Specification)  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _PassThru_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |UNRESOLVED_TOKEN_VAL(PS_PD_Passthru_Generic_CurrentObjects)  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Remove-CsSlaConfiguration** cmdlet accepts a pipelined object representing a user account that has been enabled for UNRESOLVED_TOKEN_VAL(skype16_control_panel). 
  
## Return Types
<a name="ReturnTypes"> </a>

None.
  

