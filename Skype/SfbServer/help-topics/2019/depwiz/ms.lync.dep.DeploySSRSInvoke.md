---
title: "SQL Server Reporting Services (Invoke)"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.dep.DeploySSRSInvoke
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 4a4ba8d6-ba43-45b3-b834-372d092561e7
ROBOTS: NOINDEX, NOFOLLOW
description: "After supplying the required information for the deployment of the Monitoring Server reports to the Microsoft SQL Server 2008 R2, or to Microsoft SQL Server 2012 Report Services, the page Execute Commands displays a summary of commands that are issued to install the reports to the SQL Server Reporting Services."
---

# SQL Server Reporting Services (Invoke)
 
After supplying the required information for the deployment of the Monitoring Server reports to the Microsoft SQL Server Report Services, the page Execute Commands displays a summary of commands that are issued to install the reports to the SQL Server Reporting Services.
  
Review the summary of commands and note any error or warning messages displayed from the commands. If a log file is generated, select the log file from the drop-down list under the summary window, and click **View Log** to display the log file.
  
> [!IMPORTANT]
> For the Reporting Services reports to deploy successfully, and to access the reports after deployment is complete, you must have TCP/IP port 80 (and optionally, TCP port 443 for SSL, if you assign a certificate to the Reporting Services) open in the Windows Firewall with Advanced Security on the SQL Server. For details, see [Configure the Windows Firewall to Allow SQL Server Access](https://go.microsoft.com/fwlink/p/?linkId=218031) for Microsoft SQL Server 2008 R2.
  
After reviewing the summary, click **Finish** to complete the installation of the reports to the SQL Server Reporting Services.
  

