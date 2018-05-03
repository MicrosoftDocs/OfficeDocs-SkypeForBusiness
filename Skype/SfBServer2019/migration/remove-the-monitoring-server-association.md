---
title: "Remove the Monitoring server association"
ms.author: kenwith
author: kenwith
manager: serdars
ms.date: 11/17/2018
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c45b22ae-fc06-484a-a05b-735bd1bb7448
description: "To remove the Monitoring Server, you need to change or clear the dependency on the associated Front End pool, Front End Server, Survivable Branch Appliance and Survivable Branch Server. You edit the properties of the Front End pool, Front End Server, Survivable Branch Appliance and Survivable Branch Server to remove the dependency. After you clear the dependency and delete the server in Topology Builder, you are notified that the associated database store object in Topology Builder will also be deleted."
---

# Remove the Monitoring server association
[]
To remove the Monitoring Server, you need to change or clear the dependency on the associated Front End pool, Front End Server, Survivable Branch Appliance and Survivable Branch Server. You edit the properties of the Front End pool, Front End Server, Survivable Branch Appliance and Survivable Branch Server to remove the dependency. After you clear the dependency and delete the server in Topology Builder, you are notified that the associated database store object in Topology Builder will also be deleted.
  
### To remove the Monitoring Server association

1. Open the Lync Server 2013 Front End Server, open Topology Builder.
    
2. Navigate to the Lync Server 2010 node.
    
3. In Topology Builder, expand **Enterprise Edition Front End pools**, **Standard Edition Front End Servers**, or **Branch sites**, based on where the Monitoring Server is defined.
    
4. If you have Survivable Branch Server associated, expand **Branch sites**, expand the branch site name, and then expand **Survivable Branch Appliances**.
    
    > [!NOTE]
    > **Survivable Branch Appliances** in the user interface applies to both Survivable Branch Server and Survivable Branch Appliance. 
  
5. Right-click the pool, server, or device that is associated with the Monitoring Server, and then click **Edit Properties**.
    
6. In **Edit Properties**, under **General**, under **Associations**, clear the **Associate Monitoring Server** check box, and then click **OK**.
    
7. Repeat the previous step for any other pool, server or device associated with the Monitoring Server.
    
8. Right-click the Monitoring Server, and then click **Delete**. 
    
9. On **Delete Dependent Stores**, click **OK**.
    
10. Publish the topology, check replication status, and run the Lync Server Deployment Wizard as needed. 
    

