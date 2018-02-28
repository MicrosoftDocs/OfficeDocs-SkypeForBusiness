---
title: "Get-CsVoicePolicy"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 05096aec-321c-4a50-99be-6e9fbbbe17fa
description: "Returns information about one or more voice policies configured for your organization. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsVoicePolicy
[]
Returns information about one or more voice policies configured for your organization. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsVoicePolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

This example displays all the voice policies that have been defined for an organization along with the settings for each.
  
```
Get-CsVoicePolicy
```

### EXAMPLE 2

This example uses the Identity parameter to retrieve the voice policy settings for the per-user policy named UserPolicy1.
  
```
Get-CsVoicePolicy -Identity UserPolicy1
```

### EXAMPLE 3

This example uses the Filter parameter to retrieve all the voice policy settings that can be assigned to users. All per-user voice policies have an Identity in the format **tag:\<UserVoicePolicy\>**, so we filter on tag to retrieve all user voice policies.
  
```
Get-CsVoicePolicy -Filter tag*
```

## Detailed Description

This cmdlet retrieves voice policy information. Voice policies are used to manage such Enterprise Voice-related features as simultaneous ringing (the ability to have a second phone ring each time someone calls your office phone) and call forwarding. Use this cmdlet to retrieve the settings that enable and disable many of these features.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |This parameter accepts a wildcard string and returns all voice policies with identities matching that string. For example, a Filter value of site:\* will return all voice policies defined at the site level.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |A unique identifier specifying the scope, and in some cases the name, of the policy. If this parameter is omitted, all voice policies for the organization are returned.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the voice policy from the local replica of the Central Management store, rather than the Central Management store itself.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account whose voice policy is to be retrieved. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> If you are using a remote session of Windows PowerShell and are connected only to Skype for Business Online you do not have to include the Tenant parameter. Instead, the tenant ID will automatically be filled in for you based on your connection information. The Tenant parameter is primarily for use in a hybrid deployment.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None.
  
## Return Types

This cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoicePolicy object.
  
## See also

#### 

[New-CsVoicePolicy](new-csvoicepolicy.md)
  
[Remove-CsVoicePolicy](remove-csvoicepolicy.md)
  
[Set-CsVoicePolicy](set-csvoicepolicy.md)
  
[Grant-CsVoicePolicy](grant-csvoicepolicy.md)
  
[Test-CsVoicePolicy](test-csvoicepolicy.md)

