---
title: "First Run Checklist for Skype for Business Server Control Panel"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
audience: ITPro
ms.topic: article
ms.custom:
- ms.lync.lscp.Home1stRunChkList
ms.prod: skype-for-business-itpro
f1.keywords:
- CSH
ms.localizationpriority: medium
ms.assetid: 4d0c7306-e87e-464a-82ad-a5537f141500
ROBOTS: NOINDEX, NOFOLLOW
description: "Welcome to the Skype for Business Server Control Panel, the web-based user interface for administration and management of Skype for Business Server. You can use the control panel to perform the types of administrative tasks that were performed for by using the Microsoft Management Console in previous releases."
---

# First Run Checklist for Skype for Business Server Control Panel

Welcome to the Skype for Business Server Control Panel, the web-based user interface for administration and management of Skype for Business Server. You can use the control panel to perform the types of administrative tasks that were performed for by using the Microsoft Management Console in previous releases.

There are a number of important tasks that we strongly recommend you perform after you have deployed Skype for Business Server. Some of these tasks are initial configuration steps that you may have already performed during deployment, while others are refinements or modifications to settings that you configured during deployment or default settings. Other tasks described in this topic validate the configurations you made during the deployment process.

> [!NOTE]
> Before performing the tasks in the following table, ensure that you log on using the correct user rights, permissions, and role as described in the "Roles and Scope" section of the [Role-Based Access Control](/previous-versions/office/lync-server-2013/lync-server-2013-planning-for-role-based-access-control) topic.

## First Run Checklist

We strongly recommend that you review the tasks referred to in this topic, and then perform the appropriate procedures for deployment in your organization.

|**Task**|**Control Panel group**|**Documentation**|
|:-----|:-----|:-----|
|Verify the services that you installed in your topology are running as expected.  <br/> |**Topology** <br/> |[View Details About a Service](/previous-versions/office/lync-server-2013/lync-server-2013-view-details-about-a-service) <br/> |
|Enable users for Skype for Business Server. Optionally and, if migrating from a previous release, move users to Skype for Business Server.  <br/> |**Users** <br/> |[Managing Users](/previous-versions/office/lync-server-2013/lync-server-2013-user-accounts-enabled-for-lync-server) <br/> |
|If you deployed or want to deploy Enterprise Voice, configure a SIP trunk connection to enable connectivity to the public switched telephone network (PSTN).  <br/> |**Voice Routing** <br/> |[Configuring Trunks and Translation Rules](/previous-versions/office/lync-server-2013/lync-server-2013-configuring-trunks) <br/> |
|If you deployed Enterprise Voice, verify Enterprise Voice routing settings.  <br/> |**Voice Routing** <br/> |[Test Voice Routing](/previous-versions/office/lync-server-2013/lync-server-2013-test-voice-routing) <br/> |
|If you deployed Archiving Server, verify that archiving policies and settings meet the compliance needs of your organization.  <br/> |**Monitoring and Archiving** <br/> |[Managing Archiving](/previous-versions/office/lync-server-2013/lync-server-2013-managing-archiving) <br/> |
|If you deployed Monitoring Server, view Monitoring Server reports to view usage and diagnostic information.  <br/> |**Home** <br/> |[Manage health and monitoring in Skype for Business Server](../../../manage/health-and-monitoring/health-and-monitoring.md) <br/> |