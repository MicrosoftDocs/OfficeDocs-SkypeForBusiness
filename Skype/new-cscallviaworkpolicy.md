---
title: New-CsCallViaWorkPolicy
ms.prod: SKYPEFORBUSINESS
ms.assetid: 952ab367-5c68-4869-9827-873605e7c41e
---


# New-CsCallViaWorkPolicy
[]
Use the **New-CsCallViaWorkPolicy** cmdlet to create a new call via work policy that enables and manages the characteristics of outbound calls placed through the Skype for Business client.
  
    
    


```

New-CsCallViaWorkPolicy -Identity <XdsIdentity> [-AdminCallbackNumber <String>] [-Confirm [<SwitchParameter>]] [-Enabled <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-Tenant <Guid>] [-UseAdminCallbackNumber <$true | $false>] [-WhatIf [<SwitchParameter>]]

```


## Examples
<a name="Examples"> </a>


### Example 1

This example creates a call via work policy for the Redmond site. The policy is enabled, the administrative callback number is specified and enforced.
  
    
    

```

New-CsCallViaWorkPolicy -Identity Site:Redmond -Enabled $true  -AdminCallbackNumber +14258881234 -UseAdminCallbackNumber $true
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
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identity to be assigned to the policy. New policies can be created at the site or per-user scope. To create a new site policy, use the prefix "site:" and the name of the site as the  _Identity_. For example, to create a new policy for the Redmond site you would use this syntax: `-Identity site:Redmond`. To create a new per-user policy, this syntax: `-Identity SalesDepartmentPolicy`.  <br/> You cannot create a new global policy. If you want to make changes to the global policy, use the **Set-CsCallViawork** cmdlet instead. Likewise, you cannot create a new site or per-user policy if a policy with that _Identity_ already exists. If you need to make changes to an existing policy, use the **Set-CsCallViawork** cmdlet. <br/> |
| _AdminCallbackNumber_ <br/> |Optional  <br/> |System.String  <br/> |Specifies the number that will be called during the call back to the Skype for Business user before placing the external call. Typically this is the user's desk phone. If you want the user be able to change the callback number, use the  _UseAdminCallbackNumber_ switch. The input must contain only digits and can optionally start with a "+". For instance, "12068881234" or "+12068881234". <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Enabled_ <br/> |Optional  <br/> |System.Boolean  <br/> |Specifies whether the policy is enabled at creation. The default is false ($False).  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error messages and completes the cmdlet operation.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching **Set-<cmdlet>**. <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |This parameter is reserved for internal Microsoft use.  <br/> |
| _UseAdminCallbackNumber_ <br/> |Optional  <br/> |System.Boolean  <br/> |If true ($True), the number specified in the  _AdminCallbackNumber_ is the only number that will be used for the callback to the user, or first leg, of the outbound call. If false ($False), the user has the opportunity to change the callback number through the client. The user might choose to change the call back number to a personal phone number like a mobile, home, or hotel phone number. <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

None.
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

The **New-CsCallViaWorkPolicy** returns **[Microsoft.Rtc.Management.WritableConfig.Policy.CallViaWork.CallViaWorkPolicy]** instances.
  
    
    

## See also
<a name="ReturnTypes"> </a>


#### 


  
    
    
 [Remove-CsCallViaWorkPolicy](remove-cscallviaworkpolicy.md)
  
    
    
 [Set-CsCallViaWorkPolicy](set-cscallviaworkpolicy.md)
  
    
    
 [Grant-CsCallViaWorkPolicy](grant-cscallviaworkpolicy.md)
  
    
    
 [Get-CsCallViaWorkPolicy](get-cscallviaworkpolicy.md)
