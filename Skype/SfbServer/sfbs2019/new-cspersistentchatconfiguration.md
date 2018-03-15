---
title: "New-CsPersistentChatConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: df83eebe-c20c-4e22-a5d4-1546a7f06e25
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# New-CsPersistentChatConfiguration
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Creates a new collection of Persistent Chat configuration settings at the site or service scope. Persistent Chat configuration settings are used to manage the Persistent Chat service. For example, these settings allow you to specify the maximum number of users who can participate in a chat room. This cmdlet was introduced in Lync Server 2013.
  
```
New-CsPersistentChatConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-DefaultChatHistory <Int16>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-MaxFileSizeKB <UInt32>] [-ParticipantUpdateLimit <UInt32>] [-RoomManagementUrl <String>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 creates a new set of Persistent Chat configuration settings applied to the Redmond site. In this example, the ParticipantUpdateLimit property is set to 100.
  
```
New-CsPersistentChatConfiguration -Identity "site:Redmond" -ParticipantUpdateLimit 100
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Persistent Chat service (which replaces the Group Chat service used in Microsoft Lync Server 2010) provides organizations with messaging and collaboration capabilities similar to those found in Internet discussion forums: users can exchange messages in real-time, yet can also revisit and restart those conversations at any time. Conversations can be based around specific topics, and these conversations can be made available to everyone or to only a selected set of users. Likewise, individual chat rooms can be configured so that anyone can post a message or configured so that only designated presenters can post messages.
  
The Persistent Chat service is managed, in part, by Persistent Chat configuration settings, which dictate such things as the number of previously-posted chat messages immediately available when you log on to a chat room (the chat history) or the maximum size of a file that can be uploaded to (or downloaded from) the service. These settings can be configured at the global or the site scope, or at the service scope (that is, you can have a custom collection of settings assigned to an individual Persistent Chat pool).
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "New-CsPersistentChatConfiguration"}
  
 **Lync Server Control Panel:** To create a new collection of Persistent Chat configuration settings using the Lync Server Control Panel, click **Persistent Chat**, click **Persistent Chat Configuration**, click **New**, and then click either **Site configuration** or **Pool configuration**.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the new Persistent Chat configuration settings being created. New configuration settings can be created at either the site or the service scope (for the Persistent Chat Server service, only). To create new settings at the site scope, use syntax similar to this:  <br/> -Identity "site:Redmond"  <br/> To create new settings at the service scope, use syntax like this:  <br/> -Identity "service:PersistentChatServer:atl-gc-001.litwarein.com"  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DefaultChatHistory_ <br/> |Optional  <br/> |System.Int16  <br/> |Default number of chat messages instantly available in a chat room. Note that this value represents only the number of messages immediately available; it does not place a limit on the total amount of messages that can be retrieved.  <br/> DefaultChatHistory can be set to any value between 1 and 500, inclusive. The default value is 30.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching Set- cmdlet.  <br/> |
| _MaxFileSizeKB_ <br/> |Optional  <br/> |System.UInt32  <br/> |Maximum size of a file (in kilobytes) that can be uploaded or downloaded by the web service. The default value is 20000 KB.  <br/> |
| _ParticipantUpdateLimit_ <br/> |Optional  <br/> |System.UInt32  <br/> |Maximum number of users who can participate in a chat room before the active participant list updates are disabled. The default value is 75.  <br/> |
| _RoomManagementUrl_ <br/> |Optional  <br/> |System.String  <br/> |URL for the Web page that administrators can use to manage individual chat rooms.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **New-CsPersistentChatConfiguration** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="ReturnTypes"> </a>

The **New-CsPersistentChatConfiguration** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.PersistentChat.PersistentChatConfiguration object. 
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsPersistentChatConfiguration](get-cspersistentchatconfiguration.md)
  
[Remove-CsPersistentChatConfiguration](remove-cspersistentchatconfiguration.md)
  
[Set-CsPersistentChatConfiguration](set-cspersistentchatconfiguration.md)

