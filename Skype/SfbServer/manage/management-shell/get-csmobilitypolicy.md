---
title: "Get-CsMobilityPolicy"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 51ef83de-9cc2-4df8-b4f1-8d816b8de431
description: "Retrieves information about the mobility policies currently in use in an organization. Mobility policies determine whether or not a user can use Skype for Business Mobile. These policies also manage a user's ability to employ Call via Work, a feature that enables users to make and receive phone calls on their mobile phone by using their work phone number instead of their mobile phone number. Mobility policies can also be used to require Wi-Fi connections when making or receiving calls. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsMobilityPolicy
 
Retrieves information about the mobility policies currently in use in an organization. Mobility policies determine whether or not a user can use Skype for Business Mobile. These policies also manage a user's ability to employ Call via Work, a feature that enables users to make and receive phone calls on their mobile phone by using their work phone number instead of their mobile phone number. Mobility policies can also be used to require Wi-Fi connections when making or receiving calls. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsMobilityPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

The command shown in Example 1 returns information about all the mobility policies configured for use in your organization.
  
```
Get-CsMobilityPolicy
```

### EXAMPLE 2

Example 2 returns information about a single mobility policy: the policy with the Identity site:Redmond.
  
```
Get-CsMobilityPolicy -Identity "site:Redmond"
```

### EXAMPLE 3

In Example 3, information is returned for all of your per-user mobility policies. To do this, the Filter parameter is included along with the filter value "tag:\*"; this returns any policy that has an Identity that begins with the string value "tag:". By definition, any policy that has an identity beginning with that string value is a per-user policy.
  
```
Get-CsMobilityPolicy -Filter "tag:*"
```

### EXAMPLE 4

The command shown in Example 4 limits the returned data to mobility policies where Call via Work has been disabled. To carry out this task, the command first calls the **Get-CsMobilityPolicy** cmdlet without any parameters; that returns a collection of all the mobility policies configured for use in the organization. This collection is then piped to the **Where-Object** cmdlet, which picks out only those policies where the EnableOutsideVoice property is equal to (-eq) False.
  
```
Get-CsMobilityPolicy | Where-Object {$_.EnableOutsideVoice -eq $False}

```

## Detailed Description

Skype for Business Mobile is a client application that enables users to run Skype for Business on their mobile phones. Call via Work provides a way for users to make calls on their mobile phone and yet have it appear as though the call originated from their work phone number instead of their mobile phone number. Users who have been enabled for Call via Work can achieve this either by dialing directly from their mobile phone or by using the dial-out conferencing option. With dial-out conferencing, a user effectively asks the Skype for Business Server 2015 Mobility Service server to make a call for them. The server will set up the call, and then call the user back on their mobile phone. After the user has answered, the server will then dial the party being called. Both of these capabilities can be managed using mobility policies.
  
With Skype for Business Server 2015, mobile devices can make or receive phone calls by using either the standard cellular phone network. or by using Wi-Fi connections. Mobility policies can be used to require Wi-Fi connections and to prevent calls over the cellular network.
  
Mobility policies can be configured at the global, site, or the per-user scope, and information about those policies can be retrieved by using the **Get-CsMobilityPolicy** cmdlet.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard characters when indicating the policy (or policies) to be returned. For example, to return all the policies configured at the site scope use this syntax:  <br/>  `-Filter "site:*"` <br/> To return a collection of all the per-user policies, use this syntax:  <br/>  `-Filter "tag:*"` <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier of the mobility policy to be returned. To refer to the global policy, use this syntax:  <br/>  `-Identity global` <br/> To refer to a site policy, use syntax similar to this:  <br/>  `-Identity site:Redmond` <br/> To refer to a per-user policy, use syntax similar to this:  <br/>  `-Identity SalesDepartmentPolicy` <br/> If this parameter is not specified, then the **Get-CsMobilityPolicy** cmdlet returns a collection of all the mobility policies in use in the organization. <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the mobility policy data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |PARAMVALUE: Guid  <br/> |
   
## Input Types

The **Get-CsMobilityPolicy** cmdlet does not accept pipelined input.
  
## Return Types

The **Get-CsMobilityPolicy** cmdlet returns instances of the Microsoft.Rtc.Management.WriteableConfig.Policy.Mobility.Mobility object.
  

