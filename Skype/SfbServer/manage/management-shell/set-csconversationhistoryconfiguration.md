---
title: "Set-CsConversationHistoryConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: d580b9ea-ee07-4511-923e-03adad6a4db7
description: "Modifies the conversation history configuration settings for the organization. These settings manage conversation histories for mobile device users."
---

# Set-CsConversationHistoryConfiguration
 
Modifies the conversation history configuration settings for the organization. These settings manage conversation histories for mobile device users.
  
This cmdlet was introduced in Skype for Business Server 2015.
  
```
Set-CsConversationHistoryConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

In Example 1, the EnableServerConversationHistory property is set to True ($True). In turn, conversation histories, missed call notifications, and missed IM notifications will be stored on the server rather than in client mailboxes.
  
```
Set-CsConversationHistoryConfiguration -Identity "global" -EnableServerConversationHistory $True
```

### Example 2

The command shown in Example 2 modifies the global collection of conversation history configuration settings. (Each deployment is limited to a single, global collection of conversation history configuration settings.) In this example, the CachedUserThreshold property is set to 2000000.
  
```
Set-CsConversationHistoryConfiguration -Identity "global" -CachedUserThreshold 2000000
```

## Detailed Description
<a name="DetailedDescription"> </a>

Prior to the release of Skype for Business Server 2015, conversation histories were stored exclusively in the Conversation History folder, written by the Skype for Business rich client. Unfortunately, that proved to be a problem for mobile device users, because the Conversation History folder is typically not replicated to mobile devices. With Skype for Business Server 2015, however, conversation histories, missed call notifications, and missed IM notifications can now be stored on the server instead of in client mailboxes; this change makes these items readily available to mobile devices. That also means that administrators can manage the server-side storage of these conversation histories by using the conversation history configuration settings. Keep in mind that a single, global collection of these settings is used to manage conversation history throughout your deployment; there is no option for creating additional conversation history. However, the global settings can be modified by using the Set-CsConversationHistoryConfiguration cmdlet. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EnableDisplayNameResolution_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _EnableServerConversationHistory_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True ($True), conversation histories and related information will be stored on the server. The default value is False, which means that this information is stored in user mailboxes.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique Identity of the conversation history configuration settings being modified. Because you can only have a single, global instance of these settings, you do not need to specify an Identity when calling the Set-CsConversationHistoryConfiguration cmdlet. However, you can still use the following syntax to reference the global settings:  <br/>  `-Identity "global"` <br/> |
| _Instance_ <br/> |Optional  <br/> |System.Management.Automation.PSObject  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _MaxContinuedConversationRetry_ <br/> |Optional  <br/> |System.UInt32  <br/> |Specifies the maximum number of times the Skype for Business Server will search for a previous conversation item from Exchange to create a continued conversation. If the previous conversation is not found in the specified number of attempts, a new conversation is created. Increasing this value will present more continued conversations, but at the cost of decreased performance. This parameter should not be used except in situations where Exchange connections are known to be unreliable. The default value is 3.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

Set-CsConversationHistoryConfiguration accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.ConversationHistory.ConversationHistorySettings object. 
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, Set-CsConversationHistoryConfiguration modifies instances of the Microsoft.Rtc.Management.WritableConfig.Settings.ConversationHistory.ConversationHistorySettings object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsConversationHistoryConfiguration](get-csconversationhistoryconfiguration.md)
  
[Remove-CsConversationHistoryConfiguration](remove-csconversationhistoryconfiguration.md)

