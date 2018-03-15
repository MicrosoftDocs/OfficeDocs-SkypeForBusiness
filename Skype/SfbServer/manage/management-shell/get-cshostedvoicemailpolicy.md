---
title: "Get-CsHostedVoicemailPolicy"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 5/22/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 52dd4397-b1c5-44a5-a744-75d715a4511b
description: "Retrieves a hosted voice mail policy. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsHostedVoicemailPolicy
 
Retrieves a hosted voice mail policy. This cmdlet was introduced in Lync Server 2010.
  
> [!NOTE]
> This cmdlet can be used only with Skype for Business on-premises. 
  
```
Get-CsHostedVoicemailPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

This command returns all defined hosted voice mail policies for the Skype for Business Server 2015 implementation.
  
```
Get-CsHostedVoicemailPolicy
```

### EXAMPLE 2

This command returns the policy settings for the per-user hosted voice mail policy ExRedmond.
  
```
Get-CsHostedVoicemailPolicy -Identity ExRedmond
```

### EXAMPLE 3

This command returns the policy settings for all per-user hosted voice mail policies (policies beginning with the tag scope).
  
```
Get-CsHostedVoicemailPolicy -Filter tag:*
```

### EXAMPLE 4

This command returns the hosted voice mail policy for the Skype for Business Online tenant with the tenant ID 73d355dd-ce5d-4ab9-bf49-7b822c18dd98.
  
```
Get-CsHostedVoicemailPolicy -Tenant "73d355dd-ce5d-4ab9-bf49-7b822c18dd98"
```

## Detailed Description

This cmdlet retrieves a policy that specifies how to route unanswered calls to a user to a hosted Exchange Unified Messaging (UM) service.
  
A user must be enabled for Exchange UM hosted voice mail for this policy to take effect. You can call the **Get-CsUser** cmdlet and check the HostedVoiceMail property to determine whether a user is enabled for hosted voice mail. (A value of True means the user is enabled.)
  
```

```

## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |This parameter allows you to do a wildcard search on the Identity of the hosted voice mail policy. This will retrieve all instances of a hosted voice mail policy where the Identity matches the wildcard pattern specified in the Filter value.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The unique identifier for the hosted voice mail policy you want to retrieve. The Identity includes the scope (in the case of global), the scope and site (for a site policy, such as site:Redmond), or the policy name (for a per-user policy, such as HVUserPolicy).  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the hosted voice mail policy from the local replica of the Central Management store, rather than the Central Management store itself.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account whose voicemail policy is to be retrieved.  <br/> For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> If you are using a remote session of Windows PowerShell and are connected only to Skype for Business Online you do not have to include the Tenant parameter. Instead, the tenant ID will automatically be filled in for you based on your connection information. The Tenant parameter is primarily for use in a hybrid deployment.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None.
  
## Return Types

This cmdlet returns an object of type Microsoft.Rtc.Management.WritableConfig.Policy.Voice.HostedVoicemailPolicy
  
## See also

#### 

[New-CsHostedVoicemailPolicy](new-cshostedvoicemailpolicy.md)
  
[Remove-CsHostedVoicemailPolicy](remove-cshostedvoicemailpolicy.md)
  
[Set-CsHostedVoicemailPolicy](set-cshostedvoicemailpolicy.md)
  
[Grant-CsHostedVoicemailPolicy](grant-cshostedvoicemailpolicy.md)

