---
title: Patch or update a SQL Server in an AlwaysOn Availability Group in Skype for Business Server 2015
ms.prod: SKYPEFORBUSINESS
ms.assetid: 7298254b-bc33-450e-846a-2612f6dc7006
---


# Patch or update a SQL Server in an AlwaysOn Availability Group in Skype for Business Server 2015
[] **Summary:** Find out about the necessary additional steps after you patch or upgrade a Back End Server that is part of a AlwaysOn Availability Group in Skype for Business Server.
After patching a Back End Server that is part of an AlwaysOn Availability Group, you must republish the topology.
  
    
    


### Patching or updating a SQL Server that is part of an AlwaysOn Availability Group


1. Perform the patch on the server.
    
  
2. Make sure that in Topology Builder, the FQDN of the listener for the AlwaysOn Availability Group is set as the FQDN for the group. 
    
  - Open Topology Builder, select ** Download topology from existing deployment**, and click **OK**.
    
  
  - Expand Skype for Business Server, expand your topology, and expand **SQL Server Stores**. Right-click the SQL store of the new AlwaysOn Availability Group, and click ** Edit Properties**.
    
  
  - At the bottom of the page, in the **SQL Server FQDN** box, change the value to the FQDN of the Listener of the AlwaysOn Availability Group.
    
  
3. Publish the topology. From the **Action** menu click **Topology** and then **Publish**. Then in the confirmation page click **Next**.
    
  

