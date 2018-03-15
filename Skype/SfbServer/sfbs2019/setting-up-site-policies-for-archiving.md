---
title: "Setting up site policies for Archiving in Lync Server 2013"
ms.author: crowe
author: CarolynRowe
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: dc2ea206-8b9c-44dd-a479-efb217593c89
description: "You can enable or disable Archiving for specific sites by creating and configuring an Archiving policy for each of those sites. A site policy overrides the global policy, but user policies override site policies. Archiving policies only apply if you do not use Microsoft Exchange integration or, if you do use Microsoft Exchange integration, but have some users who are not homed on Exchange 2013 and have their mailboxes put on In-Place Hold."
---

# Setting up site policies for Archiving in Lync Server 2013
[]
You can enable or disable Archiving for specific sites by creating and configuring an Archiving policy for each of those sites. A site policy overrides the global policy, but user policies override site policies. Archiving policies only apply if you do not use Microsoft Exchange integration or, if you do use Microsoft Exchange integration, but have some users who are not homed on Exchange 2013 and have their mailboxes put on In-Place Hold.
  
For details about how Archiving policies work, including the hierarchy for global, site, and user policies, see [How Archiving works in Lync Server 2013](how-archiving-works.md) Planning documentation, Deployment documentation, or Operations documentation. 
  
> [!NOTE]
> If you enable Microsoft Exchange integration for your deployment, Exchange In-Place Hold policies control whether archiving is enabled for the users who are homed on Exchange 2013 and have their mailboxes put on In-Place Hold. For details, see [Setting up policies for Archiving in Lync Server 2013 when using Exchange Server integration](setting-up-policies-for-archiving-when-using-exchange-server-integration.md) in the Deployment documentation. > You should specify all appropriate options in the Archiving configurations before enabling Archiving of internal or external communications in the Archiving policies. For details, see [Configuring Archiving options in Lync Server 2013](configuring-archiving-options.md) in the Deployment documentation. 
  
### To create an archiving policy for a site

1. From a user account that is assigned to the CsArchivingAdministrator or CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server 2013 Control Panel.
    
3. In the left navigation bar, click **Monitoring and Archiving**, and then click **Archiving Policy**.
    
    For details about how Archiving policies work, including the hierarchy for global, site, and user policies, see [How Archiving works in Lync Server 2013](how-archiving-works.md) Planning documentation, Deployment documentation, or Operations documentation. 
    
4. Click **New**, and then click **Site policy**.
    
5. In **Select a site**, click the site to which the policy is to be applied.
    
6. In **New Archiving Policy**, do the following:
    
  - In **Name**, specify the name for the site policy. 
    
  - In **Description**, provide information about what the site policy is (for example, site policy for Redmond).
    
  - To control archiving of internal communications for the specified site, select or clear the **Archive internal communications** check box. 
    
  - To control archiving of external communications for the specified site, select or clear the **Archive external communications** check box. 
    
7. Click **Commit**.
    

