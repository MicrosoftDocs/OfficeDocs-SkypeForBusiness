---
title: "Get-CsPresencePolicy"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 65880bdb-4482-4cfb-83de-19b239784fe5
description: "Returns information about the presence policies configured for use in your organization. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsPresencePolicy
 
Returns information about the presence policies configured for use in your organization. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsPresencePolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

The command shown in Example 1 returns information about all the presence policies configured for use in the organization. This is done by calling the **Get-CsPresencePolicy** cmdlet without any parameters.
  
```
Get-CsPresencePolicy
```

### EXAMPLE 2

Example 2 returns a single per-user presence policy: the policy with the Identity RedmondPresencePolicy.
  
```
Get-CsPresencePolicy -Identity "RedmondPresencePolicy"
```

### EXAMPLE 3

Example 3 returns information about all the presence policies that have been configured at the site scope. To do this, the command uses the Filter parameter and the filter value "site:\*"; that filter value limits returned data to all the presence policies that have an Identity that begins with the string value "site:".
  
```
Get-CsPresencePolicy -Filter "site:*"
```

### EXAMPLE 4

In Example 4, information is returned for all the presence policies that limit the maximum number of prompted subscribers to 100 or less. To carry out this task, the command first calls the **Get-CsPresencePolicy** cmdlet without any parameters in order to return a collection of all the presence policies configured for use in the organization. This collection is then piped to the **Where-Object** cmdlet, which selects only those policies where the MaxPromptedSubscriber property is less than or equal to 100.
  
```
Get-CsPresencePolicy | Where-Object {$_.MaxPromptedSubscriber -le 100}
```

## Detailed Description

Presence information (which, among other things, lets you know whether a contact is available to take part in an instant messaging conversation) is invaluable. At the same time, however, there is a cost associated with presence information: the more presence subscriptions you have the more network bandwidth must be devoted to updating presence information. If network bandwidth is a concern, you might want to limit the number of presence subscriptions any one user can have.
  
The **CsPresencePolicy** cmdlets enable you to manage two important aspects of presence subscriptions: prompted subscribers and category subscriptions. When you are added to another person's Skype for Business Contacts list, the default behavior is for you to receive a pop-up notification informing you that you have been added to that list. Until you dismiss the pop-up, each notification counts as a prompted subscriber. The presence policy's MaxPromptedSubscriber property enables you to specify the maximum number of unresolved notification dialogs a user can have. (If a user reaches the maximum amount then he or she will not receive new contact notifications, at least not until some of those dialogs have been resolved.)
  
Category subscriptions represent a request for a specific category of information; for example, an application that requests calendar data. The MaxCategorySubscription property enables administrators to place a limit on the number of category subscriptions a user can have.
  
Prior to the release of Lync Server, prompted subscriber and category subscriptions were managed on a global basis. With the **CsPresencePolicy** cmdlets you can now manage these presence subscriptions at the global scope, the site scope, or the per-user scope. This enables you to control bandwidth use while, at the same time, ensuring that users have access to the presence information they need to do their jobs.
  
The **Get-CsPresencePolicy** cmdlet provides a way for you to return information about all the presence policies configured for use in your organization.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcards when specifying the policy (or policies) to be returned. For example, this syntax returns all the presence policies configured at the site scope:  <br/>  `-Filter "site:*"` <br/> The Filter and Identity parameters cannot be used in the same command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier of the presence policy to be retrieved. To return the global policy, use this syntax:  <br/>  `-Identity global` <br/> To return a policy configured at the site scope, use syntax similar to this:  <br/>  `-Identity "site:Redmond"` <br/> To return a policy configured at the per-user scope, use syntax like this:  <br/>  `-Identity "RedmondPresencePolicy"` <br/> You cannot use wildcard characters when specifying the Identity.  <br/> If neither the Identity nor the Filter parameters are specified, then the **Get-CsPresencePolicy** cmdlet returns all the presence policies configured for use in the organization. <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the presence policy data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account whose presence policies are being returned. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your Skype for Business Online tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **Get-CsPresencePolicy** cmdlet does not accept pipelined input.
  
## Return Types

The **Get-CsPresencePolicy** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Policy.Presence.PresencePolicy object.
  
## See also

#### 

[Grant-CsPresencePolicy](grant-cspresencepolicy.md)
  
[New-CsPresencePolicy](new-cspresencepolicy.md)
  
[Remove-CsPresencePolicy](remove-cspresencepolicy.md)
  
[Set-CsPresencePolicy](set-cspresencepolicy.md)

