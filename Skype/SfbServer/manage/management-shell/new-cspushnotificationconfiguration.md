---
title: "New-CsPushNotificationConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8bf61c72-7902-4075-9388-47a7dd4e649c
description: "Creates a new collection of push notification configuration settings at the site scope. The push notification service (Apple Push Notification Service and Microsoft Push Notification Service) provides a way to send notifications about events such as new instant messages or new voice mail to mobile devices such as iPhones and Windows Phones, even if the Skype for Business application on those devices is currently suspended or running in the background. This cmdlet was introduced in the cumulative update for Lync Server 2010: November 2011."
---

# New-CsPushNotificationConfiguration
[]
Creates a new collection of push notification configuration settings at the site scope. The push notification service (Apple Push Notification Service and Microsoft Push Notification Service) provides a way to send notifications about events such as new instant messages or new voice mail to mobile devices such as iPhones and Windows Phones, even if the Skype for Business application on those devices is currently suspended or running in the background. This cmdlet was introduced in the cumulative update for Lync Server 2010: November 2011.
  
```
New-CsPushNotificationConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-EnableApplePushNotificationService <$true | $false>] [-EnableMicrosoftPushNotificationService <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 creates a new collection of push notification settings for the Redmond site, and enables push notifications from both the Apple Push Notification Service and the Microsoft Push Notification Service. The latter is done by setting both the EnableApplePushNotificationService and the EnableMicrosoftPushNotificationService properties to True.
  
```
New-CsPushNotificationConfiguration -Identity "site:Redmond" -EnableApplePushNotificationService $True -EnableMicrosoftPushNotificationService -$True

```

### EXAMPLE 2

Example 2 shows how you can create a set of push configuration settings for each of your Skype for Business Server 2015 sites. To do this, the command first uses the **Get-CsSite** cmdlet to return a collection of all your Skype for Business Server 2015 sites. That collection is then piped to the **ForEach-Object** cmdlet, which takes each site in the collection, calls the **New-CsPushNotificationConfiguration** cmdlet, and creates a new set of push notification configuration settings for that site. Note that this command will fail for any site that already hosts a collection of push notification configuration settings.
  
```
Get-CsSite | ForEach-Object {New-CsPushNotificationConfiguration -Identity $_.Identity}

```

### EXAMPLE 3

Example 3 demonstrates the use of the InMemory parameter to create a collection of push notification configuration settings that initially exist only in memory. To do this, the example creates a new collection of settings (with the Identity site:Redmond) and stores this collection in a variable named $x. Note that, after this first command executes, the collection exists only in memory; if you run the **Get-CsPushNotificationConfiguration** cmdlet, you will not see an entry for site:Redmond.
  
In the next two commands, both the EnableApplePushNotificationService and the EnableMicrosoftPushNotificationService properties for this virtual collection of settings are set to True, which enables push notifications from both the Apple Push Notification Service and the Microsoft Push Notification Service. Finally, the last command uses the **Set-CsPushNotificationConfiguration** cmdlet to transform the virtual push notification settings into an actual collection of settings applied to the Redmond site. If you do not call the **Set-CsPushNotificationConfiguration** cmdlet, these settings will remain in memory only and will disappear when your Windows PowerShell session is terminated or the variable $x is deleted.
  
```
$x = New-CsPushNotificationConfiguration -Identity "site:Redmond" -InMemory
$x.EnableApplePushNotificationService = $True 
$x.EnableMicrosoftPushNotificationService = $True
Set-CsPushNotificationConfiguration -Instance $x

```

## Detailed Description

The Apple Push Notification Service and the Microsoft Push Notification Service enable users running Skype for Business on their Apple iPhone or Windows Phone to receive notifications about Skype for Business Server 2015 events even when Skype for Business is suspended or running in the background. For example, users can receive notice for events such as these:
  
- Invitations to a new instant messaging session or conference
  
- New instant messages
  
- New voice mail
  
Without the push notification service, users would receive these notices only when Skype for Business was in the foreground and serving as the active application.
  
Administrators have the ability to enable or disable push notifications for iPhone users and/or Windows Phone users. (By default, push notifications are disabled for both iPhone users and Windows Phone users.) Administrators can enable or disable push notifications at the global scope by using the **Set-CsPushNotificationConfiguration** cmdlet. They can also create custom push notification settings at the site scope by using the **New-CsPushNotificationConfiguration** cmdlet. That gives Administrators the ability to provide push notifications to users in some sites (for example, Redmond) while restricting the use of these notifications in other sites.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Push notification settings can only be created at the site scope. To specify a new collection of settings for a site, use syntax similar to this:  <br/>  `-Identity "site:Redmond"` <br/> Note that this command will fail if the Redmond site already hosts a collection of push notification settings.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EnableApplePushNotificationService_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, iPhone users will receive push notifications from the Apple Push Notification Service. When set to False, iPhone users will not receive these notifications.  <br/> The default value is False.  <br/> |
| _EnableMicrosoftPushNotificationService_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, Windows Phone users will receive push notifications from the Microsoft Push Notification Service. When set to False, Windows Phone users will not receive these notifications.  <br/> The default value is False.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of a command called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching Set- cmdlet.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account for which the new push notification configuration settings are being created. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **New-CsPushNotificationConfiguration** cmdlet does not accept pipelined input.
  
## Return Types

The **New-CsPushNotificationConfiguration** cmdlet creates new instances of the Microsoft.Rtc.Management.WriteableConfig.Settings.PushNotificationConfiguration.PushNotificationConfiguration object.
  

