---
title: Set-CsUserServicesPolicy
ms.prod: SKYPEFORBUSINESS
ms.assetid: fbe18ddf-5094-4d8b-ad27-75b73173b8c4
---


# Set-CsUserServicesPolicy
[]
Modifies an existing User Services policy. User Services policies determine whether or not a user's contacts are stored in Skype for Business Server 2015 or in the Unified Contact Store. The Unified Contact Store provides a way for users to maintain a single set of contacts that can be accessed using Skype for Business, Outlook, and/or Outlook Web Access. This cmdlet was introduced in Lync Server 2013.
  
    
    


```

Set-CsUserServicesPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```


## Examples
<a name="Examples"> </a>


### Example 1

The command shown in Example 1 disables the use of the Unified Contact Store for the per-user User Services policy RedmondUserServicesPolicy. This means that users managed by this policy will not have their contacts stored in the Unified Contact Store.
  
    
    

```

Set-CsUserServicesPolicy -Identity "RedmondUserServicesPolicy" -UcsAllowed $False
```


### Example 2

In Example 2, all the User Services policies configured at the site scope are modified to disable the use of the Unified Contact Store. To do this, the command first calls the **Get-CsUserServicesPolicy** cmdlet and the Filter parameter to return a collection of all the policies configured at the site scope. This collection is then piped to the **Set-CsUserServicesPolicy** cmdlet, which takes each policy in the collection and sets the UcsAllowed property to False ($False).
  
    
    

```
Get-CsUserServicesPolicy -Filter "site:*" | Set-CsUserServicesPolicy -UcsAllowed $False
```


## Detailed Description
<a name="DetailedDescription"> </a>

The unified contact store introduced in Lync Server 2013 gives administrators the option of storing a user's contacts in Exchange instead of in Skype for Business Server 2015; in turn that allows the user to access the same set of contacts in Outlook and Outlook Web Access as well as. (Alternatively, you can continue to store contacts in Skype for Business Server 2015. In that case, users will have to maintain two separate sets of contacts: one for use with Outlook and Outlook Web Access, and one for use with Skype for Business.)
  
    
    
In order to take advantage of the unified contact store you must (among other things) assign the user a user services policy that enables the use of the unified contact store. User service policies (which can be configured at the global, site, or the per-user scope) contain only a single property: UcsAllowed. When this property is set to True then (assuming all the other prerequisites have been met) the next time a user logs on to Skype for Business Server 2015 his or her contacts will automatically be migrated to the unified contact store.
  
    
    
If this property is set to False this automatic migration will not take place. However, simply setting UcsAllowed will not cause a user's contacts to be moved from the unified contact store back to Skype for Business Server 2015. In order to do that, you must first assign the user a user services policy that does not allow the use of the unified contact store. After that, you must then use the **Invoke-CsUcsRollback** cmdlet to "manually" migrate the contacts from the unified contact store back to Skype for Business Server 2015.
  
    
    
 **Skype for Business Server Control Panel:** The functions carried out by the **Set-CsUserServicesPolicy** cmdlet are not available in the Skype for Business Server Control Panel.
  
    
    

## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command. Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _EnableAwaySinceIndication_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the policy to be modified. To modify the global policy, use this syntax:  <br/>  `-Identity "global"` <br/> To modify a policy configured at the site scope, use syntax similar to this:  <br/>  `-Identity "site:Redmond"` <br/> To modify a policy configured at the service scope, use syntax similar to this:  <br/>  `-Identity "UserServer:atl-cs-001.litwareinc.com"` <br/> Note that the UserServer service is the only service that can host a user services policy.  <br/> If this parameter is not included then the **Set-CsUserServicesPolicy** cmdlet will automatically modify the global policy. <br/> |
| _Instance_ <br/> |Optional  <br/> |System.Management.Automation.PSObject  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _MigrationDelayInDays_ <br/> |Optional  <br/> |System.Int32  <br/> |Specifies the number of days the system will wait before beginning a migration to or from the unified contact store. MigrationDelayInDays can be set to any value between 0 and 180, inclusive. The default value is 0.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account for which the user services policy being modified. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _UcsAllowed_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value) users affected by the policy will automatically be migrated to the unified contact store (assuming that they have an account on Exchange and that they log on using Skype for Business). When set to False, users can be removed from the unified contact store, but only if they are "manually" removed by the **Invoke-CsUcsRollback** cmdlet. <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

The **Set-CsUserServicesPolicy** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Policy.UserServices.UserServicesPolicy object.
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Set-CsUserServicesPolicy** cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Policy.UserServices.UserServicesPolicy object.
  
    
    

## See also
<a name="ReturnTypes"> </a>


#### 


  
    
    
 [Get-CsUserServicesPolicy](get-csuserservicespolicy.md)
  
    
    
 [Grant-CsUserServicesPolicy](grant-csuserservicespolicy.md)
  
    
    
 [New-CsUserServicesPolicy](new-csuserservicespolicy.md)
  
    
    
 [Remove-CsUserServicesPolicy](remove-csuserservicespolicy.md)
