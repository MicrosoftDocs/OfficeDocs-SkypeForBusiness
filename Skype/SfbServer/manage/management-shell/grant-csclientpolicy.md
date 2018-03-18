---
title: "Grant-CsClientPolicy"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: c09d743d-cf2c-4622-b00c-cc815852e4a6
description: "Assigns a client policy to a user or a group of users. Among other things, client policies help determine the features of Skype for Business Server 2015 that are available to users; for example, you might give some users the right to transfer files while denying this right to other users. This cmdlet was introduced in Lync Server 2010."
---

# Grant-CsClientPolicy
 
Assigns a client policy to a user or a group of users. Among other things, client policies help determine the features of Skype for Business Server 2015 that are available to users; for example, you might give some users the right to transfer files while denying this right to other users. This cmdlet was introduced in Lync Server 2010.
  
```
Grant-CsClientPolicy -Identity <UserIdParameter> -PolicyName <String> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-PassThru <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

In Example 1, the client policy SalesPolicy is assigned to the user with the Identity Ken Myer. 
  
```
Grant-CsClientPolicy -Identity "Ken Myer" -PolicyName SalesPolicy
```

### EXAMPLE 2

In Example 2, all the users who belong to the Sales department are assigned the SalesPolicy client policy. The command first uses the **Get-CsUser** cmdlet and the LdapFilter parameter to return a collection of all the users who are members of the Sales department. This collection of users is then piped to the **Grant-CsClientPolicy** cmdlet, which assigns the policy SalesPolicy to each user in the collection.
  
```
Get-CsUser -LDAPFilter "Department=Sales" | Grant-CsClientPolicy -PolicyName SalesPolicy
```

### EXAMPLE 3

In Example 3, the client policy RedmondAccountingPolicy is assigned to all the users who meet two criteria: 1) the user must have the job title Accountant; and, 2) the user must work in the city of Redmond. To do this, the command first uses the **Get-CsUser** cmdlet and the LdapFilter parameter to return a collection of all the users who work in Redmond and have the job title Accountant. The filter value "(&amp;(Title=Accountant)(l=Redmond))" limits the returned data to users who have the job title Accountant (Title=Accountant) and (&amp;) who work in Redmond (l=Redmond). (The "l" is a lowercase L, and represents the user's locality.)
  
The resulting collection is then piped to the **Grant-CsClientPolicy** cmdlet, which assigns the policy RedmondAccountingPolicy to each user in the collection.
  
```
Get-CsUser -LDAPFilter "(&amp;(Title=Accountant)(l=Redmond))" | Grant-CsClientPolicy -PolicyName RedmondAccountingPolicy
```

### EXAMPLE 4

Example 4 assigns the policy AccountingPolicy to all the users who meet one of two criteria: either the user has the job title Accountant or the user has the job title Senior Accountant. To carry out this task, the **Get-CsUser** cmdlet and the LdapFilter parameter are used to return a collection of users with the job title Accountant or Senior Accountant. The filter value "(|(Title=Accountant)(Title=Senior Accountant))" limits the returned data to users with the job title Accountant (Title=Accountant) or (|) users with the job title Senior Accountant (Title=Senior Accountant). This filtered collection is then piped to the **Grant-CsClientPolicy** cmdlet, which assigns the client policy AccountingPolicy to each user in the collection.
  
```
Get-CsUser -LdapFilter "(|(Title=Accountant)(Title=Senior Accountant))" | Grant-CsClientPolicy -PolicyName AccountingPolicy
```

### EXAMPLE 5

In Example 5 all the users with accounts on the Registrar pool atl-cs-001.litwareinc.com are assigned the client policy AtlantaBranchPolicy. To do this, the **Get-CsUser** cmdlet is first called to return the appropriate user accounts; the Filter parameter and the filter value {RegistrarPool -eq "atl-cs-001.litwareinc.com"} ensure that only user accounts homed on the Registrar pool atl-cs-001.litwareinc.com will be returned. This collection is then piped to the **Grant-CsClientPolicy** cmdlet, which assigns each user the client policy AtlantaBranchPolicy.
  
```
Get-CsUser -Filter {RegistrarPool -eq "atl-cs-001.litwareinc.com"} | Grant-CsClientPolicy -PolicyName AtlantaBranchPolicy
```

## Detailed Description

Client policies are applied each time a user accesses the system, regardless of where the user logs on from and regardless of the type of device the user logs on with. In addition, client policies, like other Skype for Business Server 2015 policies, can readily be targeted to selected groups of users. You can even create a custom policy that gets assigned to a single user.
  
Client policies can be configured at the global, site, and per-user scopes. In order to assign per-user policies to users, you must use the **Grant-CsClientPolicy** cmdlet.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |Indicates the Identity of the user account the policy should be assigned to. User Identities can be specified by using one of four formats: 1) the user's SIP address; 2) the user's user principal name (UPN); 3) the user's domain name and logon name, in the form domain\logon (for example, litwareinc\kenmyer); and, 4) the user's Active Directory display name (for example, Ken Myer). User Identities can also be referenced by using the user's Active Directory distinguished name.  <br/> In addition, you can use the asterisk (\*) wildcard character when using the Display Name as the user Identity. For example, the Identity "\* Smith" returns all the users who have a display name that ends in the string value " Smith".  <br/> |
| _PolicyName_ <br/> |Required  <br/> |System.String  <br/> |"Name" of the policy to be assigned. The PolicyName is simply the policy Identity minus the policy scope ("tag:"). For example, a policy that has the Identity tag:Redmond has a PolicyName equal to Redmond; a policy with the Identity tag:RedmondConferencingPolicy has a PolicyName equal to RedmondConferencingPolicy.  <br/> If you set PolicyName to a null value, then the command will unassign any per-user policy assigned to the user. For example:  <br/>  `Grant-CsClientPolicy -Identity "Ken Myer" -PolicyName $Null` <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Enables you to specify a domain controller to connect to when assigning the policy. If this parameter is not included then the cmdlet will use the first available domain controller.  <br/> |
| _PassThru_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |If present, causes the cmdlet to pass the user object (or objects) through the Windows PowerShell pipeline. By default, the **Grant-CsClientPolicy** cmdlet does not pass objects through the pipeline. <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |PARAMVALUE: Guid  <br/> |
   
## Input Types

String value or Microsoft.Rtc.Management.ADConnect.Schema.ADUser object. The **Grant-CsClientPolicy** cmdlet accepts pipelined input of string values representing the Identity of a user account. The cmdlet also accepts pipelined input of user objects.
  
## Return Types

By default, the **Grant-CsClientPolicy** cmdlet returns no objects or values. However, if you include the PassThru parameter, the cmdlet will return instances of the Microsoft.Rtc.Management.ADConnect.Schema.OCSUserOrAppContact object.
  
## See also

#### 

[Get-CsClientPolicy](get-csclientpolicy.md)
  
[New-CsClientPolicy](new-csclientpolicy.md)
  
[Remove-CsClientPolicy](remove-csclientpolicy.md)
  
[Set-CsClientPolicy](set-csclientpolicy.md)

