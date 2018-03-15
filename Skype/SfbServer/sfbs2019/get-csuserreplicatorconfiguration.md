---
title: "Get-CsUserReplicatorConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 7318ae92-e07b-4817-9ec1-be9c7f35aa26
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsUserReplicatorConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Returns information about the User Replicator configuration settings currently employed in your organization. The User Replicator periodically retrieves up-to-date user account information from Active Directory and then synchronizes the new information with the current user data stored by Lync Server. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsUserReplicatorConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 returns information about all the User Replicator configuration settings currently in use in your organization.
  
```
Get-CsUserReplicatorConfiguration
```

## Detailed Description
<a name="sectionSection1"> </a>

Although Lync Server maintains its own database of user accounts and user account data, Lync Server still relies on Active Directory as the ultimate source for user information. For example, when a new Active Directory user account is created, you must supply basic information about the user account (such as the Active Directory display name). When a user is enabled for Lync Server, however, you do not need to specify a new display name for that user. That's because Lync Server uses the display name already stored in Active Directory Domain Services.
  
Of course, user account information (including the Active Directory display name) is subject to change over time. For example, a user who gets married might change her last name and, in turn, need to change her display name as well. In order to ensure that the Lync Server database and Active Directory remain in synch, Lync Server must periodically check in with Active Directory, retrieve the latest user account updates, and then modify its own user database accordingly. This synchronization between Active Directory and Lync Server is carried out by the User Replicator.
  
When you install Lync Server a global set of User Replicator configuration settings is created for you. By default, these settings are used to manage the User Replicator on an organization-wide basis. Management of the User Replicator consists of identifying the domains that Lync Server needs to synch with as well as indicating how often the User Replicator checks Active Directory for user account updates. By default, the User Replicator discovers and synchs with all available domains. However, by using the AdDomainNamingContextList property you can restrict synchronization to a specific set of domains: the domains that appear in the AdDomainNamingContextList property.
  
If you are working with Lync Server you can also use the CsUserReplicatorConfiguration cmdlets to create and manage configuration settings at the service scope. However, with the on-premises version of Lync Server you are limited to a single collection of configuration settings assigned to the global scope.
  
The **Get-CsUserReplicatorConfiguration** cmdlet enables administrators to return information about all the User Replicator settings currently employed in their organization. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsUserReplicatorConfiguration** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself) run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsUserReplicatorConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcards when specifying the collection (or collections) of User Replicator configuration settings to be returned. For example, this command returns all the settings configured at the service scope: -Filter "service:\*".  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier of the User Replicator configuration settings to be returned. To return settings at the service scope, use syntax similar to this: -Identity "service:Registrar:atl-cs-001.litwareinc.com". (Note that service scope settings are available only if you are running Skype for Business Online). To return the global settings, use this syntax: -Identity global. If this parameter is not specified then all the User Replicator configurations settings currently in use in your organization will be returned.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the User Replicator configuration data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Get-CsUserReplicatorConfiguration** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Get-CsUserReplicatorConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.UserReplicator.UserReplicatorConfiguration object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsUserReplicatorConfiguration](new-csuserreplicatorconfiguration.md)
  
[Remove-CsUserReplicatorConfiguration](remove-csuserreplicatorconfiguration.md)
  
[Set-CsUserReplicatorConfiguration](set-csuserreplicatorconfiguration.md)

