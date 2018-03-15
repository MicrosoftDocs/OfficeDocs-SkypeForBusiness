---
title: "Remove-CsPersistentChatPolicy"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d6bfe22b-084b-4d7f-8e4a-58f738493b31
description: "Removes an existing Persistent Chat policy. Persistent Chat policies determine whether or not users are allowed access to Persistent Chat chat rooms. This cmdlet was introduced in Lync Server 2013."
---

# Remove-CsPersistentChatPolicy
 
Removes an existing Persistent Chat policy. Persistent Chat policies determine whether or not users are allowed access to Persistent Chat chat rooms. This cmdlet was introduced in Lync Server 2013.
  
```
Remove-CsPersistentChatPolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 removes the per-user Persistent Chat policy with the Identity RedmondPersistentChatPolicy.
  
```
Remove-CsPersistentChatPolicy -Identity "RedmondPersistentChatPolicy"
```

### Example 2

In Example 2, all the Persistent Chat policies applied to the site scope are deleted. To do this, the command first uses the **Get-CsPersistentChatPolicy** cmdlet and the Filter parameter to return all the Persistent Chat policies configured at the site scope. (This is done by using the filter value "site:*".) These policies are then piped to, and deleted by, the **Remove-CsPersistentChatPolicy** cmdlet.
  
```
Get-CsPersistentChatPolicy -Filter "site:*" | Remove-CsPersistentChatPolicy
```

### Example 3

In Example 3, all the Persistent Chat policies in which Persistent Chat is enabled are deleted. To carry out this task, the command first calls the **Get-CsPersistentChatPolicy** cmdlet without any parameters; this returns a collection of all the Persistent Chat policies configured for use in the organization. This collection is then piped to the **Where-Object** cmdlet, which picks out only those policies where the EnablePersistentChat property is equal to true ($True). That collection is then piped to the **Remove-CsPersistentChatPolicy** cmdlet, which deletes each policy in the collection.
  
```
Get-CsPersistentChatPolicy | Where-Object {$_.EnablePersistentChat -eq $True} | Remove-CsPersistentChatPolicy
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Persistent Chat service (which replaces the Group Chat service used in Microsoft Lync Server 2010) provides organizations with messaging and collaboration capabilities similar to those found in Internet discussion forums: users can exchange messages in real-time, yet can also revisit and restart those conversations at any time. Conversations can be based around specific topics, and these conversations can be made available to everyone or to only a selected set of users. Likewise, individual chat rooms can be configured so that anyone can post a message or configured so that only designated presenters can post messages.
  
By default, users are not granted access to the Persistent Chat service; that access can only be granted if the user is managed by a Persistent Chat policy that allows for the user of the service. When you install Skype for Business Server 2015, all your users are managed by a global Persistent Chat policy in which the use of Persistent Chat is disabled. If you want to give all your users access to the service you can simply set the EnablePersistentChat property in this global policy to True. Alternatively, you can create additional policies at the site or at the per-user scope, and thus provide Persistent Chat access to some users while denying this access to other users.
  
 **Skype for Business Server Control Panel:** To remove a Persistent Chat policy using the Skype for Business Server Control Panel, click **Persistent Chat** and then click **Persistent Chat Policy**. Select the policy to be removed, click **Edit**, and then click **Delete**.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identity of the Persistent Chat policy to be deleted. To remove a site-scoped policy, use syntax similar to this:  <br/>  `-Identity site:Redmond` <br/> To delete per-user policy, use syntax similar to this:  <br/>  `-Identity RedmondPolicy` <br/> The **Remove-CsPersistentChatPolicy** cmdlet can also be run against the global Persistent Chat policy. In that case, however, the global policy will not actually be deleted. Instead, all the properties in the global policy will be reset to their default values. <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |If present, causes the **Remove-CsPersistentChatPolicy** cmdlet to delete the per-user policy even if the policy is currently assigned to at least one user. If not present, you will be asked to confirm the deletion request before a policy still in use will be removed. <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account for whom the Persistent Chat policy is being removed. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your Skype for Business Online tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Remove-CsPersistentChatPolicy** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Policy.PersistentChat.PersistentChatPolicy object.
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Remove-CsPersistentChatPolicy** cmdlet deletes existing instances of the Microsoft.Rtc.Management.WritableConfig.Policy.PersistentChat.PersistentChatPolicy object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsPersistentChatPolicy](get-cspersistentchatpolicy.md)
  
[Grant-CsPersistentChatPolicy](grant-cspersistentchatpolicy.md)
  
[New-CsPersistentChatPolicy](new-cspersistentchatpolicy.md)
  
[Set-CsPersistentChatPolicy](set-cspersistentchatpolicy.md)

