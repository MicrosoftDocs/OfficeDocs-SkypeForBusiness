---
title: "Remove-CsExternalAccessPolicy"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: eae27b8f-0c25-4723-95e9-435e36f06a79
description: "Enables you to remove an existing external access policy. External access policies determine whether or not your users can: 1) communicate with users who have Session Initiation Protocol (SIP) accounts with a federated organization; 2) communicate with users who have SIP accounts with a public instant messaging (IM) provider such as Windows Live; and, 3) access Skype for Business Server 2015 over the Internet, without having to log on to your internal network. This cmdlet was introduced in Lync Server 2010."
---

# Remove-CsExternalAccessPolicy
 
Enables you to remove an existing external access policy. External access policies determine whether or not your users can: 1) communicate with users who have Session Initiation Protocol (SIP) accounts with a federated organization; 2) communicate with users who have SIP accounts with a public instant messaging (IM) provider such as Windows Live; and, 3) access Skype for Business Server 2015 over the Internet, without having to log on to your internal network. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsExternalAccessPolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

In Example 1, the external access policy with the Identity site:Redmond is deleted. After the policy is removed, users in the Redmond site will have their external access permissions governed by the global policy.
  
```
Remove-CsExternalAccessPolicy -Identity site:Redmond
```

### EXAMPLE 2

Example 2 deletes all the external access policies that have been configured at the site scope. To carry out this task, the command first uses the **Get-CsExternalAccessPolicy** cmdlet and the Filter parameter to return a collection of policies configured at the site scope; the filter value "site:*" limits the returned data to external access policies that have an Identity that begins with the string value "site:". The filtered collection is then piped to the **Remove-CsExternalAccessPolicy** cmdlet, which deletes each policy in the collection.
  
```
Get-CsExternalAccessPolicy -Filter site:* | Remove-CsExternalAccessPolicy 
```

### EXAMPLE 3

In Example 3, all the external access policies that allow federation access are deleted. To do this, the command first calls the **Get-CsExternalAccessPolicy** cmdlet to return a collection of all the external access policies configured for use in the organization. This collection is then piped to the **Where-Object** cmdlet, which picks out only those policies where the EnableFederationAccess property is equal to True. This filtered collection is then piped to the **Remove-CsExternalAccessPolicy** cmdlet, which deletes each policy in the collection.
  
```
Get-CsExternalAccessPolicy | Where-Object {$_.EnableFederationAccess -eq $True} | Remove-CsExternalAccessPolicy 
```

### EXAMPLE 4

Example 4 deletes all the external access policies that meet at least one of two criteria: federation access is allowed, public cloud access is allowed, or both are allowed. To carry out this task, the command first uses the **Get-CsExternalAccessPolicy** cmdlet to return a collection of all the external access policies configured for use in the organization. This collection is then piped to the **Where-Object** cmdlet, which selects only those policies that meet the following criteria: either EnableFederationAccess is equal to True, and/or EnablePublicCloudAccess is equal to True. Policies meeting one (or both) of those criteria are then piped to, and removed by, the **Remove-CsExternalAccessPolicy** cmdlet.
  
To delete all the policies where both EnableFederationAccess and EnablePublicCloudAccess are True use the -and operator when calling the **Where-Object** cmdlet:
  
```
Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $True}

```

```
Get-CsExternalAccessPolicy | Where-Object {$_.EnableFederationAccess -eq $True -or $_.EnablePublicCloudAccess -eq $True} | Remove-CsExternalAccessPolicy 
```

## Detailed Description

When you install Skype for Business Server 2015 your users are only allowed to exchange instant messages and presence information among themselves: by default, they can only communicate with other people who have SIP accounts in your Active Directory Domain Services. In addition, users are not allowed to access Skype for Business Server 2015 over the Internet; instead, they must be logged on to your internal network before they will be able to log on to Skype for Business Server 2015.
  
1. That might be sufficient to meet your communication needs. If it doesn't meet your needs you can use external access policies to extend the ability of your users to communicate and collaborate. External access policies can grant (or revoke) the ability of your users to do any or all of the following: 
  
2. Communicate with people who have SIP accounts with a federated organization. Note that enabling federation alone will not provide users with this capability. Instead, you must enable federation and then assign users an external access policy that gives them the right to communicate with federated users.
  
3. Communicate with people who have SIP accounts with a public instant messaging service such as Windows Live.
  
Access Skype for Business Server 2015 over the Internet, without having to first log on to your internal network. This enables your users to use Skype for Business and log on to Skype for Business Server 2015 from an Internet café or other remote location.
  
When you install Skype for Business Server 2015, a global external access policy is automatically created for you. In addition to the global policy, you can use the **New-CsExternalAccessPolicy** cmdlet to create external access policies configured at the site or per-user scopes.
  
The **Remove-CsExternalAccessPolicy** cmdlet enables you to delete any policies that were created by using the **New-CsExternalAccessPolicy** cmdlet; that means you can delete any policies assigned to the site scope or the per-user scope. You can also run the **Remove-CsExternalAccessPolicy** cmdlet against the global external access policy. In that case, however, the global policies will not be deleted; by design, global policies cannot be deleted. Instead, the properties of the global policy will simply be reset to their default values.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the external access policy to be removed. External access policies can be configured at the global, site, or per-user scopes. To "remove" the global policy, use this syntax:  `-Identity global`. (Note that the global policy cannot actually be removed. Instead, all the properties in the global policy will be reset to their default values.) To remove a site policy, use syntax similar to this:  `-Identity site:Redmond`. To remove a per-user policy, use syntax similar to this:  `-Identity SalesAccessPolicy`.  <br/> Note that wildcards are not allowed when specifying an Identity.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account for whom the external access policy is being removed. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your Skype for Business Online tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Policy.ExternalAccess.ExternalAccessPolicy object. The **Remove-CsExternalAccessPolicy** cmdlet accepts pipelined input of the external access policy object.
  
## Return Types

None. Instead, the **Remove-CsExternalAccessPolicy** cmdlet does not return a value or object. Instead, the cmdlet deletes instances of the Microsoft.Rtc.Management.WritableConfig.Policy.ExternalAccess.ExternalAccessPolicy object.
  
## See also

#### 

[Get-CsExternalAccessPolicy](get-csexternalaccesspolicy.md)
  
[Grant-CsExternalAccessPolicy](grant-csexternalaccesspolicy.md)
  
[New-CsExternalAccessPolicy](new-csexternalaccesspolicy.md)
  
[Set-CsExternalAccessPolicy](set-csexternalaccesspolicy.md)

