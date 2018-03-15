---
title: "Configuring Lync Server 2013 to work with System Center Operations Manager"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b55a24ab-648b-4142-b3cd-3792860ba872
description: "In order to configure your Microsoft Lync Server 2013 infrastructure to work with System Center Operations Manager you must do three things:"
---

# Configuring Lync Server 2013 to work with System Center Operations Manager
[]
In order to configure your Microsoft Lync Server 2013 infrastructure to work with System Center Operations Manager you must do three things:
  
- Identify and configure your primary System Center Operations Manager management server. Configuring the management server includes installing System Center Operations Manager 2012 or System Center Operations Manager 2007 R2, as well as setting up a back-end database using SQL Server. The actual version of SQL Server that you need to be use depends on the version of System Center Operations Manager you are using. For details, see [Configuring the primary management server in Lync Server 2013](configuring-the-primary-management-server.md).
    
- Identify and configure the Lync Server computers that you want to monitor. To monitor a Lync Server computer by using System Center Operations Manager you must install the System Center Operations Manager agent files, and configure each server to act as a proxy.
    
- Identify and configure the computers that you want to act as Lync Server watcher nodes. Watcher nodes are computers that periodically run Lync Server synthetic transactions, which are Windows PowerShell cmdlets that verify that key Lync Server components, such as the ability to log on to the system or the ability to exchange instant messages are working as expected.
    
The topics in this section contain instructions for carrying out each of these tasks.
  
## In This Section

- [Configuring the primary management server in Lync Server 2013](configuring-the-primary-management-server.md)
    
- [Installing the Lync Server 2013 management packs](installing-the-lync-server-2013-management-packs.md)
    
- [Configuring the Lync Server computers that will be monitored in Lync Server 2013](configuring-the-lync-server-computers-that-will-be-monitored.md)
    
- [Installing and configuring watcher nodes in Lync Server 2013](installing-and-configuring-watcher-nodes.md)
    

