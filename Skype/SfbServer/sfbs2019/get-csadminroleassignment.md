---
title: "Get-CsAdminRoleAssignment"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 61374f9b-e85a-4866-91f2-037a862ba0d6
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsAdminRoleAssignment
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Returns the role-based access control (RBAC) roles assigned to a user. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsAdminRoleAssignment -Identity <String> [-Force <SwitchParameter>] [-LocalStore <SwitchParameter>]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 returns all of the RBAC roles assigned to the user kenmyer.
  
```
Get-CsAdminRoleAssignment -Identity "kenmyer"
```

### EXAMPLE 2

Example 2 returns the RBAC roles for all of the users who have been enabled for Lync Server. To do this, the command begins by calling the **Get-CsUser** cmdlet without any parameters; that returns a collection of all the users in the organization who have been enabled for Lync Server or Office Communications Server. This data is then piped to the **ForEach-Object** cmdlet, which loops through each user account in the collection and does the following: 1) echoes the user's display name to the screen; and 2) uses the **Get-CsAdminRoleAssignment** cmdlet to return the user's RBAC roles. The user account information must be piped to the **ForEach-Object** cmdlet because the **Get-CsAdminRoleAssignment** cmdlet does not directly accept pipelined data. 
  
```
Get-CsUser | ForEach-Object {$_.DisplayName; Get-CsAdminRoleAssignment -Identity $_.SamAccountName}
```

## Detailed Description
<a name="sectionSection1"> </a>

Role-based access control (RBAC) enables administrators to delegate control of specific management tasks for Lync Server. For example, instead of granting your organization's help desk full administrator privileges you can give these employees very specific rights: the right to manage only user accounts; the right to manage only Enterprise Voice components; and the right to manage only archiving and Archiving Server. In addition, these rights can be limited in scope: one user can be given the right to manage Enterprise Voice, but only in the Redmond site; while another user can be given the right to manage user accounts, but only if those accounts are in the Finance organizational unit (OU).
  
The **Get-CsAdminRoleAssignment** cmdlet provides a way for you to retrieve a list of the RBAC roles that have been assigned to a user. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsAdminRoleAssignment** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins, RTCUniversalReadOnlyAdmins. To return a list of all the RBAC roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsAdminRoleAssignment"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |System.String  <br/> |SamAccountName of the user whose RBAC roles are to be returned, You can retrieve the SamAccountName for a user by using a command similar to this:  <br/> Get-CsUser "Ken Myer" | Select-Object SamAccountName  <br/> Note that you must use the SamAccountName when specifying the user Identity. Other common values used when specifying identities, such as the Active Directory display name or the user's SIP address, will not work with **Get-CsAdminRoleAssignment**.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the RBAC role assignment data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

String. The **Get-CsAdminRoleAssignment** cmdlet accepts a pipelined string value representing the SamAccountName of a user. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Get-CsAdminRoleAssignment** cmdlet returns string values representing the RBAC roles held by the specified user. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsAdminRole](get-csadminrole.md)

