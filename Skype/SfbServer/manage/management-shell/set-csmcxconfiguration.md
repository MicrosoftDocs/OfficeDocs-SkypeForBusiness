---
title: "Set-CsMcxConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: eaff70d9-97fa-482c-b9fb-a90263685b29
description: "Modifies an existing collection of Skype for Business Server 2015 Mobility Service configuration settings. The Mobility Service enables users of mobile phones such as iPhones and Windows Phones to do such things as exchange instant messages and presence information; store and retrieve voice mail internally instead of with their wireless provider; and take advantage of Skype for Business capabilities such as Call via Work and dial-out conferencing. This cmdlet was introduced in the cumulative update for Lync Server 2010: November 2011."
---

# Set-CsMcxConfiguration
 
Modifies an existing collection of Skype for Business Server 2015 Mobility Service configuration settings. The Mobility Service enables users of mobile phones such as iPhones and Windows Phones to do such things as exchange instant messages and presence information; store and retrieve voice mail internally instead of with their wireless provider; and take advantage of Skype for Business capabilities such as Call via Work and dial-out conferencing. This cmdlet was introduced in the cumulative update for Lync Server 2010: November 2011.
  
```
Set-CsMcxConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

In Example 1, the ExposedWebURL property for the Mobility Service configuration settings assigned to the Redmond site is set to External.
  
```
Set-CsMcxConfiguration -Identity site:Redmond -ExposedWebURL External

```

### EXAMPLE 2

Example 2 shows how a single command can assign the same property value to all the Mobility Service configuration settings currently in use in an organization. To do this, the command first uses the **Get-CsMcxConfiguration** cmdlet without any parameters in order to return a collection of all the existing Mobility Service configuration settings. That collection is then piped to the **Set-CsMcxConfiguration**, which sets the ExposedWebURL property for each item in the collection to External.
  
```
Get-CsMcxConfiguration | Set-CsMcxConfiguration -ExposedWebURL External

```

### EXAMPLE 3

In Example 3, all the Mobility Service configuration settings that have a SessionShortExpirationInterval of more than 3600 seconds are modified to set that property value to 3600; that effectively makes 3600 seconds the maximum value for all the Mobility Service configuration settings in the organization. To do this, the **Get-CsMcxConfiguration** cmdlet is first called (without any parameters) in order to return a collection of all the Mobility Service configuration settings currently in use. That collection is then piped to the Where-Object cmdlet, which picks out only those settings where the SessionShortExpirationInterval property is greater than (-gt) 3600. This filtered collection is then piped to the **Set-CsMcxConfiguration** cmdlet, which sets the value of the SessionShortExpirationInterval property for each item in the collection to 3600.
  
```
Get-CsMcxConfiguration | Where-Object {$_.SessionShortExpirationInterval -gt 3600} | Set-CsMcxConfiguration -SessionShortExpirationInterval 3600

```

## Detailed Description

Skype for Business Server 2015 Mobility Service extends many of the capabilities of Skype for Business to mobile devices such as Apple iPhones, Windows Phone, Android phones, and Nokia phones. Among other things, users can use these phones to exchange instant message and presence information, and to receive notifications of new voice mails. Thanks to the push notification service (Apple Push Notification Service and Microsoft Push Notification Service), users with iPhones or Windows Phones can receive these notifications even if Skype for Business is running in the background. The Mobility Service also provides the opportunity for organizations to enable Call via Work. With Call via Work, users can make a call from their mobile phone and make it appear as though the call originated from their work phone; for example, Caller ID systems will display the user's work number instead of his or her mobile phone number.
  
The Mobility Service itself is managed by using Mobility Service configuration settings that can be applied to the global scope, the site scope, or the service scope (for the Web server service only). These settings control such things as the maximum length of time for a Mobility Service session; whether or not the Skype for Business Server 2015 Autodiscovery Service (which directs Mobility Service users to the appropriate Registrar pool) is available to users who log on outside the organization's firewall); and the location of the push notification service provider. 
  
The **Set-CsMcxConfiguration** cmdlet provides a way for administrators to modify any of their existing Mobility Service configuration settings.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _ExposedWebURL_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.McxConfiguration.ExposedWebURL  <br/> |Indicates whether the URL used by the Autodiscovery Service is accessible to users both inside and outside the organization firewall (External) or only accessible to users inside the firewall (Internal).  <br/> Allowed values are: Internal or External. The default value is External.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Represents the unique identifier of the collection of Mobility Service configuration settings to be modified. To modify the global settings, use the following syntax:  <br/>  `-Identity global` <br/> To modify settings at the site scope, use the prefix "site:" followed by the site name. For example:  <br/>  `-Identity "site:Redmond"` <br/> To modify settings configured at the service scope, use syntax like this:  <br/>  `-Identity service:WebServer:atl-cs-001.litwareinc.com` <br/> If this parameter is not specified, then the **Set-CsMcxConfiguration** cmdlet will modify the global settings. <br/> |
| _Instance_ <br/> |Optional  <br/> |MCX Configuration object  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _PushNotificationProxyUri_ <br/> |Optional  <br/> |System.String  <br/> |URI of a service provider that can forward push notification requests to the Apple Push Notification Service and the Microsoft Push Notification Service. The PushNotificationProxyUri must be in the form of a SIP address; for example:  <br/>  `-PushNotificationProxyUri "sip:push@push.lync.com"` <br/> |
| _SessionExpirationInterval_ <br/> |Optional  <br/> |System.UInt32  <br/> |Length of time, in seconds, of a mobile session for iPhone or Widows Phone users. If Skype for Business is running in the background on these phones, users will receive push notifications as long as the session expiration interval has not expired.  <br/> The mobile device must send a notice to the server indicating that the device is still active before the session timeout is reached. If it does not, the device will be listed as inactive and the user will have to log back on to the system.  <br/> This property can be set to any integer value between 120 and 4294967295, inclusive. The default value is 259200 seconds (3 days). Note that the value of the SessionExpirationInterval property must be greater than the value of the SessionShortExpirationInterval property.  <br/> |
| _SessionShortExpirationInterval_ <br/> |Optional  <br/> |System.UInt32  <br/> |Length of time, in seconds, of a mobile session for Android or Nokia phone users.  <br/> The mobile device must send a notice to the server indicating that the device is still active before the session timeout is reached. If it does not, the device will be listed as inactive and the user will have to log back on to the system.  <br/> This property can be set to any integer value between 120 and 4294967295, inclusive. The default value is 3600 seconds (1 hour). Note that the value of the SessionExpirationInterval property must be greater than the value of the SessionShortExpirationInterval property.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WriteableConfig.Settings.McxConfiguration.McxConfiguration object. The **Set-CsMcxConfiguration** cmdlet accepts pipelined instances of the McxConfiguration object.
  
## Return Types

None. Instead, the **Set-CsMcxConfiguration** cmdlet modifies existing instances of the Microsoft.Rtc.Management.WriteableConfig.Settings.McxConfiguration.McxConfiguration object.
  

