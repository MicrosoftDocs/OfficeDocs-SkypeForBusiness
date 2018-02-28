---
title: "Get-CsConversationHistoryConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e724a882-f178-49ce-bf37-95c0d2e0bb0c
description: "Returns the conversation history configuration settings for the organization. These settings manage conversation histories for mobile device users."
---

# Get-CsConversationHistoryConfiguration
[]
Returns the conversation history configuration settings for the organization. These settings manage conversation histories for mobile device users.
  
This cmdlet was introduced in Skype for Business Server 2015.
  
```
Get-CsConversationHistoryConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 returns the conversation history configuration settings for the organization. Note that you will always get back just one collection of settings; that's because Skype for Business Server 2015 limits you to a single, global collection of conversation history settings.
  
```
Get-CsConversationHistoryConfiguration
```

## Detailed Description
<a name="DetailedDescription"> </a>

Prior to the release of Skype for Business Server 2015, conversation histories were stored in the Conversation History folder in users's mailbox, written by the rich client. This made it difficult to access the conversation history from mobile devices because the Conversation History folder is typically not replicated to mobile devices. With Skype for Business Server 2015, conversation histories and missed IM notifications can be stored on the server in user mailboxes, which makes them easily accessible from mobile devices. Administrators can manage the server-side processing of these conversation histories by using the conversation history configuration settings. Just keep in mind that a single, global, collection of these settings is used to manage conversation histories throughout your deployment. There is no option for creating additional conversation history settings at the site, service, or per-user scope.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard values when referencing a collection of conversation history configuration settings. Because you can only have a single, global instance of these settings there is no reason to use the Filter parameter. However, if you prefer you can use the following syntax to reference the global settings:  <br/>  `-Filter "g*"` <br/> That syntax brings back all the conversation history configuration settings that have an Identity that begins with the letter "g".  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique Identity of the conversation history configuration settings. Because you can only have a single, global instance of these settings, you do not need to specify an Identity when calling the Get-CsConversationHistoryConfiguration cmdlet. If you prefer, however, you can use the following syntax to reference the global settings:  <br/>  `-Identity "global"` <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the conversation history configuration data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. Get-CsConversationHistoryConfiguration does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

Get-CsConversationHistoryConfiguration returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.ConversationHistory.ConversationHistorySettings object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Remove-CsConversationHistoryConfiguration](remove-csconversationhistoryconfiguration.md)
  
[Set-CsConversationHistoryConfiguration](set-csconversationhistoryconfiguration.md)

