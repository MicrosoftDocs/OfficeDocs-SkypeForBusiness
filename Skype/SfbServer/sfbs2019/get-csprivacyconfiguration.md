---
title: "Get-CsPrivacyConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f10ebf4a-1af5-48cf-96dc-4f5d56281848
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsPrivacyConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Returns information about the privacy configuration settings currently in use in your organization. Privacy configuration settings help determine how much information users make available to other users. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsPrivacyConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 returns all the privacy configuration settings currently in use in the organization. 
  
```
Get-CsPrivacyConfiguration
```

### EXAMPLE 2

Example 2 returns a single collection of privacy configuration settings: the settings that have the Identity site:Redmond. 
  
```
Get-CsPrivacyConfiguration -Identity site:Redmond
```

### EXAMPLE 3

In Example 3, information is returned for all the privacy configuration settings that have been assigned to the site scope. To do this, the Filter parameter is included, along with the filter value "site:\*". That filter value ensures that only settings where the Identity (the only property you can filter on) begins with the characters "site:".
  
```
Get-CsPrivacyConfiguration -Filter "site:*"
```

### EXAMPLE 4

The command shown in Example 4 returns information about all the privacy configuration settings where privacy mode has been enabled. This is done by first calling the **Get-CsPrivacyConfiguration** cmdlet without any parameters in order to return a collection of all the privacy settings. This collection is then piped to the **Where-Object** cmdlet, which picks out only those settings where the EnablePrivacyMode property is equal to True. 
  
```
Get-CsPrivacyConfiguration | Where-Object {$_.EnablePrivacyMode -eq $True}
```

## Detailed Description
<a name="sectionSection1"> </a>

Lync Server gives users the opportunity to share a wealth of presence information with other people: they can publish a photograph of themselves; they can provide detailed location information; they can have presence information automatically made available to everyone in the organization (as opposed to having this information available only to people on their Contacts list). 
  
Some users will welcome the opportunity to make this information available to their colleagues; other users might be more reluctant to share this data. (For example, many people might be hesitant about having their photo included in their presence data.) As a general rule, users have control over what information they will (or will not) share; for example, users can select or clear a check box in order to control whether or not their location information is shared with others. In addition, the privacy configuration cmdlets enable administrators to manage privacy settings for their users. In some cases, administrators can enable or disable settings; for example, if the property AutoInitiateContacts is set to True, then team members will automatically be added to each user's Contacts list; if set to False, team members will not be automatically be added to each user's Contacts list. 
  
In other cases, administrators can configure the default values in Lync Server while still giving users the right to change these values. For example, by default location data is published for users, although users do have the right to stop location publication. By setting the PublishLocationDataByDefault property to False, administrators can change this behavior: in that case, location data will not be published by default, although users will still have the right to publish this data if they choose.
  
Privacy configuration settings can be applied at the global scope, the site scope, and at the service scope (albeit only for the User Server service). The **Get-CsPrivacyConfiguration** cmdlet enables you to retrieve information about all the privacy configuration settings currently in use in your organization. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsPrivacyConfiguration** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsPrivacyConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcards to return one or more collections of privacy configuration settings. For example, to return all the settings configured at the site scope, you can use this syntax: -Filter "site:\*". To return all the settings configured at the service scope, use this syntax: -Filter "service:\*".  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the privacy configuration settings to be retrieved. To return the global settings, use this syntax: -Identity global. To return settings configured at the site scope, use syntax similar to this: -Identity site:Redmond. To modify settings at the service level, use syntax like this: -Identity service:UserServer:atl-cs-001.litwareinc.com  <br/> If this parameter is not specified then the **Get-CsPrivacyConfiguration** cmdlet returns all the privacy configuration settings currently in use in your organization.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the privacy configuration data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account whose privacy configuration settings are to be retrieved.  <br/> For example:  <br/> -Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"  <br/> You can return the tenant ID for each of your tenants by running this command:  <br/> Get-CsTenant | Select-Object DisplayName, TenantID  <br/> If you are using a remote session of Windows PowerShell and are connected only to Skype for Business Online you do not have to include the Tenant parameter. Instead, the tenant ID will automatically be filled in for you based on your connection information. The Tenant parameter is primarily for use in a hybrid deployment.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Get-CsPrivacyConfiguration** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Get-CsPrivacyConfiguration** cmdlet returns existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.PrivacyConfiguration object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsPrivacyConfiguration](new-csprivacyconfiguration.md)
  
[Remove-CsPrivacyConfiguration](remove-csprivacyconfiguration.md)
  
[Set-CsPrivacyConfiguration](set-csprivacyconfiguration.md)

