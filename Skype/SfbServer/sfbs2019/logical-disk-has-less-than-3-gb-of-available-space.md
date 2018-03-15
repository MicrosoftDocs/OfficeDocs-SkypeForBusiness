---
title: "Logical disk has less than 3 GB of available space"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 784bba7a-8018-49db-b555-9dc5d4cf8272
description: "Issue: The logical disk has less than 3 GB of available space."
---

# Logical disk has less than 3 GB of available space
[]
Issue: The logical disk has less than 3 GB of available space.
  
## Description of the Issue

The Office 365 Best Practices Analyzer tool for Lync Server queries a Windows Management Instrumentation (WMI) class (Win32_LogicalDisk). This query determines the value of the **FreeSpace** key for disks that have the Win32_LogicalDisk **DriveType** key set to 3 (which indicates a local disk). 
  
A warning appears if the value of the **FreeSpace** key for a local disk indicates that less than 3 gigabytes (GB) of storage space is available for the logical disk. All disks in computers that are running Lync Server should have at least 6GB total capacity, and they should always have at least half of that capacity (3 GB) free. For warnings about physical disk space, see [Mount point has less than 3 GB of available space](mount-point-has-less-than-3-gb-of-available-space.md).
  
To maintain your deployment, you should ensure that you have sufficient disk capacity at all times. When a database disk runs out of capacity, the database goes offline. When a transaction log disk runs out of capacity, all databases in the associated storage group go offline. You probably cannot provision additional capacity or perform offline compaction to reclaim space quickly enough to avoid significant downtime, data loss, or both. In most cases, if you run out of disk capacity, you will be unable to access one or more databases for a period of time that is longer than your recovery time objectives (RTO).
  
## Issue Resolution

To resolve this issue, reclaim or add disk capacity to the computer. To resolve a warning about logical disk capacity:
  
- Delete unnecessary files from the disk.
    
- If you can safely move data to another disk, move the data.
    
- Add disk capacity.
    

