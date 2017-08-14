---
title: Set-CsCallViaWorkPolicy
ms.prod: SKYPEFORBUSINESS
ms.assetid: 72d772fa-6a1e-416a-bd85-c6ba27619092
---


# Set-CsCallViaWorkPolicy
[]
Use the **Set-CsCallViaWorkPolicy** to modify an existing call via work policy that enables and manages the characteristics of outbound calls placed through the Skype for Business client.
  
    
    


```

Set-CsCallViaWorkPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```


## Examples
<a name="Examples"> </a>


### Example 1

This example enables the existing call via work policy of the Redmond site and enforces the use of the specified callback number.
  
    
    

```

Set-CsCallViaWorkPolicy -Identity Site:Redmond -Enabled $true  -AdminCallbackNumber +14258881234 -UseAdminCallbackNumber $true
```


## Detailed Description
<a name="DetailedDescription"> </a>

To return a list of all the Role-Based Access Control (RBAC) roles a cmdlet has been assigned to (including any custom RBAC roles you have created), run the following command from the Windows PowerShell prompt.
  
    
    

```
Get-CsAdminRole | Where-Object {$_.Cmdlets -Match "<DesiredCmdletName>"}
```


## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _AdminCallbackNumber_ <br/> |Optional  <br/> |System.String  <br/> |Specifies the number that will be called during the call back to the Skype for Business user before placing the external call. Typically this is the user's desk phone. If you want the user be able to change the callback number, use the  _UseAdminCallbackNumber_ switch. The input must contain only digits and can optionally start with a "+". For instance, "12068881234" or "+12068881234". <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Enabled_ <br/> |Optional  <br/> |System.Boolean  <br/> |If true ($True) the policy is enabled. The default at policy creation is false ($False).  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error messages and completes the cmdlet operation.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> | Specifies the unique identifier assigned to the policy when it was created. Call via work policies can be assigned at the global, site, or per-user scope. <br/>  Global syntax: `-Identity Global` <br/>  Site syntax: `-Identity Site:Redmond` <br/>  Per-user syntax: `-Identity CallviaWorkStandard` <br/> |
| _Instance_ <br/> |Optional  <br/> |System.Management.Automation.PSObject  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |This parameter is reserved for internal Microsoft use.  <br/> |
| _UseAdminCallbackNumber_ <br/> |Optional  <br/> |System.Boolean  <br/> |If true ($True), the number specified in the  _AdminCallbackNumber_ is the only number that will be used for the callback to the user, or first leg, of the outbound call. If false ($False), the user has the opportunity to change the callback number through the client. The user might choose to change the call back number to a conference room or home number. <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

Input Types
  
    
    
None.
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

None.
  
    
    

## See also
<a name="ReturnTypes"> </a>


#### 


  
    
    
 [Remove-CsCallViaWorkPolicy](remove-cscallviaworkpolicy.md)
  
    
    
 [New-CsCallViaWorkPolicy](new-cscallviaworkpolicy.md)
  
    
    
 [Grant-CsCallViaWorkPolicy](grant-cscallviaworkpolicy.md)
  
    
    
 [Get-CsCallViaWorkPolicy](get-cscallviaworkpolicy.md)
