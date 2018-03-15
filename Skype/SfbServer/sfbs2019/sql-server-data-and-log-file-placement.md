---
title: "SQL Server data and log file placement for Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 67aa525b-8aa3-474f-827e-8e1d4697f30f
description: "During the planning and deployment of Microsoft SQL Server 2012 or Microsoft SQL Server 2008 R2 SP1 for your Lync Server 2013 Front End pool, an important consideration is the placement of data and log files onto physical hard disks for performance. The recommended disk configuration is to implement a 1+0 RAID set using 6 spindles. Placing all database and log files that are used by the Front End pool and associated server roles and services (that is, Archiving and Monitoring Server, Lync Server Response Group service, Lync Server Call Park service) onto the RAID drive set using the Lync Server Deployment Wizard will result in a configuration that has been tested for good performance. The database files and what they are responsible for is detailed in the following table."
---

# SQL Server data and log file placement for Lync Server 2013
[]
During the planning and deployment of Microsoft SQL Server 2012 or Microsoft SQL Server 2008 R2 SP1 for your Lync Server 2013 Front End pool, an important consideration is the placement of data and log files onto physical hard disks for performance. The recommended disk configuration is to implement a 1+0 RAID set using 6 spindles. Placing all database and log files that are used by the Front End pool and associated server roles and services (that is, Archiving and Monitoring Server, Lync Server Response Group service, Lync Server Call Park service) onto the RAID drive set using the Lync Server Deployment Wizard will result in a configuration that has been tested for good performance. The database files and what they are responsible for is detailed in the following table.
  
> [!NOTE]
> If your policies and SQL Server configurations require a more specialized installation, the database and log files can be installed to any pre-defined location using the Lync Server Management Shell. See [Database installation using Lync Server Management Shell in Lync Server 2013](database-installation-using-lync-server-management-shell.md) for more details. 
  
**Data and Log Files for Central Management Store**

|**Central Management store database files**|**Data file or log purpose**|
|:-----|:-----|
|Xds.ldf  <br/> |Transaction log file for the Central Management store  <br/> |
|Xds.mdf  <br/> |Maintains the configuration of the current Lync Server 2013 topology, as defined and published by Topology Builder  <br/> |
|Lis.mdf  <br/> |Location Information service data file  <br/> |
|Lis.ldf  <br/> |Transaction log for the Location Information service data file  <br/> |
   
**Data and Log files for User, Conferencing, and Address Book**

|**Core Lync Server 2013 database files**|**Data file or log purpose**|
|:-----|:-----|
|Rtc.mdf  <br/> |Persistent user data (for example, access control lists (ACLs), contacts, scheduled conferences)  <br/> |
|Rtc.ldf  <br/> |Transaction log for Rtc data  <br/> |
|Rtcdyn.mdf  <br/> |Maintains transient user data (presence runtime data)  <br/> |
|Rtcdyn.ldf  <br/> |Transaction log for Rtcdyn data  <br/> |
|Rtcab.mdf  <br/> |Real-time communications (RTC) address book database is the SQL Server repository where Address Book service information is stored  <br/> |
|Rtcab.ldf  <br/> |Transaction log for Address Book Service  <br/> |
|Rtclocal.mdb  <br/> |Hosts the conference directory  <br/> |
|Rtcxds.mdf  <br/> |Maintains the backup for user data  <br/> |
|Rtcxds.ldf  <br/> |Transaction log for Rtcxds data  <br/> |
   
**Data and Log Files for Call Park and Response Group**

|**Application database**|**Data file or log purpose**|
|:-----|:-----|
|Cpsdyn.mdf  <br/> |Dynamic information database for the Call Park application  <br/> |
|Cpsdyn.ldf  <br/> |Transaction log for Call Park application data file  <br/> |
|Rgsconfig.mdf  <br/> |Lync Server Response Group service data file for the configuration of the services  <br/> |
|Rgsconfig.ldf  <br/> |Transaction log file for the Response Group application configuration  <br/> |
|Rgsdyn.mdf  <br/> |Response Group service data file for runtime operations  <br/> |
|Rgsdyn.ldf  <br/> |Transaction log for the Response Group service runtime data file  <br/> |
   
**Data and Log Files for Archiving and Monitoring Server**

|**Archiving and Monitoring database files**|**Data file or log purpose**|
|:-----|:-----|
|LcsCdr.mdf  <br/> |Data store for the call detail recording (CDR) process of the Monitoring Server  <br/> |
|LcsCdr.ldf  <br/> |Transaction log for call detail recording (CDR) data  <br/> |
|QoEMetrics.mdf  <br/> |Quality of Experience data file stored from the Monitoring Server  <br/> |
|QoEMetrics.ldf  <br/> |Transaction log for Monitoring data  <br/> |
|Lcslog.mdf  <br/> |Data file for the retention of instant messaging and conferencing data on an Archiving Server  <br/> |
|Lcslog.ldf  <br/> |Transaction log for Archiving data  <br/> |
   
In this topic, references are made to disk and to RAID set. Note that in the configuration of SQL Server resources, referring to a disk means a single hardware device. A hard disk drive with two partitions, one holding log files and the other partition holding data files, is not the same as two disks, each dedicated to either log or data files.
  
In reference to RAID sets, there are a number of different RAID technologies from various vendors. And, with the proliferation of storage area networks (SAN), RAID sets dedicated to a single system are rarer. You should consult with your RAID or SAN vendor to determine what the best configuration is for your disk layout when configuring for SQL Server performance with Lync Server 2013.
  
Note also that not all disk drives are created equally; some perform better than others. Even drives from the same manufacturer can vary in performance because of rotational speed, hardware cache size, and other factors. 
  

