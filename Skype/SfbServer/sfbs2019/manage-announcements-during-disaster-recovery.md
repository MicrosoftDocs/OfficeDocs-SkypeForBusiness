---
title: "Manage announcements during disaster recovery in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c33e51ea-421f-42d2-826b-b73968f6bd5b
description: "In this articleBefore an OutageDuring an OutageAfter the Outage"
---

# Manage announcements during disaster recovery in Lync Server 2013
[]
 **In this article**
  
[Before an Outage](#sectionSection0)
  
[During an Outage](#sectionSection1)
  
[After the Outage](#sectionSection2)
  
Lync Server 2013 supports announcements for calls to unassigned numbers during outages. Restoring announcement functionality during an outage is optional. If you choose to restore announcements during an outage, you need recreate your announcement configuration in the backup pool. This section describes what you need to do if you choose to restore announcements during disaster recovery.
  
This section applies to unassigned number ranges that use the Announcement application. This section does not apply to unassigned number ranges that use Exchange Unified Messaging (UM) Auto Attendant.
  
## Before an Outage
<a name="sectionSection0"> </a>

Regardless of whether you choose to use announcements during outages, you should take separate backups of any customized audio files that you configured for the Announcement application. Customized announcements are not backed up as part of the Lync Server disaster recovery process. If you do not take separate backups of the files and the files that you uploaded to the server or pool are damaged, corrupted, or erased, the files will be lost.
  
If you do not have backup copies of customized audio files, and the original audio files are no longer available, you can find the audio files that you configured for an Announcement application by looking in the File Store for the server or pool where you originally imported the files. You can copy all the audio files that you configured for the Announcement application from the File Store.
  
### To copy audio files from the file store

- At the command line, run:
    
  ```
  Xcopy <Source: Pool Announcement Service File Store path> <Destination>
  ```

    For example:
    
  ```
  Xcopy "<Pool File Store Path>\X-ApplicationServer-X\AppServerFiles\RGS\AS" "<Destination: Backup location>"
  ```

    Where X-ApplicationServer-X refers to the service ID of the Application Server of the pool (for example, 1-ApplicationServer-1")
    
## During an Outage
<a name="sectionSection1"> </a>

To use the Announcement application during an outage, you need to recreate the announcement configuration in the backup pool by performing the tasks described in this section.
  
> [!NOTE]
> We recommend that you perform these tasks after you fail over to the backup pool, because as soon as you perform step 2, the backup pool takes ownership of the unassigned number ranges. 
  
> [!NOTE]
> These steps are not required for number ranges that use an Exchange UM Auto Attendant phone number. 
  
### To recreate the announcement configuration in the backup pool

1. Recreate the announcements that you deployed in the primary pool in the backup pool by doing the following: 
    
1. Import any audio files used in the primary pool to the backup pool by using the **Import-CsAnnouncementFile** cmdlet and specifying the backup pool for the Parent parameter. 
    
2. Recreate each announcement by using the **New-CsAnnouncement** cmdlet and specifying the backup pool for the Parent parameter. 
    
    > [!NOTE]
    > For details about using these parameters to create announcements in the backup pool, see [Create an announcement in Lync Server 2013](create-an-announcement.md). 
  
2. After all announcements are recreated in the backup pool, redirect all the unassigned number ranges that use announcements in the primary pool to the recreated announcements in the backup pool.
    
    For each unassigned number range that uses an announcement in the primary pool, run the following:
    
  ```
  Set-CsUnassignedNumber -Identity "<name of number range>" -AnnouncementService "<FQDN of backup pool>" -AnnouncementName "<announcement name in backup pool>"
  ```

## After the Outage
<a name="sectionSection2"> </a>

When the primary pool becomes available, you need to redirect the unassigned number ranges that you changed for the outage back to the primary pool. 
  
> [!NOTE]
> These steps are not required for number ranges that use an Exchange UM Auto Attendant phone number. 
  
### To restore announcements in the primary pool

1. If you had to rebuild the primary pool during the recovery, you need to recreate the announcements in the primary pool by importing the audio files and creating announcements, just as you did in the backup pool, except that you specify the primary pool for the Parent parameter. For details, see "During an Outage" earlier in this topic.
    
2. For each unassigned number range that you changed for the outage, run the following:
    
  ```
  Set-CsUnassignedNumber [-Identity "<name of number range>"] -AnnouncementService "<FQDN of primary pool>" -AnnouncementName "<announcement name in primary pool>"
  ```

3. Optionally, remove the announcements that you recreated in the backup pool. Get a list of announcements for the backup pool Announcement application. At the command line, run:
    
  ```
  Get-CsAnnouncement -Identity "<Service:service ID>"
  ```

    For example:
    
  ```
  Get-CsAnnouncement -Identity "ApplicationServer:redmond.contoso.com
  ```

    In the resulting list, locate the announcements you want to remove and copy the GUIDs. For each announcement you want to remove, run:
    
  ```
  Remove-CsAnnouncement -Identity "<Service:service ID/guid>"
  ```

    For example:
    
  ```
  Remove-CsAnnouncement -Identity "ApplicationServer:redmond.contoso.com/1951f734-c80f-4fb2-965d-51807c792b90"
  ```


