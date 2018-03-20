---
title: "Set-CsHostedVoicemailPolicy"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 9c47d2a5-356c-4bab-9cef-8346c4b5d99c
description: "Modifies a hosted voice mail policy. This cmdlet was introduced in Lync Server 2010."
---

# Set-CsHostedVoicemailPolicy
 
Modifies a hosted voice mail policy. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsHostedVoicemailPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

This command modifies the Destination property of a hosted voice mail policy named ExRedmond. It sets the Exchange UM destination for this policy to be at FQDN ExUM.contoso.com.
  
```
Set-CsHostedVoicemailPolicy -Identity ExRedmond -Destination ExUM.contoso.com
```

### EXAMPLE 2

This command adds an Exchange tenant to the comma-separated list of tenants (organizations) for the policy ExRedmond. The first line calls the **Get-CsHostedVoicemailPolicy** cmdlet to retrieve the policy with the Identity ExRedmond. This cmdlet call is in parentheses because we need to first retrieve this policy. We then use "dot notation" to retrieve the Organization property of the policy. We save the returned string in the variable $a. The next line uses the += operator to append the assigned string (,corp3.litwareinc.com) to the end of the string stored in variable $a. (Note the comma in the assigned string. Organization is a comma-separated list, so if there's already a value in the list any additional values need to be preceded by a comma.) Finally, in the last line we call the **Set-CsHostedVoicemailPolicy** cmdlet and assign the new Organization string by passing the variable $a to the parameter Organization.
  
```
$a = (Get-CsHostedVoicemailPolicy -Identity ExRedmond).Organization
$a += ",corp3.litwareinc.com"
Set-CsHostedVoicemailPolicy -Identity ExRedmond -Organization $a
```

### Example 3

The command shown in Example 3 modifies the Destination property of the hosted voicemail policy assigned to the Skype for Business Online tenant with the tenant ID 73d355dd-ce5d-4ab9-bf49-7b822c18dd98.
  
```
Set-CsHostedVoicemailPolicy -Tenant "73d355dd-ce5d-4ab9-bf49-7b822c18dd98" -Destination "ExUM.contoso.com"
```

## Detailed Description

This cmdlet modifies a policy that configures a user account enabled for Skype for Business Server 2015 to use an Exchange Unified Messaging (UM) hosted voice mail service. The policy determines how to route unanswered calls to the user to a hosted Exchange UM service.
  
A user must be enabled for Exchange UM hosted voice mail for this policy to take effect. You can call the **Get-CsUser** cmdlet and check the HostedVoiceMail property to determine whether a user is enabled for hosted voice mail. (A value of True means the user is enabled.)
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Description_ <br/> |Optional  <br/> |System.String  <br/> |A friendly description of the policy.  <br/> |
| _Destination_ <br/> |Optional  <br/> |System.String  <br/> |The value assigned to this parameter is the fully qualified domain name (FQDN) of the hosted Exchange UM service. Note that the chosen destination must be trusted for routing.  <br/> If you attempt to enable a user for hosted voice mail and the user's assigned policy does not have a Destination value, the enable will fail.  <br/> This value must be 255 characters or less and in a format matching the regular expression string ^[a-zA-Z0-9\-_]+(\.[a-zA-Z0-9\-_]+){0,}$. This just means it should be in the form of an FQDN, such as server.litwareinc.com.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |A unique identifier for the hosted voice mail policy you want to modify. This identifier includes the scope (in the case of global), the scope and site (for a site policy, such as site:Redmond), or the policy name (for a per-user policy, such as HVUserPolicy).  <br/> |
| _Instance_ <br/> |Optional  <br/> |HostedVoicemailPolicy  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values. The object must be of type HostedVoicemailPolicy and can be retrieved by calling the **Get-CsHostedVoicemailPolicy** cmdlet. <br/> |
| _Organization_ <br/> |Optional  <br/> |System.String  <br/> |This parameter contains a comma-separated list of the Exchange tenants that contain Skype for Business Server 2015 users. Each tenant must be specified as an FQDN of the tenant on the hosted Exchange Service.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Server 2015 tenant account for which hosted voicemail policy being modified. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.HostedVoicemailPolicy object. Accepts pipelined input of hosted voice mail policy objects.
  
## Return Types

This cmdlet modifies an object of type Microsoft.Rtc.Management.WritableConfig.Policy.Voice.HostedVoicemailPolicy
  
## See also

#### 

[New-CsHostedVoicemailPolicy](new-cshostedvoicemailpolicy.md)
  
[Remove-CsHostedVoicemailPolicy](remove-cshostedvoicemailpolicy.md)
  
[Get-CsHostedVoicemailPolicy](get-cshostedvoicemailpolicy.md)
  
[Grant-CsHostedVoicemailPolicy](grant-cshostedvoicemailpolicy.md)

