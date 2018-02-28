---
title: "Set-CsPushNotificationConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3aacdb2b-b6dd-4615-a3f9-68360f3ae483
description: "Modifies an existing collection of push notification configuration settings. The push notification service (Apple Push Notification Service and Microsoft Push Notification Service) provides a way to send notifications about events such as new instant messages or new voice mail to mobile devices such as iPhones and Windows Phones, even if the Skype for Business application on those devices is currently suspended or running in the background. This cmdlet was introduced in the cumulative update for Lync Server 2010: November 2011."
---

# Set-CsPushNotificationConfiguration
[]
Modifies an existing collection of push notification configuration settings. The push notification service (Apple Push Notification Service and Microsoft Push Notification Service) provides a way to send notifications about events such as new instant messages or new voice mail to mobile devices such as iPhones and Windows Phones, even if the Skype for Business application on those devices is currently suspended or running in the background. This cmdlet was introduced in the cumulative update for Lync Server 2010: November 2011.
  
```
Set-CsPushNotificationConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

The command shown in Example 1 disables push notifications from the Apple Push Notification Service for the Redmond site.
  
```
Set-CsPushNotificationConfiguration -Identity "site:Redmond" -EnableApplePushNotificationService $False

```

### EXAMPLE 2

Example 2 disables push notifications from the Apple Push Notification Service for all the sites currently hosting push notification settings. To do this, the command first uses the **Get-CsPushNotificationConfiguration** cmdlet and the Filter parameter to return all the push notification settings configured at the site scope; the filter value "site:*" limits the returned settings to those that have an Identity that begins with the string value "site:". That collection of settings is then piped to the **Set-CsPushNotificationConfiguration** cmdlet, which takes each item in the collection and sets the EnableApplePushNotificationService property to False.
  
```
Get-CsPushNotificationConfiguration -Filter "site:*" | Set-CsPushNotificationConfiguration -EnableApplePushNotificationService $False

```

### EXAMPLE 3

Example 3 demonstrates how you can locate all the push notification settings where push notifications from the Microsoft Push Notification Service are disabled, and then disable push notifications from the Apple Push Notification Service for each of those settings as well. To carry out this task, the command first uses the **Get-CsPushNotificationConfiguration** cmdlet to return a collection of all the push notification settings currently in use the organization. This collection is then piped to the **Where-Object** cmdlet, which selects only those settings where the EnableMicrosoftPushNotificationService property is equal to (-eq) False. That filtered collection is then piped to the **Set-CsPushNotificationConfiguration** cmdlet, which takes each item in the filtered collection and sets the EnableApplePushNotificationService property to False.
  
```
Get-CsPushNotificationConfiguration | Where-Object {$_.EnableMicrosoftPushNotificationService -eq $False} | Set-CsPushNotificationConfiguration -EnableApplePushNotificationService $False

```

## Detailed Description

The Apple Push Notification Service and the Microsoft Push Notification Service enable users running Skype for Business on their Apple iPhone or Windows Phone to receive notifications about Skype for Business Server 2015 events even when Skype for Business is suspended or running in the background. For example, users can receive notice for events such as these:
  
- Invitations to a new instant messaging session or conference
  
- New instant messages
  
- New voice mail
  
Without the push notification service users would receive these notices only when Skype for Business was in the foreground and serving as the active application.
  
Administrators have the ability to enable or disable push notifications for iPhone users and/or Windows Phone users. (By default, push notifications are disabled for both iPhone users and Windows Phone users.) Administrators can enable or disable push notifications at the global scope by using the **Set-CsPushNotificationConfiguration** cmdlet. They can also create custom push notification settings at the site scope by using the **New-CsPushNotificationConfiguration** cmdlet. These custom settings can also be modified by using the **Set-CsPushNotificationConfiguration** cmdlet.
  
With the push notification configuration settings there are only two property values for Administrators to manage: EnableApplePushNotificationService, which determines whether push notifications are sent to iPhone users; and EnableMicrosoftPushNotificationService, which determines whether push notifications are sent to Windows Phone users. Note that these property values do not have to be set to the same value. For example, you could enable push notifications to Windows Phone users (by setting EnableMicrosoftPushNotificationService to True) yet, at the same, disable notifications to iPhone users by setting EnableApplePushNotificationService to False.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EnableApplePushNotificationService_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, iPhone users will receive push notifications from the Apple Push Notification Service. When set to False, iPhone users will not receive these notifications.  <br/> The default value is False.  <br/> |
| _EnableMicrosoftPushNotificationService_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, Windows Phone users will receive push notifications from the Microsoft Push Notification Service. When set to False, Windows Phone users will not receive these notifications.  <br/> The default value is False.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Indicates the Identity of the push notification configuration settings to be modified. To refer to the global settings, use this syntax:  <br/>  `-Identity global` <br/> To refer to site settings, use syntax similar to this:  <br/>  `-Identity site:Redmond` <br/> Note that you cannot use wildcards when specifying an Identity.  <br/> |
| _Instance_ <br/> |Optional  <br/> |Push configuration object  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account for the push notification settings being modified. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> If you are using a remote session of Windows PowerShell and are connected only to Skype for Business Online you do not have to include the Tenant parameter. Instead, the tenant ID will automatically be filled in for you based on your connection information. The Tenant parameter is primarily for use in a hybrid deployment.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WriteableConfig.Settings.PushNotificationConfiguration.PushNotificationConfiguration. The **Set-CsPushNotificationConfiguration** cmdlet accepts pipelined instances of the PushNotificationConfiguration object.
  
## Return Types

None. Instead, the **Set-CsPushNotificationConfiguration** cmdlet modifies existing instances of the Microsoft.Rtc.Management.WriteableConfig.Settings.PushNotificationConfiguration.PushNotificationConfiguration object.
  

