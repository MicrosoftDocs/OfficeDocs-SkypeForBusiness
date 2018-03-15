---
title: "Setting up user policies for Archiving in Lync Server 2013"
ms.author: crowe
author: CarolynRowe
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 22d6cc76-6b5c-4a8c-bb8a-7996450ec085
description: "Enabling or disabling Archiving for specific users homed on Lync Server 2013 requires creating and configuring one or more user policies, and then applying the appropriate policy to specific users or user groups. User policies override site and global policies, but only for users homed on Lync Server 2013."
---

# Setting up user policies for Archiving in Lync Server 2013
[]
Enabling or disabling Archiving for specific users homed on Lync Server 2013 requires creating and configuring one or more user policies, and then applying the appropriate policy to specific users or user groups. User policies override site and global policies, but only for users homed on Lync Server 2013.
  
Users are always homed in Lync Server. If Microsoft Exchange integration is enabled, users whose mailboxes are in Microsoft Exchange Server 2013 don't need to have their Archiving policies in Lync Server managed. These users with Archiving will be managed by Exchange In-Place Hold.
  
For details about how Archiving policies work, including the hierarchy for global, site, and user policies, see [How Archiving works in Lync Server 2013](how-archiving-works.md) in the Planning documentation, Deployment documentation, or Operations documentation. 
  
> [!NOTE]
> If you enabled Microsoft Exchange integration for your deployment, Exchange In-Place Hold policies control whether archiving is enabled for the users who are homed on Exchange 2013. Archiving for these users requires that they have their mailboxes put on In-Place Hold. For details, see [Setting up policies for Archiving in Lync Server 2013 when using Exchange Server integration](setting-up-policies-for-archiving-when-using-exchange-server-integration.md) in the Deployment documentation. > You should specify all appropriate options in the Archiving configurations before enabling Archiving. For details, see [Configuring Archiving options in Lync Server 2013](configuring-archiving-options.md) in the Deployment documentation. 
  
## In this section

- [Creating and configuring user policies for Archiving in Lync Server 2013](creating-and-configuring-user-policies-for-archiving-in-lync-server-2013.md)
    
- [Applying a Lync Server Archiving policy to a user in Lync Server 2013](applying-a-lync-server-archiving-policy-to-a-user.md)
    

