---
title: "Configuring Archiving options in Lync Server 2013"
ms.author: crowe
author: CarolynRowe
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b2f7f74d-e1ad-494e-9d46-5eb0efe5fb29
description: "In Lync Server 2013 Control Panel, you use Archiving configurations to specify how archiving is implemented. This includes the following Archiving configurations:"
---

# Configuring Archiving options in Lync Server 2013
[]
In Lync Server 2013 Control Panel, you use Archiving configurations to specify how archiving is implemented. This includes the following Archiving configurations:
  
- A global configuration that is created by default when you deploy Lync Server 2013.
    
- Optional site-level and pool-level configurations that you can create and use to specify how archiving is implemented for specific sites or pools.
    
You initially set up Archiving configurations when you deploy Archiving, but you can change, add, and delete configurations after deployment. In Lync Server 2013 Control Panel, you can use the **Archiving Configuration** page of the **Archiving and Monitoring** group to manage configurations at the global level, site level, and pool level. For details about how Archiving configurations are implemented, including which options you can specify and the hierarchy of Archiving configurations, see [How Archiving works in Lync Server 2013](how-archiving-works.md) in the Planning documentation, Deployment documentation, or Operations documentation. For details about how to manage configurations after deployment, see [Managing Archiving configuration options in Lync Server 2013 for your organization, sites, and pools](managing-archiving-configuration-options-for-your-organization-sites-and-pools.md) in the Operations documentation. 
  
> [!NOTE]
> To use archiving, you must configure Archiving policies to specify whether to enable archiving for internal communications, for external communications, or for both for users homed on Lync Server 2013. By default, archiving is not enabled for either internal or external communications. Before enabling Archiving in any policies, you should specify the appropriate Archiving configurations for your deployment and, optionally, for specific sites and pools, as described in this section. For details about enabling Archiving, see [Configuring and assigning Archiving policies in Lync Server 2013](configuring-and-assigning-archiving-policies.md) in the Deployment documentation. > If you do not use Microsoft Exchange integration for all users in your deployment, you must configure Archiving policies to specify whether to enable archiving for internal communications, for external communications, or for both. By default, archiving is not enabled for either internal or external communications for archiving of data when using Lync Server 2013 Archiving databases. Prior to enabling Archiving in any policies, you should specify the appropriate Archiving configurations for your deployment and, optionally, for specific sites and pools, as described in this section. For details about enabling Archiving for use with Lync Server 2013 Archiving databases, see [Configuring and assigning Archiving policies in Lync Server 2013](configuring-and-assigning-archiving-policies.md) in the Deployment documentation. 
  
## In this section

- [Configuring Archiving options at the global level in Lync Server 2013](configuring-archiving-options-at-the-global-level.md)
    
- [Configuring Archiving options for a site in Lync Server 2013](configuring-archiving-options-for-a-site.md)
    
- [Configuring Archiving options for a pool in Lync Server 2013](configuring-archiving-options-for-a-pool.md)
    

