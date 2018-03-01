---
title: "Remove-CsHostedVoicemailPolicy"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 13968bbe-1403-46de-b02a-ed61e712d1b3
description: "Removes a hosted voice mail policy. This cmdlet was introduced in Lync Server 2010."
---

# Remove-CsHostedVoicemailPolicy
 
Removes a hosted voice mail policy. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsHostedVoicemailPolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

This command removes the hosted voice mail policy for the ExRedmond per-user policy.
  
```
Remove-CsHostedVoicemailPolicy -Identity ExRedmond
```

### EXAMPLE 2

The command in Example 2 removes all per-user hosted voice mail policies. The command starts by calling the **Get-CsHostedVoicemailPolicy** cmdlet with a Filter of tag*, which will retrieve all policies defined as per-user policies. That set of policies is then piped to the **Remove-CsHostedVoicemailPolicy** cmdlet, which deletes each one.
  
```
Get-CsHostedVoicemailPolicy -Filter tag* | Remove-CsHostedVoicemailPolicy
```

## Detailed Description

This cmdlet removes a policy that specifies how to route unanswered calls to the user to a hosted Exchange Unified Messaging (UM) service.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |A unique identifier for the hosted voice mail policy that you want to remove. This identifier includes the scope (in the case of global), the scope and site (for a site policy, such as site:Redmond), or the policy name (for a per-user policy, such as HVUserPolicy).  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account for the hosted voicemail policy being deleted. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.HostedVoicemailPolicy object. Accepts pipelined input of hosted voice mail policy objects.
  
## Return Types

This cmdlet does not return an object. It removes an object of type Microsoft.Rtc.Management.WritableConfig.Policy.Voice.HostedVoicemailPolicy.
  
## See also

#### 

[New-CsHostedVoicemailPolicy](new-cshostedvoicemailpolicy.md)
  
[Set-CsHostedVoicemailPolicy](set-cshostedvoicemailpolicy.md)
  
[Get-CsHostedVoicemailPolicy](get-cshostedvoicemailpolicy.md)
  
[Grant-CsHostedVoicemailPolicy](grant-cshostedvoicemailpolicy.md)

