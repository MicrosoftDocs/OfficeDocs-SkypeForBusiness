---
title: "New-CsUserReplicatorConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: eb4dee9e-9ba4-4726-8f7c-b355433ed594
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# New-CsUserReplicatorConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Creates a new collection of User Replicator configuration settings. The User Replicator periodically retrieves up-to-date user account information from Active Directory and then synchronizes the new information with the current user data stored by Lync Server. This cmdlet is designed for use with Skype for Business Online and will not work with the on-premises version of Lync Server.
  
```
New-CsUserReplicatorConfiguration -Identity <XdsIdentity> [-ADDomainNamingContextList <PSListModifier>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-ReplicationCycleInterval <TimeSpan>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 creates a new collection of User Replicator configuration settings for the service Registrar:atl-cs-001.litwareinc.com. Because no additional parameters are specified, the new collection will use the default user replicator values. 
  
```
New-CsUserReplicatorConfiguration -Identity "service:Registrar:atl-cs-001.litwareinc.com"
```

### EXAMPLE 2

Example 2 also creates a new collection of user replicator configuration settings for the service Registrar:atl-cs-001.litwareinc.com. In this case, however, the ADDomainNamingContextList is added, along with the distinguished names of the two domains to synchronize with: fabrikam.com and contoso.com. This new collection of user replicator configuration settings will only configure with those two domains, even if other domains are available.
  
```
New-CsUserReplicatorConfiguration -Identity "service:Registrar:atl-cs-001.litwareinc.com" -ADDomaiNamingContextList @{Add="dc=fabrikam,dc=com","dc=contoso.com"}
```

## Detailed Description
<a name="sectionSection1"> </a>

Although Lync Server maintains its own database of user accounts and user account data, Lync Server still relies on Active Directory as the ultimate source for user information. For example, when a new Active Directory user account is created, you must supply basic information about the user account (such as the Active Directory display name). When a user is enabled for Lync Server, however, you do not need to specify a new display name. That's because Lync Server uses the display name already stored in Active Directory.
  
User account information, including the Active Directory display name, is subject to change over time. For example, a user who gets married might change her last name and, in turn, need to change her display name as well. In order to ensure that the Lync Server database and Active Directory remain in synch, Lync Server must periodically check in with Active Directory, retrieve the latest user account updates, and then modify the Lync Server user database accordingly. This synchronization between Active Directory and Lync Server is carried out by the User Replicator.
  
When you install Lync Server a global set of User Replicator configuration settings is created for you. By default, these settings are used to manage the User Replicator on an organization-wide basis. Management of the User Replicator consists of identifying the domains that Lync Server needs to synch with as well as indicating how often the User Replicator checks Active Directory for user account updates. You can also create additional collections at the service scope, but only if you are working with Skype for Business Online.
  
New User Replicator configurations settings are created using the **New-CsUserReplicatorConfiguration** cmdlet. Note that these settings can only be created at the service scope and only for Skype for Business Online. You cannot create new User Replicator settings for the on-premises version of Lync Server. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsUserReplicatorConfiguration** cmdlet: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself) run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "New-CsUserReplicatorConfiguration"}
  
```

```

## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier of the User Replicator configuration settings to be created. Settings can only be created at the service scope, and only for the Registrar service. That means that new settings must have an Identity similar to this: -Identity "service:Registrar:atl-cs-001.litwareinc.com".  <br/> Note that this applies only to Lync Server.  <br/> |
| _ADDomainNamingContextList_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Distinguished names of the Active Directory domains that the User Replicator must synchronize with. For example, to add a domain to the list use syntax similar to this:  <br/> -ADDomainNamingContextList @{Add="dc=fabrikam,dc=com"}  <br/> You can add more than one domain name when calling the **New-CsUserReplicatorConfiguration** cmdlet. To do this, simply separate the domain names by using a comma:  <br/> -ADDomainNamingContextList @{Add="dc=fabrikam,dc=com","dc=contoso,dc=com"}  <br/> If you set this property to a null value the user replicator will discover and synchronize with all available domains. If this property is not null then the replicator will only synchronize with the domains specified in the ADDomainNamingContextList.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching Set- cmdlet.  <br/> |
| _ReplicationCycleInterval_ <br/> |Optional  <br/> |System.TimeSpan  <br/> |Represents the amount of time that the User Replicator waits before checking for user account updates in Active Directory. The replication cycle interval can be any time value between 1 second, and 23 hours, 59 minutes, and 59 seconds; the default value is 1 minute. The interval must be expressed using the format hours:minutes:seconds. For example, this syntax sets to time interval to one hour and 15 minutes: -ReplicationCycleInterval 01:15:00.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **New-CsUserReplicatorConfiguration** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **New-CsUserReplicatorConfiguration** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.UserReplicator.UserReplicatorConfiguration object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsUserReplicatorConfiguration](get-csuserreplicatorconfiguration.md)
  
[Remove-CsUserReplicatorConfiguration](remove-csuserreplicatorconfiguration.md)
  
[Set-CsUserReplicatorConfiguration](set-csuserreplicatorconfiguration.md)

