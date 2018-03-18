---
title: "New-CsPersistentChatPolicy"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: f7d42a24-598a-4ea3-8a0f-25575b5235ea
description: "Creates a new Persistent Chat policy at the site or the per-user scope. Persistent Chat policies determine whether or not users are allowed access to Persistent Chat chat rooms. This cmdlet was introduced in Lync Server 2013."
---

# New-CsPersistentChatPolicy
 
Creates a new Persistent Chat policy at the site or the per-user scope. Persistent Chat policies determine whether or not users are allowed access to Persistent Chat chat rooms. This cmdlet was introduced in Lync Server 2013.
  
```
New-CsPersistentChatPolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Description <String>] [-EnablePersistentChat <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 creates a new per-user Persistent Chat policy with the Identity RedmondPersistentChatPolicy. In this example, Persistent Chat is enabled by using the parameter EnablePersistentChat and the parameter value $True.
  
```
New-CsPersistentChatPolicy -Identity "RedmondPersistentChatPolicy" -EnablePersistentChat $True
```

### Example 2

Example 2 is a variation of the command shown in Example 1; the only difference is that the new policy is applied to the site scope instead of the per-user scope. That's done by setting the Identity to the string value "site:" followed by the name of the site itself; in this case, site:Redmond.
  
```
New-CsPersistentChatPolicy -Identity "site:Redmond" -EnablePersistentChat $True
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Persistent Chat service (which replaces the Group Chat service used in Microsoft Lync Server 2010) provides organizations with messaging and collaboration capabilities similar to those found in Internet discussion forums: users can exchange messages in real-time, yet can also revisit and restart those conversations at any time. Conversations can be based around specific topics, and these conversations can be made available to everyone or to only a selected set of users. Likewise, individual chat rooms can be configured so that anyone can post a message or configured so that only designated presenters can post messages.
  
By default, users are not granted access to the Persistent Chat service; that access can only be granted if the user is managed by a Persistent Chat policy that allows for the user of the service. When you install Skype for Business Server 2015, all your users are managed by a global Persistent Chat policy in which the use of Persistent Chat is disabled. If you want to give all your users access to the service you can simply set the EnablePersistentChat property in this global policy to True. Alternatively, you can create additional policies at the site or at the per-user scope, and thus provide Persistent Chat access to some users while denying this access to other users.
  
 **Skype for Business Server Control Panel:** To create a new Persistent Chat policy using the Skype for Business Server Control Panel, click **Persistent Chat**, click **Persistent Chat Policy**, click **New**, and then click either **Site policy** or **User policy**.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier to be assigned to the policy. New Persistent Chat policies can be created at the site scope or the per-user scope. To create a new site policy, use the prefix "site:" and the name of the site as your Identity. For example, use this syntax to create a new policy for the Redmond site:  <br/>  `-Identity site:Redmond` <br/> To create a new per-user policy, use an Identity similar to this:  <br/>  `-Identity SalesPersistentChatPolicy` <br/> Note that you cannot create a new global policy; if you want to make changes to the global policy, use the **Set-CsPersistentChatPolicy** cmdlet instead. Likewise, you cannot create a new site or per-user policy if a policy with that Identity already exists. If you need to make changes to an existing policy, use the **Set-CsPersistentChatPolicy** cmdlet. <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Description_ <br/> |Optional  <br/> |System.String  <br/> |Enables administrators to provide explanatory text to accompany the policy. For example, the Description might include information about the users the policy should be assigned to.  <br/> |
| _EnablePersistentChat_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, users affected by the policy will be allowed to use Persistent Chat. When set to False (the default value) users affected by the policy will not be allowed to use Persistent Chat.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching Set- cmdlet.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account for whom the new Persistent Chat policy is being created. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your Skype for Business Online tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **New-CsPersistentChatPolicy** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The **New-CsPersistentChatPolicy** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Policy.PersistentChat.PersistentChatPolicy object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsPersistentChatPolicy](get-cspersistentchatpolicy.md)
  
[Grant-CsPersistentChatPolicy](grant-cspersistentchatpolicy.md)
  
[Remove-CsPersistentChatPolicy](remove-cspersistentchatpolicy.md)
  
[Set-CsPersistentChatPolicy](set-cspersistentchatpolicy.md)

