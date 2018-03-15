---
title: "New-CsClientVersionConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e7aac850-9e29-4d18-8929-74a89e9355cd
description: "Creates a new collection of client version configuration settings. Client version configuration settings determine whether or not Skype for Business Server 2015 checks the version number of each client application that logs on to the system. If client version filtering is enabled, then the ability of that client application to access the system will be based on settings configured in the appropriate client version policy. This cmdlet was introduced in Lync Server 2010."
---

# New-CsClientVersionConfiguration
 
Creates a new collection of client version configuration settings. Client version configuration settings determine whether or not Skype for Business Server 2015 checks the version number of each client application that logs on to the system. If client version filtering is enabled, then the ability of that client application to access the system will be based on settings configured in the appropriate client version policy. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsClientVersionConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-DefaultAction <Allow | AllowWithUrl | Block | BlockWithUrl>] [-DefaultURL <String>] [-Enabled <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 creates a new collection of client version configuration settings for the Redmond site. In this command, the Enabled parameter is set to False, which means that client filtering is disabled for the Redmond site. 
  
```
New-CsClientVersionConfiguration -Identity site:Redmond -Enabled $False
```

### EXAMPLE 2

Example 2 shows how you can create a new collection of client version configuration settings in memory, modify that collection, and then turn these virtual settings into an actual collection of settings applied to the Redmond site. To do this, the first command uses the **New-CsClientVersionConfiguration** cmdlet and the InMemory parameter to create an in-memory-only collection of settings with the Identity site:Redmond. This collection is stored in a variable named $x and exists in memory only: if you terminate your Windows PowerShell session or delete the variable $x these client version configuration settings will disappear and will never be applied to the Redmond site.
  
In command 2 the value of the DefaultAction property for the virtual settings is set to Block. In command 3, the **Set-CsClientVersionConfiguration** cmdlet is used to transform the virtual settings into an actual collection of client version configuration settings applied to the Redmond site.
  
```
$x = New-CsClientVersionConfiguration -Identity site:Redmond -InMemory
$x.DefaultAction = "Block" 
Set-CsClientVersionConfiguration -Instance $x
```

## Detailed Description

Skype for Business Server 2015 gives administrators considerable leeway when it comes to specifying the client software (and, equally important, the version number of that software) that users can use to log on to the system. For example, there is no technical reason that requires users to log on to Skype for Business Server 2015 by using Skype for Business; there are no technical limitations that would prevent users from logging on by using Microsoft Office Communicator 2007 R2.
  
However, there might be some non-technical reasons why you would prefer that your users do not log on by using Office Communicator 2007 R2. For example, Office Communicator 2007 R2 does not support all of the features and capabilities found in Skype for Business; as a result, users who log on with Office Communicator 2007 R2 will have a different experience than users who log on by using Skype for Business. This can create difficulties for your users; it can also create difficulties for help desk personnel, who must provide support for a number of different client applications. 
  
If this could be a problem for your organization you can employ client version filtering in order to specify the client applications that can be used to log on to Skype for Business Server 2015. When you install Skype for Business Server 2015, a global set of client version configuration settings is installed and enabled. These settings are used to determine whether or not client version filtering is enabled. 
  
In addition to the global settings, the **New-CsClientVersionConfiguration** cmdlet enables you to create client version configuration settings at the site scope. When client version configuration settings are applied at the site scope, those settings take precedence over the global settings. For example, suppose you have enabled client version filtering at the global scope, and then you create a separate collection of settings for the Redmond site, a collection of settings where client version filtering is disabled. In that case, client version filtering will be disabled for all the users who have accounts on the Redmond site.
  
Note, however, that anonymous users are only affected by global settings. That's because anonymous users are not associated with a site.
  
Note that client version configuration is not a security feature. The technology relies on self-reporting from client applications, and does not attempt to verify that an application is really the application and the version number of that application that it claims to be.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Represents the unique identifier to be assigned to the new collection of client version configuration settings. Because you can only create new collections at the site scope, the Identity will always be the prefix "site:" followed by the site name; for example "site:Redmond". Note that the preceding command will fail if a collection of settings with the Identity site:Redmond already exists.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DefaultAction_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.DefaultAction  <br/> |Indicates the action to be taken if a user tries to log on from a client application with a version number that cannot be found in the appropriate client version policy. DefaultAction must be set to one of the following values:  <br/> Allow. The client application will be allowed to log on.  <br/> AllowWithUrl. The client application will be allowed to log on. In addition, a message box will be displayed to the user that includes the URL of a webpage where that user can download an approved client application. The URL for this webpage should be specified as the value for the DefaultUrl property.  <br/> Block. The client application will be prevented from logging on.  <br/> BlockWithUrl. The client application will be prevented from logging on. However, the "Access denied" message box displayed to the user will include the URL of a webpage where that user can download an approved client application. The URL for this webpage should be specified as the value for the DefaultUrl property.  <br/> This property is ignored if the Enabled property is set to False. When the Enabled property is set to False, then no client version filtering of any kind takes place.  <br/> |
| _DefaultURL_ <br/> |Optional  <br/> |System.String  <br/> |Specifies the URL of the webpage where users can download an approved client application. If specified, and if the DefaultAction is set to BlockWithUrl, this URL will appear in the "Access denied" message box displayed any time a user tries to log on from an unsupported client application.  <br/> |
| _Enabled_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether client version filtering is enabled or disabled. If the Enabled property is True, the server will check the version number of each client application that attempts to log on; the server will then allow or deny access based on the appropriate client version policy. If the Enabled property is False, then any client application capable of logging on will be allowed to log on.  <br/> The default value is True.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching **Set-\<cmdlet\>**. <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **New-CsClientVersionConfiguration** cmdlet does not accept pipelined input.
  
## Return Types

Creates new instances of the Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.ClientVersionConfiguration object.
  
## See also

#### 

[Get-CsClientVersionConfiguration](get-csclientversionconfiguration.md)
  
[Remove-CsClientVersionConfiguration](remove-csclientversionconfiguration.md)
  
[Set-CsClientVersionConfiguration](set-csclientversionconfiguration.md)

