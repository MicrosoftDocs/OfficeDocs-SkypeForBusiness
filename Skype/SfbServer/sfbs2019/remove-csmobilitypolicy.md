---
title: "Remove-CsMobilityPolicy"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d3dc4653-25ab-45ef-b325-fba01e45acca
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsMobilityPolicy
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Removes an existing mobility policy. Mobility policies determine whether or not a user can use Call via Work, a feature that enables users to make and receive phone calls on their mobile phone by using their work phone number instead of their mobile phone number. Mobility policies can also be used to require Wi-Fi connections when making or receiving calls. This cmdlet was introduced in the cumulative update for Lync Server 2010: November 2011.
  
```
Remove-CsMobilityPolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 removes the mobility policy configured for the Redmond site. When the policy is removed, users previously managed by the Redmond site policy will now be managed by the global policy.
  
```
Remove-CsMobilityPolicy -Identity "site:Redmond"

```

### EXAMPLE 2

In Example 2, all the mobility policies configured at the per-user scope are removed. To do this, the command first uses the **Get-CsMobilityPolicy** cmdlet and the Filter parameter to retrieve all the policies that have an Identity that begins with the string value "Tag:"; by definition, any policy meeting that criterion will be a per-user policy. That collection of per-user policies is then piped to the **Remove-CsMobilityPolicy** cmdlet, which deletes each policy in the collection. 
  
```
Get-CsMobilityPolicy -Filter "tag:*" | Remove-CsMobilityPolicy

```

### EXAMPLE 3

Example 3 demonstrates a way to delete all the mobility policies where Call via Work has been enabled. To do this, the command first uses the **Get-CsMobilityPolicy** cmdlet to retrieve a collection of all the mobility policies currently in use in the organization. That collection is then piped to the where-Object cmdlet, which picks out only those policies where the EnableOutsideVoice property is set to False. Any policies where EnableOutsideVoice is False are then piped to, and removed by, the **Remove-CsMobilityPolicy** cmdlet. 
  
```
Get-CsMobilityPolicy | Where-Object {$_.EnableOutsideVoice -eq $False} | Remove-CsMobilityPolicy

```

## Detailed Description
<a name="sectionSection1"> </a>

Lync Mobile is a client application that enables users to run Lync on their mobile phones. Call via Work provides a way for users to make calls on their mobile phone and yet have it appear as though the call originated from their work phone number instead of their mobile phone number. Users who have been enabled for Call via Work can achieve this either by dialing directly from their mobile phone or by using the dial-out conferencing option. With dial-out conferencing, a user effectively asks the Mobility Service server to make a call for them. The server will set up the call, and then call the user back on their mobile phone. After the user has answered, the server will then dial the party being called. Both of these capabilities can be managed by using mobility policies.
  
With Lync Server 2013 mobile devices can make or receive phone calls by using either the standard cellular phone network. or by using Wi-Fi connections. Mobility policies can be used to require Wi-Fi connections and prevent calls over the cellular network.
  
When you install Lync Server, you will have a single, global mobility policy that applies to all your users. However, administrators can use the **New-CsMobilityPolicy** cmdlet to create custom policies at either the site or the per-user scope. 
  
If you do create custom policies at either the site or the per-user scope you can later delete those policies by using the **Remove-CsMobilityPolicy** cmdlet. If you delete a per-user policy, then any users assigned that policy will be managed by the appropriate site policy (if one exists) or by the global policy. If you remove a site policy, users governed by that policy will then be managed by the global policy. 
  
Note that you can also run the **Remove-CsMobilityPolicy** cmdlet against the global policy. If you do that, however, the global policy will not actually be deleted; instead, the properties in that policy will be reset to their default values. In this case, that means enabling Call via Work. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsMobilityPolicy** cmdlet locally: RTCUniversalServerAdmins. 
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the client policy to be removed. To "remove" the global policy, use the following syntax:  <br/> -Identity global  <br/> Note, however, that the global policy cannot actually be removed. Instead, all the properties in that policy will be reset to their default values.  <br/> To remove a site policy, use syntax similar to this:  <br/> -Identity "site:Redmond"  <br/> To remove a per-user policy, use syntax similar to this:  <br/> -Identity "SalesDepartmentPolicy"  <br/> You cannot use wildcards when specifying a policy Identity.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |If this parameter is present, the policy will be removed even if it is currently assigned to at least one user. If this parameter is not present, then the **Remove-CsMobilityPolicy** cmdlet will not automatically remove a per-user policy that is assigned to at least one user. Instead, a confirmation prompt will appear asking if you are sure that you want to remove the policy. You must answer yes (by pressing the Y key) before the command will continue and the policy is removed.  <br/> This parameter applies only to per-user policies.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.WriteableConfig.Policy.Mobility.Mobility. The **Remove-CsMobilityPolicy** cmdlet accepts pipelined instances of the Mobility object. 
  
## Return Types
<a name="sectionSection3"> </a>

None. Instead, the **Remove-CsMobilityPolicy** cmdlet deletes instances of the Microsoft.Rtc.Management.WriteableConfig.Policy.Mobility.Mobility object. 
  

