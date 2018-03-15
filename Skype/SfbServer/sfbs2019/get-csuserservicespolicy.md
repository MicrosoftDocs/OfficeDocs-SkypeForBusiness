---
title: "Get-CsUserServicesPolicy"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 424cd3ca-6df4-4715-97f1-95d2da3b6d90
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsUserServicesPolicy
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Returns information about the User Services policies configured for use in the organization. User Services policies determine whether or not a user's contacts are stored in Lync Server 2013 or in the Unified Contact Store. The Unified Contact Store provides a way for users to maintain a single set of contacts that can be accessed using Lync 2013, Outlook, and/or Outlook Web Access. This cmdlet was introduced in Lync Server 2013.
  
```
Get-CsUserServicesPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 returns information about all the User Services policies currently in use in the organization.
  
```
Get-CsUserServicesPolicy
```

### Example 2

In Example 2, information is returned for a single User Services policy: the policy configured for the Redmond site.
  
```
Get-CsUserServicesPolicy -Identity "site:Redmond"
```

### Example 3

Example 3 returns information for all the User Services policies configured at the site scope. This is done by including the Filter parameter and the filter value "site:\*".
  
```
Get-CsUserServicesPolicy -Filter "site:*"
```

### Example 4

The command shown in Example 4 returns information about the User Services policies where the use of the Unified Contact Store has been disabled. To carry out this task, the command first calls the **Get-CsUserServicesPolicy** cmdlet without any parameters; this returns a collection of all the User Services policies configured for use in the organization. That collection is then piped to the **Where-Object** cmdlet, which picks out only those policies where the UcsAllowed property has been set to false ($False). 
  
```
Get-CsUserServicesPolicy | Where-Object {$_.UcsAllowed -eq $False}
```

## Detailed Description
<a name="DetailedDescription"> </a>

The unified contact store introduced in Lync Server 2013 gives administrators the option of storing a user's contacts in Microsoft Exchange Server 2013 instead of in Lync Server; in turn that allows the user to access the same set of contacts in Outlook and Outlook Web Access as well as in Lync 2013. (Alternatively, you can continue to store contacts in Lync Server 2013. In that case, users will have to maintain two separate sets of contacts: one for use with Outlook and Outlook Web Access, and one for use with Lync 2013.)
  
In order to take advantage of the unified contact store you must (among other things) assign the user a user services policy that enables the use of the unified contact store. User service policies (which can be configured at the global, site, or the per-user scope) contain only a single property: UcsAllowed. When this property is set to True then (assuming all the other prerequisites have been met) the next time a user logs on to Lync Server 2013 his or her contacts will automatically be migrated to the unified contact store.
  
If this property is set to False this automatic migration will not take place. However, simply setting UcsAllowed will not cause a user's contacts to be moved from the unified contact store back to Lync Server. In order to do that, you must first assign the user a user services policy that does not allow the use of the unified contact store. After that, you must then use the **Invoke-UcsRollback** cmdlet to "manually" migrate the contacts from the unified contact store back to Lync Server. 
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsUserServicesPolicy"}
  
 **Lync Server Control Panel:** The functions carried out by the **Get-CsUserServicesPolicy** cmdlet are not available in the Lync Server Control Panel. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcards when specifying the policy (or policies) to be retrieved. For example, this syntax returns all the policies that have been configured at the site scope:  <br/> -Filter "site:\*"  <br/> This syntax returns all the policies that have been configured at the per-user scope:  <br/> -Filter "tag:\*"  <br/> You cannot use both the Filter and the Identity parameters in the same command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the policy to be returned. To return the global policy, use this syntax:  <br/> -Identity global  <br/> To return a policy configured at the site scope, use syntax similar to this: -Identity "site:Redmond"  <br/> To return a policy configured at the service scope, use syntax similar to this: -Identity "UserServer:atl-cs-001.litwareinc.com"  <br/> Note that the UserServer service is the only service that can host a user services policy.  <br/> Policies can also be configured at the per-user scope. To return one of these policies, use syntax similar to this:  <br/> -Identity "RedmondUserServicesPolicy"  <br/> If this parameter is not included then all of the user services policies configured for use in your organization will be returned.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the user services policy data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |When used, retrieves the user services policy for the specified Skype for Business Online tenant. For example:  <br/> -Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"  <br/> You should not use the Tenant parameter and the Identity parameter in the same command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Get-CsUserServicesPolicy** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="ReturnTypes"> </a>

The **Get-CsUserServicesPolicy** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Policy.UsersServices.UserServicesPolicy object. 
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Grant-CsUserServicesPolicy](grant-csuserservicespolicy.md)
  
[New-CsUserServicesPolicy](new-csuserservicespolicy.md)
  
[Remove-CsUserServicesPolicy](remove-csuserservicespolicy.md)
  
[Set-CsUserServicesPolicy](set-csuserservicespolicy.md)

