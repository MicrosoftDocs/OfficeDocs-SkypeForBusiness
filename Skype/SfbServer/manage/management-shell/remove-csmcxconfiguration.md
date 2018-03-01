---
title: "Remove-CsMcxConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 71904a62-a1f1-4466-9921-0a175909e117
description: "Removes the specified collection of Skype for Business Server 2015 Mobility Service configuration settings. The Mobility Service enables users of mobile phones such as iPhones and Windows Phones to do such things as exchange instant messages and presence information; store and retrieve voice mail internally instead of with their wireless provider; and take advantage of Skype for Business Server 2015 capabilities such as Call via Work and dial-out conferencing. This cmdlet was introduced in the cumulative update for Lync Server 2010: November 2011."
---

# Remove-CsMcxConfiguration
 
Removes the specified collection of Skype for Business Server 2015 Mobility Service configuration settings. The Mobility Service enables users of mobile phones such as iPhones and Windows Phones to do such things as exchange instant messages and presence information; store and retrieve voice mail internally instead of with their wireless provider; and take advantage of Skype for Business Server 2015 capabilities such as Call via Work and dial-out conferencing. This cmdlet was introduced in the cumulative update for Lync Server 2010: November 2011.
  
```
Remove-CsMcxConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 deletes the collection of Mobility Service configuration settings assigned to the Redmond site.
  
```
Remove-CsMcxConfiguration -Identity "site:Redmond"

```

### EXAMPLE 2

In Example 2, all the Mobility Service configuration settings assigned to the service scope are removed. To do this, the **Get-CsMcxConfiguration** cmdlet is used along with the Filter parameter; the filter value "service:*" ensures that only settings that have an Identity that begins with the string value "service:" will be returned. That filtered collection is then piped to, and deleted by, the **Remove-CsMcxConfiguration** cmdlet.
  
```
Get-CsMcxConfiguration -Filter "service:*" | Remove-CsMcxConfiguration

```

### EXAMPLE 3

Example 3 deletes all the Mobility Service configuration settings where the ExposedWebURL property has been set to Internal. To perform this task, the command first calls the **Get-CsMcxConfiguration** cmdlet without any parameters; that returns a collection of all the Mobility Service configuration settings currently in use in the organization. This collection is then piped to the **Where-Object** cmdlet, which picks out only those settings where ExposedWebURL is equal to (-eq) Internal. In turn, that filtered collection is piped to the **Remove-CsMcxConfiguration** cmdlet, which deletes each item in that filtered collection.
  
```
Get-CsMcxConfiguration | Where-Object {$_.ExposedWebURL -eq "Internal"} | Remove-CsMcxConfiguration

```

### EXAMPLE 4

In Example 4, all the Mobility Service configuration settings that do not have an assigned push notification proxy URI are removed from Skype for Business Server 2015. To do this, the command first uses the **Get-CsMcxConfiguration** cmdlet (without any parameters) to return a collection of all the Mobility Service configuration settings currently in use. This collection is then piped to the **Where-Object** cmdlet, which picks out any settings where the PushNotificationProxyUri property is equal to (-eq) a Null value. Any settings that meet that criterion are then piped to, and deleted by, the **Remove-CsMcxConfiguration** cmdlet.
  
```
Get-CsMcxConfiguration | Where-Object {$_.PushNotificationProxyUri -eq $Null} | Remove-CsMcxConfiguration

```

## Detailed Description

The Mobility Service extends many of the capabilities of Skype for Business Server 2015 to mobile devices such as Apple iPhones, Windows Phone, Android phones, and Nokia phones. Among other things, users can use these phones to exchange instant message and presence information, and to receive notifications of new voice mails. Thanks to the push notification service (Apple Push Notification Service and Microsoft Push Notification Service), users with iPhones or Windows Phones can receive these notifications even if Skype for Business Server 2015 is running in the background. The Mobility Service also provides the opportunity for organizations to enable Call via Work. With Call via Work, users can make a call from their mobile phone and have it appear as though the call originated from their work phone; for example, Caller ID systems will display the user's work number instead of his or her mobile phone number.
  
The Mobility Service itself is managed by using Mobility Service configuration settings that can be applied to the global scope, the site scope, or the service scope (for the Web server service only). These settings control such things as the maximum length of time for a Mobility Service session; whether or not the Autodiscovery Service (which directs Mobility Service users to the appropriate Registrar pool) is available to users who log on outside the organization's firewall); and the location of the push notification service provider. 
  
When you install Skype for Business Server 2015, a single collection of Mobility Service configuration settings is created at the global scope; however, administrators can create custom configuration settings at either the site or the service scope. Later, these custom settings can be removed by using the **Remove-CsMcxConfiguration** cmdlet. If you remove service settings, Mobility Service servers formerly managed by those settings will be managed by the site settings (if they exist) or by the global settings. If you remove site settings, servers will be managed by the global settings.
  
Note that you can also run the **Remove-CsMcxConfiguration** cmdlet against the global settings. If you do that, however, the global settings will not be removed. Instead, the properties in the global collection will simply be reset to their default values.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier of the Mobility Service configuration settings to be removed. To "remove" the global settings, use this syntax:  <br/>  `-Identity global` <br/> Note that you cannot actually remove the global settings; all you can do is reset the properties to their default values.  <br/> To remove settings from the site scope, use syntax similar to this:  <br/>  `-Identity site:Redmond` <br/> To remove settings configured at the service scope, use syntax like this:  <br/>  `-Identity service:WebServer:atl-cs-001.litwareinc.com` <br/> You cannot use wildcards when specifying an Identity.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WriteableConfig.Settings.McxConfiguration.McxConfiguration. The **Remove-CsMcxConfiguration** cmdlet accepts pipelined input of McxConfiguration objects.
  
## Return Types

None. Instead, the cmdlet deletes instances of the Microsoft.Rtc.Management.WriteableConfig.Settings.McxConfiguration.McxConfiguration object.
  

