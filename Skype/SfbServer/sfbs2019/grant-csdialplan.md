---
title: "Grant-CsDialPlan"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 730ad014-b1e8-4f0a-be78-32b1b5488b78
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Grant-CsDialPlan
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Assigns a dial plan to one or more users or groups. This cmdlet was introduced in Lync Server 2010.
  
```
Grant-CsDialPlan -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-PassThru <SwitchParameter>] [-PolicyName <String>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

In the example, the **Grant-CsDialPlan** cmdlet is used to assign the dial plan RedmondDialPlan to the user with the Identity (in this case the display name) Ken Myer. 
  
```
Grant-CsDialPlan -Identity "Ken Myer" -PolicyName RedmondDialPlan
```

### EXAMPLE 2

In Example 2, the RedmondDialPlan dial plan is assigned to all the users who have offices in the city of Redmond. To do this, the **Get-CsUser** cmdlet is invoked in order to retrieve a collection of all the users who have an office in the city of Redmond; this is done by using the LdapFilter parameter and the LDAP query l=Redmond. (In the LDAP query language used by Active Directory Domain Services, the l indicates a user's locality, or city.) This collection is then piped to the **Grant-CsDialPlan** cmdlet, which assigns the Redmond dial plan to each user in the collection. 
  
```
Get-CsUser -LDAPFilter "l=Redmond" | Grant-CsDialPlan -PolicyName RedmondDialPlan
```

## Detailed Description
<a name="sectionSection1"> </a>

This cmdlet assigns an existing user-specific dial plan to a user. Dial plans provide information required to enable Enterprise Voice users to make telephone calls. Users who do not have a valid dial plan will not be enabled to make calls by using Enterprise Voice. A dial plan determines such things as how normalization rules are applied and whether a prefix must be dialed for external calls.
  
You can check whether a user has been granted a per-user dial plan by calling a command in this format: Get-CsUser "\<user name\>" | Select-Object DialPlan. For example:
  
Get-CsUser "Ken Myer" | Select-Object DialPlan
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Grant-CsDialPlan** cmdlet locally: RTCUniversalUserAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Grant-CsDialPlan"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |The Identity (unique identifier) of the user to whom the dial plan is being assigned.  <br/> User identities can be specified using one of four formats: 1) The user's SIP address; 2) the user's user principal name (UPN); 3) the user's domain name and logon name, in the form domain\logon (for example, litwareinc\kenmyer); and, 4) the user's Active Directory display name (for example, Ken Myer).  <br/> Note that you can use the asterisk (\*) wildcard character when using the Display Name as the user Identity. For example, the Identity "\* Smith" would return all the users with the last name Smith.  <br/> Full data type: Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Allows you to specify a domain controller. If no domain controller is specified, the first available will be used.  <br/> |
| _PassThru_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Returns the results of the command. By default, this cmdlet does not generate any output.  <br/> |
| _PolicyName_ <br/> |Optional  <br/> |System.String  <br/> |The Identity value of the dial plan to be assigned to the user. (Note that this includes only the name portion of the Identity. Per-user dial plan identities include a prefix of tag: that should not be included with the PolicyName.)  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

String. Accepts a pipelined string value representing the Identity of a user account to which the dial plan is being granted.
  
## Return Types
<a name="sectionSection3"> </a>

When used with the PassThru parameter, returns an object of type Microsoft.Rtc.Management.ADConnect.Schema.OCSADUserOrAppContact.
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsDialPlan](new-csdialplan.md)
  
[Remove-CsDialPlan](remove-csdialplan.md)
  
[Set-CsDialPlan](set-csdialplan.md)
  
[Get-CsDialPlan](get-csdialplan.md)
  
[Test-CsDialPlan](test-csdialplan.md)
  
[Get-CsUser](get-csuser.md)

