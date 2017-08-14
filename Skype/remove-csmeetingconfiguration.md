---
title: Remove-CsMeetingConfiguration
ms.prod: SKYPEFORBUSINESS
ms.assetid: a5d4c758-25f6-4cdb-a5b7-dbb0fb1d8488
---


# Remove-CsMeetingConfiguration
[]
The **Remove-CsMeetingConfiguration** cmdlet enables you to delete an existing collection of meeting configuration settings. Meeting configuration settings help dictate the type of meetings (also called "conferences") that users can create, as well as control how (or even if) anonymous users and dial-in conferencing users can join these meetings. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Remove-CsMeetingConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

In Example 1, the meeting configuration settings that have the Identity site:Redmond are removed. When these settings are removed from the Redmond site users in that site will automatically inherit the global meeting configuration settings.
  
    
    

```

Remove-CsMeetingConfiguration -Identity site:Redmond
```


### EXAMPLE 2

The command shown in Example 2 removes all the meeting settings that have been configured at the site scope. To do this, the command first calls the **Get-CsMeetingConfiguration** cmdlet along with the Filter parameter; the filter value "site:*" ensures that only settings that have an Identity that begins with the characters "site:" are selected. This filtered collection is then piped to the **Remove-CsMeetingConfiguration** cmdlet, which deletes each item in the collection.
  
    
    

```
Get-CsMeetingConfiguration -Filter "site:*" | Remove-CsMeetingConfiguration
```


### EXAMPLE 3

Example 3 deletes each collection of meeting configuration settings where the AdmitAnonymousUsersByDefault property is True. To carry out this task, the command first calls the **Get-CsMeetingConfiguration** cmdlet in order to return a collection of all the meeting configuration settings currently in use. This collection is then piped to the **Where-Object** cmdlet, which picks out only those settings where the AdmitAnonymousUsersByDefault property is equal to True. The filtered collection is then piped to the **Remove-CsMeetingConfiguration** cmdlet, which proceeds to remove each item in that collection.
  
    
    

```
Get-CsMeetingConfiguration | Where-Object {$_.AdmitAnonymousUsersByDefault -eq $True} | Remove-CsMeetingConfiguration
```


## Detailed Description

Online meetings (also called conferences) are an integral part of Skype for Business Server 2015. The **CsMeetingConfiguration** cmdlets enable administrators to control the type of meetings that users can create as well as determine how meetings deal with anonymous users and dial-in conferencing users. For example, you can configure meetings so that anyone dialing in over the public switched telephone network (PSTN) is automatically admitted to the meeting. Alternatively, you can configure meetings so that dial-in users are not automatically admitted the meeting, but are instead routed to the meeting lobby. These dial-in users remain on hold in the lobby until a presenter admits them to the meeting.
  
    
    
Meeting configuration settings can be assigned to the global, site, or service scopes. If you create new settings at the site or service scope, those settings can later be removed by using the **Remove-CsMeetingConfiguration** cmdlet. The **Remove-CsMeetingConfiguration** cmdlet can also be run against the global meeting settings. In that case, however, the settings will not be removed; that's because the global settings cannot be removed. Instead, all the properties in the global collection will be reset to their default values.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier of the meeting configuration settings to be removed. To "remove" the global settings, use this syntax: -Identity global. (As noted previously, you cannot actually remove the global settings; all you can do is reset the properties to their default values.) To remove settings from the site scope, use syntax similar to this:  `-Identity site:Redmond`. Service settings can be removed using this syntax:  `-Identity service:UserServer:atl-cs-001.litwareinc.com`.  <br/> Note that you cannot use wildcards when specifying an Identity.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account for the meeting configuration settings being deleted. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.MeetingConfiguration object. The **Remove-CsMeetingConfiguration** cmdlet accepts pipelined instances of the meeting configuration object.
  
    
    

## Return Types

None. Instead, the **Remove-CsMeetingConfiguration** cmdlet deletes existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.MeetingConfiguration object.
  
    
    

## See also


#### 


  
    
    
 [Get-CsMeetingConfiguration](get-csmeetingconfiguration.md)
  
    
    
 [New-CsMeetingConfiguration](new-csmeetingconfiguration.md)
  
    
    
 [Set-CsMeetingConfiguration](set-csmeetingconfiguration.md)
