---
title: "Remove the Archiving server association"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "To remove an Archiving Server, you need to change or clear the dependency on the associated Front End pool, Front End Server, Survivable Branch Appliance and Survivable Branch Server. You edit the properties of the Front End pool, Front End Server, Survivable Branch Appliance and Survivable Branch Server to remove the dependency. After you clear the dependency and you delete the server in Topology Builder, you are notified that the associated database store object in Topology Builder will also be deleted."
---

# Remove the Archiving server association

To remove an Archiving Server, you need to change or clear the dependency on the associated Front End pool, Front End Server, Survivable Branch Appliance, and Survivable Branch Server. You edit the properties of the Front End pool, Front End Server, Survivable Branch Appliance, and Survivable Branch Server to remove the dependency. After you clear the dependency and delete the server in Topology Builder, you are notified that the associated database store object in Topology Builder will also be deleted.
  
### To remove the Archiving Server association

1. On the Skype for Business Server 2019 Front End Server, open Topology Builder.
    
2. Navigate to the legacy install node.
    
3. In Topology Builder, expand **Enterprise Edition Front End pools**, **Standard Edition Front End Servers**, or **Branch sites**, depending on where the Archiving Server is defined.
    
4. If you have Survivable Branch Server associated, expand **Branch sites**, expand the branch site name, and then expand **Survivable Branch Appliances**.
    
    > [!NOTE]
    > **Survivable Branch Appliances** in the user interface applies to both Survivable Branch Server and Survivable Branch Appliance. 
  
5. Right-click the pool, server, or device that is associated with the Archiving Server, and then click **Edit Properties**.
    
6. In **Edit Properties**, under **General** > **Associations**, clear the **Associate Archiving Server** check box, and then click **OK**.
    
7. Repeat the previous step for any other pool, server, or device associated with the Archiving Server that you want to remove.
    
8. Right-click the Archiving Server, and then click **Delete**.
    
9. On **Delete Dependent Stores**, click **OK**.
    
10. Publish the topology, check replication status, and then run the Skype for Business Server Deployment Wizard as needed. 
    

