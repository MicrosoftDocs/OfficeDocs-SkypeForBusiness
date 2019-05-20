---
title: "Manage databases with an AlwaysOn Availability Group in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 026c4469-f471-4e4f-a77d-a7d22a925e5a
description: "Summary: Learn how to add more Skype for Business Server databases to an existing AlwaysOn Availability Group, and learn about the necessary additional steps after you patch or upgrade a Back End Server that is part of a AlwaysOn Availability Group in Skype for Business Server."
---

# Manage databases with an AlwaysOn Availability Group in Skype for Business Server

Use the steps in this article to add more Skype for Business Server databases to an existing AlwaysOn Availability Group in Skype for Business Server, and find out about the necessary additional steps after you patch or upgrade a Back End Server that is part of a AlwaysOn Availability Group in Skype for Business Server.

## Add databases to an AlwaysOn Availability Group 

1. Open SQL Server Management Studio, and navigate to the AlwaysOn Availability Group. Fail it over to the primary replica.
    
2. In Topology Builder, set the SQL Server FQDN of the AlwaysOn Availability Group to the FQDN of the primary node of that group.
    
   - Open Topology Builder, select **Download topology from existing deployment**, and click **OK**.
    
   - Expand Skype for Business Server, expand your topology, and expand **SQL Server Stores**. Right-click the SQL store of the new AlwaysOn Availability Group, and click **Edit Properties**.
    
   - At the bottom of the page, in the **SQL Server FQDN** box, type in the FQDN of the primary node of the AlwaysOn Availability Group.
    
3. Publish the topology. From the **Action** menu click **Topology** and then **Publish**. Then in the confirmation page click **Next**.
    
4. Use SQL Server Management Studio to add the new database to the AlwaysOn Availability Group.
    
## Patch or update a SQL Server in an AlwaysOn Availability Group

After patching a Back End Server that is part of an AlwaysOn Availability Group, you must republish the topology.

1. Install the update on your Skype for Business server or servers.
    
2. Run the following PowerShell command in your Skype for Business Management Shell (logged in with an account that's appropriately permissioned to apply changes to the SQL AlwaysOn databases) as follows:
    
    ```
    Install-CsDatabase -Update -ConfiguredDatabases -SqlServerFqdn [sqlpool.contoso.com] -Verbose
    ```

    Where [sqlpool.contoso.com] is replaced with the fully qualified domain name (FQDN) of your AlwaysOn availability group.
