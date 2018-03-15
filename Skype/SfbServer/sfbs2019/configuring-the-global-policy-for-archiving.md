---
title: "Configuring the global policy for Archiving in Lync Server 2013"
ms.author: crowe
author: CarolynRowe
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 58341d6b-c3ff-4dd9-b1c7-0048f33861ca
description: "When you deploy your Front End Servers, Lync Server creates a global policy for Archiving. By default, Archiving is disabled in the global policy. The global policy controls whether archiving is enabled for internal and external communications for your entire deployment, unless you set up site or user policies, which override the global policy, or if you use Microsoft Exchange integration for some or all of your users. If you use Microsoft Exchange integration, the global policy does not apply to any users who are homed on Exchange 2013 and have the mailboxes put on In-Place Hold."
---

# Configuring the global policy for Archiving in Lync Server 2013
[]
When you deploy your Front End Servers, Lync Server creates a global policy for Archiving. By default, Archiving is disabled in the global policy. The global policy controls whether archiving is enabled for internal and external communications for your entire deployment, unless you set up site or user policies, which override the global policy, or if you use Microsoft Exchange integration for some or all of your users. If you use Microsoft Exchange integration, the global policy does not apply to any users who are homed on Exchange 2013 and have the mailboxes put on In-Place Hold.
  
For details about how Archiving policies work, including the hierarchy for global, site, and user policies, see [How Archiving works in Lync Server 2013](how-archiving-works.md) Planning documentation, Deployment documentation, or Operations documentation. 
  
> [!NOTE]
> If you enable Microsoft Exchange integration for your deployment, Exchange In-Place Hold policies control whether archiving is enabled for the users who are homed on Exchange 2013 and have their mailboxes put on In-Place Hold. For details, see [Setting up policies for Archiving in Lync Server 2013 when using Exchange Server integration](setting-up-policies-for-archiving-when-using-exchange-server-integration.md) in the Deployment documentation. > You should specify all appropriate options in the Archiving configurations before enabling Archiving. For details, see [Configuring Archiving options in Lync Server 2013](configuring-archiving-options.md) in the Deployment documentation. 
  
### To configure the global policy for archiving when using Lync Server Archiving databases

1. From a user account that is assigned to the CsArchivingAdministrator or CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server 2013 Control Panel. For details about the different methods you can use to start Lync Server 2013 Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Monitoring and Archiving**, and then click **Archiving Policy**.
    
4. On the **Archiving Policy** page, click **Global**, click **Edit**, and then click **Show details**.
    
5. In **Edit Archiving Policy - Global**, do the following:
    
  - In **Name**, if you do not want to use the default name of Global, specify a new name for the global policy. 
    
  - In **Description**, provide information about what the policy is (for example, Global policy for  *divisionName*  ). 
    
  - To control archiving of internal communications for all sites and users not specifically controlled through a site policy or user policy, select or clear the **Archive internal communications** check box. 
    
  - To control archiving of external communications for all sites and users not specifically controlled through a site policy or user policy, select or clear the **Archive external communications** check box. 
    
6. Click **Commit**.
    

