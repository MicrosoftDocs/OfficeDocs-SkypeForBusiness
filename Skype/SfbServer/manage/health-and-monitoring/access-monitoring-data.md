---
title: "Access monitoring data in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 845385ca-5532-4fa2-91b9-51c6de6fec91
description: "Summary: Learn about the monitoring data used in Skype for Business Server."
---

# Access monitoring data in Skype for Business Server
 
**Summary:** Learn about the monitoring data used in Skype for Business Server.
  
Monitoring data is stored in a pair of SQL Server databases: LcsCdr for call detail recording data, and QoEMetrics for Quality of Experience data. There is nothing special about these two databases; that means that the data stored in those databases can be accessed using any of the tools you typically use for accessing and analyzing SQL Server data.
  
One tool you should consider for accessing and analyzing monitoring data is the Skype for Business Server Monitoring Reports. Monitoring Reports are a set of standard reports that are published by Microsoft SQL Server Reporting Service. These reports, which are accessible by using a web browser, provide usage, call diagnostic information, and media quality information, all based on call detail recording (CDR) and Quality of Experience (QoE) records stored in the CDR and QoE databases. Monitoring Reports ship with Skype for Business Server and can be installed from the Skype for Business Server Deployment Wizard after Skype for Business Server has been installed and monitoring has been configured.
  
As noted, Monitoring Reports requires the use of SQL Server Reporting Service. SQL Server Reporting Service can be installed at the same time you install SQL Server or can be installed any time after SQL Server itself has been installed.
  
For more information, see the topic [Install Monitoring Reports in Skype for Business Server](../../deploy/deploy-monitoring/install-monitoring-reports.md).
  

