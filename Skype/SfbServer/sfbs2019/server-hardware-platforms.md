---
title: "Server hardware platforms for Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c964c1c0-0153-472b-88ad-a38866e0df0c

description: "Lync Server 2013 server roles and computers running Lync Server administrative tools require 64-bit hardware."
---

# Server hardware platforms for Lync Server 2013
[]
Lync Server 2013 server roles and computers running Lync Server administrative tools require 64-bit hardware.
  
The specific hardware used for Lync Server 2013 deployment can vary, depending on size and usage requirements. This section describes the recommended hardware. Although these are recommendations, not requirements, using hardware that does not meet these recommendations may result in significant performance issues and other issues.
  
## Recommended Hardware Platform

For best performance, we recommend that you run Lync Server on servers with hardware that meets the requirements in the following table. If you use less powerful hardware, you may experience functionality problems or poor performance. Note that these hardware requirements are higher than those of previous versions of Lync Server, primarily because in Lync Server 2013, all Front End Servers run SQL Server. 
  
> [!NOTE]
> NIC teaming is supported and should be transparent to Lync Server. For details, see [Communications Server or Lync Server and network adapter teaming](https://go.microsoft.com/fwlink/p/?LinkId=389910). 
  
**Recommended Hardware for Front End Servers, Back End Servers, Standard Edition Servers, Persistent Chat Servers, and Persistent Chat Store and Persistent Chat Compliance Store (Back End Server Roles for Persistent Chat Server)**

|**Hardware component**|**Recommended**|
|:-----|:-----|
|CPU  <br/> |64-bit dual processor, hex-core, 2.26 gigahertz (GHz) or higher.  <br/> Intel Itanium processors are not supported for Lync Server server roles.  <br/> |
|Memory  <br/> |32 gigabytes (GB).  <br/> |
|Disk  <br/> | 8 or more 10,000 RPM hard disk drives with at least 72 GB free disk space.  <br/>  Two of the disks should use RAID 1, and six should use RAID 10.  <br/>  - OR -  <br/>  Solid state drives (SSDs) which provide performance similar to 8 10,000-RPM mechanical disk drives.  <br/> |
|Network  <br/> | 1 dual-port network adapter, 1 Gbps or higher (2 recommended, which requires teaming with a single MAC address and single IP address).  <br/> > [!NOTE]>  Dual or multi-homed configurations are not supported for Front End Servers, Back End Servers, Standard Edition servers, and Persistent Chat Servers. >  ILO/DRAC/etc. connections not exposed to the Operating System and used to monitor and manage the server hardware do not constitute a multi-homed server and thus are supported.           |
   
**Recommended Hardware for Edge Servers, Standalone Mediation Servers, and Directors**

|**Hardware component**|**Recommended**|
|:-----|:-----|
|CPU  <br/> | 64-bit dual processor, quad-core, 2.0 gigahertz (GHz) or higher.  <br/>  - OR -  <br/>  64-bit 4-way processor, dual-core, 2.0 GHz or higher.  <br/>  Intel Itanium processors are not supported for Lync Server server roles.  <br/> |
|Memory  <br/> |16 gigabytes (GB).  <br/> |
|Disk  <br/> | 4 or more 10,000 RPM hard disk drives with at least 72 GB free disk space.  <br/>  The disks should be in a 2x RAID 1 configuration.  <br/>  - OR -  <br/>  Solid state drives (SSDs) which provide performance similar to 4 10,000-RPM mechanical disk drives.  <br/> |
|Network  <br/> | 1 dual-port network adapter, 1 Gbps or higher (2 recommended, which requires teaming with a single MAC address and single IP address). 2 network interfaces are required on Edge Servers, and are supported on standalone Mediation Servers.  <br/> > [!NOTE]>  Dual or multi-homed configurations are not supported for Directors. >  ILO/DRAC/etc. connections not exposed to the Operating System and used to monitor and manage the server hardware do not constitute a multi-homed server and thus are supported.            Edge Servers will require two network interfaces that are dual-port network adapters, 1 Gbps or higher (or two paired network adapters, for a total of four, each pair being teamed with a single MAC address and a single IP address, for a total of two pairs).  <br/>  Installation of additional network interface cards (NICs) to allow the configuration of a specific PSTN IP address is supported on standalone Mediation Servers.  <br/> |
   

