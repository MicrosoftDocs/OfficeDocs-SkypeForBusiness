---
title: "First Run Checklist for Skype for Business Server Control Panel"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/23/2015
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.lscp.Home1stRunChkList
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 4d0c7306-e87e-464a-82ad-a5537f141500
description: "Welcome to the Skype for Business Server Control Panel, the web-based user interface for administration and management of Skype for Business Server. You can use the control panel to perform the types of administrative tasks that were performed for by using the Microsoft Management Console in previous releases."
---

# First Run Checklist for Skype for Business Server Control Panel

Welcome to the Skype for Business Server Control Panel, the web-based user interface for administration and management of Skype for Business Server. You can use the control panel to perform the types of administrative tasks that were performed for by using the Microsoft Management Console in previous releases.

There are a number of important tasks that we strongly recommend you perform after you have deployed Skype for Business Server. Some of these tasks are initial configuration steps that you may have already performed during deployment, while others are refinements or modifications to settings that you configured during deployment or default settings. Other tasks described in this topic validate the configurations you made during the deployment process.

> [!NOTE]
> Before performing the tasks in the following table, ensure that you log on using the correct user rights, permissions, and role as described in the "Roles and Scope" section of the [Role-Based Access Control](https://technet.microsoft.com/library/41204ba3-ce5b-41a8-a6c3-b444468fa328.aspx) topic.

## First Run Checklist

We strongly recommend that you review the tasks referred to in this topic, and then perform the appropriate procedures for the Lync Server deployment in your organization.

|**Task**|**Control Panel group**|**Documentation**|
|:-----|:-----|:-----|
|Verify the services that you installed in your topology are running as expected.  <br/> |**Topology** <br/> |[View Details About a Service](https://technet.microsoft.com/library/bc8e8202-cd68-47e4-95b2-bb36e51cc124.aspx) <br/> |
|Enable users for Skype for Business Server. Optionally and, if migrating from a previous release, move users to Skype for Business Server.  <br/> |**Users** <br/> |[Managing Users](https://technet.microsoft.com/library/8021087e-5084-4a39-9fef-ab9376c6d371.aspx) <br/> |
|If you deployed or want to deploy Enterprise Voice, configure a SIP trunk connection to enable connectivity to the public switched telephone network (PSTN).  <br/> |**Voice Routing** <br/> |[Configuring Trunks and Translation Rules](https://technet.microsoft.com/library/0c339511-a185-484e-94f0-dbe918b7e48a.aspx) <br/> |
|If you deployed Enterprise Voice, verify Enterprise Voice routing settings.  <br/> |**Voice Routing** <br/> |[Test Voice Routing](https://technet.microsoft.com/library/d3aae909-fef6-440f-b144-0b62dc82bf5d.aspx) <br/> |
|If you deployed Archiving Server, verify that archiving policies and settings meet the compliance needs of your organization.  <br/> |**Monitoring and Archiving** <br/> |[Managing Archiving](https://technet.microsoft.com/library/48c6cc8c-c2c1-4534-9a8a-fd5eb738076a.aspx) <br/> |
|If you deployed Monitoring Server, view Monitoring Server reports to view usage and diagnostic information.  <br/> |**Home** <br/> |[Manage health and monitoring in Skype for Business Server 2015](../../manage/health-and-monitoring/health-and-monitoring.md) <br/> |


