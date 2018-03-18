---
title: "Remove-CsConversationHistoryConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 105d9ca9-3864-4615-9d4b-506977b83714
description: "Resets the conversation history configuration settings for the organization. These settings manage conversation histories for mobile device users."
---

# Remove-CsConversationHistoryConfiguration
 
Resets the conversation history configuration settings for the organization. These settings manage conversation histories for mobile device users.
  
This cmdlet was introduced in Skype for Business Server 2015.
  
```
Remove-CsConversationHistoryConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 resets all the properties in the global collection of conversation history configuration settings to their default values.
  
```
Remove-CsConversationHistoryConfiguration -Identity "global"
```

## Detailed Description
<a name="DetailedDescription"> </a>

Prior to the release of Skype for Business Server 2015, conversation histories were stored in the Conversation History folder in users's mailbox, written by the Skype for Business rich client. Unfortunately, that proved to be a problem for mobile device users, because the Conversation History folder is typically not replicated to mobile devices. With Skype for Business Server 2015, however, conversation histories, missed call notifications, and missed IM notifications can be stored on the server in user mailboxes; this change makes these items readily available to mobile devices. Administrators can manage the server-side storage of these conversation histories by using the conversation history configuration settings. Just keep in mind that a single, global collection of these settings is used to manage conversation histories throughout your deployment. There is no option for creating additional conversation history settings at the site, service, or per-user scope. 
  
Despite the name, the Remove-CsConversationHistoryConfiguration cmdlet does not actually delete the global collection of settings; that's because the global collection cannot be deleted. Instead, the Remove-CsConversationHistoryConfiguration cmdlet resets all the properties in the global collection to their default values. For example, when you install Skype for Business Server 2015 the CachedUserThreshold property is set to 1000000. Suppose you change this value to 500000. If you run the Remove-CsConversationHistoryConfiguration cmdlet then CachedUserThreshold will revert back to its default value of 1000000.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the conversation history configuration settings to be deleted. Because there is only a single, global collection of settings per deployment, the only allowed syntax is the following:  <br/> -Identity "global"  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

Remove-CsConversationHistoryConfiguration accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.ConversationHistory.ConversationHistorySettings object.
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, Remove-CsConversationHistoryConfiguration resets instances of the Microsoft.Rtc.Management.WritableConfig.Settings.ConversationHistory.ConversationHistorySettings object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsConversationHistoryConfiguration](get-csconversationhistoryconfiguration.md)
  
[Set-CsConversationHistoryConfiguration](set-csconversationhistoryconfiguration.md)

