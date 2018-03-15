---
title: "Remove-CsConferencingPolicy"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8fe81ace-d167-414b-9455-8be7ddc0cab5
description: "Removes the specified conferencing policy. Conferencing policies determine the features and capabilities that can be used in a conference; this includes everything from whether or not the conference can include IP audio and video to the maximum number of people who can attend a meeting. This cmdlet was introduced in Lync Server 2010."
---

# Remove-CsConferencingPolicy
 
Removes the specified conferencing policy. Conferencing policies determine the features and capabilities that can be used in a conference; this includes everything from whether or not the conference can include IP audio and video to the maximum number of people who can attend a meeting. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsConferencingPolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

In Example 1, the **Remove-CsConferencingPolicy** cmdlet is used to delete the conferencing policy with the Identity SalesConferencingPolicy.
  
```
Remove-CsConferencingPolicy -Identity SalesConferencingPolicy
```

### EXAMPLE 2

In Example 2, all the conferencing policies that have been configured at the site scope are deleted. To accomplish this task, the command first uses the **Get-CsConferencingPolicy** cmdlet and the Filter parameter to return a collection of all the site-level policies; the filter value "site:*" ensures that only policies that have an Identity that begins with the string value "site" are returned. That filtered collection is then piped to the **Remove-CsConferencingPolicy** cmdlet, which deletes each item in the collection.
  
```
Get-CsConferencingPolicy -Filter "site:*" | Remove-CsConferencingPolicy
```

### EXAMPLE 3

In Example 3, all the policies that allow a maximum meeting size (MaxMeetingSize) of more than 100 people are deleted. To do this, the command first uses the **Get-CsConferencingPolicy** cmdlet to retrieve a collection of all the conferencing policies configured for use in the organization. That collection is then piped to the **Where-Object** cmdlet, which applies a filter that limits the returned data to those policies where the MaxMeetingSize value is greater than 100. Finally, that filtered collection is passed to the **Remove-CsConferencingPolicy** cmdlet, which deletes all the policies in the filtered collection.
  
```
Get-CsConferencingPolicy | Where-Object {$_.MaxMeetingSize -gt 100} | Remove-CsConferencingPolicy 
```

## Detailed Description

Conferencing is an important part of Skype for Business Server 2015: conferencing enables groups of users to come together online to view slides and video, share applications, exchange files, and otherwise communicate and collaborate. 
  
It's important for administrators to maintain control over conferences and conference settings. In some cases, there might be security concerns: by default, anyone, including unauthenticated users, can participate in meetings and save any of the slides or handouts distributed during those meetings. In other cases, there might be bandwidth concerns: having a multitude of simultaneous meetings, each involving hundreds of participants and each featuring video feeds and file sharing, has the potential to cause problems with your network. In addition, there might be legal concerns. For example, by default meeting participants are allowed to make annotations on shared content; however, these annotations are not saved when the meeting is archived. If your organization is required to keep a record of all electronic communication, you might want to disable annotations. 
  
Of course, needing to manage conferencing settings is one thing; actually managing these settings is another. In Skype for Business Server 2015, conferences are managed by using conferencing policies. (In previous versions of the software, these were known as meeting policies.) As noted, conferencing policies determine the features and capabilities that can be used in a conference, including everything from whether or not the conference can include IP audio and video to the maximum number of people who can attend a meeting. Conferencing policies can be configured at the global scope; at the site scope; or at the per-user scope. This provides administrators with enormous flexibility when it comes to deciding which capabilities will be made available to which users.
  
You can use the **Remove-CsConferencingPolicy** cmdlet to delete any of the conferencing policies configured for use in your organization, with one exception: you cannot delete the global policy. You can still run the **Remove-CsConferencingPolicy** cmdlet against the global policy. In that case, however the policy will not be removed; instead, all the global policy properties will be reset to their default values.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the conferencing policy to be removed. Conferencing policies can be configured at the global, site, or per-user scopes. To remove the global policy, use this syntax: -Identity global. (Note that the global policy cannot actually be removed. Instead, all the policy properties will be reset to their default values.) To remove a site policy, use syntax similar to this:  `-Identity site:Redmond`. To remove a per-user policy, use syntax similar to this:  `-Identity SalesConferencingPolicy`.  <br/> Wildcards are not allowed when specifying an Identity.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |If present, causes the **Remove-CsConferencingPolicy** cmdlet to delete the per-user policy even if the policy in question is currently assigned to at least one user. If not present, you will be asked to confirm the deletion request before the policy will be removed. <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account for whom the conferencing policy is being removed. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your Skype for Business Online tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Policy.Meeting.MeetingPolicy object. The **Remove-CsConferencingPolicy** cmdlet accepts pipelined instances of the meeting policy object.
  
## Return Types

The **Remove-CsConferencingPolicy** cmdlet does not return a value or object. Instead, the cmdlet deletes instances of the Microsoft.Rtc.Management.WritableConfig.Policy.Meeting.MeetingPolicy object.
  
## See also

#### 

[Get-CsConferencingPolicy](get-csconferencingpolicy.md)
  
[Grant-CsConferencingPolicy](grant-csconferencingpolicy.md)
  
[New-CsConferencingPolicy](new-csconferencingpolicy.md)
  
[Set-CsConferencingPolicy](set-csconferencingpolicy.md)

