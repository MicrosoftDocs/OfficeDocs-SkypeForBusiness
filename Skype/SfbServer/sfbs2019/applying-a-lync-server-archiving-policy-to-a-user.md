---
title: "Applying a Lync Server Archiving policy to a user in Lync Server 2013"
ms.author: crowe
author: CarolynRowe
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a23e4876-aa8d-4f49-a3bd-3696616e8290
description: "After creating a Lync Server user policy, you must apply it to specific the users or user groups that are homed on Lync Server 2013 before it can take effect. For details about creating user policies for specific users, see Creating and configuring user policies for Archiving in Lync Server 2013 in the Deployment documentation."
---

# Applying a Lync Server Archiving policy to a user in Lync Server 2013
[]
After creating a Lync Server user policy, you must apply it to specific the users or user groups that are homed on Lync Server 2013 before it can take effect. For details about creating user policies for specific users, see [Creating and configuring user policies for Archiving in Lync Server 2013](creating-and-configuring-user-policies-for-archiving-in-lync-server-2013.md) in the Deployment documentation. 
  
For details about how Archiving policies work, including the hierarchy for global, site, and user policies, see [How Archiving works in Lync Server 2013](how-archiving-works.md) in the Planning documentation, Deployment documentation, or Operations documentation. 
  
> [!NOTE]
> In order to configure and use archiving, you must first deploy archiving. For details, see [Deploying Archiving in Lync Server 2013](deploying-archiving.md) in the Deployment documentation. > If you enabled Microsoft Exchange integration for your deployment, Exchange In-Place Hold policies control whether archiving is enabled for the users who are homed on Exchange 2013 and have their mailboxes put on In-Place Hold. For details, see [Setting up policies for Archiving in Lync Server 2013 when using Exchange Server integration](setting-up-policies-for-archiving-when-using-exchange-server-integration.md) in the Deployment documentation. > You should specify all appropriate options in the Archiving configurations before enabling Archiving. For details, see [Configuring Archiving options in Lync Server 2013](configuring-archiving-options.md) in the Deployment documentation. 
  
### To apply a Lync Server archiving policy to a user

1. From a user account that is assigned to the CsArchivingAdministrator or CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server 2013 Control Panel. For details about the different methods you can use to start Lync Server 2013 Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Users**, and then search for the user account that you want to configure.
    
4. In the table that lists the search results, click the user account, click **Edit**, and then click **Show details**.
    
5. In **Edit Lync Server user** under **Archiving policy**, select the archiving user policy that you want to apply.
    
    > [!NOTE]
    > The **\<Automatic\>** settings apply the default server installation settings. These settings are applied automatically by the server. 
  
6. Click **Commit**.
    

