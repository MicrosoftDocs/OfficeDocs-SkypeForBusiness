---
title: "Grant-CsHostedVoicemailPolicy"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ae69358f-1618-4a08-9ec2-225ded3f301f
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Grant-CsHostedVoicemailPolicy
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Assigns a hosted voice mail policy at the per-user scope. (The per-user scope enables you to assign policies to individual users or groups.) This cmdlet was introduced in Lync Server 2010.
  
```
Grant-CsHostedVoicemailPolicy -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-PassThru <SwitchParameter>] [-PolicyName <String>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

This example assigns the hosted voice mail policy with the Identity ExRedmond to the user with the display name Ken Myer.
  
```
Grant-CsHostedVoicemailPolicy -Identity "Ken Myer" -PolicyName ExRedmond
```

### EXAMPLE 2

This example assigns the hosted voice mail policy with the Identity ExRedmond to all users in the Finance organizational unit (OU): OU=Finance,OU=NorthAmerica,DC=litwareinc,DC=com. The first part of the command calls the **Get-CsUser** cmdlet to retrieve all users who are enabled for Lync Server or Office Communications Server from the specified OU. This collection of users is then piped to the **Grant-CsHostedVoicemailPolicy** cmdlet, which assigns the policy ExRedmond to each of these users. 
  
```
Get-CsUser -OU "ou=Finance,ou=North America,dc=litwareinc,dc=com" | Grant-CsHostedVoicemailPolicy -PolicyName ExRedmond
```

## Detailed Description
<a name="sectionSection1"> </a>

This cmdlet assigns an existing user-specific hosted voice mail policy to a user. A hosted voice mail policy specifies how to route unanswered calls to a user to a hosted Exchange Unified Messaging (UM) service.
  
You can check whether a user has been granted a per-user hosted voice mail policy by calling a command in this format: Get-CsUser "\<user name\>" | Select-Object HostedVoicemailPolicy. For example:
  
Get-CsUser "Ken Myer" | Select-Object HostedVoicemailPolicy
  
If you assign to a user a hosted voice mail policy that does not include a destination, you cannot enable that user for hosted voice mail.
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Grant-CsHostedVoicemailPolicy** cmdlet locally: RTCUniversalUserAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Grant-CsHostedVoicemailPolicy"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |The Identity (unique identifier) of the user to whom the hosted voice mail policy is being assigned.  <br/> User identities can be specified using one of four formats: 1) The user's SIP address; 2) the user's user principal name (UPN); 3) the user's domain name and logon name, in the form domain\logon (for example, litwareinc\kenmyer); and, 4) the user's Active Directory display name (for example, Ken Myer).  <br/> Note that you can use the asterisk (\*) wildcard character when using the Display Name as the user Identity. For example, the Identity "\* Smith" would return all the users with the last name Smith.  <br/> Full data type: Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Allows you to specify a domain controller. If no domain controller is specified, the first available will be used.  <br/> |
| _PassThru_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Returns the results of the command. By default, this cmdlet does not generate any output.  <br/> |
| _PolicyName_ <br/> |Optional  <br/> |System.String  <br/> |The name (Identity) of the hosted voice mail policy to be assigned to the user. (Note that this includes only the name portion of the Identity. Per-user hosted voice mail policy identities include a prefix of tag: that should not be included with the PolicyName.)  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

String. Accepts a pipelined string value representing the Identity of a user account to which the hosted voice mail policy is being granted.
  
## Return Types
<a name="sectionSection3"> </a>

When used with the PassThru parameter, returns an object of type Microsoft.Rtc.Management.ADConnect.Schema.OCSADUserOrAppContact.
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsHostedVoicemailPolicy](new-cshostedvoicemailpolicy.md)
  
[Remove-CsHostedVoicemailPolicy](remove-cshostedvoicemailpolicy.md)
  
[Set-CsHostedVoicemailPolicy](set-cshostedvoicemailpolicy.md)
  
[Get-CsHostedVoicemailPolicy](get-cshostedvoicemailpolicy.md)
  
[Get-CsUser](get-csuser.md)

