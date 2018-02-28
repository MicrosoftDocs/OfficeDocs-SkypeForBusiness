---
title: "Get-CsUserServicesConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 07884f7a-d9f7-4a3f-a5ef-7f4ba71c2769
description: "Returns information about the User Services configuration settings in use in your organization. The User Services service helps maintain presence information and manage conferencing. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsUserServicesConfiguration
[]
Returns information about the User Services configuration settings in use in your organization. The User Services service helps maintain presence information and manage conferencing. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsUserServicesConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

The command shown in Example 1 returns a collection of all the User Services configuration settings currently in use in the organization. This is achieved by calling the **Get-CsUserServicesConfiguration** cmdlet without any additional parameters.
  
```
Get-CsUserServicesConfiguration
```

### EXAMPLE 2

In Example 2, only one collection of User Services configuration settings is returned: the collection with the Identity site:Redmond. Because identities must be unique, this command can never return more than one item.
  
```
Get-CsUserServicesConfiguration -Identity site:Redmond
```

### EXAMPLE 3

Example 3 returns a collection of all the User Services configuration settings that have been applied at the service scope. This is done by calling the **Get-CsUserServicesConfiguration** cmdlet along with the -Filter parameter; the filter value "service:*" limits the returned data to settings where the Identity begins with the characters "service:". By definition, those are settings configured at the service scope.
  
```
Get-CsUserServicesConfiguration -Filter "service:*"
```

### EXAMPLE 4

Example 4 returns all the User Services configuration settings that allow users to have more than 250 contacts. To do this, the command first calls the **Get-CsUserServicesConfiguration** cmdlet without any additional parameters in order to return a collection of all the User Services configuration settings currently in use. That collection is then piped to the **Where-Object** cmdlet, which picks out only those settings where the MaxContacts property is greater than 250.
  
```
Get-CsUserServicesConfiguration | Where-Object {$_.MaxContacts -gt 250}
```

### EXAMPLE 5

In Example 5, information is reported for those User Services configuration settings where the anonymous user grace period is longer than 10 minutes. To carry out this task, the command first calls the **Get-CsUserServicesConfiguration** cmdlet without any additional parameters; this returns a collection of all the User Services configuration settings being used in the organization. The returned collection is then piped to the **Where-Object** cmdlet, which selects only the settings where the AnonymousUserGracePeriod property is greater than 10 minutes (00 hours: 10 minutes: 00 seconds).
  
```
Get-CsUserServicesConfiguration | Where-Object {$_.AnonymousUserGracePeriod -gt "00:10:00"}
```

## Detailed Description

Skype for Business Server 2015 relies on the User Services service to help maintain presence information for users and to manage meetings and conferences. In turn, the **CsUserServicesConfiguration** cmdlets are used to administer User Services settings at the global, site, and service scope. (Note that the only service that can host User Services configuration settings is the User Services itself.) These settings help determine such things as the number of contacts a user can have, the number of meetings a user can have scheduled at any one time, and the length of time that a given meeting can remain active.
  
The **Get-CsUserServicesConfiguration** cmdlet provides a way for administrators to retrieve information about any (or all) of the User Services configuration settings currently in use.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcards when retrieving one or more collections of User Services configuration settings. For example, to return all the settings configured at the site scope, use this syntax:  <br/>  `-Filter "site:*"` <br/> To return all the settings configured at the service scope, use this syntax:  <br/>  `-Filter "service:*"` <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the User Services configuration settings to be returned. To return the global settings, use this syntax:.  <br/>  `-Identity global` <br/> To return settings configured at the site scope, use syntax similar to this:  <br/>  `-Identity site:Redmond` <br/> To return settings at the service level, use syntax like this:  <br/>  `-Identity service:UserServer:atl-cs-001.litwareinc.com` <br/> If this parameter is omitted then the **Get-CsUserServicesConfiguration** cmdlet returns all the User Services configuration settings currently in use in your organization. <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the User Services configuration data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **Get-CsUserServicesConfiguration** cmdlet does not accept pipelined input.
  
## Return Types

The **Get-CsUserServicesConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.UserServicesSettings object.
  
## See also

#### 

[New-CsUserServicesConfiguration](new-csuserservicesconfiguration.md)
  
[Remove-CsUserServicesConfiguration](remove-csuserservicesconfiguration.md)
  
[Set-CsUserServicesConfiguration](set-csuserservicesconfiguration.md)

