---
title: "Export-CsPersistentChatData"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f4855109-26e0-41b8-8a9f-890f8d892645
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Export-CsPersistentChatData
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Exports data from a Persistent Chat database. This cmdlet was introduced in Lync Server 2013.
  
```
Export-CsPersistentChatData [-FileName <String>] <COMMON PARAMETERS>
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 exports Persistent Chat data from the Persistent Chat database located on the server atl-sql-001.litwareinc.com; the exported data will be stored in the file C:\Logs\PersistentChatData.zip. Because the Level parameter was not specified, the **Export-CsPersistentChatData** cmdlet will do a full export of the Persistent Chat information. 
  
```
Export-CsPersistentChatData -DBInstance "atl-sql-001.litwareinc.com\rtc" -FileName "C:\Logs\PersistentChatData.zip"
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Persistent Chat service (which replaces the Group Chat service used in Microsoft Lync Server 2010) provides organizations with messaging and collaboration capabilities similar to those found in Internet discussion forums: users can exchange messages in real-time, yet can also revisit and restart those conversations at any time. Conversations can be based around specific topics, and these conversations can be made available to everyone or to only a selected set of users. Likewise, individual chat rooms can be configured so that anyone can post a message or configured so that only designated presenters can post messages.
  
If you are currently running Lync Server 2010, you can migrate your current Group Chat implementation by using the **Export-CsPersistentChatData** cmdlet to export your existing Group Chat configuration settings, then use the **Import-CsPersistentChatData** cmdlet to migrate that information to Lync Server 2013 and the Persistent Chat service. Note that the **Export-CsPersistentChatData** cmdlet gives you the option of importing all your Group Chat settings and data or only a portion of your Group Chat settings and data; for example, you can export (and then import) your Group Chat categories and chat rooms without exporting all the content associated with those categories and chat rooms. 
  
Although primarily intended for migration purposes, the **CsPersistentChatData** cmdlets can also be used to manage Persistent Chat data on Lync Server 2013. 
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Export-CsPersistentChatData"}
  
Lync Server Control Panel: The functions carried out by the **Export-CsPersistentChatData** cmdlet are not available in the Lync Server Control Panel. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _DBInstance_ <br/> |Required  <br/> |System.String  <br/> |Fully qualified domain name and name of the SQL Server instance where the Lync Server 2013 Persistent Chat database is located. For example, this syntax specifies the database found in the RTC database instance on the server atl-sql-001.litwareinc.com:  <br/> -DBInstance "atl-sql-001.litwareinc.com\rtc"  <br/> |
| _AsBytes_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Returns Persistent Chat information as a byte array; the returned data must then be stored in a variable in order to be used by the **Import-CsPersistentChatData** cmdlet. You cannot use both AsBytes and FileName in the same command.  <br/> |
| _DBName_ <br/> |Optional  <br/> |System.String  <br/> |SQL instance name of the Persistent Chat database.  <br/> |
| _DisableExportedNodes_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When present, all exported categories and chat rooms will be disabled when the export is complete.  <br/> |
| _FileName_ <br/> |Optional  <br/> |System.String  <br/> |Full path to the .ZIP file that the **Export-CsPersistentChatData** cmdlet will create; this file will contain the exported user data. For example:  <br/> -FileName "C:\Logs\PersistentChatData.zip"  <br/> |
| _Level_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Chat.Cmdlets.ExportLevel  <br/> |Enables you to specify which Persistent Chat information will be exported. Allowed values are:  <br/> \* All  <br/> \* User  <br/> \* Category  <br/> \* RoomDirectory  <br/> \* Content  <br/> The default value is All, which means that all the Persistent Chat information will be exported.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Full path for the log file created when the cmdlet runs. For example:  <br/> -Report "C:\Logs\ExportPersistentChat.html"  <br/> |
| _Scope_ <br/> |Optional  <br/> |System.Collections.Generic.List  <br/> |Enables you to export data for a specified set of categories (and their corresponding chat rooms). By default all Categories are exported.  <br/> |
| _StartDate_ <br/> |Optional  <br/> |System.DateTime  <br/> |Beginning date for the time period for which Persistent Chat chat room content should be exported. For example:  <br/> -StartDate "1/1/2012"  <br/> This parameter is valid only when they Level is set to RoomDirectory.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Export-CsPersistentChatData** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="ReturnTypes"> </a>

The **Export-CsPersistentChatData** cmdlet creates .ZIP files. 
  

