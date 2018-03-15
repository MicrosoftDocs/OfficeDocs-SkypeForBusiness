---
title: "Set-CsPrivacyConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 67fbd99a-0708-4e6f-8755-cb1a08d07ff3
description: "Modifies an existing set of privacy configuration settings. Privacy configuration settings help determine how much information users make available to other users. This cmdlet was introduced in Lync Server 2010."
---

# Set-CsPrivacyConfiguration
 
Modifies an existing set of privacy configuration settings. Privacy configuration settings help determine how much information users make available to other users. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsPrivacyConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

The command shown in Example 1 modifies three property values for the privacy configuration settings with the Identity site:Redmond. The three property values modified are AutoInitiateContacts, PublishLocationDataDefault, and DisplayPublishedPhotoDefault.
  
```
Set-CsPrivacyConfiguration -Identity site:Redmond -EnablePrivacyMode $False -AutoInitiateContacts $True -PublishLocationDataDefault $True -DisplayPublishedPhotoDefault $True
```

### EXAMPLE 2

Example 2 enables privacy mode for all the privacy configuration settings currently in use in the organization. To do this, the command first calls the **Get-CsPrivacyConfiguration** cmdlet without any parameters; this returns the complete collection of privacy settings. This collection is then piped to the **Set-CsPrivacyConfiguration** cmdlet, which takes each item in the collection and sets the EnablePrivacyMode property to True.
  
```
Get-CsPrivacyConfiguration | Set-CsPrivacyConfiguration -EnablePrivacyMode $True
```

### EXAMPLE 3

In Example 3, modifications are made to all the privacy configuration settings that are not currently using privacy mode. To carry out this task, the **Get-CsPrivacyConfiguration** cmdlet is first used in order to return a collection of all the privacy configuration settings. This collection is piped to the **Where-Object** cmdlet, which selects only those settings where the EnablePrivacyMode property is equal to False. The filtered collection is then piped to the **Set-CsPrivacyConfiguration** cmdlet, which assigns values to the AutoInitiateContacts, PublishLocationDataDefault, and DisplayPublishedPhotoDefault properties for each item in the collection.
  
```
Get-CsPrivacyConfiguration | Where-Object {$_.EnablePrivacyMode -eq $False} | Set-CsPrivacyConfiguration -AutoInitiateContacts $True -PublishLocationDataDefault $True -DisplayPublishedPhotoDefault $True
```

## Detailed Description

Skype for Business Server 2015 gives users the opportunity to share a wealth of presence information with other people: they can publish a photograph of themselves; they can provide detailed location information; they can have presence information automatically made available to everyone in the organization (as opposed to having this information available only to people on their Contacts list). 
  
Some users will welcome the opportunity to make this information available to their colleagues; other users might be more reluctant to share this data. (For example, many people might be hesitant about having their photo included in their presence data.) As a general rule, users have control over what information they will (or will not) share; for example, users can select or clear a check box in order to control whether or not their location information is shared with others. In addition, the privacy configuration cmdlets enable administrators to manage privacy settings for their users. In some cases, administrators can enable or disable settings; for example, if the property AutoInitiateContacts is set to True, then team members will automatically be added to each user's Contacts list; if set to False, team members will not be automatically be added to each user's Contacts list. 
  
In other cases, administrators can configure the default values in Skype for Business while still giving users the right to change these values. For example, by default location data is published for users, although users do have the right to stop location publication. By setting the PublishLocationDataByDefault property to False, administrators can change this behavior: in that case, location data will not be published by default, although users will still have the right to publish this data if they choose.
  
Privacy configuration settings can be applied at the global scope, the site scope, and at the service scope (albeit only for the User Server service). The **Set-CsPrivacyConfiguration** cmdlet enables you to modify any of the privacy configuration settings currently in use in your organization.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _AutoInitiateContacts_ <br/> |Optional  <br/> |System.Boolean  <br/> |If True, Skype for Business will automatically add your manager and your direct reports to your Contacts list. The default value is True.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DisplayPublishedPhotoDefault_ <br/> |Optional  <br/> |System.Boolean  <br/> |If True, the user's photo will automatically be published in Skype for Business. If False, the user's photo will not be available unless he or she explicitly selects the option Let others see my photo. The default value is True.  <br/> |
| _EnablePrivacyMode_ <br/> |Optional  <br/> |System.Boolean  <br/> | If True, gives users the opportunity to enable the advanced privacy mode. In advanced privacy mode, only people on your Contacts list will be allowed to view your presence information. If False, your presence information will be available to anyone in your organization. The default value is False. <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the privacy configuration settings to be modified. To modify the global settings, use this syntax:  <br/>  `-Identity global` <br/> To modify settings configured at the site scope, use syntax similar to this:  <br/>  `-Identity site:Redmond` <br/> To modify settings at the service level, use syntax like this:  <br/>  `-Identity service:Redmond-UserServices-1` <br/> Note that privacy settings can only be applied to the User Server service. An error will occur if you try to apply these settings to any other service.  <br/> If this parameter is not specified then the global settings will be updated when you call the **Set-CsPrivacyConfiguration** cmdlet. <br/> |
| _Instance_ <br/> |Optional  <br/> |PrivacyConfiguration object  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _PublishLocationDataDefault_ <br/> |Optional  <br/> |System.Boolean  <br/> |If True, location data will automatically be published in Skype for Business. If False, location data will not be available unless the user explicitly selects the option Show Contacts My Location. The default value is True.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account for the privacy configuration settings being modified. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> If you are using a remote session of Windows PowerShell and are connected only to Skype for Business Online you do not have to include the Tenant parameter. Instead, the tenant ID will automatically be filled in for you based on your connection information. The Tenant parameter is primarily for use in a hybrid deployment.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.PrivacyConfiguration object. The **Set-CsPrivacyConfiguration** cmdlet accepts pipelined input of the privacy configuration object.
  
## Return Types

The **Set-CsPrivacyConfiguration** cmdlet does not return any objects or values. Instead, the cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.PrivacyConfiguration object.
  
## See also

#### 

[Get-CsPrivacyConfiguration](get-csprivacyconfiguration.md)
  
[New-CsPrivacyConfiguration](new-csprivacyconfiguration.md)
  
[Remove-CsPrivacyConfiguration](remove-csprivacyconfiguration.md)

