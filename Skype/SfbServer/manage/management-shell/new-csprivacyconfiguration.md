---
title: "New-CsPrivacyConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 9b7f02d7-93a5-4fa5-a74c-3fe4baf8bbfc
description: "Creates a new collection of privacy configuration settings. Privacy configuration settings help determine how much information users make available to other users. This cmdlet was introduced in Lync Server 2010."
---

# New-CsPrivacyConfiguration
 
Creates a new collection of privacy configuration settings. Privacy configuration settings help determine how much information users make available to other users. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsPrivacyConfiguration -Identity <XdsIdentity> [-AutoInitiateContacts <$true | $false>] [-Confirm [<SwitchParameter>]] [-DisplayPublishedPhotoDefault <$true | $false>] [-EnablePrivacyMode <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-PublishLocationDataDefault <$true | $false>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 creates a new collection of privacy configuration settings that will be applied to the Redmond site (-Identity site:Redmond). The new settings enable privacy mode; this is done by adding the EnablePrivacyMode parameter and setting the parameter value to True. Note that this command will fail if the Redmond site already has a collection of privacy settings.
  
```
New-CsPrivacyConfiguration -Identity site:Redmond -EnablePrivacyMode $True
```

### EXAMPLE 2

Example 2 demonstrates how you can use the InMemory parameter to create a new collection of privacy configuration settings that initially exist only in memory. To do this, the **New-CsPrivacyConfiguration** cmdlet is called along with the Identity and InMemory parameters; the resulting object is stored in a variable named $x. At this point, the privacy settings exist only in memory; if you run the **Get-CsPrivacyConfiguration** cmdlet you will not see a listing for site:Redmond.
  
In the second command, the value of the EnablePrivacyMode property is set to True. Finally, the third command uses the **Set-CsPrivacyConfiguration** cmdlet to transform this virtual collection of privacy settings into an actual collection of settings applied to the Redmond site. Calling the **Set-CsPrivacyConfiguration** cmdlet is critical: if you fail to call this cmdlet then your new privacy settings will not be applied to the Redmond site, and will disappear when you end your Windows PowerShell session or delete the variable $x
  
```
$x = New-CsPrivacyConfiguration -Identity site:Redmond -InMemory
$x.EnablePrivacyMode = $True
Set-CsPrivacyConfiguration -Instance $x
```

## Detailed Description

Skype for Business Server 2015 gives users the opportunity to share a wealth of presence information with other people: they can publish a photograph of themselves; they can provide detailed location information; they can have presence information automatically made available to everyone in the organization (as opposed to having this information available only to people on their Contacts list).
  
Some users will welcome the opportunity to make this information available to their colleagues; other users might be more reluctant to share this data. (For example, many people might be hesitant about having their photo included in their presence data.) As a general rule, users have control over what information they will (or will not) share; for example, users can select or clear a check box in order to control whether or not their location information is shared with others. In addition, the privacy configuration cmdlets enable administrators to manage privacy settings for their users. In some cases, administrators can enable or disable settings; for example, if the property AutoInitiateContacts is set to True, then team members will automatically be added to each user's Contacts list; if set to False, team members will not be automatically be added to each user's Contacts list.
  
In other cases, administrators can configure the default values in Skype for Business while still giving users the right to change these values. For example, by default location data is published for users, although users do have the right to stop location publication. By setting the PublishLocationDataByDefault property to False, administrators can change this behavior: in that case, location data will not be published by default, although users will still have the right to publish this data if they choose.
  
Privacy configuration settings can be applied at the global scope, the site scope, and at the service scope (albeit only for the User Server service). The **New-CsPrivacyConfiguration** cmdlet enables you to create new privacy configuration settings to be applied to a site or service. (New collections cannot be created at the global scope.) Note that each individual site or service can have, at most, a single collection of privacy configuration settings: if you try to create a new collection for the Redmond site and that site already has a collection of privacy settings then your command will fail.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the privacy configuration settings to be created. To create a new collection of settings at the site scope, use syntax similar to this:  <br/>  `-Identity site:Redmond` <br/> To create new settings at the service scope, use syntax like this:  <br/>  `-Identity service:UserServer:atl-cs-001.litwareinc.com` <br/> Privacy settings can only be created for the User Server service. An error will occur if you try to apply these settings to any other service.  <br/> Note that your command will fail if privacy configuration settings already exist for the specified site or service. Likewise, your command will fail if you attempt to create a new collection of global settings.  <br/> |
| _AutoInitiateContacts_ <br/> |Optional  <br/> |System.Boolean  <br/> |If True, Skype for Business will automatically add your manager and your direct reports to your Contacts list. The default value is True.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DisplayPublishedPhotoDefault_ <br/> |Optional  <br/> |System.Boolean  <br/> |If True, the user's photo will automatically be published in Skype for Business. If False, the user's photo will not be available unless he or she explicitly selects the option Let others see my photo. The default value is True.  <br/> |
| _EnablePrivacyMode_ <br/> |Optional  <br/> |System.Boolean  <br/> |If True, gives users the opportunity to enable the advanced privacy mode. In advanced privacy mode, only people on your Contacts list will be allowed to view your presence information. If False, your presence information will be available to anyone in your organization. The default value is False.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching **Set-\<cmdlet\>**. <br/> |
| _PublishLocationDataDefault_ <br/> |Optional  <br/> |System.Boolean  <br/> |If True, location data will automatically be published in Skype for Business. If False, location data will not be available unless the user explicitly selects the option Show Contacts My Location. The default value is True.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account for which the new privacy configuration settings are being created. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **New-CsPrivacyConfiguration** cmdlet does not accept pipelined input.
  
## Return Types

The **New-CsPrivacyConfiguration** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.PrivacyConfiguration object.
  
## See also

#### 

[Get-CsPrivacyConfiguration](get-csprivacyconfiguration.md)
  
[Remove-CsPrivacyConfiguration](remove-csprivacyconfiguration.md)
  
[Set-CsPrivacyConfiguration](set-csprivacyconfiguration.md)

