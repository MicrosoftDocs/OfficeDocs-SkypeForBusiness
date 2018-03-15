---
title: "Set-CsAdminRole"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ec927ce6-a37b-4876-a6df-a347404f4e84
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsAdminRole
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Modifies an existing role-based access control (RBAC) role. RBAC roles are used to specify the management tasks that users are allowed to carry out, and to determine the scope in which users will be allowed to perform these tasks. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsAdminRole -Identity <String> [-Cmdlets <PSListModifier>] [-ConfigScopes <PSListModifier>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-ScriptModules <PSListModifier>] [-UserScopes <PSListModifier>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

Example 1 adds a new OU (Portland) to the UserScopes property for the RBAC role RedmondVoiceAdministrators. To do this, the command includes the UserScopes parameter and the following parameter value: @{Add="OU:ou=Portland,dc=litwareinc,dc=com"}. This syntax adds the OU with the distinguished name "ou=Portland,dc=litwareinc,dc=com" to the OUs already in the UserScopes property.
  
```
Set-CsAdminRole -Identity "RedmondVoiceAdministrators" -UserScopes @{Add="OU:ou=Portland,dc=litwareinc,dc=com"}
```

### EXAMPLE 2

The command shown in Example 2 removes the Portland OU from the RBAC role RedmondVoiceAdministrators. To do this, the command includes the UserScopes parameter and the following parameter value: @{Remove="OU:ou=Portland,dc=litwareinc,dc=com"}. This syntax deletes the OU with the distinguished name "ou=Portland,dc=litwareinc,dc=com" from the collection of OUs already in the UserScopes property.
  
```
Set-CsAdminRole -Identity "RedmondVoiceAdministrators" -UserScopes @{Remove="OU:ou=Portland,dc=litwareinc,dc=com"}
```

### EXAMPLE 3

In Example 3, a new site (one with the SiteId Redmond) is added to the ConfigScopes property for the RBAC role RedmondVoiceAdministrators. To do this, the command includes the ConfigScopes parameter and the following parameter value: @{Add="OU:ou=Portland,dc=litwareinc,dc=com"}. This syntax adds the Redmond site to any items already in the ConfigScopes property.
  
```
Set-CsAdminRole -Identity "RedmondVoiceAdministrators" -ConfigScopes @{Add="site:Redmond"}
```

### EXAMPLE 4

The command shown in Example 4 removes the Redmond site from the RBAC role RedmondVoiceAdministrators. To do this, the command includes the ConfigScopes parameter and the following parameter value: @{Remove="site:Redmond"}. This parameter deletes the Redmond site from the collection of items already in the ConfigScopes property. Note that this command will fail if the Redmond site is the only site in the ConfigScopes property. If you are removing the only site in the ConfigScopes property you should use a command similar to this, which replaces all the items in ConfigScopes with the Global property:
  
Set-CsAdminRole -Identity "RedmondVoiceAdministrators" -ConfigScopes @{Replace="Global"}
  
```
Set-CsAdminRole -Identity "RedmondVoiceAdministrators" -ConfigScopes @{Remove="siteRedmond"}
```

## Detailed Description
<a name="sectionSection1"> </a>

RBAC enables administrators to delegate control of specific management tasks in Lync Server. For example, instead of granting your organization's help desk full administrator privileges you can give these employees very specific rights: the right to manage only user accounts; the right to manage only Enterprise Voice components; the right to manage only archiving and Archiving Server. In addition, these rights can be limited in scope: someone can be given the right to manage Enterprise Voice, but only in the Redmond site; someone else can be given the right to manage users, but only if those user accounts are in the Finance organizational unit (OU).
  
The Lync Server implementation of RBAC is based on two key elements: Active Directory security groups and Windows PowerShell cmdlets. When you install Lync Server, a number of universal security groups, such as CsAdministrator, CsArchivingAdministrator, and CsViewOnlyAdministrator, are created for you. These universal security groups have a one-to-one correspondence with RBAC roles, which means that any user who is in the CsArchivingAdministrator security group has all the rights granted to the CsArchivingAdministrator RBAC role. In turn, the rights granted to an RBAC role are based on the cmdlets assigned to that role (cmdlets can be assigned to multiple RBAC roles). For example, suppose a role has been assigned the following cmdlets:
  
Get-ArchivingPolicy
  
Grant-ArchivingPolicy
  
New-ArchivingPolicy
  
Remove-ArchivingPolicy
  
Set-ArchivingPolicy
  
Get-ArchivingConfiguration
  
New-ArchivingConfiguration
  
Remove-ArchivingConfiguration
  
Set-ArchivingConfiguration
  
Get-CsUser
  
Export-CsArchivingData
  
Get-CsComputer
  
Get-CsPool
  
Get-CsService
  
Get-CsSite
  
The preceding list represents the only cmdlets that a user assigned a hypothetical RBAC role is allowed to run in a remote Windows PowerShell command-line interface session. If the user tries to run the **Disable-CsUser** cmdlet, that command will fail because users assigned the hypothetical role do not have the right to run the **Disable-CsUser** cmdlet. This also applies to Lync Server Control Panel. For example, an Archiving Administrator cannot disable a user by using Lync Server Control Panel because Lync Server Control Panel abides by RBAC roles. (Any time you run a command in Lync Server Control Panel, you are actually calling a Windows PowerShell cmdlet.) If you are not allowed to run the **Disable-CsUser** cmdlet, it won't matter whether you directly run that cmdlet from Windows PowerShell or if you indirectly run the cmdlet from within Lync Server Control Panel: the command will fail. 
  
Note that RBAC applies only to remote management. If you are logged on to a computer running Lync Server and you open Lync Server Management Shell, RBAC roles will not be enforced. Instead, security is enforced primarily through the security groups RTCUniversalServerAdmins; RTCUniversalUserAdmins; and RTCUniversalReadOnlyAdmins.
  
When you install Lync Server, Setup creates several built-in RBAC roles that cover common administrative areas such as voice administration, user management, and Response Group administration. These built-in roles cannot be modified in any way: you cannot add or remove cmdlets to the roles and you cannot delete these roles. (Any attempt to delete a built-in role will result in an error message.) However, you can use the built-in roles to create custom RBAC roles. These custom roles can then be modified by changing the administrative scopes; for example, you can limit the role to managing user accounts in a particular Active Directory OU.
  
Any custom role you create must be based on a template: an existing RBAC role. For example, to create a Dial-In Conferencing Administrator role you must effectively clone an existing RBAC role (for example, you might base the Dial-In Conferencing Administrator role on the existing Voice Administrator role). After the custom role has been created, you can then use the **Set-CsAdminRole** cmdlet to modify the properties of that new role. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsAdminRole cmdlet** locally: RTCUniversalServerAdmins. To return a list of all the RBAC roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself) run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsAdminRole"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |System.String  <br/> |Unique identifier for the RBAC role to be modified. The Identity for an RBAC role must be the same as the SamAccountName for the Active Directory universal security group associated with that role. For example, the help desk role has an Identity equal to CsHelpDesk; CsHelpDesk is also the SamAccountName of the Active Directory security group associated with that role.  <br/> |
| _Cmdlets_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Enables you to specify the cmdlets that will be available to users who hold the RBAC role. For example, to provide access to just one cmdlet (the **Export-CsArchivingData** cmdlet) use syntax like this:  <br/> -Cmdlets "Export-CsArchivingData"  <br/> The preceding syntax replaces all the items currently stored in the Cmdlets property with the single item Export-CsArchivingData. If you want to add the **Export-CsArchivingData** cmdlet to the cmdlets already stored in that property, use this syntax instead:  <br/> -Cmdlets @{Add="Export-CsArchivingData"}  <br/> Multiple cmdlets can be added by separated the cmdlet names using commas:  <br/> -Cmdlets @{Add="Export-CsArchivingData","Invoke-CsArchivingDatabasePurge"}  <br/> To remove a cmdlet from a role, use this syntax:  <br/> -Cmdlets @{Remove="Export-CsArchivingData"}  <br/> |
| _ConfigScopes_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Limits the scope of the cmdlet to configuration settings within the specified site. To limit the cmdlet scope to a single site, use syntax similar to this: -ConfigScopes site:Redmond. Multiple sites can be specified by using a comma-separated list: -ConfigScopes "site:Redmond, "site:Dublin". You can also set the ConfigScopes property to "global".  <br/> When assigning a value to the ConfigScopes parameter you must use the "site:" prefix followed by the value of the site's SiteId property; the SiteId is not necessarily the same value as the site's Identity or the site's DisplayName. To determine the SiteId for a given site you can use a command similar to this:  <br/> Get-CsSite "Redmond" | Select-Object SiteId  <br/> You must specify a value for either (or both) the ConfigScopes and UserScopes properties.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _ScriptModules_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Enables you to specify a function within a Windows PowerShell script that will then be available to users who hold the new RBAC role. For example, this syntax provides access to a function named Reset in a script named UpdateDatabase.ps1 :  <br/> -ScriptCmdlets "UpdateDatabase.ps1:Reset"  <br/> The preceding command replaces any scripts currently stored in the ScriptCmdlets property with the Reset function and the UpdateDatabase.ps1 script. To add this script/function to items currently stored in the ScriptCmdlets property use this syntax:  <br/> -ScriptCmdlets @{Add="UpdateDatabase.ps1:Reset"}  <br/> To remove a script/function use this syntax:  <br/> -ScriptCmdlets @{Add="UpdateDatabase.ps1:Reset"}  <br/> You can delete all the ScriptCmdlets assigned to a role by using this syntax:  <br/> -ScriptCmdlets $Null  <br/> |
| _UserScopes_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Limits the scope of the cmdlet to user management activities within the specified OU. To limit the cmdlet scope to a single OU, use syntax similar to this: -UserScopes "OU:ou=Redmond,dc=litwareinc,dc=com". Multiple OUs can be specified by using a comma-separated list: -UserScopes "OU:ou=Redmond,dc=litwareinc,dc=com", "OU:ou=Dublin,dc=litwareinc,dc=com". To add new scopes (or remove existing scopes) from a role, use the Windows PowerShell list modifiers syntax. For details, see the Examples section in this Help topic.  <br/> You must specify a value for either (or both) the ConfigScopes and UserScopes properties.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None.
  
## Return Types
<a name="sectionSection3"> </a>

The **Set-CsAdminRole** cmdlet does not return a value or object. Instead, the cmdlet configures instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Roles.Role object. 
  

