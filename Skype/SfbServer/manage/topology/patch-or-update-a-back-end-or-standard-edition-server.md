---
title: "Patch or update a Back End Server or Standard Edition server in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: f95f8d3a-e039-484e-97bd-d727db21a12b
description: "Summary: Learn how to install an update or patch on a Back End Server in Skype for Business Server."
---

# Patch or update a Back End Server or Standard Edition server in Skype for Business Server
 
**Summary:** Learn how to install an update or patch on a Back End Server in Skype for Business Server.
  
This topic explains how to install an update on an Enterprise Edition Back End Server or a Standard Edition server.
  
If a Back End Server is down for at least 30 minutes while you are upgrading it, users may then go into resiliency mode. When the upgrade is finished and the Back End Servers has again connected with the Front End Servers in the pool, users are returned to full functionality. If the upgrade takes less than 30 minutes, users will not be affected.
  
### To update a back end server or Standard Edition server

1. Log on to the server you are upgrading as a member of the CsAdministrator role.
    
2. Download the update and extract it to the local hard disk.
    
3. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business**, and then click **Skype for Business Server Management Shell**..
    
4. Stop Skype for Business Server services. At the command line, type:
    
    ```
    Stop-CsWindowsService
    ```

5. Stop the World Wide Web service. At the command line, type:
    
    ```
    net stop w3svc
   ```

6. Close all Skype for Business Server Management Shell windows.
    
7. Install the update.
    
8. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business**, and then click **Skype for Business Server Management Shell**.
    
9. Stop Skype for Business Server services again to catch Global Assembly Cache (GAC) -d assemblies. At the command line, type:
    
    ```
    Stop-CsWindowsService
    ```

10. Restart the World Wide Web service. At the command line, type:
    
    ```
    net start w3svc
    ```

11. Apply the changes made to the SQL Server databases by doing one of the following:
    
    - If this is an Enterprise Edition Back End Server and there are no collocated databases on this server, such as Archiving or Monitoring databases, then type the following at a command line:
    
    ```
    Install-CsDatabase -Update -ConfiguredDatabases -SqlServerFqdn <SQL Server FQDN>
    ```

    - If this is an Enterprise Edition Back End Server and there are collocated databases on this server, then type the following at a command line:
    
    ```
    Install-CsDatabase -Update -ConfiguredDatabases -SqlServerFqdn <SQL Server FQDN>  -ExcludeCollocatedStores
    ```

    - If this is an Standard Edition server, type the following at a command line:
    
    ```
    Install-CsDatabase -Update -LocalDatabases

    ```
