---
title: "Remove-CsPushNotificationConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 77574e30-a75f-4aaa-b2d8-ccbabda31797
description: "Deletes an existing collection of push notification settings. The push notification service (Apple Push Notification Service and Microsoft Push Notification Service) provides a way to send notifications about events such as new instant messages or new voice mail to mobile devices such as iPhones and Windows Phones, even if the Skype for Business application on those devices is currently suspended or running in the background. This cmdlet was introduced in the cumulative update for Lync Server 2010: November 2011."
---

# Remove-CsPushNotificationConfiguration
 
Deletes an existing collection of push notification settings. The push notification service (Apple Push Notification Service and Microsoft Push Notification Service) provides a way to send notifications about events such as new instant messages or new voice mail to mobile devices such as iPhones and Windows Phones, even if the Skype for Business application on those devices is currently suspended or running in the background. This cmdlet was introduced in the cumulative update for Lync Server 2010: November 2011.
  
```
Remove-CsPushNotificationConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 deletes the collection of push notification settings assigned to the Redmond site.
  
```
Remove-CsPushNotificationConfiguration -Identity "site:Redmond"

```

### EXAMPLE 2

Example 2 deletes all the push notification settings configured at the site scope. To perform this task, the cmdlet first uses the **Get-CsPushNotificationConfiguration** cmdlet and the Filter parameter to return a collection of all the settings configured at the site scope; the filter value "site:*" limits the returned items to settings that have an Identity that begins with the string value "site:". The site-scoped settings are then piped to, and deleted by, the **Remove-CsPushNotificationConfiguration** cmdlet.
  
```
Get-CsPushNotificationConfiguration -Filter "site:*" | Remove-CsPushNotificationConfiguration

```

### EXAMPLE 3

Example 3 shows you how can remove all the push notification configuration settings where push notifications from the Microsoft Push Notification Service have been disabled. To do this, the command first uses the **Get-CsPushNotificationConfiguration** cmdlet to return a collection of all the push notification settings currently in use. That collection is then piped to the **Where-Object** cmdlet, which selects only those settings where the EnableMicrosoftPushNotificationService property is equal to (-eq) False. This filtered collection is then piped to the **Remove-CsPushNotificationConfiguration** cmdlet which, in turn, deletes each item in the collection.
  
```
Get-CsPushNotificationConfiguration | Where-Object {$_.EnableMicrosoftPushNotificationService -eq $False} | Remove-CsPushNotificationConfiguration

```

## Detailed Description

The Apple Push Notification Service and the Microsoft Push Notification Service enable users running Skype for Business on their Apple iPhone or Windows Phone to receive notifications about Skype for Business Server 2015 events even when Skype for Business is suspended or running in the background. For example, users can receive notice for events such as these:
  
- Invitations to a new instant messaging session or conference
  
- New instant messages
  
- New voice mail
  
Without the push notification service users would receive these notices only when Skype for Business was in the foreground and serving as the active application.
  
Administrators have the ability to enable or disable push notifications for iPhone users and/or Windows Phone users. (By default, push notifications are disabled for both iPhone users and Windows Phone users.) Administrators can enable or disable push notifications at the global scope by using the **Set-CsPushNotificationConfiguration** cmdlet. They can also create custom push notification settings at the site scope by using the **New-CsPushNotificationConfiguration** cmdlet.
  
These custom settings can later be deleted by using the **Remove-CsPushNotificationConfiguration** cmdlet. If you delete settings configured at the site scope, then users in that site will automatically be managed by the global push notification settings.
  
Note that the **Remove-CsPushNotificationConfiguration** cmdlet can also be run against the global settings. If you do that, however, the global settings will not be removed; instead, the properties in the global settings will all be reset to their default values. In this case, that means that push notifications will be disabled from both the Apple Push Notification Service and the Microsoft Push Notification Service.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the collection of push notification configuration settings to be removed. To remove the global collection, use the following syntax:  <br/>  `-Identity global` <br/> Note that you cannot actually remove the global settings; instead, you can only reset the properties to their default values.  <br/> To remove a site collection, use syntax similar to this:  <br/>  `-Identity site:Redmond` <br/> You cannot use wildcards when specifying a policy Identity.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account for the push notification configuration settings being deleted. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WriteableConfig.Settings.PushNotificationConfiguration.PushNotificationConfiguration. The **Remove-CsPushNotificationConfiguration** cmdlet accepts pipelined instances of the PushNotificationConfiguration object.
  
## Return Types

None. Instead, the **Remove-CsPushNotificationConfiguration** cmdlet deletes instances of the Microsoft.Rtc.Management.WriteableConfig.Settings.PushNotificationConfiguration.PushNotificationConfiguration object.
  

