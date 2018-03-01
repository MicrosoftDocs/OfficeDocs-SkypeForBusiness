---
title: "Set-CsPersistentChatConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 97d23d2e-878c-4573-bfce-0ddddc5a190e
description: "Modifies an existing collection of Persistent Chat configuration settings. Persistent Chat configuration settings are used to manage the Persistent Chat service. For example, these settings allow you to specify the maximum number of users who can participate in a chat room. This cmdlet was introduced in Lync Server 2013."
---

# Set-CsPersistentChatConfiguration
 
Modifies an existing collection of Persistent Chat configuration settings. Persistent Chat configuration settings are used to manage the Persistent Chat service. For example, these settings allow you to specify the maximum number of users who can participate in a chat room. This cmdlet was introduced in Lync Server 2013.
  
```
Set-CsPersistentChatConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 sets the DefaultChatHistory property of the global Persistent Chat configuration settings to 100.
  
```
Set-CsPersistentChatConfiguration -Identity "global" -DefaultChatHistory 100
```

### Example 2

In Example 2, the DefaultChatHistory property is set to 100 for all the Persistent Chat configuration settings. To carry out this task, the command first uses the **Get-CsPersistentChatConfiguration** cmdlet to return a collection of all the Persistent Chat configuration settings in the organization. This collection is then piped to the **Set-CsPersistentChatConfiguration** cmdlet, which modifies the DefaultChatHistory property for all the items in the collection.
  
```
Get-CsPersistentChatConfiguration | Set-CsPersistentChatConfiguration -DefaultChatHistory 100
```

### Example 3

Example 3 shows how you can modify the DefaultChatHistory property for all the Persistent Chat configuration settings applied to the site scope. To do this, the command first calls the **Get-CsPersistentChatConfiguration** cmdlet along with the Filter parameter; the parameter value "site:*" limits the returned data to setting collections configured at the site scope. These settings are then piped to the **Set-CsPersistentChatConfiguration** cmdlet, which changes the DefaultChatHistory property for each settings collection to 100.
  
```
Get-CsPersistentChatConfiguration -Filter "site:*" | Set-CsPersistentChatConfiguration -DefaultChatHistory 100
```

### Example 4

In Example 4, the DefaultChatHistory property is modified for any collection of Persistent Chat configuration settings where the default chat history is currently greater than 100. To carry out this task, the command first uses the **Get-CsPersistentChatConfiguration** cmdlet to return a collection of all the Persistent Chat configuration settings in use in the organization. This collection is then piped to the **Where-Object** cmdlet, which picks out only those settings where the DefaultChatHistory property is greater than (-gt) 100. In turn, that filtered collection is piped to the **Set-CsPersistentChatConfiguration** cmdlet, which takes each item in the filtered collection and sets the value of the DefaultChatHistory property to 100.
  
```
Get-CsPersistentChatConfiguration | Where-Object {$_.DefaultChatHistory -gt 100} | Set-CsPersistentChatConfiguration -DefaultChatHistory 100
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Persistent Chat service (which replaces the Group Chat service used in Microsoft Lync Server 2010) provides organizations with messaging and collaboration capabilities similar to those found in Internet discussion forums: users can exchange messages in real-time, yet can also revisit and restart those conversations at any time. Conversations can be based around specific topics, and these conversations can be made available to everyone or to only a selected set of users. Likewise, individual chat rooms can be configured so that anyone can post a message or configured so that only designated presenters can post messages.
  
The Persistent Chat service is managed, in part, by Persistent Chat configuration settings, which dictate such things as the number of previously-posted chat messages immediately available when you log on to a chat room (the chat history) or the maximum size of a file that can be uploaded to (or downloaded from) the service. These settings can be configured at the global or the site scope, or at the service scope (that is, you can have a custom collection of settings assigned to an individual Persistent Chat pool).
  
 **Skype for Business Server Control Panel:** To modify an existing collection of Persistent Chat configuration settings using the Skype for Business Server Control Panel, click **Persistent Chat**, click **Persistent Chat Configuration**, then double-click the collection to be modified.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DefaultChatHistory_ <br/> |Optional  <br/> |System.Int16  <br/> |Default number of chat messages instantly available in a chat room. Note that this value represents only the number of messages immediately available; it does not place a limit on the total amount of messages that can be retrieved.  <br/> DefaultChatHistory can be set to any value between 1 and 500, inclusive. The default value is 30.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the Persistent Chat configuration settings to be modified. To modify a collection of settings configured at the site scope, use syntax similar to this:  <br/>  `-Identity "site:Redmond"` <br/> To modify a collection configured at the service scope, use syntax like this:  <br/>  `-Identity "service:PersistentChatServer:atl-gc-001.litwareinc.com"` <br/> To modify the global collection, use this syntax:  <br/>  `-Identity "global"` <br/> If you do not include the Identity parameter the **Set-CsPersistentChatConfiguration** cmdlet will automatically modify the global settings. <br/> |
| _Instance_ <br/> |Optional  <br/> |System.Management.Automation.PSObject  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _MaxFileSizeKB_ <br/> |Optional  <br/> |System.UInt32  <br/> |Maximum size of a file (in kilobytes) that can be uploaded or downloaded by the web service. The default value is 20000 KB.  <br/> |
| _ParticipantUpdateLimit_ <br/> |Optional  <br/> |System.UInt32  <br/> |Maximum number of users who can participate in a chat room before the active participant list updates are disabled. The default value is 75.  <br/> |
| _RoomManagementUrl_ <br/> |Optional  <br/> |System.String  <br/> |URL for the Web page administrators can use to manage individual chat rooms.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Set-CsPersistentChatConfiguration** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.PersistentChat.PersistentChatConfiguration object.
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Set-CsPersistentChatConfiguration** cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.PersistentChat.PersistentChatConfiguration object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsPersistentChatConfiguration](get-cspersistentchatconfiguration.md)
  
[New-CsPersistentChatConfiguration](new-cspersistentchatconfiguration.md)
  
[Remove-CsPersistentChatConfiguration](remove-cspersistentchatconfiguration.md)

