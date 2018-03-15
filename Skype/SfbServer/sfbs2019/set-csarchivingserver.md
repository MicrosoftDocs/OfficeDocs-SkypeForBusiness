---
title: "Set-CsArchivingServer"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d4e51c14-34a6-4134-bb71-87bc2f11092d
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsArchivingServer
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Enables you to specify a new database location for one or more Archiving Servers. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsArchivingServer [-Identity <XdsGlobalRelativeIdentity>] [-ArchivingDatabase <String>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 changes the location of the Archiving database for the ArchivingServer:atl-cs-001.litwareinc.com Archiving Server . In this example, the new database is located at ArchivingDatabase:atl-sql-001.litwareinc.com.
  
```
Set-CsArchivingServer -Identity "ArchivingServer:atl-cs-001.litwareinc.com" -ArchivingDatabase "ArchivingDatabase:atl-sql-001.litwareinc.com"
```

## Detailed Description
<a name="sectionSection1"> </a>

Archiving Servers provide a way for you to save complete transcripts of the instant messaging (IM) sessions that take place in your organization. In some organizations, it can be useful to have copies of these IM sessions. In other organizations, where records must be kept of all electronic communications, it can be mandatory to have copies of these IM sessions.
  
Archiving Server records the transcript of each IM session (as well as information about when the session took place, and who participated in the session) in a SQL Server database. The location of this database must be specified when you install Archiving Server; in most cases, you will not need to change the location of that database. However, if a hardware failure or other problem should occur, you can point Archiving Server to a new database by using the **Set-CsArchivingServer** cmdlet. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsArchivingServer** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsArchivingServer"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _ArchivingDatabase_ <br/> |Optional  <br/> |System.String  <br/> |Service location where the new Archiving database is located. For example: -ArchivingDatabase ArchivingDatabase:atl-sql-001.litwareinc.com. Make sure you use the service location and not the SQL Server path when specifying the database location.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Service location of the Archiving Server instance to be modified. For example: -Identity ArchivingServer:atl-cs-001.litwareinc.com. You can retrieve the service location for all your Archiving servers by running this command:  <br/> Get-CsService -ArchivingServer | Select-Object Identity  <br/> Note that you can leave off the prefix "ArchivingServer:" when specifying an Archiving server. For example: -Identity "atl-cs-001.litwareinc.com".  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Set-CsArchivingServer** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Set-CsArchivingServer** cmdlet does not return any objects or values. Instead, the cmdlet modifies instances of the Microsoft.Rtc.Management.Xds.DisplayArchivingServer object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsArchivingConfiguration](get-csarchivingconfiguration.md)

