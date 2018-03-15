---
title: "Backup and restoration worksheets for Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 26c78155-0306-41ac-845b-7ad58000a1d6
description: "In this articleDatabase Backup and Restoration WorksheetFile Store Backup and Restoration WorksheetSettings Backup and Restoration Worksheet"
---

# Backup and restoration worksheets for Lync Server 2013
[]
 **In this article**
  
[Database Backup and Restoration Worksheet](#sectionSection0)
  
[File Store Backup and Restoration Worksheet](#sectionSection1)
  
[Settings Backup and Restoration Worksheet](#sectionSection2)
  
The backup and restoration plan for your organization should contain details about how and when you back up data and settings. You can use the worksheets presented here to help you document this information for your specific deployment and for your organization's backup and restoration requirements.
  
Use the following worksheets to record the information that you need to back up and restore database, File Store, and settings information for a Lync Server pool or Standard Edition server. Keep one or more copies of these worksheets in a secure location so that they are readily accessible if you need to restore Lync Server.
  
> [!NOTE]
> The worksheets in this section cover only the information that is required to restore the data and settings of Lync Server databases and servers. If you need to document other restoration information, such as the information for reinstalling operating systems and other software, use your organization's deployment plans and backup and restoration plans to address those requirements. 
  
## Database Backup and Restoration Worksheet
<a name="sectionSection0"> </a>

Use the following table to record the information that you need to back up and restore Lync Server databases.
  
**Database Information for Backup and Restoration**

|**Database**|**Server name (FQDN)**|**Backup schedule**|**Database backup tool**|**Backup set**|**Backup destination**|**Notes**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|Rtc database on Back End Server for user data  <br/> | <br/> | <br/> |**Export-CsUserData** cmdlet  <br/> |Name:  <br/> Expiration:  <br/>  <br/> | <br/> | <br/> |
|LcsLog (default name) database on Archiving database server  <br/> | <br/> | <br/> | SQL Server management tool  <br/> |Name:  <br/> Expiration:  <br/> | <br/> | <br/> |
|LcsCdr database on Monitoring database server for call detail records (CDRs)  <br/> | <br/> | <br/> | SQL Server management tool  <br/> |Name:  <br/> Expiration:  <br/> | <br/> | <br/> |
|QoEMetrics database on Monitoring database server for Quality of Experience (QoE) data  <br/> | <br/> | <br/> | SQL Server management tool  <br/> |Name:  <br/> Expiration:  <br/> | <br/> | <br/> |
|Persistent Chat Database  <br/> |||SQL Server management tool or **Export-CsPersistentChatData** cmdlet  <br/> |Name:  <br/> Expiration:  <br/> |||
   
No backup or restoration is required of the following databases:
  
- Rtcdyn. The transient user data in this database is not necessary for restoration of service.
    
- Rtcab. The Address Book database is automatically recreated from the Global Address List (GAL) in Active Directory Domain Services.
    
- Rgsdyn. The transient Response Group service data in this database is not necessary for restoration of service.
    
- Cpsdyn. The dynamic information for the Call Park application is not necessary for restoration of service.
    
- MgcComp. The compliance database for Persistent Chat is not necessary for restoration of service.
    
## File Store Backup and Restoration Worksheet
<a name="sectionSection1"> </a>

Use the following table to record the information that you need to back up and restore the File Stores. File Stores contain data such as meeting content metadata, meeting compliance logs, update logs for device updates, and audio files for the Response Group, Call Park, and Announcement applications.
  
**File Store Information for Backup and Restoration**

|**Content**|**Server name (FQDN)**|**Backup schedule**|**File system backup tool**|**File share to be backed up \***|**Backup destination**|**Notes**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|Lync Server File Store  <br/> |||Standard backup tool, such as Robocopy  <br/> |On file server for Enterprise Edition. On Standard Edition by default, for Standard Edition deployment. Typically, one per site.  <br/> ||Files named **Meeting.Active** should not be backed up. These files are in use and are locked while a meeting takes place.  <br/> |
   
## Settings Backup and Restoration Worksheet
<a name="sectionSection2"> </a>

Use the following table to record the information that you need to back up and restore settings.
  
**Settings Information for Backup and Restoration**

|**Database**|**Server name (FQDN)**|**Backup schedule**|**Backup tool**|**Configuration file (.xml) name**|**Backup location**|**Notes**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|Xds database in Central Management store for topology configuration (global)  <br/> | <br/> | <br/> |**Export-CsConfiguration** cmdlet  <br/> | <br/> | <br/> | <br/> |
|Lis database in Central Management store for E9-1-1 location information (global)  <br/> | <br/> | <br/> |**Export-CsLisConfiguration** cmdlet  <br/> || <br/> | <br/> |
|RgsConfig database on Back End Server for Response Group configuration (pool)  <br/> | <br/> | <br/> |**Export-CsRgsConfiguration** cmdlet  <br/> || <br/> | <br/> |
   

