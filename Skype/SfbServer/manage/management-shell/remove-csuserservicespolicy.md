---
title: "Remove-CsUserServicesPolicy"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 025f9a94-ff44-4e06-8b14-721f8fd9924f
description: "Deletes an existing User Services policy. User Services policies determine whether or not a user's contacts are stored in Skype for Business Server 2015 or in the Unified Contact Store. The Unified Contact Store provides a way for users to maintain a single set of contacts that can be accessed using Skype for Business, Microsoft Outlook, and/or Microsoft Outlook Web Access. This cmdlet was introduced in Lync Server 2013."
---

# Remove-CsUserServicesPolicy
 
Deletes an existing User Services policy. User Services policies determine whether or not a user's contacts are stored in Skype for Business Server 2015 or in the Unified Contact Store. The Unified Contact Store provides a way for users to maintain a single set of contacts that can be accessed using Skype for Business, Microsoft Outlook, and/or Microsoft Outlook Web Access. This cmdlet was introduced in Lync Server 2013.
  
```
Remove-CsUserServicesPolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 deletes the per-user User Services policy RedmondUserServicesPolicy.
  
```
Remove-CsUserServicesPolicy -Identity "RedmondUserServicesPolicy"
```

### Example 2

Example 2 deletes all the User Services policies configured at the site scope. To do this, the command first uses the **Get-CsUserServicesPolicy** cmdlet and the Filter value to return a collection of all the policies configured at the site scope; that's accomplished by using the filter value "site:*". The resulting collection is then piped to the **Remove-CsUserServicesPolicy** cmdlet, which deletes each policy in the collection.
  
```
Get-CsUserServicesPolicy -Filter "site:*" | Remove-CsUserServicesPolicy
```

### Example 3

In Example 3, all the User Services policies that allow the use of the Unified Contact Store are deleted. To carry out this task, the command first calls the **Get-CsUserServicesPolicy** cmdlet without any parameters in order to return a collection of all the User Services policies configured for use in the organization. That collection is then piped to the **Where-Object** cmdlet, which picks out only those policies where the UcsAllowed property is equal to (-eq) True ($True). Those policies are then piped to, and removed by, the **Remove-CsUserServicesPolicy** cmdlet.
  
```
Get-CsUserServicesPolicy | Where-Object {$_.UcsAllowed -eq $True} | Remove-CsUserServicesPolicy
```

## Detailed Description
<a name="DetailedDescription"> </a>

The unified contact store introduced in Lync Server 2013 gives administrators the option of storing a user's contacts in Exchange instead of in Skype for Business Server 2015; in turn that allows the user to access the same set of contacts in Outlook and Outlook Web App as well as in Skype for Business. (Alternatively, you can continue to store contacts in Skype for Business Server 2015. In that case, users will have to maintain two separate sets of contacts: one for use with Outlook and Outlook Web Access, and one for use with Skype for Business.)
  
In order to take advantage of the unified contact store you must (among other things) assign the user a user services policy that enables the use of the unified contact store. User service policies (which can be configured at the global, site, or the per-user scope) contain only a single property: UcsAllowed. When this property is set to True then (assuming all the other prerequisites have been met) the next time a user logs on to Skype for Business Server 2015 his or her contacts will automatically be migrated to the unified contact store.
  
If this property is set to False this automatic migration will not take place. However, simply setting UcsAllowed will not cause a user's contacts to be moved from the unified contact store back to Skype for Business Server 2015. In order to do that, you must first assign the user a user services policy that does not allow the use of the unified contact store. After that, you must then use the **Invoke-CsUcsRollback** cmdlet to "manually" migrate the contacts from the unified contact store back to Skype for Business Server 2015.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Remove-CsUserServicesPolicy** cmdlet are not available in the Skype for Business Server 2015.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the policy to be deleted. To remove a policy configured at the site scope, use syntax similar to this:  <br/>  `-Identity "site:Redmond"` <br/> To remove a policy configured at the service scope, use syntax similar to this:  <br/>  `-Identity "UserServer:atl-cs-001.litwareinc.com"` <br/> The User Server service is the only service that can host a user services policy.  <br/> Policies can also be removed at the per-user scope. To remove per-user policies, use syntax similar to this:  <br/>  `-Identity "RedmondUserServicesPolicy"` <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Removes the user services policy assigned to the specified Skype for Business Online tenant. When removing a policy assigned to a tenant, you must also include the Identity parameter along with the parameter value "global":  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308" -Identity "global"` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Remove-CsUserServicesPolicy** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Policy.UserServices.UserServicesPolicy object.
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Remove-CsUserServicesPolicy** cmdlet deletes existing instances of the Microsoft.Rtc.Management.WritableConfig.Policy.UserServices.UserServicesPolicy object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsUserServicesPolicy](get-csuserservicespolicy.md)
  
[Grant-CsUserServicesPolicy](grant-csuserservicespolicy.md)
  
[New-CsUserServicesPolicy](new-csuserservicespolicy.md)
  
[Set-CsUserServicesPolicy](set-csuserservicespolicy.md)

