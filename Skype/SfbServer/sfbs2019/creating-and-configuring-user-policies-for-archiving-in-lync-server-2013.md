---
title: "Creating and configuring user policies for Archiving in Lync Server 2013"
ms.author: crowe
author: CarolynRowe
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 5af0e605-3563-4d6f-a3c6-511d204a3165
description: "To enable or disable Archiving for specific users homed on Lync Server, you must first create a user policy and then apply the policy to one or more users or user groups. For details about applying user policies to specific users and user groups, see Applying a Lync Server Archiving policy to a user in Lync Server 2013 in the Deployment documentation."
---

# Creating and configuring user policies for Archiving in Lync Server 2013
[]
To enable or disable Archiving for specific users homed on Lync Server, you must first create a user policy and then apply the policy to one or more users or user groups. For details about applying user policies to specific users and user groups, see [Applying a Lync Server Archiving policy to a user in Lync Server 2013](applying-a-lync-server-archiving-policy-to-a-user.md) in the Deployment documentation. 
  
For details about how Archiving policies work, including the hierarchy for global, site, and user policies, see [How Archiving works in Lync Server 2013](how-archiving-works.md) in the Planning documentation, in the Deployment documentation, or in the Operations documentation. 
  
> [!NOTE]
> If you enabled Microsoft Exchange integration for your deployment, Exchange In-Place Hold policies control whether archiving is enabled for the users who are homed on Exchange 2013 and have their mailboxes put on In-Place Hold. For details, see [Setting up policies for Archiving in Lync Server 2013 when using Exchange Server integration](setting-up-policies-for-archiving-when-using-exchange-server-integration.md) in the Deployment documentation. > You should specify all appropriate options in the Archiving configurations before enabling Archiving. For details, see [Configuring Archiving options in Lync Server 2013](configuring-archiving-options.md) in the Deployment documentation. 
  
### To configure an archiving policy for users homed on Lync Server

1. From a user account that is assigned to the CsArchivingAdministrator or CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server 2013 Control Panel. For details about the different methods that you can use to start Lync Server 2013 Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Monitoring and Archiving**, and then click **Archiving Policy**.
    
4. Click **New**, and then click **User policy**.
    
5. In **New Archiving Policy**, do the following:
    
  - In **Name**, specify the name for the user policy. 
    
  - In **Description**, provide information about what the user policy is (for example, user policy for legal department).
    
  - To control archiving of internal communications for the user policy, select or clear the **Archive internal communications** check box. 
    
  - To control archiving of external communications for the user policy, select or clear the **Archive external communications** check box. 
    
6. Click **Commit**.
    
A user policy applies only to users to whom you assign the policy. For details about applying a user policy to specific users, see [Applying a Lync Server Archiving policy to a user in Lync Server 2013](applying-a-lync-server-archiving-policy-to-a-user.md) in the Deployment documentation. 

