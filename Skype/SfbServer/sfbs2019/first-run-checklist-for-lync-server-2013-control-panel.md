---
title: "First Run Checklist for Lync Server 2013 Control Panel"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/11/2015
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.lscp.Home1stRunChkList
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 4d0c7306-e87e-464a-82ad-a5537f141500
description: "Welcome to the Lync Server 2013 Control Panel, the new web-based user interface for administration and management of Lync Server 2013. You can use the control panel to perform the types of administrative tasks that were performed by using cmdlets in the Lync Server Management Shell in previous releases."
---

# First Run Checklist for Lync Server 2013 Control Panel
[]
Welcome to the Lync Server 2013 Control Panel, the new web-based user interface for administration and management of Lync Server 2013. You can use the control panel to perform the types of administrative tasks that were performed by using cmdlets in the Lync Server Management Shell in previous releases.
  
There are a number of important tasks that we strongly recommend you perform after you have deployed Lync Server 2013. Some of these tasks are initial configuration steps that you may have already performed during deployment, while others are refinements or modifications to settings that you configured during deployment or default settings. Other tasks described in this topic validate the configurations you made during the deployment process.
  
> [!NOTE]
> Before performing the Lync Server Control Panel tasks in the following table, ensure that you log on using the correct user rights, permissions, and role as described in the "Roles and Scope" section of the [Planning for role-based access control in Lync Server 2013](planning-for-role-based-access-control-rbac.md) topic in the Planning documentation. 
  
## First Run Checklist

We strongly recommend that you review the tasks referred to in this topic, and then perform the appropriate procedures for the Lync Server 2013 deployment in your organization.
  
|**Task**|**Lync Server Control Panel group**|**Documentation**|
|:-----|:-----|:-----|
|Verify the services that you installed in your topology are running as expected.  <br/> |**Topology** <br/> |[View details about a service in Lync Server 2013](view-details-about-a-service.md) <br/> |
|Enable users for Lync Server 2013. Optionally and, if migrating from a previous release of Lync Server, move users to Lync Server 2013.  <br/> |**Users** <br/> |[User accounts enabled for Lync Server 2013](user-accounts-enabled-for-lync-server-2013.md) <br/> |
|If you deployed or want to deploy Enterprise Voice, configure a SIP trunk connection to enable connectivity to the public switched telephone network (PSTN).  <br/> |**Voice Routing** <br/> |[Configuring trunks in Lync Server 2013](configuring-trunks.md) <br/> |
|If you deployed Enterprise Voice, verify Enterprise Voice routing settings.  <br/> |**Voice Routing** <br/> |[Test voice routing in Lync Server 2013](test-voice-routing.md) <br/> |
|If you deployed Archiving Server, verify that archiving policies and settings meet the compliance needs of your organization.  <br/> |**Monitoring and Archiving** <br/> |[Managing Lync Server 2013 Archiving](managing-lync-server-2013-archiving.md) <br/> |
|If you deployed Monitoring Server, view Monitoring Server reports to view usage and diagnostic information.  <br/> |**Home** <br/> |[Monitoring and health configuration in Lync Server 2013](monitoring-and-health-configuration.md) <br/> |
   

