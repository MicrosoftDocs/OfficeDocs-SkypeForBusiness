---
title: "Plan Skype Room Systems v2 management with Azure Monitor"
ms.author: jambirk
author: jambirk
ms.reviewer: Turgayo
manager: serdars
ms.date: 2/13/2018
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 9fd16866-27eb-47a9-b335-2f6bc9044a80
description: "This article discusses planning considerations for using Azure Monitor to administer Skype Room Systems v2 devices in your Skype for Business or Teams implementation."
---

# Plan Skype Room Systems v2 management with Azure Monitor
 
 This article discusses planning considerations for using Azure Monitor to administer Skype Room Systems v2 devices in your Skype for Business Server implementation.
  
[Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview) is a collection of management services that were designed in the cloud from the start. Rather than deploying and managing on-premise resources, Azure Monitor components are entirely hosted in Azure. Configuration is minimal, and you can be up and running literally in a matter of minutes. With some customization work, it can aid in managing Skype Room Systems v2 conferencing systems by providing real-time notifications of system health or faults for individual room systems, and it can potentially scale up to managing thousands of Skype Room Systems v2 conference rooms.
  
This article provides a discussion of the requirements, design/architecture, and implementation best practices needed to implement Azure Monitor based management of Skype Room Systems v2 conference devices, and provides links to detailed articles on implementing Azure Monitor for Skype Room Systems v2 and critical reference information for ongoing monitoring of Skype Room Systems v2 rooms. 
  
## Functional overview

![diagram of SRS management using Azure Monitor](../../media/3f2ae1b8-61ea-4cd6-afb4-4bd75ccc746a.png)
  
The Skype Room Systems v2 app on the console device writes events to its Windows Event Log. A Microsoft Monitoring agent, once installed, passes the information to Azure Monitor service. 
  
Once properly configured, Log Analytics parses the JSON payload embedded in the event descriptions to describe how each Skype Room Systems v2 system is functioning and what faults are detected. 
  
An administrator using Azure Monitor can get notifications of Skype Room Systems v2 systems that are offline or are experiencing app, connectivity, or hardware failures as well as knowing if a system needs to be restarted. Each system status is updated frequently, so these notifications are close to real-time updates.
  
## Azure Monitor requirements

You must have a valid Azure subscription for Azure Monitor to use Log Analytics feature. See [Get started with a Log Analytics workspace](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace) to create a subscription for your organization.
  
You should familiarize yourself as necessary on how to use the Log Analytics View Designer. See [Views in Log Analytics ](https://docs.microsoft.com/azure/azure-monitor/platform/view-designer) for those details.
  
### Related Tasks

1. Once subscribed to Azure Monitor Log Analytics, create custom fields (as described in [Map custom fields](../../deploy/deploy-clients/azure-monitor.md#Custom_fields)) needed to parse the information that will be sent from Skype Room Systems v2 consoles. This includes understanding the JSON schema documented in [Understand the log entries](../../manage/skype-room-systems-v2/azure-monitor.md#understand-the-log-entries).
    
2. Develop a Skype Room Systems v2 management view in Log Analytics. You can either [Create a Skype Room Systems v2 dashboard by using the import method](../../deploy/deploy-clients/azure-monitor.md#create-a-skype-room-systems-v2-dashboard-by-using-the-import-method) ) or [Create a Skype Room Systems v2 dashboard manually](../../deploy/deploy-clients/azure-monitor.md#create-a-skype-room-systems-v2-dashboard-manually).
    
## Individual Skype Room Systems v2 Console requirements

Each Skype Room Systems v2 console is an app running on a Surface Pro device in kiosk mode (normally, it's configured to be the only app that can run on the device). As with any Windows app, the Skype Room Systems v2 app writes events like startup and hardware faults to the Windows Event Log. Adding an Microsoft Monitor agent on your Skype Room Systems v2 device allows these events to be collected. (See [Connect Windows computers to the Log Analytics service in Azure](https://docs.microsoft.com/azure/azure-monitor/platform/agent-windows) for details.)
  
## Ongoing management

While using Azure Monitor to manage your Skype Room Systems v2 devices, you'll need to understand the information contained in the event logs used by Azure Monitor. See [Understand the log entries](../../manage/skype-room-systems-v2/azure-monitor.md#understand-the-log-entries) for details on these health messages.
  
### Related Tasks

- Understand the Alerts generated by Skype Room Systems v2 and how to resolve them (see the section titled [Understand the log entries](../../manage/skype-room-systems-v2/azure-monitor.md#understand-the-log-entries))
    
## See also

[Deploy Skype Room Systems v2 management with Azure Monitor](../../deploy/deploy-clients/azure-monitor.md)
  
[Manage Skype Room Systems v2 devices with Azure Monitor](../../manage/skype-room-systems-v2/azure-monitor.md)