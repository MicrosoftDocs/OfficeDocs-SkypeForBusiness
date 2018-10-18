---
title: "Patch or update a SQL Server in an AlwaysOn Availability Group in Skype for Business Server"
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 7298254b-bc33-450e-846a-2612f6dc7006
description: "Summary: Find out about the necessary additional steps after you patch or upgrade a Back End Server that is part of a AlwaysOn Availability Group in Skype for Business Server."
---

# Patch or update a SQL Server in an AlwaysOn Availability Group in Skype for Business Server
 
**Summary:** Find out about the necessary additional steps after you patch or upgrade a Back End Server that is part of a AlwaysOn Availability Group in Skype for Business Server.
  
After patching a Back End Server that is part of an AlwaysOn Availability Group, you must republish the topology.
  
### Patching or updating a SQL Server that is part of an AlwaysOn Availability Group

1. Install the update on your Skype for Business server or servers.
    
2. Run the following PowerShell command in your Skype for Business Management Shell (logged in with an account that's appropriately permissioned to apply changes to the SQL AlwaysOn databases) as follows:
    
    ```
    Install-CsDatabase -Update -ConfiguredDatabases -SqlServerFqdn [sqlpool.contoso.com] -Verbose
    ```

    Where [sqlpool.contoso.com] is replaced with the fully qualified domain name (FQDN) of your AlwaysOn availability group.
    

