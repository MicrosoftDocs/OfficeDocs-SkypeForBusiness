---
title: Plan Call Data Connector | Call Quality Dashboard Monitoring Hybrid Analytics
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
description: "Overview of using Skype for Business Online telemetry tools to monitor an on-premises implementation in a hybrid scenario."
---

# Plan Call Data Connector

## Overview

This topic describes benefits, planning considerations, and requirements for implementing Skype for Business Server Call Data Connector. For more information on configuring Call Data Connector, see [Configure Call Data Connector](configure-call-data-connector.md).

> [!NOTE]
> At public preview release, only Call Analytics dashboard is available.

Call Data Connector greatly simplifies call monitoring in a hybrid environment because you no longer need to use different sets of on-premises and online tools to monitor all of your users call quality. Whether your users are homed on premises or online, you can choose to view call quality for your entire organization online.

With Call Data Connector, you can perform the following tasks by using a single toolset:

- Monitor your user experience across Microsoft Teams, Skype for Business Online, and Skype for Business Server.

- View and troubleshoot problems across your network.

- Assign helpdesk and administrator roles for Call Analytics, so that you can empower helpdesk workers to view and troubleshoot their areas of responsibility.

With Call Data Connector, the Skype for Business Server pushes call data to the cloud service so that you can leverage the Skype for Business Online Call Analytics (CA) and Call Quality Dashboard (CQD) tools, as shown in the following diagram:

![SfB Cloud Voicemail](../../sfbserver2019/media/call-data-connector-plan-1.png)

The server pushes both Quality of Experience (QoE) and Call Detail Recording (CDR) data to the online service.

The Call Analytics and CQD tools enable you to monitor the quality of calls and troubleshoot connection problems with Microsoft Teams and Skype for Business services as follows:

- Call Analytics focuses on quality problems with specific calls. It shows detailed information about calls and meetings for each user in a Skype for Business account.  With Call Analytics, you can assign permissions to a helpdesk operator who can then monitor calls without having access to the rest of the Skype for Business Admin center.

- Call Quality Dashboard focuses on network performance and issues across an organization. Skype for Business administrators and network engineers use this tool to troubleshoot and optimize network performance.

For more information, see [Call Analytics and Call Quality Dashboard](https://docs.microsoft.com/SkypeForBusiness/using-call-quality-in-your-organization/difference-between-call-analytics-and-call-quality-dashboard).

Of course, you might want to keep some call quality data on premises. This might be the case, for example, if you are using a third-party solution with customized reports and workflows.  Call Data Connector allows you to configure sending data to the online service while also keeping a copy of the data on your on-premises server, as shown in the following diagram:

![SfB Cloud Voicemail](../../sfbserver2019/media/call-data-connector-plan-2.png)

## Requirements

The following requirements assume that you already have Skype for Business Server deployed in a supported topology.  For more information about deploying Skype for Business Server and supported topologies, see [Topology Basics](https://docs.microsoft.com/SkypeForBusiness/plan-your-deployment/topology-basics/topology-basics). To configure Call Data Connector, you must:

- Enable Hybrid connectivity. If you already have Skype for Business Server deployed and you want to enable Call Data Connector, you must ensure that you have hybrid connectivity set up between your on-premises and online environments. This is sometimes called a split domain configuration.

   For more information, see [Plan hybrid connectivity between Skype for Business Server and Office 365](plan-hybrid-connectivity.md) and [Configure hybrid connectivity between Skype for Business Server and Office 365](configure-hybrid-connectivity.md).

- Authenticate to your Office 365 tenant and ensure that you have the following roles enabled:

  - Skype for Business Server Administrator
  - Office 365 Global Administrator

- If you have not already done so, turn on Call Quality Dashboard as described in [Turning on and using Call Quality Dashboard for Microsoft Teams and Skype for Business Online](/microsoftteams/turning-on-and-using-call-quality-dashboard).

- Enable the front end pool for Monitoring, with local LCSCdr and QoEMetrics databases. Without this, Call Data Connector won't have metrics data to work with.

> [!IMPORTANT]
> Call Data Connector will not function if Monitoring is not enabled on the front end pool.

## Comparison of on-premises and online Call Quality Dashboard (CQD) reports

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
||||
