---
title: "Remove-CsPersistentChatConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 5b71b66b-9b9b-4833-94b8-528260cd7589
description: "Removes an existing collection of Persistent Chat configuration settings. Persistent Chat configuration settings are used to manage the Persistent Chat service. For example, these settings allow you to specify the maximum number of users who can participate in a chat room. This cmdlet was introduced in Lync Server 2013."
---

# Remove-CsPersistentChatConfiguration
 
Removes an existing collection of Persistent Chat configuration settings. Persistent Chat configuration settings are used to manage the Persistent Chat service. For example, these settings allow you to specify the maximum number of users who can participate in a chat room. This cmdlet was introduced in Lync Server 2013.
  
```
Remove-CsPersistentChatConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 deletes the Persistent Chat configuration settings for the Redmond site.
  
```
Remove-CsPersistentChatConfiguration -Identity "site:Redmond"
```

### Example 2

In Example 2, all the Persistent Chat configuration settings applied to the site scope are removed. To do this, the command first employs the **Get-CsPersistentChatConfiguration** cmdlet and the -Filter parameter; the filter value "site:*" limits the returned data to settings applied at the site scope. These settings are then piped to the **Remove-CsPersistentChatConfiguration** cmdlet, which deletes all the settings applied to the site scope.
  
```
Get-CsPersistentChatConfiguration -Filter "site:*" | Remove-CsPersistentChatConfiguration
```

### Example 3

Example 3 deletes all the Persistent Chat configuration settings where the default chat history is greater than 30. To carry out this task the command first uses the **Get-CsPersistentChatConfiguration** cmdlet to return a collection of all the Persistent Chat configuration settings. This collection is then piped to the **Where-Object** cmdlet, which picks out only those settings where the DefaultChatHistory property is greater than (-gt) 30. The filtered collection is then piped to the **Remove-CsPersistentChatConfiguration** cmdlet, which deletes each item in the filtered collection.
  
```
Get-CsPersistentChatConfiguration | Where-Object {$_.DefaultChatHistory -gt 30} | Remove-CsPersistentChatConfiguration
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Persistent Chat service (which replaces the Group Chat service used in Microsoft Lync Server 2010) provides organizations with messaging and collaboration capabilities similar to those found in Internet discussion forums: users can exchange messages in real-time, yet can also revisit and restart those conversations at any time. Conversations can be based around specific topics, and these conversations can be made available to everyone or to only a selected set of users. Likewise, individual chat rooms can be configured so that anyone can post a message or configured so that only designated presenters can post messages.
  
The Persistent Chat service is managed, in part, by Persistent Chat configuration settings, which dictate such things as the number of previously-posted chat messages immediately available when you log on to a chat room (the chat history) or the maximum size of a file that can be uploaded to (or downloaded from) the service. These settings can be configured at the global or the site scope, or at the service scope (that is, you can have a custom collection of settings assigned to an individual Persistent Chat pool).
  
 **Skype for Business Server Control Panel:** To remove a collection of Persistent Chat configuration settings using the Skype for Business Server Control Panel, click **Persistent Chat** and then click **Persistent Chat Configuration**. Select the collection to be removed, click **Edit**, and then click **Delete**.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the Persistent Chat configuration settings to be removed. To remove a collection of settings configured at the site scope, use syntax similar to this:  <br/>  `-Identity "site:Redmond"` <br/> To remove a collection configured at the service scope, use syntax like this:  <br/>  `-Identity "service:PersistentChatServer:atl-gc-001.litwareinc.com"` <br/> Note that you cannot use wildcards with the Identity parameter.  <br/> You can also run the **Remove-CsPersistentChatConfiguration** against cmdlet the global settings collection. In that case, however, the global collection will not be removed. Instead, all the properties within that collection will be reset to their default values. <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Remove-CsPersistentChatConfiguration** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.PersistentChat.PersistentChatConfiguration object.
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Remove-CsPersistentChatConfiguration** cmdlet deletes existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.PersistentChat.PersistentChatConfiguration object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsPersistentChatConfiguration](get-cspersistentchatconfiguration.md)
  
[New-CsPersistentChatConfiguration](new-cspersistentchatconfiguration.md)
  
[Set-CsPersistentChatConfiguration](set-cspersistentchatconfiguration.md)

