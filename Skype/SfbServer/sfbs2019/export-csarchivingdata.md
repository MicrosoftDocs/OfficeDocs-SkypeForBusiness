---
title: "Export-CsArchivingData"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 644bf86e-0e7e-4607-bedf-d491b1c16745
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Export-CsArchivingData
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Enables you to export records that have been stored in the Lync Server Archiving database. This cmdlet was introduced in Lync Server 2010.
  
```
Export-CsArchivingData -DBInstance <String> -Identity <XdsIdentity> <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 extracts records from the Archiving database located on the server atl-sql-001.litwareinc.com, and then saves the resulting EML file to the folder C:\ArchivingExports. The specified start date of June 1, 2012 (-StartDate 6/1/2012) ensures that only items recorded in the database after 5/31/2012 will be exported.
  
```
Export-CsArchivingData -Identity "ArchivingDatabase:atl-sql-001.litwareinc.com" -StartDate 6/1/2012 -OutputFolder "C:\ArchivingExports"
```

### EXAMPLE 2

Example 2 is a variation of the command shown in Example 1; in this case, however, only the records pertaining to the user Ken Myer are exported. To limit your export to records pertaining to a single user, include the UserUri parameter followed by appropriate SIP address.
  
```
Export-CsArchivingData -Identity "ArchivingDatabase:atl-sql-001.litwareinc.com" -StartDate 6/1/2012 -OutputFolder "C:\ArchivingExports" -UserUri "kenmyer@litwareinc.com"
```

### EXAMPLE 3

Example 3 represents another variation of the command shown in Example 1. In Example 3, however, only items recorded in the database during the month of June, 2012 are exported. To limit exporting to this time interval, the EndDate parameter is included along with the StartDate parameter. With a start date of June 1, 2012 and an end date of June 30, 2012, exporting is limited to items recorded during June 2012.
  
```
Export-CsArchivingData -Identity "ArchivingDatabase:atl-sql-001.litwareinc.com" -StartDate 6/1/2012 -EndDate 6/30/2012 -OutputFolder "C:\ArchivingExports"
```

## Detailed Description
<a name="sectionSection1"> </a>

Many organizations find it useful to keep a transcript of all the instant messaging (IM) sessions carried out by their users. Other organizations find it mandatory to keep such transcripts. For example, organizations in the financial world are often required by law to keep copies of all their electronic communications.
  
Regardless of the reason, Lync Server gives you flexibility when it comes to archiving IM and conferencing sessions. If you have deployed Archiving Server, you can use the various **CsArchivingConfiguration** cmdlets to enable and disable instant message archiving and to manage your Archiving database. You can also suspend IM should archiving fail, which helps ensure that you keep a record of all your electronic communications. 
  
If you have enabled archiving, records of your users' electronic communications are stored in the Archiving database. If you would like to view all of these records (or a selected subset of these records), you can use the **Export-CsArchivingData** cmdlet to extract these records from the database and save them as an Outlook Express Electronic Mail (EML) file (.EML file extension). 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Export-CsArchivingData** cmdlet locally: RTCComponentUniversalServices. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Export-CsArchivingData"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _DBInstance_ <br/> |Required  <br/> |System.String  <br/> |Path to the SQL Server database instance where archiving data is recorded. For example: "atl-sql-001\Archinst".  <br/> This parameter is intended for use only with Microsoft Lync Server 2010. If you are using the **Export-CsArchivingData** cmdlet on Lync Server 2013 you should use the Identity parameter instead.  <br/> |
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Service identity of the archiving database to be exported. For example:  <br/> -Identity "ArchivingDatabase:atl-sql-001.litwareinc.com"  <br/> You can also specify the database by using just the pool name:  <br/> -Identity "atl-sql-001.litwareinc.com"  <br/> You can retrieve the service identities for your archiving databases by using this command:  <br/> Get-CsService -ArchivingDatabase | Select-Object Identity  <br/> |
| _OutputFolder_ <br/> |Required  <br/> |System.String  <br/> |Full path to the folder where the exported data should be stored (for example, C:\ArchivingExports). If this folder does not exist, then the **Export-CsArchivingData** cmdlet will create it.  <br/> |
| _StartDate_ <br/> |Required  <br/> |System.DateTime  <br/> |Indicates the earliest activity date for the records to be exported. For example, if you set the start date to 6/1/2010 (June 1, 2010, in U.S. English) any items recorded in the database prior to that date (for example, items recorded on May 31, 2010) will be excluded from the export.  <br/> Use the date-time formats specified by your Regional and Language Options settings when assigning values to the StartDate and EndDate properties.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EndDate_ <br/> |Optional  <br/> |System.DateTime  <br/> |Indicates the latest activity date for records to be exported. For example, if you set the end date to 6/1/2010 (June 1, 2010, in U.S. English) any items recorded in the database after that date (for example, items recorded on June 2, 2010) will be excluded from the export. Although you will not receive an error message, your export will fail if the end date occurs before the start date (for example, an end date of 1/1/2010 and a start date of 6/1/2010).  <br/> Use the date-time formats specified by your Regional and Language Options settings when assigning values to the StartDate and EndDate properties.  <br/> If an end date is not specified then the current date will be used.  <br/> |
| _ExcludeWebConfArchive_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Instructs the **Export-CsArchivingData** cmdlet to only export instant messaging records. By default, the cmdlet exports both IM and conferencing records.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _IncludeTrustedApplication_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When included, instructs the **Export-CsArchivingData** cmdlet to include data logged by trusted applications when exporting records.  <br/> |
| _Purge_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When included, the Purge parameter causes any record that has been successfully exported to be deleted from the Archiving database. If you do not include this parameter, exported records will be retained in the database.  <br/> |
| _UserUri_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to export archiving data for a single user; this is done by using the UserUri parameter and specifying the SIP address of the user. The UserUri parameter will accept only one URI at a time.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Export-CsArchivingData** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Export-CsArchivingData** cmdlet returns Archiving database records in EML format. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsArchivingConfiguration](get-csarchivingconfiguration.md)

