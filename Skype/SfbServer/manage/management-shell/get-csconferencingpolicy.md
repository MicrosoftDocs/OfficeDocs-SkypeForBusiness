---
title: "Get-CsConferencingPolicy"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 21dc4774-2306-4425-a561-71e0b293f8df
description: "Returns information about the conferencing policies that have been configured for use in your organization. Conferencing policies determine the features and capabilities that can be used in a conference; this includes everything from whether or not the conference can include IP audio and video to the maximum number of people who can attend a meeting. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsConferencingPolicy
 
Returns information about the conferencing policies that have been configured for use in your organization. Conferencing policies determine the features and capabilities that can be used in a conference; this includes everything from whether or not the conference can include IP audio and video to the maximum number of people who can attend a meeting. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsConferencingPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

The first example returns a collection of all the conferencing policies configured for use in your organization.
  
```
Get-CsConferencingPolicy
```

### EXAMPLE 2

In Example 2, the Identity parameter is used to limit the retrieved information to conferencing policies that have an identity equal to Global. Because policy Identities must be unique, this command returns a single policy: the Global conferencing policy.
  
```
Get-CsConferencingPolicy -Identity Global
```

### EXAMPLE 3

Example 3 uses the Filter parameter to return a collection of all the conferencing policies that have been configured at the per-user scope. The wildcard value "tag:\*" tells Windows PowerShell to limit the returned data to conferencing policies that have an identity beginning with the string value "tag:". 
  
```
Get-CsConferencingPolicy -Filter tag:*
```

### EXAMPLE 4

Example 4 returns a collection of all the conferencing policies where the MaxMeetingSize property is greater than 100. The command starts out by using the **Get-CsConferencingPolicy** cmdlet to return a collection of all the conferencing policies configured for use in the organization. That collection is then piped to the **Where-Object** cmdlet, which applies a filter that limits the returned data to policies where the MaxMeetingSize property is greater than 100.
  
```
Get-CsConferencingPolicy | Where-Object {$_.MaxMeetingSize -gt 100}
```

### EXAMPLE 5

Example 5 returns all the conferencing policies that meet two criteria: the AllowExternalUsersToSaveContent property is equal to True and the AllowExternalUserControl property is also equal to True. To do this, the command calls the **Get-CsConferencingPolicy** cmdlet without any additional parameters; this returns a collection of all the conferencing policies configured for use in the organization. That collection is then piped to the **Where-Object** cmdlet, which picks out only those policies where both AllowExternalUsersToSaveContent and AllowExternalUserControl are True. The -and operator tells the **Where-Object** cmdlet that an object must meet all the specified criteria in order to be returned.
  
```
Get-CsConferencingPolicy | Where-Object {$_.AllowExternalUsersToSaveContent -eq $True -and $_.AllowExternalUserControl -eq $True}
```

### EXAMPLE 6

Example 6 is a variation of the command shown in Example 5. In this case, the command returns any policy that meets at least one (but not necessarily both) of the specified criteria: either the AllowExternalUsersToSaveContent property is equal to True and/or the AllowExternalUserControl property is equal to True. To do this, the command calls the **Get-CsConferencingPolicy** cmdlet without any additional parameters; this returns a collection of all the conferencing policies configured for use in the organization. That collection is then piped to the **Where-Object** cmdlet, which picks out only those policies where either AllowExternalUsersToSaveContent and/or AllowExternalUserControl are equal to True. The -or operator tells the **Where-Object** cmdlet that an object must meet just one of the specified criteria in order to be returned.
  
```
Get-CsConferencingPolicy | Where-Object {$_.AllowExternalUsersToSaveContent -eq $True -or $_.AllowExternalUserControl -eq $True}
```

## Detailed Description

Conferencing is an important part of Skype for Business Server 2015: conferencing enables groups of users to come together online to view slides and video, share applications, exchange files, and otherwise communicate and collaborate. 
  
It's important for administrators to maintain control over conferences and conference settings. In some cases, there might be security concerns: by default, anyone, including unauthenticated users, can participate in meetings and save any of the slides or handouts distributed during those meetings. In other cases, there might be bandwidth concerns: having a multitude of simultaneous meetings, each involving hundreds of participants and each featuring video feeds and file sharing, has the potential cause problems with your network. In addition, there might be occasional legal concerns. For example, by default meeting participants are allowed to make annotations on shared content; however, these annotations are not saved when the meeting is archived. If your organization is required to keep a record of all electronic communication, you might want to disable annotations. 
  
Of course, needing to manage conferencing settings is one thing; actually managing these settings is another. In Skype for Business Server 2015, conferences are managed by using conferencing policies. (In previous versions of the software, these were known as meeting policies.) As noted, conferencing policies determine the features and capabilities that can be used in a conference, including everything from whether or not the conference can include IP audio and video to the maximum number of people who can attend a meeting. Conferencing policies can be configured at the global scope; at the site scope; or at the per-user scope. This provides administrators with enormous flexibility when it comes to deciding which capabilities will be made available to which users.
  
The **Get-CsConferencingPolicy** cmdlet provides a way for you to return information about all the conferencing policies that have been configured for use in your organization.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard characters when specifying the conferencing policy (or policies) to be returned. For example, this syntax returns all the policies configured at the site scope,  `-Filter site:*`. To return a collection of all the policies configured at the per-user scope, use this syntax,  `-Filter tag:*`.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the conferencing policy to be retrieved. Conferencing policies can be configured at the global, site, or per-user scopes. To retrieve the global policy, use this syntax:  `-Identity global`. To retrieve a site policy, use syntax similar to this:  `-Identity site:Redmond`. To retrieve a per-user policy use syntax similar to this:  `-Identity SalesConferencingPolicy`.  <br/> If this parameter is not included, the **Get-CsConferencingPolicy** cmdlet will return a collection of all the conferencing policies configured for use in your organization. <br/> Note that wildcards are not allowed when specifying an Identity. Use the Filter parameter if you need to use wildcards when specifying a conferencing policy.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the conferencing policy data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |PARAMVALUE: Guid  <br/> |
   
## Input Types

None. The **Get-CsConferencingPolicy** cmdlet does not accept pipelined input.
  
## Return Types

The **Get-CsConferencingPolicy** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Meeting.MeetingPolicy object.
  
## See also

#### 

[Grant-CsConferencingPolicy](grant-csconferencingpolicy.md)
  
[New-CsConferencingPolicy](new-csconferencingpolicy.md)
  
[Remove-CsConferencingPolicy](remove-csconferencingpolicy.md)
  
[Set-CsConferencingPolicy](set-csconferencingpolicy.md)

