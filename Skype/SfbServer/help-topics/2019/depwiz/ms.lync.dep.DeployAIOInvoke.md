---
ms.date: 03/17/2018
title: "Prepare Single Standard Edition Server (Invoke)"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
audience: ITPro
ms.topic: article
ms.custom:
- ms.lync.dep.DeployAIOInvoke
ms.service: skype-for-business-server
f1.keywords:
- CSH
ms.localizationpriority: medium
ms.assetid: 5da0aa73-8bf8-41f3-81e7-94f955cda541
ROBOTS: NOINDEX, NOFOLLOW
description: "On the Executing commands page, the tasks of installing the SQL Server Express and configuring to act as the Central Management store can be viewed in the task pane. By default, an instance of a SQL Server-based database named RTC is created. Firewall rules are also created to allow inbound and outbound access for servers and clients to communicate with the database and instance. After the task is completed, you can select the log file from the drop-down list. The log file is named Bootstrap local machine. After selecting the log file, click View Log. Review the log file for any errors and warnings. When you are ready to proceed, click Finish. You should now define your topology with Topology Builder if you have not already done so."
---

# Prepare Single Standard Edition Server (Invoke)
 
On the **Executing commands** page, the tasks of installing the SQL Server Express and configuring to act as the Central Management store can be viewed in the task pane. By default, an instance of a SQL Server-based database named RTC is created. Firewall rules are also created to allow inbound and outbound access for servers and clients to communicate with the database and instance. After the task is completed, you can select the log file from the drop-down list. The log file is named **Bootstrap local machine**. After selecting the log file, click **View Log**. Review the log file for any errors and warnings. When you are ready to proceed, click **Finish.** You should now define your topology with Topology Builder if you have not already done so.
  
> [!IMPORTANT]
> The installation of the SQL Server Express can take some time to complete. During the installation, there is no progress visible on the screen or the task pane. To monitor the installation, you should use Windows Task Manager and look for the MSIExec processes and the Setup files for SQL Server. In this way, you can view the status of the install and be sure that the install is proceeding. Depending on factors beyond the scope of this help topic, it can take up to 15 minutes or more for the install the SQL Server instance to complete. 
  


