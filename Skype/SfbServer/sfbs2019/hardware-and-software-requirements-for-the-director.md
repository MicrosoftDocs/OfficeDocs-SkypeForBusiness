---
title: "Hardware and software requirements for the Director in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 5/19/2016
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 747b701e-7f97-46fe-91c5-1e8d9addf9f7
description: "In this articleHardware Requirements for the DirectorSoftware Requirements for the DirectorSupported Collocation"
---

# Hardware and software requirements for the Director in Lync Server 2013
[]
 **In this article**
  
[Hardware Requirements for the Director](#sectionSection0)
  
[Software Requirements for the Director](#sectionSection1)
  
[Supported Collocation](#sectionSection2)
  
This section details the hardware and software requirements for the Director, and the supported collocation scenarios for the Director.
  
## Hardware Requirements for the Director
<a name="sectionSection0"> </a>

The following table lists the hardware requirements for the Director:
  
**Hardware Requirements for the Director**

|**Hardware component**|**Minimum requirement**|
|:-----|:-----|
|CPU  <br/> | 64-bit processor, quad-core, 2.0 GHz or higher  <br/>  64-bit dual processor, dual-core, 2.0 GHz or higher  <br/> |
|Memory  <br/> |4 gigabytes (GB)  <br/> |
|Disk  <br/> | 10K RPM hard disk drive (HDD)  <br/>  High-performance solid state drive (SSD) with performance equal to or better than 10K RPM HDD  <br/>  2x RAID 10 (striped and mirrored) 15K RPM disks for database data files  <br/> |
|Network  <br/> | Dual 1 gigabit per second (Gbps) network adapters (recommended)  <br/>  Single 1 Gbps network adapter (supported)  <br/> |
   
## Software Requirements for the Director
<a name="sectionSection1"> </a>

The Director role can be deployed only on servers running Lync Server 2013 Enterprise Edition.
  
One of the following 64-bit operating systems is required for the Directors:
  
- The Windows Server 2008 R2 Standard operating system with Service Pack 1 (SP1)
    
- The Windows Server 2008 R2 Enterprise operating system with SP1
    
- The Windows Server 2008 R2 Datacenter operating system with SP1
    
- The Windows Server 2012 Standard operating system
    
- The Windows Server 2012 Datacenter operating system
    
- The Windows Server 2012 R2 Standard operating system
    
- The Windows Server 2012 R2 Datacenter operating system
    
Lync Server 2013 also requires installation of the following programs and updates detailed in the topic [Additional server support and requirements in Lync Server 2013](additional-server-support-and-requirements.md).
  
## Supported Collocation
<a name="sectionSection2"> </a>

The Director server role cannot be collocated with any other server role in Lync Server 2013. However, if you do not deploy a Director, the Front End Servers will assume the role.
  

