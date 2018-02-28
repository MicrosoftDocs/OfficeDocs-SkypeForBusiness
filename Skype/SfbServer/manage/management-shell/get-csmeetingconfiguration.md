---
title: "Get-CsMeetingConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3aa2d905-0ce0-4675-8543-c7bb9b4a3d1a
description: "The Get-CsMeetingConfiguration cmdlet enables you to return information about the meeting configuration settings currently in use in your organization. Meeting configuration settings help dictate the type of meetings (also calledconferences) that users can create, and control how (or even if) anonymous users and dial-in conferencing users can join these meetings. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsMeetingConfiguration
[]
The **Get-CsMeetingConfiguration** cmdlet enables you to return information about the meeting configuration settings currently in use in your organization. Meeting configuration settings help dictate the type of meetings (also called "conferences") that users can create, and control how (or even if) anonymous users and dial-in conferencing users can join these meetings. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsMeetingConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

The command shown in Example 1 returns a collection of all the meeting configuration settings currently in use in the organization.
  
```
Get-CsMeetingConfiguration
```

### EXAMPLE 2

In Example 2, only one collection of meeting configuration settings is returned: the settings that have the Identity site:Redmond. 
  
```
Get-CsMeetingConfiguration -Identity site:Redmond
```

### EXAMPLE 3

Example 3 returns all the meeting configuration settings that have been configured at the service scope. This is done by including the Filter parameter and the filter value "service:\*", which limits returned data to settings where the Identity property begins with the characters "service:".
  
```
Get-CsMeetingConfiguration -Filter "service:*"
```

### EXAMPLE 4

In Example 4, information is returned for all the meeting configuration settings where anonymous users are admitted by default. To accomplish this task, the command first uses the **Get-CsMeetingConfiguration** cmdlet without any parameters to return a collection of all the meeting configuration settings currently in use. That collection is then piped to the **Where-Object** cmdlet, which selects only those settings where the AdmitAnonymousUsersByDefault property is equal to True.
  
```
Get-CsMeetingConfiguration | Where-Object {$_.AdmitAnonymousUsersByDefault -eq $True}
```

## Detailed Description

Meetings (also called "conferences") are an integral part of Skype for Business Server 2015. The **CsMeetingConfiguration** cmdlets enable administrators to control the type of meetings that users can create, and determine how meetings handle anonymous users and dial-in conferencing users. For example, you can configure meetings so that anyone dialing in over the public switched telephone network (PSTN) is automatically admitted to the meeting. Alternatively, you can configure meetings so that dial-in users are not automatically admitted the meeting, but are instead routed to the meeting lobby. These dial-in users remain on hold in the lobby until a presenter admits them to the meeting.
  
The **Get-CsMeetingConfiguration** cmdlet enables you to return information about the meeting configuration setting collections currently in use in your organization.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard characters in order to return a collection (or collections) of meeting configuration settings. To return a collection of all the settings configured at the site scope, use this syntax,  `-Filter site:*`. To return a collection of all the settings that have the string value "EMEA" somewhere in their Identity (the only property you can filter on) use this syntax,  `-Filter *EMEA*`.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Indicates the unique identifier for the collection of meeting configuration settings you want to return. To refer to the global settings, use this syntax:  `-Identity global`. To refer to a collection configured at the site scope, use syntax similar to this,  `-Identity site:Redmond`. Settings configured at the service scope can be retrieved using syntax like this,  `-Identity service:UserServer:atl-cs-001.litwareinc.com`.  <br/> If this parameter is not specified, then the **Get-CsMeetingConfiguration** cmdlet will return a collection of all the meeting settings in use in the organization. <br/> Note that you cannot use wildcards when specifying an Identity. If you need to use wildcards, then include the Filter parameter instead.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the meeting configuration data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account whose meeting configuration settings are to be retrieved.  <br/> For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> If you are using a remote session of Windows PowerShell and are connected only to Skype for Business Online you do not have to include the Tenant parameter. Instead, the tenant ID will automatically be filled in for you based on your connection information. The Tenant parameter is primarily for use in a hybrid deployment.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **Get-CsMeetingConfiguration** cmdlet does not accept pipelined data.
  
## Return Types

The **Get-CsMeetingConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.MeetingConfiguration object.
  
## See also

#### 

[New-CsMeetingConfiguration](new-csmeetingconfiguration.md)
  
[Remove-CsMeetingConfiguration](remove-csmeetingconfiguration.md)
  
[Set-CsMeetingConfiguration](set-csmeetingconfiguration.md)

