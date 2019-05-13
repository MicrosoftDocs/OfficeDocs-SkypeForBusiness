---
title: "Install the files for Mediation Server in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom: 
ms.assetid: f0f7dd15-58e1-40fd-aa7e-6db50ceafacd
description: "Summary: Learn how to install the files for Mediation Server in Skype for Business Server."
---

# Install the files for Mediation Server in Skype for Business Server
 
**Summary:** Learn how to install the files for Mediation Server in Skype for Business Server.
  
To successfully complete this procedure, you should be logged on to the server, at the minimum, as a local administrator and a domain user who has membership in at least the RTCUniversalReadOnlyAdmins group.
  
Use the steps in this topic to run Skype for Business Server Deployment Wizard to install the files for Mediation Server on a computer that you added to a Mediation Server pool after you have used Topology Builder to define and publish the pool. When installing files Mediation Server, you also install and assign the certificate required by each computer in a Mediation Server pool. 
  
> [!NOTE]
> This topic assumes that you have already defined and published a stand-alone Mediation Server pool in your topology, as described in [Deploy a Mediation Server in Topology Builder in Skype for Business Server](deploy-a-mediation-server.md). 
  
### To install the files for a stand-alone Mediation Server pool

1. From the installation media, right-click  _\<installation media\>_ **\Setup\amd64\Setup.exe**, and then click **Run as Administrator**.
    
2. On the **Installation Location** page, click **OK**.
    
3. On the **End User License Agreement** page, click **I accept**, and then click **OK**. (Required to continue.)
    
4. On the **Skype for Business Server Deployment Wizard** page, click **Install or Update Skype for Business Server System**.
    
5. Next to **Step 1: Install Local Configuration Store**, click **Run**, and then follow the instructions on the screen.
    
6. On the **Configure Local Replica of Central Management Store** page, accept the default **Retrieve directly from the Central Management Store**, and then click **Next**.
    
7. On the **Executing Commands** page, when the task status is shown as **Completed**, click **Finish**.
    
8. Next to **Step 2: Setup or Remove Skype for Business Server Components**, click **Run**, and then click **Next**.
    
9. On the **Executing Commands** page, when the task status is shown as **Completed**, click **Finish**.
    
10. Next to **Step 3: Request, Install or Assign Certificates**, click **Run**. Follow the instructions on the screen, accepting the default settings. The Mediation Server requires one certificate, and so you will run **Step 3** twice: once to issue the required certificate, and once more to assign it.
    
11. When the certificate has been issued and assigned correctly, beside **Step 4: Start Services**, click **Run**, and then follow the instructions on the screen.
    
12. When **Step 4** has completed successfully, restart the server, and log on to the server as a member of the DomainAdmins group.
    
13. On the computer where you are running Skype for Business Server Control Panel, verify on the **Topology** page of Skype for Business Server Control Panel that the service status of the Mediation Server is shown as a green check mark. If a red X appears instead, select the Mediation Server. On the **Action** menu, click **Start All Services**. 
    
If you added more than one computer to the Mediation Server pool, perform the steps in this procedure on all other computers in the Mediation Server pool. If you do not need to install files for Mediation Server for any other computers, then follow the procedures in [Configure trunks in Skype for Business Server](configure-trunks.md) to configure settings for the trunk connection between this Mediation Server pool (or all Mediation Servers at a site) and its peer.

