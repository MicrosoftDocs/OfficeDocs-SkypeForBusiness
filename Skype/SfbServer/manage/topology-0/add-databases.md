---
title: "Add databases to an AlwaysOn Availability Group in Skype for Business Server 2015"
ms.author: kenwith
author: kenwith
manager: serdars
ms.date: 1/30/2018
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 026c4469-f471-4e4f-a77d-a7d22a925e5a
description: "Summary: Learn how to add more Skype for Business Server databases to an existing AlwaysOn Availability Group in Skype for Business Server 2015."
---

# Add databases to an AlwaysOn Availability Group in Skype for Business Server 2015
 
**Summary:** Learn how to add more Skype for Business Server databases to an existing AlwaysOn Availability Group in Skype for Business Server 2015.
  
### Adding databases to an AlwaysOn Availability Group

1. Open SQL Server Management Studio, and navigate to the AlwaysOn Availability Group. Fail it over to the primary replica.
    
2. In Topology Builder, set the SQL Server FQDN of the AlwaysOn Availability Group to the FQDN of the primary node of that group.
    
  - Open Topology Builder, select **Download topology from existing deployment**, and click **OK**.
    
  - Expand Skype for Business Server, expand your topology, and expand **SQL Server Stores**. Right-click the SQL store of the new AlwaysOn Availability Group, and click **Edit Properties**.
    
  - At the bottom of the page, in the **SQL Server FQDN** box, type in the FQDN of the primary node of the AlwaysOn Availability Group.
    
3. Publish the topology. From the **Action** menu click **Topology** and then **Publish**. Then in the confirmation page click **Next**.
    
4. Use SQL Server Management Studio to add the new database to the AlwaysOn Availability Group.
    

