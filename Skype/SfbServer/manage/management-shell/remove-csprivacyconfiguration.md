---
title: "Remove-CsPrivacyConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 32052c51-953d-4278-9425-306245d297ed
description: "Removes an existing collection of privacy configuration settings. Privacy configuration settings help determine how much information users make available to other users. This cmdlet was introduced in Lync Server 2010."
---

# Remove-CsPrivacyConfiguration
 
Removes an existing collection of privacy configuration settings. Privacy configuration settings help determine how much information users make available to other users. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsPrivacyConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

Example 1 returns the privacy configuration settings assigned to the Redmond site. When these settings are deleted, users in the Redmond site will automatically inherit the global privacy configuration settings.
  
```
Remove-CsPrivacyConfiguration -Identity site:Redmond
```

### EXAMPLE 2

In Example 2, all the privacy configuration settings assigned at the site scope are deleted, To do this, the command first calls the **Get-CsPrivacyConfiguration** cmdlet along with the Filter parameter; the filter value "site:*" ensures that only those settings that have an Identity that begins with the characters "site" are returned. The filtered collection is then piped to the **Remove-CsPrivacyConfiguration** cmdlet, which removes each item in the collection.
  
```
Get-CsPrivacyConfiguration -Filter "site:*" | Remove-CsPrivacyConfiguration
```

### EXAMPLE 3

The command shown in Example 3 deletes all the privacy configuration settings where privacy mode has been disabled. To carry out this task, the command first calls the **Get-CsPrivacyConfiguration** cmdlet without any parameters; that returns a collection of all the privacy configuration settings in use in the organization. This collection is then piped to the **Where-Object** cmdlet, which selects only those settings where the EnablePrivacyMode property is equal to False. This filtered collection is piped to the **Remove-CsPrivacyConfiguration** cmdlet, which deletes each item in the collection.
  
```
Get-CsPrivacyConfiguration | Where-Object {$_.EnablePrivacyMode -eq $False} | Remove-CsPrivacyConfiguration
```

## Detailed Description

Skype for Business Server 2015 gives users the opportunity to share a wealth of presence information with other people: they can publish a photograph of themselves; they can provide detailed location information; they can have presence information automatically made available to everyone in the organization (as opposed to having this information available only to people on their Contacts list). 
  
Some users will welcome the opportunity to make this information available to their colleagues; other users might be more reluctant to share this data. (For example, many people might be hesitant about having their photo included in their presence data.) As a general rule, users have control over what information they will (or will not) share; for example, users can select or clear a check box in order to control whether or not their location information is shared with others. In addition, the privacy configuration cmdlets enable administrators to manage privacy settings for their users. In some cases, administrators can enable or disable settings. For example, if the property AutoInitiateContacts is set to True, then team members will automatically be added to each user's Contacts list; if set to False, team members will not be automatically be added to each user's Contacts list. 
  
In other cases, administrators can configure the default values in Skype for Business Server 2015 while still giving users the right to change these values. For example, by default location data is published for users, although users do have the right to stop location publication. By setting the PublishLocationDataByDefault property to False, administrators can change this behavior: in that case, location data will not be published by default, although users will still have the right to publish this data if they choose.
  
Privacy configuration settings can be applied at the global scope, the site scope, and at the service scope (albeit only for the User Server service). The **Remove-CsPrivacyConfiguration** cmdlet provides a way for you to delete settings that have been configured at either the site or service scope; for example, if you run the cmdlet against settings configured at the site scope, those settings will be deleted and users in that site will have their privacy settings governed by the global collection. The **Remove-CsPrivacyConfiguration** cmdlet can also be run against the global collection; however, the global collection will not be deleted. Instead, all that properties in that collection will be reset to their default values. For example, suppose you previously changed the EnablePrivacyMode property to True. If you now "delete" the global collection EnablePrivacyMode will revert to its default value of False.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the privacy configuration settings to be removed. To remove settings configured at the site scope, use syntax similar to this:  <br/>  `-Identity site:Redmond` <br/> To remove settings at the service level, use syntax like this:  <br/>  `-Identity service:UserServer:atl-cs-001.litwareinc.com` <br/> The **Remove-CsPrivacyConfiguration** cmdlet can also be run against the global collection of settings. In that case, however, the global settings will not be deleted. Instead, all the properties in that collection will be reset to their default values. <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account for which privacy configuration settings being deleted. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.PrivacyConfiguration object. The **Remove-CsPrivacyConfiguration** cmdlet accepts pipelined input of the privacy configuration object.
  
## Return Types

None. Instead, the **Remove-CsPrivacyConfiguration** cmdlet deletes existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.PrivacyConfiguration object.
  
## See also

#### 

[Get-CsPrivacyConfiguration](get-csprivacyconfiguration.md)
  
[New-CsPrivacyConfiguration](new-csprivacyconfiguration.md)
  
[Set-CsPrivacyConfiguration](set-csprivacyconfiguration.md)

