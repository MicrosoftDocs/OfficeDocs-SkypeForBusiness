---
title: "Setting up system platforms for Archiving in Lync Server 2013"
ms.author: crowe
author: CarolynRowe
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 2df40fdf-0e32-46d4-9fb2-1ce1d7bfa328
description: "Before starting the deployment of Archiving, you must install the required operating system and any other prerequisite software on hardware that meets system requirements:"
---

# Setting up system platforms for Archiving in Lync Server 2013
[]
Before starting the deployment of Archiving, you must install the required operating system and any other prerequisite software on hardware that meets system requirements:
  
- **Lync Server 2013 platform** Lync Server 2013 deployments do not have Archiving Servers. Instead, Unified Data Collection Agents run on Front End Servers and Standard Edition servers to capture data for archiving, so no separate system platform is required to host Archiving. 
    
- **Data storage platform** In Lync Server 2013, you can store data by using either of the following: 
    
  - **Microsoft Exchange integration** If you want to store Lync Server 2013 Archiving data by using your Exchange 2013 deployment, instead of or in addition to setting up a separate database for storage of Archiving data, your Exchange deployment must be running Exchange 2013. For details about setting up system platforms for Exchange 2013, see the Exchange product documentation. 
    
  - **SQL Server** If you want to use a separate SQL Server database for storage of archiving data, instead of or in addition to using Microsoft Exchange integration, you must set up the system platform for the database prior to deployment of Archiving. The specific system platform requirements depend on whether you use Microsoft SQL Server 2008 R2 or Microsoft SQL Server 2012 for the Archiving database. For details about setting up system platforms for these databases, see the Microsoft SQL Server 2008 R2 and Microsoft SQL Server 2012 product documentation. 
    
- **File server platform** Lync Server 2013 stores Lync Server archiving files in the same location that you specify for file storage when you set up your Front End Servers or Standard Edition servers. You cannot specify a separate location for archiving file storage, so no separate system platform is required for Archiving file storage. If you use Microsoft Exchange integration, Exchange 2013 the files for archived Lync communications are stored on Exchange 2013 servers for users homed on those Exchange servers. 
    

