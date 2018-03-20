---
title: "Grant-CsPersistentChatPolicy"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 58889550-167a-4267-9f3d-0f244e898599
description: "Assigns a per-user Persistent Chat policy to a user. Persistent Chat policies determine whether or not users are allowed access to Persistent Chat chat rooms. This cmdlet was introduced in Lync Server 2013."
---

# Grant-CsPersistentChatPolicy
 
Assigns a per-user Persistent Chat policy to a user. Persistent Chat policies determine whether or not users are allowed access to Persistent Chat chat rooms. This cmdlet was introduced in Lync Server 2013.
  
```
Grant-CsPersistentChatPolicy -Identity <UserIdParameter> -PolicyName <String> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-PassThru <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 assigns the per-user policy RedmondUsersPersistentChatPolicy to the user with the Active Directory display name "Ken Myer".
  
```
Grant-CsPersistentChatPolicy -Identity "Ken Myer" -PolicyName "RedmondUsersPersistentChatPolicy"
```

### Example 2

In Example 2, the per-user policy RedmondUsersPersistentChatPolicy is assigned to all the users who work in the IT department. To do this, the command first calls the **Get-CsUser** cmdlet along with the LdapFilter property; the filter value "Department=IT" limits the returned data to users who work in the IT department. That collection of users is then piped to the **Grant-CsPersistentChatPolicy** cmdlet, which assigns the policy RedmondUsersPersistentChatPolicy to each user in the collection.
  
```
Get-CsUser -LdapFilter "Department=IT" | Grant-CsPersistentChatPolicy -PolicyName "RedmondUsersPersistentChatPolicy"
```

### Example 3

In Example 3, the per-user Persistent Chat policy RedmondUsersPersistentChatPolicy is assigned to all the users who do not currently have a per-user Persistent Chat policy assigned to them. To carry out this task, the command first employs the **Get-CsUser** cmdlet and the Filter parameter; the filter value {PersistentChatPolicy -eq $Null} limits the returned data to user accounts in which the PersistentChatPolicy property is currently null ($Null). That collection of users is then piped to the **Grant-CsPersistentChatPolicy** cmdlet, which assigns each user in the collection the policy RedmondUsersPersistentChatPolicy.
  
```
Get-CsUser -Filter {PersistentChatPolicy -eq $Null} | Grant-CsPersistentChatPolicy -PolicyName "RedmondUsersPersistentChatPolicy"
```

### Example 4

The command shown in Example 4 unassigns the per-user Persistent Chat policy RedmondUsersPersistentChatPolicy from any user currently assigned that policy. To carry out this task, the command first uses the **Get-CsUser** cmdlet and the Filter parameter to return a collection of users currently assigned the policy RedmondUsersPersistentChatPolicy; the filter value {PersistentChatPolicy -eq "RedmondUsersPersistentChatPolicy"} restricts the returned items to user accounts where the PersistentChatPolicy property is equal to RedmondUsersPersistentChatPolicy. That collection is then piped the **Grant-CsPersistentChatPolicy** cmdlet, which unassigns the per-user policy by setting the PersistentChatPolicy property to a null value ($Null).
  
After the per-user policy has been unassigned, users will have their Persistent Chat capabilities managed by their Persistent Chat site policy (if it exists) or, if not, by the global Persistent Chat policy.
  
```
Get-CsUser -Filter {PersistentChatPolicy -eq "RedmondUsersPersistentChatPolicy"} | Grant-CsPersistentChatPolicy -PolicyName $Null
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Persistent Chat service (which replaces the Group Chat service used in Microsoft Lync Server 2010) provides organizations with messaging and collaboration capabilities similar to those found in Internet discussion forums: users can exchange messages in real-time, yet can also revisit and restart those conversations at any time. Conversations can be based around specific topics, and these conversations can be made available to everyone or to only a selected set of users. Likewise, individual chat rooms can be configured so that anyone can post a message or configured so that only designated presenters can post messages.
  
By default, users are not granted access to the Persistent Chat service; that access can only be granted if the user is managed by a Persistent Chat policy that allows for the user of the service. When you install Skype for Business Server 2015, all your users are managed by a global Persistent Chat policy in which the use of Persistent Chat is disabled. If you want to give all your users access to the service you can simply set the EnablePersistentChat property in this global policy to True. Alternatively, you can create additional policies at the site or at the per-user scope, and thus provide Persistent Chat access to some users while denying this access to other users.
  
 **Skype for Business Server Control Panel:** To assign a Persistent Chat policy to a user in the Skype for Business Server Control Panel, double-click the appropriate user account. In the **Edit Lync Server User** dialog box, select a policy from the **Persistent Chat policy** dropdown list and then click **Commit**.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |Indicates the Identity of the user account to be assigned the per-user Persistent Chat policy. User Identities are typically specified using one of four formats: 1) the user's SIP address; 2) the user's user principal name (UPN); 3) the user's domain name and logon name, in the form domain\logon (four example, litwareinc\kenmyer); and, 4) the user's Active Directory display name (for example, Ken Myer). User Identities can also be specified by using the user's Active Directory distinguished name.  <br/> In addition, you can use the asterisk (\*) wildcard character when using the Display Name as the user Identity. For example, the Identity "\* Smith" returns all the users who have a display name that ends with the string value " Smith".  <br/> |
| _PolicyName_ <br/> |Required  <br/> |System.String  <br/> |"Name" of the policy to be assigned. The PolicyName is simply the policy Identity minus the policy scope (the "tag:" prefix). For example, a policy with the Identity tag:Redmond has a PolicyName equal to Redmond; a policy with the Identity tag:RedmondUsersPersistentChatPolicy has a PolicyName equal to RedmondUsersPersistentChatPolicy. To unassign a per-user policy previously assigned to a user, set the PolicyName to a null value ($Null).  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Enables you to specify the fully qualified domain name of a domain controller to be contacted when assigning the new policy. If this parameter is not specified then the **Grant-CsPersistentChatPolicy** cmdlet will contact the first available domain controller. <br/> |
| _PassThru_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Enables you to pass a user object through the pipeline that represents the user being assigned the policy. By default, the **Grant-CsPersistentChatPolicy** cmdlet does not pass objects through the pipeline. <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |PARAMVALUE: Guid  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

String value or Microsoft.Rtc.Management.WritableConfig.Policy.PersistentChat.PersistentChatPolicy object. The **Grant-CsPersistentChatPolicy** cmdlet accepts pipelined input of string values representing the Identity of a user account. The cmdlet also accepts pipelined input of user objects.
  
## Return Types
<a name="ReturnTypes"> </a>

By default, the **Grant-CsPersistentChatPolicy** cmdlet does not return an objects or values. However, if you include the PassThru parameter, the cmdlet will return instances of the Microsoft.Rtc.Management.ADConnect.Schema.OCSUserOrAppContact.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsPersistentChatPolicy](get-cspersistentchatpolicy.md)
  
[New-CsPersistentChatPolicy](new-cspersistentchatpolicy.md)
  
[Remove-CsPersistentChatPolicy](remove-cspersistentchatpolicy.md)
  
[Set-CsPersistentChatPolicy](set-cspersistentchatpolicy.md)

