---
title: "Managing the Archiving of internal and external communications in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6c2cf941-3204-4f1a-a7e0-416c828056d9
description: "In Lync Server 2013, you use Archiving policies to enable and disable archiving for internal communications and external communications if you do not use Microsoft Exchange integration or you have users who are not homed on Exchange 2013 with their mailboxes put on In-Place Hold. This includes the following Archiving policies:"
---

# Managing the Archiving of internal and external communications in Lync Server 2013
[]
In Lync Server 2013, you use Archiving policies to enable and disable archiving for internal communications and external communications if you do not use Microsoft Exchange integration or you have users who are not homed on Exchange 2013 with their mailboxes put on In-Place Hold. This includes the following Archiving policies:
  
- A global policy that is created by default when you deploy Lync Server 2013.
    
- Optional site-level and user-level policies that you can create and use to specify how archiving is implemented for specific sites or users.
    
You initially set up Archiving policies when you deploy Archiving, but you can change, add, and delete policies after deployment. In Lync Server 2013 Control Panel, you can use the **Archiving Policy** page of the **Archiving and Monitoring** group to manage policies at the global level, site level, and user level. If you integrate your Lync Server storage with Exchange 2013 storage, the Exchange user policies take precedence over the Lync Server 2013 archiving policies. 
  
For details about how policies are implemented, including the hierarchy of policies, see [How Archiving works in Lync Server 2013](how-archiving-works.md) in the Planning documentation, Deployment documentation, or Operations documentation. 
  
> [!NOTE]
> To control the implementation of Archiving, you must specify options in Archiving configurations, such as whether to archive IM or conferencing, the use of critical mode, and purging options. By default no options are enabled in the global Archiving configuration or any site or pool Archiving configuration. You should specify all appropriate options in the Archiving configurations before enabling Archiving for internal or external communications in the Archiving policies. For details, see [Managing Archiving configuration options in Lync Server 2013 for your organization, sites, and pools](managing-archiving-configuration-options-for-your-organization-sites-and-pools.md) in the Operations documentation. > If you enable Microsoft Exchange integration for your deployment, Exchange policies control whether archiving is enabled for the users who are homed on Exchange 2013 and have their mailboxes put on In-Place Hold. For details, see [Setting up policies for Archiving in Lync Server 2013 when using Exchange Server integration](setting-up-policies-for-archiving-when-using-exchange-server-integration.md) in the Deployment documentation. 
  
## In this section

- [Creating an Archiving policy in Lync Server 2013 to enable or disable Archiving of Internal or external communications for specific sites or users](creating-an-archiving-policy-to-enable-or-disable-archiving-of-internal-or-exter.md)
    
- [Changing an Archiving policy in Lync Server 2013 to enable or disable Archiving of internal or external communications for your organization, sites, or users](changing-an-archiving-policy-to-enable-or-disable-archiving-of-internal-or-exter.md)
    
- [Applying an Archiving policy to users in Lync Server 2013](applying-an-archiving-policy-to-users.md)
    
- [Setting up policies for Archiving in Lync Server 2013 when using Exchange Server integration](setting-up-policies-for-archiving-when-using-exchange-server-integration.md)
    
- [Deleting an Archiving policy in Lync Server 2013](deleting-an-archiving-policy.md)
    

