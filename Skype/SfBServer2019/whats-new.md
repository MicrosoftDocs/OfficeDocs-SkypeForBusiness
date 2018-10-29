---
title: "What's new in Skype for Business Server" 
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 7/10/2018
ms.audience: ITPro
ms.topic: overview
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
description: "Summary: These features are new in Skype for Business Server 2019."
---

# What's in Skype for Business Server 2019 

**Summary:** Read this topic to learn about new features in Skype for Business Server 2019.  

New features in Skype for Business Server 2019 include the following:
  
- Cloud Voicemail  
- Call Data Connector
- Side-by-side migration
- Migration to Teams

## Unified messaging services: Cloud Voicemail 

Exchange UM remains available in Skype for Business Server 2019 when you integrate Skype for Business 2019 with Exchange 2013 or Exchange 2016. Due to changes in support in Exchange 2019, Exchange UM integration is being de-emphasised in favor of Cloud Voicemail and Cloud Auto Attendant features.  

Cloud Voicemail enables all your Skype for Business 2019 users&#x2014;whether they are homed on premises or online&#x2014;to have access to the same voicemail service in the Microsoft Cloud. Cloud Voicemail provides the following benefits for both your on-premises and online users:

- Access to voicemail in their Exchange mailbox by using the Skype for Business Online, Teams, or Outlook clients 
- Ability to use the web-based portal to manage their voicemail options

See [Plan Cloud Voicemail service](hybrid/plan-cloud-voicemail.md) and [Plan for Skype for Business Server and Exchange Server migration](hybrid/plan-um-migration.md) for more information.
  
## Call monitoring: Call Data Connector

Call Data Connector greatly simplifies call monitoring in a hybrid environment because you no longer need to use different sets of on-premises and online tools to monitor all of your users call quality.  Whether your users are homed on premises or online, you can choose to view call quality for your entire organization online.

With Call Data Connector, you can perform the following tasks by using a single toolset:

- Monitor your user experience across Microsoft Teams, Skype for Business Online, and Skype for Business Server.
- View and troubleshoot problems across your network
- Assign helpdesk and administrator roles for Call Analytics, so that you can empower helpdesk workers to view and troubleshoot their areas of responsibility. 

See [Plan Call Data Connector](hybrid/plan-call-data-connector.md) for more information.
  


## Installation and Upgrade: Side-by-side migration

In a side-by-side migration, you deploy a new server running Skype for Business Server 2019 alongside a corresponding server that is running a previous version (Skype for Business Server 2015 or Lync Server 2013), and then transfer operations to the new server. If it becomes necessary to roll back to the previous version, you have only to shift operations back to the original servers. 

For complete details, see [Migration to Skype for Business Server 2019](migration/migration-to-skype-for-business-server-2019.md).

### See also

[What's deprecated from Skype for Business Server 2019](deprecated.md)