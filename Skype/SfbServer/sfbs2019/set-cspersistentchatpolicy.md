---
title: "Set-CsPersistentChatPolicy"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b724bc13-d4fe-4529-9a48-e4cec8b7dce2
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsPersistentChatPolicy
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Modifies an existing Persistent Chat policy. Persistent Chat policies determine whether or not users are allowed access to Persistent Chat chat rooms. This cmdlet was introduced in Lync Server 2013.
  
```
Set-CsPersistentChatPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

In Example 1, Persistent Chat is enabled for the global Persistent Chat policy.
  
```
Set-CsPersistentChatPolicy -Identity "global" -EnablePersistentChat $True
```

### Example 2

In Example 2, Persistent Chat is enabled for all the Persistent Chat policies in the organization. To do this, the command first uses the **Get-CsPersistentChatPolicy** cmdlet without any parameters in order to return a collection of all the Persistent Chat policies. This collection is then piped to the **Set-CsPersistentChatPolicy** cmdlet, which sets the EnablePersistentChat parameter for each policy in the collection to True ($True). 
  
```
Get-CsPersistentChatPolicy | Set-CsPersistentChatPolicy -EnablePersistentChat $True
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Persistent Chat service (which replaces the Group Chat service used in Microsoft Lync Server 2010) provides organizations with messaging and collaboration capabilities similar to those found in Internet discussion forums: users can exchange messages in real-time, yet can also revisit and restart those conversations at any time. Conversations can be based around specific topics, and these conversations can be made available to everyone or to only a selected set of users. Likewise, individual chat rooms can be configured so that anyone can post a message or configured so that only designated presenters can post messages.
  
By default, users are not granted access to the Persistent Chat service; that access can only be granted if the user is managed by a Persistent Chat policy that allows for the user of the service. When you install Lync 2013, all your users are managed by a global Persistent Chat policy in which the use of Persistent Chat is disabled. If you want to give all your users access to the service you can simply set the EnablePersistentChat property in this global policy to True. Alternatively, you can create additional policies at the site or at the per-user scope, and thus provide Persistent Chat access to some users while denying this access to other users.
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsPersistentChatPolicy"}
  
 **Lync Server Control Panel:** To modify an existing Persistent Chat policy using the Lync Server Control Panel, click **Persistent Chat**, click **Persistent Chat Policy**, then double-click the policy to be modified.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Description_ <br/> |Optional  <br/> |System.String  <br/> |Enables administrators to provide explanatory text to accompany the policy. For example, the Description might include information about the users the policy should be assigned to.  <br/> |
| _EnablePersistentChat_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True users affected by the policy will be allowed to use Persistent Chat. When set to False (the default value) users affected by the policy will not be allowed to use Persistent Chat.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identity of the Persistent Chat policy to be modified. To modify the global policy, use this syntax:  <br/> -Identity global  <br/> To modify a site-scoped policy, use this syntax:  <br/> -Identity site:Redmond  <br/> To modify a per-user policy, use syntax similar to this:  <br/> -Identity RedmondPolicy  <br/> If you do not include the Identity parameter the **Set-CsPersistentChatPolicy** cmdlet will automatically modify the global policy.  <br/> |
| _Instance_ <br/> |Optional  <br/> |System.Management.Automation.PSObject  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Set-CsPersistentChatPolicy** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Policy.PersistentChat.PersistentChatPolicy object. 
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Set-CsPersistentChatPolicy** cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Policy.PersistentChat.PersistentChatPolicy object. 
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsPersistentChatPolicy](get-cspersistentchatpolicy.md)
  
[Grant-CsPersistentChatPolicy](grant-cspersistentchatpolicy.md)
  
[New-CsPersistentChatPolicy](new-cspersistentchatpolicy.md)
  
[Remove-CsPersistentChatPolicy](remove-cspersistentchatpolicy.md)

