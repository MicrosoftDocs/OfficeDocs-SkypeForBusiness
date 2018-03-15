---
title: "Install server components for Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 186aed6e-7adf-4a92-9f2e-f9a4de5ff202
description: "Before following these steps, make sure you're logged onto the server with a domain user account that's both a local administrator and a member of the RTCUniversalReadOnlyAdmins group in Active Directory."
---

# Install server components for Lync Server 2013
[]
Before following these steps, make sure you're logged onto the server with a domain user account that's both a local administrator and a member of the RTCUniversalReadOnlyAdmins group in Active Directory.
  
The Lync Server Deployment Wizard is used to install the needed components for each Lync server role and to activate the server. This article walks you through the steps of deploying a Standard Edition server or a Front End Server in your Lync infrastructure.
  
### To install Lync Server components

1. If the Lync Server Deployment Wizard isn't running, start it on the server you want to install Lync onto. 
    
2. Click **Install or Update Lync Server System**. 
    
3. In the Deployment Wizard, confirm that **Step 1: Install Local Configuration Store** has a green check mark, which means that this server has a local copy of the store installed successfully. If it's not checked, you need to install the Local Configuration store on the server. Follow the steps at [Install the Local Configuration store in Lync Server 2013](install-the-local-configuration-store.md) and then come back here. 
    
4. When you're ready to install the Lync Server 2013 components on your server, click **Run** next to **Step 2: Setup or Remove Lync Server Components**.
    
5. On the **Set Up Lync Server Components** page, click **Next** to set up components as defined in your published topology. 
    
6. The **Executing Commands** page will display a summary of commands and installation information as the set up takes place. When it's done, you can use the list to select a log to view, and then click **View Log**.
    
7. When Lync Server 2013 components setup is done, and you've reviewed the logs as needed, click **Finish** to complete this step in the installation. 
    
    > [!NOTE]
    > If you're prompted to restart the server (which might happen if Windows Desktop Experience needed to be installed), definitely do that. When the computer is back up and running, you need to do these steps over again, starting from step three listed above (basically run Step 2 in the Deployment Wizard one more time). 
  

