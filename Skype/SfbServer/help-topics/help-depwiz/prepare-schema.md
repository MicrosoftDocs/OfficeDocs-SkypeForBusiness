---
title: "Prepare Schema"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 2/8/2018
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.dep.DeployMainSchemaPrep
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 337aa234-c5f3-4468-a047-2023848e942c
description: 'To prepare the schema for Active Directory Domain Services, you run the Prepare Schema step in the Skype for Business Server Deployment Wizard. Click Run to begin the preparation of the schema. The Prepare Schema step reads the supplied schema definition files in the /Program Files/Microsoft Lync Server 2013/Deployment/Setup directory on the system that the Deployment Wizard is running on. These files are also available on the installation media in the Support/Schema directory. The Prepare Schema step will extend the schema and report the status of the process. It will also notify you when the process is complete. The summary screen will enable you to view the logs of the process. Review the logs to be sure that the preparation was complete and successful.'
---

# Prepare Schema
 
To prepare the schema for Active Directory Domain Services, you run the Prepare Schema step in the Skype for Business Server Deployment Wizard. Click **Run** to begin the preparation of the schema. The Prepare Schema step reads the supplied schema definition files in the \Program Files\Microsoft Lync Server 2013\Deployment\Setup directory on the system that the Deployment Wizard is running on. These files are also available on the installation media in the \Support\Schema directory. The Prepare Schema step will extend the schema and report the status of the process. It will also notify you when the process is complete. The summary screen will enable you to view the logs of the process. Review the logs to be sure that the preparation was complete and successful.
  
> [!IMPORTANT]
> To extend the schema, you must be logged into the domain as a member of the Schema Admins group and the Enterprise Admins group. 
  
Classes and attributes are added to extend the Active Directory Domain Services schema to support Skype for Business Server 2015 server, service, and user objects. Before extending the schema, you should take a System State backup of the domain controller that holds the schema master role. For details about the backup process for Windows Server 2008 R2 with SP1, see [https://go.microsoft.com/fwlink/p/?linkId=207198](https://go.microsoft.com/fwlink/p/?linkId=207198). For Windows Server 2003 and Windows Server 2003 R2, see [https://go.microsoft.com/fwlink/p/?linkId=207199](https://go.microsoft.com/fwlink/p/?linkId=207199).
  
> [!CAUTION]
> Extending the schema is not reversible. You should make all possible efforts to limit the potential impact of a failed schema extension, and to ensure that the extension of the schema will be successful. This is particularly critical in the event of loss of communication or any other failure at the server. You should perform a backup of the schema master domain controller and a complete backup of Active Directory. 
  
To perform a backup of the schema master domain controller and a complete backup of Active Directory:
  
1. Disconnect the domain controller that holds the schema master role from the network.
    
2. Perform a System State backup of the domain controller that holds the schema master.
    
3. Extend the schema.
    
4. When the schema extension is successful, reconnect the domain controller to the network, and be sure that replication is active and working.
    
5. In the unlikely event of a schema extension failure, restore the systems state of the domain controller and Active Directory by using the System State backup that you took earlier.
    
> [!NOTE]
> If you need to review the log files that are created by the Skype for Business Server Deployment Wizard, you can find the files on the computer where the Deployment Wizard was run, in the Users directory of the Active Directory user who ran the step. For example, if the user logged in as the domain administrator in the domain Contoso.net, the log files are located in: C:\Users\Administrator.Contoso\AppData\Local\Temp 
  

