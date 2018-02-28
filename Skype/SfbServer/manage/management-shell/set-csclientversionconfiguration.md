---
title: "Set-CsClientVersionConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 7cd2e86f-2d31-4db2-9d0f-f1418fd4aba2
description: "Modifies the specified collection of client version configuration settings. Client version configuration settings determine whether or not Skype for Business Server 2015 checks the version number of each client application that logs on to the system. If client version filtering is enabled, then the ability of that client application to access the system will be based on settings configured in the appropriate client version policy. This cmdlet was introduced in Lync Server 2010."
---

# Set-CsClientVersionConfiguration
[]
Modifies the specified collection of client version configuration settings. Client version configuration settings determine whether or not Skype for Business Server 2015 checks the version number of each client application that logs on to the system. If client version filtering is enabled, then the ability of that client application to access the system will be based on settings configured in the appropriate client version policy. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsClientVersionConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

In Example 1, the **Set-CsClientVersionConfiguration** cmdlet is used to modify the settings collection with the Identity "site:Redmond". In this case, the Enabled parameter is set to False in order to disable the client version configuration settings.
  
```
Set-CsClientVersionConfiguration -Identity site:Redmond -Enabled $False
```

### EXAMPLE 2

In Example 2, the DefaultUrl property is modified for all the client version configuration settings currently in use in the organization. To do this, the command first calls the **Get-CsClientVersionConfiguration** cmdlet without any additional parameters in order to return all of the client version configuration settings. That information is then piped to the **Set-CsClientVersionConfiguration** cmdlet, which sets the value of the DefaultUrl for each configuration collection to https://litwareinc.com/csclients.
  
```
Get-CsClientVersionConfiguration | Set-CsClientVersionConfiguration -DefaultURL "https://litwareinc.com/csclients"
```

### EXAMPLE 3

In Example 3, modifications are made to all the client version configuration settings where the DefaultAction is currently set to Block. To carry out this task, the command first uses the **Get-CsClientVersionConfiguration** cmdlet to return all of the client version configuration settings currently in use. That information is then piped to the **Where-Object** cmdlet, which picks out only those items where the DefaultAction property is equal to "Block". In turn, that filtered collection is then piped to the **Set-CsClientVersionConfiguration** cmdlet, which does two things to each item in the collection: 1) sets the DefaultAction to BlockWithUrl; and, 2) sets the DefaultUrl to https://litwareinc.com/csclients.
  
```
Get-CsClientVersionConfiguration | Where-Object {$_.DefaultAction -eq "Block"} | Set-CsClientVersionConfiguration -DefaultAction "BlockWithUrl" -DefaultURL "https://litwareinc.com/csclients"
```

## Detailed Description

Skype for Business Server 2015 gives administrators considerable leeway when it comes to specifying the client software (and, equally important, the version number of that software) that users can use to log on to the system. For example, there is no technical reason that requires users to log on to Skype for Business Server 2015 by using Skype for Business; there are no technical limitations that would prevent users from logging on by using Microsoft Office Communicator 2007 R2.
  
On the other hand, there might be some non-technical reasons why you would prefer that your users do not log on by using Office Communicator 2007 R2. For example, Office Communicator 2007 R2 does not support all of the features and capabilities found in Skype for Business; as a result, users who log on with Office Communicator 2007 R2 will have a different experience than users who log on by using Skype for Business. This can create difficulties for your users; it can also create difficulties for help desk personnel, who must provide support for a number of different client applications. 
  
If this could be a problem for your organization you can employ client version filtering in order to specify which client applications can be used to log on to Skype for Business Server 2015. When you install Skype for Business Server 2015, a global set of client version configuration settings is installed and enabled. These settings are used to determine whether or not client version filtering is enabled. In addition to the global settings, client version configuration settings can also be applied at the site scope; in those instances, the site settings will have precedence over the global settings.
  
The **Set-CsClientVersionConfiguration** cmdlet enables you to modify an existing collection of client version configuration settings.
  
Note that client version configuration is not a security feature. The technology relies on self-reporting from client applications, and does not attempt to verify that an application is really the application and the version number of that application that it claims to be.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DefaultAction_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.DefaultAction  <br/> |Indicates the action to be taken if a user tries to log on from a client application with a version number that cannot be found in the appropriate client version policy. DefaultAction must be set to one of the following values:  <br/> Allow. The client application will be allowed to log on.  <br/> AllowWithUrl. The client application will be allowed to log on. In addition, a message box will be displayed to the user that includes the URL of a webpage where that user can download an approved client application. The URL for this webpage should be specified as the value for the DefaultUrl property.  <br/> Block. The client application will be prevented from logging on.  <br/> BlockWithUrl. The client application will be prevented from logging on. However, the "Access denied" message box displayed to the user will include the URL of a webpage where that user can download an approved client application. The URL for this webpage should be specified as the value for the DefaultUrl property.  <br/> This property is ignored if the Enabled property is set to False. When the Enabled property is set to False, then no client version filtering of any kind takes place.  <br/> |
| _DefaultURL_ <br/> |Optional  <br/> |System.String  <br/> |Specifies the URL of the webpage where users can download an approved client application. If specified, and if the DefaultAction is set to BlockWithURL, this URL will appear in the "Access denied" message box displayed any time a user tries to log on from an unsupported client application.  <br/> |
| _Enabled_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether client version filtering is enabled or disabled. If the Enabled property is True, then the server will check the version number of each client application that attempts to log on; the server will then allow or deny access based on the appropriate client version policy. If the Enabled property is False, then any client application capable of logging on will be allowed to log on.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Represents the unique identifier of the client version configuration settings to be modified. To modify the global settings, use syntax like this:  `-Identity global`. To modify settings assigned to the site scope, use syntax similar to this:  `"site:Redmond"`.  <br/> If this parameter is not included, the **Set-CsClientVersionConfiguration** cmdlet will automatically configure the global settings. <br/> |
| _Instance_ <br/> |Optional  <br/> |ClientVersionPolicy objects  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.ClientVersionConfiguration object. The **Set-CsClientVersionConfiguration** cmdlet accepts pipelined instances of the client version configuration object.
  
## Return Types

The **Set-CsClientVersionConfiguration** cmdlet does not return a value or object. Instead, the cmdlet configures instances of the Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.ClientVersionConfiguration object.
  
## See also

#### 

[Get-CsClientVersionConfiguration](get-csclientversionconfiguration.md)
  
[New-CsClientVersionConfiguration](new-csclientversionconfiguration.md)
  
[Remove-CsClientVersionConfiguration](remove-csclientversionconfiguration.md)

