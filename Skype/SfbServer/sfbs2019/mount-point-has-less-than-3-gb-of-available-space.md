---
title: "Mount point has less than 3 GB of available space"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 32fbf7d0-9418-49cc-81c7-0819105ec1d4
description: "Issue: The mount point has less than 3 GB of available space."
---

# Mount point has less than 3 GB of available space
[]
Issue: The mount point has less than 3 GB of available space.
  
## Description of the Issue

The Office 365 Best Practices Analyzer Best Practices Analyzer tool for Lync Server queries a Microsoft Windows Management Instrumentation (WMI) class (Win32_Volume) to determine the value of the **FreeSpace** key for volume mount points that the computer uses. 
  
A warning appears if the value of the **FreeSpace** key indicates that less than 3 gigabytes (GB) of storage space is available for a volume mount point. 
  
You can use volume mount points (also known as NTFS file system junction points) as a location for data storage in a clustered configuration. They are supported when you have Lync Server installed on a computer that is running Windows Server 2008 R2, Windows Server 2012, or Windows Server 2012 R2 Enterprise Edition or Datacenter Edition. By using volume mount points, you can assign more than 26 drive letters and graft or mount a target partition into a folder on another physical disk. Volume mount points are transparent to programs such as Lync Server.
  
Lync Server can use volumes that are local physical disks, logical volumes, or volume mount points. In any case, the volume should have at least 50 percent free disk space available on all drives. You should ensure a minimum of 25 to 30 percent of free disk space for maintenance, which includes tasks that you perform by using database utilities such as eseutil and isinteg. Also, for maintenance operations such as offline defragmentation, you should have as much free space as the amount that you are defragmenting. For example, if you are defragmenting a 1 GB database, you should have at least 1 GB of free disk space available.
  
For security and availability reasons, you should ensure that all disks have plenty of free space. A denial of service attack, a message loop, or a widespread outbreak of a virus can cause excessive consumption of disk space caused by increased message traffic or transaction log activity.
  
## Issue Resolution

To resolve this issue, reclaim or add disk capacity to the computer. To resolve a warning about mount point space:
  
- Investigate areas to reclaim disk space, and increase available space.
    
- If disk space is very low, consider moving data to another computer that is running Lync Server and that is not space constrained.
    

