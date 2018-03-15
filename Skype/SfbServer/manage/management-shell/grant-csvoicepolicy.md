---
title: "Grant-CsVoicePolicy"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: c8aa8d0f-6fb4-43f7-82b0-38d4da2d5611
description: "Assigns a voice policy to one or more users or groups. This cmdlet was introduced in Lync Server 2010."
---

# Grant-CsVoicePolicy
 
Assigns a voice policy to one or more users or groups. This cmdlet was introduced in Lync Server 2010.
  
```
Grant-CsVoicePolicy -Identity <UserIdParameter> -PolicyName <String> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-PassThru <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

This example assigns the voice policy with the Identity VoicePolicyRedmond to the user with the display name Ken Myer.
  
```
Grant-CsVoicePolicy -Identity "Ken Myer" -PolicyName VoicePolicyRedmond
```

### EXAMPLE 2

This example assigns the voice policy with the Identity VoicePolicyRedmond to all users in the Finance OU: OU=Finance,OU=NorthAmerica,DC=litwareinc,DC=com. The first part of the command calls the **Get-CsUser** cmdlet to retrieve all users enabled for Skype for Business Server 2015 from the specified OU. This collection of users is then piped to the **Grant-CsVoicePolicy** cmdlet, which assigns the policy VoicePolicyRedmond to each of these users.
  
```
Get-CsUser -OU "ou=Finance,ou=North America,dc=litwareinc,dc=com" | Grant-CsVoicePolicy -PolicyName VoicePolicyRedmond
```

## Detailed Description

This cmdlet assigns an existing per-user voice policy to a user. Voice policies are used to manage such Enterprise Voice-related features as simultaneous ringing (the ability to have a second phone ring each time someone calls your office phone) and call forwarding. Use this cmdlet to assign the settings that enable and disable these features for a specific user.
  
You can check whether a user has been granted a per-user voice policy by calling a command in this format:  `Get-CsUser "<user name>" | Select-Object VoicePolicy`. For example:
  
 `Get-CsUser "Ken Myer" | Select-Object VoicePolicy`
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |The Identity (unique identifier) of the user to whom the policy is being assigned.  <br/> User identities can be specified by using one of four formats: 1) The user's SIP address; 2) the user principal name (UPN); 3) the user's domain name and logon name, in the form domain\logon (for example, litwareinc\kenmyer); and, 4) the user's Active Directory display name (for example, Ken Myer).  <br/> Note that you can use the asterisk (\*) wildcard character when using the Display Name as the user Identity. For example, the Identity "\* Smith" would return all the users with the last name Smith.  <br/> Full Data Type: Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |
| _PolicyName_ <br/> |Required  <br/> |System.String  <br/> |The name (Identity) of the voice policy to be assigned to the user. (Note that this includes only the name portion of the Identity. Per-user policy identities include a prefix of tag: that should not be included with the PolicyName.)  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Allows you to specify a domain controller. If no domain controller is specified, the first available will be used.  <br/> |
| _PassThru_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Returns the results of the command. By default, this cmdlet does not generate any output.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |PARAMVALUE: Guid  <br/> |
   
## Input Types

String. Accepts a pipelined string value representing the Identity of a user account to which the voice policy is being granted.
  
## Return Types

When used with the PassThru parameter, returns an object of type Microsoft.Rtc.Management.ADConnect.Schema.OCSADUserOrAppContact.
  
## See also

#### 

[New-CsVoicePolicy](new-csvoicepolicy.md)
  
[Remove-CsVoicePolicy](remove-csvoicepolicy.md)
  
[Set-CsVoicePolicy](set-csvoicepolicy.md)
  
[Get-CsVoicePolicy](get-csvoicepolicy.md)
  
[Test-CsVoicePolicy](test-csvoicepolicy.md)
  
[Get-CsUser](get-csuser.md)

