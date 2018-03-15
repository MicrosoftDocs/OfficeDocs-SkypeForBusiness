---
title: "Enabling or disabling Archiving of IM or conferencing sessions in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: aa4b5983-dbe1-4d64-8a18-fe2c33994e94
description: "In Lync Server 2013 Control Panel, you use Archiving configurations to enable and disable archiving of IM, conferencing sessions, or both. This includes the following Archiving configurations:"
---

# Enabling or disabling Archiving of IM or conferencing sessions in Lync Server 2013
[]
In Lync Server 2013 Control Panel, you use Archiving configurations to enable and disable archiving of IM, conferencing sessions, or both. This includes the following Archiving configurations:
  
- A global configuration that is created by default when you deploy Lync Server 2013.
    
- Optional site-level and pool-level configurations that you can create and use to specify how archiving is implemented for specific sites or pools.
    
You initially set up Archiving configurations when you deploy Archiving, but you can change, add, and delete configurations after deployment. For details about how Archiving configurations are implemented, including which options you can specify and the hierarchy of Archiving configurations, see [How Archiving works in Lync Server 2013](how-archiving-works.md) in the Planning documentation, Deployment documentation, or Operations documentation. 
  
> [!NOTE]
> To use archiving, you must configure Archiving policies to specify whether to enable archiving for internal communications, for external communications, or for both for users homed on Lync Server 2013. By default, archiving is not enabled for either internal or external communications. Before enabling Archiving in any policies, you should specify the appropriate Archiving configurations for your deployment and, optionally, for specific sites and pools, as described in this section. For details about enabling Archiving, see [Configuring and assigning Archiving policies in Lync Server 2013](configuring-and-assigning-archiving-policies.md) in the Deployment documentation. > If you decide after you deploy Archiving that you want to use Microsoft Exchange integration to store archiving data and files on Exchange 2013 servers and all your users are homed on your Exchange 2013 servers, you should remove the SQL Server database configuration from your topology. You must use Topology Builder to do this. For details, see [Changing Archiving database options in Lync Server 2013](changing-archiving-database-options.md) in the Operations documentation. 
  
### To enable or disable archiving of IM or conferencing sessions

1. From a user account that is assigned to the CsArchivingAdministrator or CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Monitoring and Archiving**, and then click **Archiving Configuration**.
    
4. Select the appropriate global, site, or pool configuration from the list of archiving configurations, click **Edit**, click **Show details**, and then do the following:
    
  - To enable archiving only for instant messaging (IM) sessions, click **Archive IM sessions**.
    
  - To enable archiving for both IM sessions and conferences, click **Archive IM and conferencing sessions**.
    
  - To disable archiving for the policy, click **Disable archiving**.
    
5. Click **Commit**.
    
## See also

#### 

[Managing Archiving configuration options in Lync Server 2013 for your organization, sites, and pools](managing-archiving-configuration-options-for-your-organization-sites-and-pools.md)
  
[Configuring and assigning Archiving policies in Lync Server 2013](configuring-and-assigning-archiving-policies.md)

