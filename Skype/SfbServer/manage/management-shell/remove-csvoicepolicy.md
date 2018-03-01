---
title: "Remove-CsVoicePolicy"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 4d3e67be-c094-415f-b1e6-0719dec6f3fc
description: "Removes the specified voice policy. This cmdlet was introduced in Lync Server 2010."
---

# Remove-CsVoicePolicy
 
Removes the specified voice policy. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsVoicePolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

This example removes the UserVoicePolicy1 per-user voice policy settings.
  
```
Remove-CsVoicePolicy -Identity UserVoicePolicy1
```

### EXAMPLE 2

This example removes all the voice policy settings that can be assigned to specific users. First the **Get-CsVoicePolicy** cmdlet is called with a Filter of tag*, which retrieves all the per-user voice policies. That collection of policies is then piped to the **Remove-CsVoicePolicy** cmdlet to be removed.
  
```
Get-CsVoicePolicy -Filter tag* | Remove-CsVoicePolicy
```

## Detailed Description

This cmdlet removes an existing voice policy. Voice policies are used to manage such Enterprise Voice-related features as simultaneous ringing (the ability to have a second phone ring each time someone calls your office phone) and call forwarding. This cmdlet can also be used to remove the global voice policy. In that case, however, the policy will not actually be removed; instead, the policy settings will simply be reset to their default values.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |A unique identifier specifying the scope, and in some cases the name, of the policy to be removed.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account for the voice policy being deleted. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> If you are using a remote session of Windows PowerShell and are connected only to Skype for Business Online you do not have to include the Tenant parameter. Instead, the tenant ID will automatically be filled in for you based on your connection information. The Tenant parameter is primarily for use in a hybrid deployment.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoicePolicy object. Accepts pipelined input of voice policy objects.
  
## Return Types

This cmdlet does not return a value. It removes an instance of a Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoicePolicy object.
  
## See also

#### 

[New-CsVoicePolicy](new-csvoicepolicy.md)
  
[Set-CsVoicePolicy](set-csvoicepolicy.md)
  
[Get-CsVoicePolicy](get-csvoicepolicy.md)
  
[Grant-CsVoicePolicy](grant-csvoicepolicy.md)
  
[Test-CsVoicePolicy](test-csvoicepolicy.md)

