---
title: "Plan Call Data Connector"
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
description: "Overview of using Skype for Business Online telemetry tools to monitor an on-premises implementation in a hybrid scenario."
---
<!-- PM William Looney  -->



# Plan Call Data Connector

[!INCLUDE [disclaimer](../disclaimer.md)]

## Overview
This topic describes benefits, planning considerations, and requirements for implementing Skype for Business Server Call Data Connector.  For more information on configuring Call Data Connector, see INSERT LINK HERE.

Call Data Connector greatly simplifies call monitoring in a hybrid environment because you no longer need to use different sets of on-premises and online tools to monitor all of your users call quality.  Whether your users are homed on premises or online, you can choose to view call quality for your entire organization online.

With Call Data Connector, the Skype for Business Server pushes call data to the cloud service so that you can leverage the Skype for Business Online Call Analytics (CA) and Call Quality Dashboard (CQD) tools, as shown in the following diagram:

![SfB Cloud Voicemail](../../sfbserver2019/media/call-data-connector-plan-1.png)

The server pushes both Quality of Experience (QoE) and Session Initiation Protocol (SIP) data to the online service.

The Call Analytics and CQD tools enable you to monitor the quality of calls and troubleshoot connection problems with Microsoft Teams and Skype for Business services as follows:

- Call Analytics focuses on quality problems with specific calls. It shows detailed information about calls and meetings for each user in a Skype for Business acouunt.  With Call Analytics, you can assign permissions to a Helpdesk operator who can then monitor calls without having access to the rest of the Skype for Business Admin center.

- Call Quality Dashboard focuses on network performance and issues across an organization. Skype for Business administrators and network engineers use this tool to troubleshoot and optimize network performance.

For more information on Call Analytics and Call Quality Dashboard, see INSERT LINK(S) HERE.

Of course, you might want to keep some call quality data on premises. This might be the case, for example, if you are using a third-party solution with customized reports and workflows.  Call Data Connector allows you to configure sending some data to the cloud while keeping other data on premises, as shown in the following diagram:

![SfB Cloud Voicemail](../../sfbserver2019/media/call-data-connector-plan-2.png)


## Requirements

The following requirements assume that you already have Skype for Business Server deployed in a supported topology.  For more information about deploying Skype for Business Server and supported topologies, see INSERT LINK HERE.

If you already have Skype for Business Server deployed, and you want to enable Call Data Connector, the following are required:        

  **IS THE FOLLOWING CORRECT?**

- Hybrid connectivity between your on-premises server and the online service. This is sometimes called a split domain configuration. For details, see Plan hybrid connectivity and Configure hybrid connectivity.

- Azure Active Directory (AAD) Connect, which is used to synchronize your on-premises directory with Office 365. For more information, see Connect Active Directory with Azure Active Directory.

- An Office 365 tenant with Skype for Business Online enabled.  If you want to enable Teams, see Migration to Teams.

- You must have the following licenses:    **WHAT ARE THE REQUIRED LICENSES?**

- Enabled federation between your on-premises Skype for Business Server deployment and your Office 365 tenant. For more information, see Configure federation with Skype for Business Online.  

- Enabled shared Session Initiation Protocol (SIP) address space.  A SIP address is a unique identifier for each user on a network, similar to a phone number or an email address. For more information, see Configure federation with Skype for Business Online. 

- On-premises users must be enabled for ...

- Central Management Store (CMS) topology information

##Comparison of on-premises and online CQD reports

| Feature reports | Skype for Business Online | Skype for Business Server   |
|:---------------------------|:---------------------|:---------------------|:------------------|
| Application sharing metric |Yes | Limited |
| Customer building information| Yes | Yes |
| Drill-down analytics | Yes | No |
| Media reliability metrics | Yes | Limited |
| Out-of-the-box reports | Yes | Yes |
| Overview reports | Yes | No |
| Per user reports | Yes | Yes |
| Report set customization <br> (add, delete, modify reports) | Yes | Yes |
| Video-based screen sharing metrics | Yes | No |
| Data APIs for programmatic access <br> to CQD | No | Yes |



















