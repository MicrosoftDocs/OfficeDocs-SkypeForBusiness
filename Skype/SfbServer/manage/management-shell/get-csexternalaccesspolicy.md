---
title: "Get-CsExternalAccessPolicy"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 301403c8-aeb2-4501-a2ae-96eaa6ad68a4
description: "Returns information about the external access policies that have been configured for use in your organization. External access policies determine whether or not your users can: 1) communicate with users who have Session Initiation Protocol (SIP) accounts with a federated organization; 2) communicate with users who have SIP accounts with a public instant messaging (IM) provider such as Windows Live; and, 3) access Skype for Business Server 2015 over the Internet, without having to log on to your internal network. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsExternalAccessPolicy
 
Returns information about the external access policies that have been configured for use in your organization. External access policies determine whether or not your users can: 1) communicate with users who have Session Initiation Protocol (SIP) accounts with a federated organization; 2) communicate with users who have SIP accounts with a public instant messaging (IM) provider such as Windows Live; and, 3) access Skype for Business Server 2015 over the Internet, without having to log on to your internal network. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsExternalAccessPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

Example 1 returns a collection of all the external access policies configured for use in your organization. Calling the **Get-CsExternalAccessPolicy** cmdlet without any additional parameters always returns the complete collection of external access policies.
  
```
Get-CsExternalAccessPolicy
```

### EXAMPLE 2

Example 2 uses the Identity parameter to return the external access policy that has the Identity site:Redmond. Because access policy Identities must be unique, this command will never return more than one item.
  
```
Get-CsExternalAccessPolicy -Identity site:Redmond
```

### EXAMPLE 3

The command shown in Example 3 uses the Filter parameter to return all of the external access policies that have been configured at the per-user scope; the parameter value "tag:\*" limits returned data to those policies that have an Identity that begins with the string value "tag:". By definition, any policy that has an Identity beginning with "tag:" is a policy that has been configured at the per-user scope. 
  
```
Get-CsExternalAccessPolicy -Filter tag:*
```

### EXAMPLE 4

In Example 4, the **Get-CsExternalAccessPolicy** cmdlet and the **Where-Object** cmdlet are used to return all the external access policies that grant users federation access. To do this, the **Get-CsExternalAccessPolicy** cmdlet is first used to return a collection of all the external access policies currently in use in the organization. This collection is then piped to the **Where-Object** cmdlet, which selects only those policies where the EnableFederationAccess property is equal to True.
  
```
Get-CsExternalAccessPolicy | Where-Object {$_.EnableFederationAccess -eq $True}
```

### EXAMPLE 5

The command shown in Example 5 returns the external access policies that meet two criteria: both federation access and public cloud access are allowed. In order to perform this task, the command first uses the **Get-CsExternalAccessPolicy** cmdlet to return a collection of all the access policies in use in the organization. That collection is then piped to the **Where-Object** cmdlet, which picks out only those policies that meet two criteria: the EnableFederationAccess property must be equal to True and the EnablePublicCloudAccess property must also be equal to True. Only policies in which both EnableFederationAccess and EnablePublicCloudAccess are True will be returned and displayed on the screen.
  
```
Get-CsExternalAccessPolicy | Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $True} 
```

## Detailed Description

When you install Skype for Business Server 2015 your users are only allowed to exchange instant messages and presence information among themselves: by default, they can only communicate with other people who have SIP accounts in your Active Directory Domain Services. In addition, users are not allowed to access Skype for Business Server 2015 over the Internet; instead, they must be logged on to your internal network before they will be able to log on to Skype for Business Server 2015.
  
That might be sufficient to meet your communication needs. If it doesn't meet your needs, you can use external access policies to extend the ability of your users to communicate and collaborate. External access policies can grant (or revoke) the ability of your users to do any or all of the following: 
  
1. Communicate with people who have SIP accounts with a federated organization. Note that enabling federation alone will not provide users with this capability. Instead, you must enable federation and then assign users an external access policy that gives them the right to communicate with federated users.
  
2. Communicate with people who have SIP accounts with a public instant messaging service such as Windows Live.
  
3. Access Skype for Business Server 2015 over the Internet, without having to first log on to your internal network. This enables your users to use Skype for Business and log on to Skype for Business Server 2015 from an Internet café or other remote location.
  
The **Get-CsExternalAccessPolicy** cmdlet provides a way for you to return information about all of the external access policies that have been configured for use in your organization.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to do a wildcard search for external access policies. For example, to find all the policies configured at the site scope, use this Filter: site:\*. To find the per-user policies Seattle, Seville, and Saskatoon (all of which start with the letter "S") use this Filter: "S\*". Note that the Filter parameter can only be applied to the policy Identity.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique Identity assigned to the policy when it was created. External access policies can be assigned at the global, site, or per-user scope. To refer to the global instance use this syntax: -Identity global. To refer to a policy at the site scope, use this syntax:  `-Identity site:Redmond`. To refer to a policy at the per-user scope, use syntax similar to this:  `-Identity RedmondPolicy`.  <br/> Note that wildcard characters such as the asterisk (\*) cannot be used with the Identity parameter. To do a wildcard search for policies, use the Filter parameter instead.  <br/> If neither the Identity nor Filter parameters are specified, then the **Get-CsExternalAccessPolicy** cmdlet will bring back a collection of all the external access policies configured for use in the organization. <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the external access policy data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |PARAMVALUE: Guid  <br/> |
   
## Input Types

None. The **Get-CsExternalAccessPolicy** cmdlet does not accept pipelined input.
  
## Return Types

Returns instances of the Microsoft.Rtc.Management.WritableConfig.Policy.ExternalAccess.ExternalAccessPolicy object.
  
## See also

#### 

[Grant-CsExternalAccessPolicy](grant-csexternalaccesspolicy.md)
  
[New-CsExternalAccessPolicy](new-csexternalaccesspolicy.md)
  
[Remove-CsExternalAccessPolicy](remove-csexternalaccesspolicy.md)
  
[Set-CsExternalAccessPolicy](set-csexternalaccesspolicy.md)

