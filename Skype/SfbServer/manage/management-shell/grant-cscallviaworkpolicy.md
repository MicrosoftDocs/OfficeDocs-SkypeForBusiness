---
title: "Grant-CsCallViaWorkPolicy"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: aef9db27-23ac-469f-917a-789be09c0fc3
description: "Use the Grant-CsCallViaWorkPolicy cmdlet to assign call via work policies to a user or group of users. Call via work policies enable and manage the characteristics of outbound calls placed through the Skype for Business client."
---

# Grant-CsCallViaWorkPolicy
 
Use the **Grant-CsCallViaWorkPolicy** cmdlet to assign call via work policies to a user or group of users. Call via work policies enable and manage the characteristics of outbound calls placed through the Skype for Business client.
  
```
Grant-CsCallViaWorkPolicy -Identity <UserIdParameter> -PolicyName <String> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-PassThru <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

This example assigns the policy named "StandardUserCvW" to "Ken Myer".
  
```
Grant-CsCallViaWorkPolicy -Identity "Ken Myer" -PolicyName StandardUserCvW
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
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> | Specifies a unique identifier of the user account the policy should be assigned to. User identities can be specified by using one of four formats. <br/>  SIP address <br/>  User Principal Name (UPN) <br/>  Domain name and logon name, in the form domain\logon <br/>  Active Directory display name (Ken Myer), or distinguished name <br/>  In addition, you can use the asterisk (*) wildcard character when using the display name as the user _Identity_. For example, the Identity "* Smith" grants the policy all users who have a display name that ends in the string value " Smith".  <br/> |
| _PolicyName_ <br/> |Required  <br/> |System.String  <br/> |Specifies the name of the policy to be assigned. The  _PolicyName_ is the policy identity minus the policy scope ("tag:"). A policy that has an identity of "Tag:Redmond" has a _PolicyName_ of "Redmond". A policy with the identity "Tag:RedmondCalloutPolicy" has a _PolicyName_ of "RedmondCalloutPolicy". If you set _PolicyName_ to a null value, then the command will unassign any individual policy assigned to the user. For example: `Grant-CsCallViaWorkPolicy -Identity "Ken Myer" -PolicyName $Null` <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Enables you to specify the fully qualified domain name (FQDN) of a domain controller to be contacted when assigning the new policy. If this parameter is not specified, then the **Grant-CsCallViaWorkPolicy** cmdlet will contact the first available domain controller. <br/> |
| _PassThru_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Enables you to pass a user object through the pipeline that represents the user being assigned the policy. By default, the **Grant-CsCallViaWorkPolicy** cmdlet does not pass objects through the pipeline. <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |PARAMVALUE: Guid  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None.
  
## Return Types
<a name="ReturnTypes"> </a>

None.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Remove-CsCallViaWorkPolicy](remove-cscallviaworkpolicy.md)
  
[Set-CsCallViaWorkPolicy](set-cscallviaworkpolicy.md)
  
[New-CsCallViaWorkPolicy](new-cscallviaworkpolicy.md)
  
[Get-CsCallViaWorkPolicy](get-cscallviaworkpolicy.md)

