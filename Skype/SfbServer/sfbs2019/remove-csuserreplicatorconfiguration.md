---
title: "Remove-CsUserReplicatorConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 26c3a357-558f-406f-8df3-059911f771f0
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsUserReplicatorConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Removes the specified collection of User Replicator configuration settings. The User Replicator periodically retrieves up-to-date user account information from Active Directory and then synchronizes the new information with the current user data stored by Lync Server. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsUserReplicatorConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

Example 1 resets the global User Replicator configuration settings.
  
```
Remove-CsUserReplicatorConfiguration -Identity global
```

## Detailed Description
<a name="sectionSection1"> </a>

Although Lync Server maintains its own database of user accounts and user account data, Lync Server still relies on Active Directory as the ultimate source for user information. For example, when a new Active Directory user account is created, you must supply basic information about the user account (such as the Active Directory display name). However, when a user is enabled for Lync Server you do not need to specify a new display name. That's because Lync Server uses the display name already stored in Active Directory.
  
Of course, user account information, including the Active Directory display name, is subject to change over time. For example, a user who gets married might change her last name and, in turn, need to change her display name as well. In order to ensure that the Lync Server database and Active Directory remain in synch, Lync Server must periodically connect to Active Directory, retrieve the latest user account updates, and then modify the Lync Server user database accordingly. This synchronization between Active Directory and Lync Server is carried out by the User Replicator.
  
When you install Lync Server a global set of User Replicator configuration settings is created for you. By default, these settings are used to manage the User Replicator on an organization-wide basis. Management of the User Replicator consists of identifying the domains that Lync Server needs to synch with and indicating how often the User Replicator checks Active Directory for user account updates. By default, the User Replicator discovers and synchs with all available domains. However, by using the AdDomainNamingContextList property you can restrict synchronization to a specific set of domains: the domains that appear in the AdDomainNamingContextList property. 
  
You can also create additional collections at the service scope, but only if you are working with Skype for Business Online.
  
If your needs change, you can use the **Remove-CsUserReplicatorConfiguration** cmdlet to remove the custom settings created at the service scope. Note that you can also run this cmdlet against the global configuration settings. In that case, however, the global settings will not be removed. Instead, all the properties within the global collection will be reset to their default values. In the case of the User Replicator, that means erasing the list of domains that must be synchronized with (thus causing the replicator to synch with all discoverable domains), and setting the replication interval cycle to 1 minute. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsUserReplicatorConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself) run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsUserReplicatorConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier of the User Replicator configuration settings to be removed. To remove settings at the service scope, use syntax similar to this: -Identity "service:Registrar:atl-cs-001.litwareinc.com". (Note that you can only remove service-scoped setting if you are using Skype for Business Online). To reset the global settings, use this syntax: -Identity global. You cannot use wildcards when specifying an Identity.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.WritableConfig.Settings.UserReplicator.UserReplicatorConfiguration object. The **Remove-CsUserReplicatorConfiguration** cmdlet accepts pipelined input of the User Replicator configuration object. 
  
## Return Types
<a name="sectionSection3"> </a>

None. Instead, the **Remove-CsUserReplicatorConfiguration** cmdlet deletes instances of the Microsoft.Rtc.Management.WritableConfig.Settings.UserReplicator.UserReplicatorConfiguration object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsUserReplicatorConfiguration](get-csuserreplicatorconfiguration.md)
  
[New-CsUserReplicatorConfiguration](new-csuserreplicatorconfiguration.md)
  
[Set-CsUserReplicatorConfiguration](set-csuserreplicatorconfiguration.md)

