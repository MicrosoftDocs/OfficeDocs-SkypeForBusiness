---
title: "Get-CsClientPolicy"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c8e1cb96-2bf7-447c-b41c-d896fe85e349
description: "Returns information about the client policies configured for use in your organization. Among other things, client policies help determine the features of Skype for Business Server 2015 that are available to users; for example, you might give some users the right to transfer files while denying this right to other users. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsClientPolicy
 
Returns information about the client policies configured for use in your organization. Among other things, client policies help determine the features of Skype for Business Server 2015 that are available to users; for example, you might give some users the right to transfer files while denying this right to other users. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsClientPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

In Example 1, the **Get-CsClientPolicy** cmdlet is called without any additional parameters; this returns a collection of all the client policies configured for use in your organization.
  
```
Get-CsClientPolicy
```

### EXAMPLE 2

In Example 2, the **Get-CsClientPolicy** cmdlet is used to return the per-user client policy that has an Identity SalesPolicy. Because identities are unique, this command will never return more than one item.
  
```
Get-CsClientPolicy -Identity SalesPolicy
```

### EXAMPLE 3

Example 3 uses the Filter parameter to return all the client policies that have been configured at the per-user scope. The filter value "tag:*" tells the **Get-CsClientPolicy** cmdlet to return only those policies that have an Identity that begins with the string value "tag:".
  
```
Get-CsClientPolicy -Filter "tag:*"
```

### EXAMPLE 4

Example 4 returns a collection of all the client policies where the DisableSavingIM property is True. To do this, the **Get-CsClientPolicy** cmdlet is first called without any parameters in order to return a collection of all the client policies configured for use in the organization. This collection is then piped to the **Where-Object** cmdlet, which selects only those policies where the DisableSavingIM property is equal to True.
  
```
Get-CsClientPolicy | Where-Object {$_.DisableSavingIM -eq $True}
```

### EXAMPLE 5

In Example 5, the only client policies returned are the policies that meet two criteria: the DisableSavingIM property must be True and the EnableIMAutoArchiving property must be False. To do this, the command first calls the **Get-CsClientPolicy** cmdlet in order to return a collection of all the client policies configured for use in the organization. That collection is then piped to the **Where-Object** cmdlet, which picks out only those policies that meet both of the following criteria: DisableSavingIM must be equal to True and EnableIMAutoArchiving must be equal to False. The -and operator tells the **Where-Object** cmdlet that only objects that meet all the specified criteria should be selected.
  
```
Get-CsClientPolicy | Where-Object {$_.DisableSavingIM -eq $True -and $_.EnableIMAutoArchiving -eq $False}
```

### EXAMPLE 6

Example 6 is a variation of the command shown in Example 5. This time, however, policies are selected as long as they meet at least one of the following criteria: either the DisableSavingIM property is True and/or the EnableIMAutoArchiving property is False. To accomplish this task, the command first calls the **Get-CsClientPolicy** cmdlet to return a collection of all the client policies configured for use in the organization. That collection is then piped to the **Where-Object** cmdlet, which picks out only those policies that meet at least one of the following criteria: DisableSavingIM is equal to True and/or EnableIMAutoArchiving is equal to False. The -or operator tells the **Where-Object** cmdlet that any object that meets at least one of the specified conditions should be selected.
  
## Detailed Description

Client policies are applied each time a user accesses the system, regardless of where the user logs on from and regardless of the type of device the user logs on with. In addition, client policies, like other Skype for Business Server 2015 policies, can readily be targeted to selected groups of users. You can even create a custom policy that gets assigned to a single user.
  
Client policies can be configured at the global, site, and per-user scopes. The **Get-CsClientPolicy** cmdlet enables you to return information about all the client policies that have been configured for use in your organization.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard characters when indicating the policy (or policies) to be returned. For example, to return all the policies configured at the site scope use this syntax:  `-Filter "site:*"`. To return a collection of all the per-user policies, use this syntax:  `-Filter "tag:*"`.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier of the client policy to be returned. To refer to the global policy, use this syntax: -Identity global. To refer to a site policy, use syntax similar to this:  `-Identity site:Redmond`. To refer to a per-user policy, use syntax similar to this:  `-Identity SalesDepartmentPolicy`.  <br/> If this parameter is omitted, then all the client policies configured for use in your organization will be returned.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the client policy data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account whose client policies are being returned. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your Skype for Business Online tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **Get-CsClientPolicy** cmdlet does not accept pipelined input.
  
## Return Types

The **Get-CsClientPolicy** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Policy.Client.ClientPolicy object.
  
## See also

#### 

[Grant-CsClientPolicy](grant-csclientpolicy.md)
  
[New-CsClientPolicy](new-csclientpolicy.md)
  
[Remove-CsClientPolicy](remove-csclientpolicy.md)
  
[Set-CsClientPolicy](set-csclientpolicy.md)

