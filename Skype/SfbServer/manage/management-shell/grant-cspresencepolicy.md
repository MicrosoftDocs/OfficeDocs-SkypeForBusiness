---
title: "Grant-CsPresencePolicy"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 756c08a7-26b0-4ea8-816b-b33ebcac51aa
description: "Grants a per-user presence policy to a user or group of users. This cmdlet was introduced in Lync Server 2010."
---

# Grant-CsPresencePolicy
[]
Grants a per-user presence policy to a user or group of users. This cmdlet was introduced in Lync Server 2010.
  
```
Grant-CsPresencePolicy -Identity <UserIdParameter> -PolicyName <String> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-PassThru <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 assigns the per-user presence policy RedmondPresencePolicy to a single user: the user with the Identity Ken Myer.
  
```
Grant-CsPresencePolicy -Identity "Ken Myer" -PolicyName "RedmondPresencePolicy"
```

### EXAMPLE 2

In Example 2, the presence policy RedmondPresencePolicy is assigned to all the users who have accounts in the Redmond OU in Active Directory Domain Services. To do this, the command first uses the **Get-CsUser** cmdlet and the OU parameter to return a collection of all the user accounts found in the Redmond OU (OU=Redmond,dc=litwareinc,dc=com). This collection is then piped to the **Grant-CsPresencePolicy** cmdlet, which assigns the policy RedmondPresencePolicy to each user in the collection.
  
```
Get-CsUser -OU "OU=Redmond,dc=litwareinc,dc=com" | Grant-CsPresencePolicy -PolicyName "RedmondPresencePolicy"
```

### EXAMPLE 3

Example 3 assigns the policy RedmondPresencePolicy to all the users who work in the city of Redmond. To carry out this task, the command first uses the **Get-CsUser** cmdlet and the LdapFilter parameter to return a collection of all the users who work in Redmond; the filter value "l=Redmond" limits the returned data to users from Redmond. (In the LDAP query language, l, the lowercase L, is short for "locality.") The retrieved collection is then piped to the **Grant-CsPresencePolicy** cmdlet, which assigns the policy RedmondPresencePolicy to each user in the collection.
  
```
Get-CsUser -LdapFilter "l=Redmond" | Grant-CsPresencePolicy -PolicyName "RedmondPresencePolicy"
```

### EXAMPLE 4

The command shown in Example 4 unassigns any per-user presence policy previously assigned to users who work in Redmond. Calling the **Grant-CsPresencePolicy** cmdlet while setting the PolicyName parameter to a null value ($Null) causes the cmdlet to remove any per-user presence policies assigned to the users affected by the command.
  
```
Get-CsUser -LdapFilter "l=Redmond" | Grant-CsPresencePolicy -PolicyName $Null
```

## Detailed Description

Presence information (which, among other things, lets you know whether a contact is available to take part in an instant messaging conversation) is invaluable. At the same time, however, there is a cost associated with presence information: the more presence subscriptions you have the more network bandwidth must be devoted to updating presence information. If network bandwidth is a concern, you might want to limit the number of presence subscriptions any one user can have.
  
The CsPresencePolicy cmdlets enable you to manage two important aspects of presence subscriptions: prompted subscribers and category subscriptions. When you are added to another person's Skype for Business Contacts list, the default behavior is for you to receive a pop-up notification informing you that you have been added to that list. Until you dismiss the pop-up, each notification counts as a prompted subscriber. The presence policy's MaxPromptedSubscriber property enables you to specify the maximum number of unresolved notification dialogs a user can have. (If a user reaches the maximum amount, then he or she will not receive new contact notifications, at least not until some of those dialogs have been resolved.) 
  
Category subscriptions represent a request for a specific category of information; for example, an application that requests calendar data. The MaxCategorySubscription property enables administrators to place a limit on the number of category subscriptions a user can have.
  
Prior to the release of Lync Server, prompted subscriber and category subscriptions were managed on a global basis. With the **CsPresencePolicy** cmdlets you can now manage these presence subscriptions at the global scope, the site scope, or the per-user scope. This enables you to control bandwidth use while, at the same time, ensuring that users have access to the presence information they need to do their jobs.
  
When you create a per-user policy, that policy is not automatically assigned to anyone. Instead, per-user presence policies must be explicitly assigned to users (or groups of users) by running the **Grant-CsPresencePolicy** cmdlet.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |Indicates the Identity of the user account to be assigned the presence policy. User Identities can be specified using one of four formats: 1) the user's SIP address; 2) the user's user principal name (UPN); 3) the user's domain name and logon name, in the form domain\logon (for example, litwareinc\kenmyer); and, 4) the user's Active Directory display name (for example, Ken Myer). User Identities can also be specified by using the user's Active Directory distinguished name.  <br/> In addition, you can use the asterisk (\*) wildcard character when using the Display Name as the user Identity. For example, the Identity "\* Smith" returns all the users with display name that ends with the string value "Smith".  <br/> |
| _PolicyName_ <br/> |Required  <br/> |System.String  <br/> |Identity of the per-user policy to be assigned; for example:  <br/>  `-PolicyName "RedmondPresencePolicy"` <br/> The PolicyName is the Identity of the policy minus the "tag:" prefix. For example, a policy with the Identity "tag:NorthAmericaPresencePolicy" has a PolicyName equal to "NorthAmericaPresencePolicy".  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified name of the domain (FQDN) controller to be contacted when assigning the policy. For example:  <br/>  `-DomainController atl-dc-001.litwareinc.com` <br/> If not specified, the **Grant-CsPresencePolicy** cmdlet will contact the nearest available domain controller when assigning the policy. <br/> |
| _PassThru_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Enables you to pass a user object through the pipeline that represents the user being assigned the policy. By default, the **Grant-CsPresencePolicy** cmdlet does not pass objects through the pipeline. <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |PARAMVALUE: Guid  <br/> |
   
## Input Types

String value or Microsoft.Rtc.Management.WritebleConfig.Policy.Presence.PresencePolicy object. The **Grant-CsPresencePolicy** cmdlet accepts pipelined input of string values representing the Identity of a user account. The cmdlet also accepts pipelined input of user objects.
  
## Return Types

By default, the **Grant-CsPresencePolicy** cmdlet does not return an objects or values. However, if you include the PassThru parameter, the cmdlet will return instances of the Microsoft.Rtc.Management.ADConnect.Schema.OCSUserOrAppContact.
  
## See also

#### 

[Get-CsPresencePolicy](get-cspresencepolicy.md)
  
[New-CsPresencePolicy](new-cspresencepolicy.md)
  
[Remove-CsPresencePolicy](remove-cspresencepolicy.md)
  
[Set-CsPresencePolicy](set-cspresencepolicy.md)

