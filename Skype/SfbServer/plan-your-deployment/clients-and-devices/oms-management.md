---
title: "Plan Microsoft Teams Rooms management with OMS"
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
ms.collection: M365-voice
description: "This article discusses planning considerations for using Operations Management Suite to administer Microsoft Teams Rooms devices in your Skype for Business Server implementation."
---

# Plan Microsoft Teams Rooms management with OMS
 
 This article discusses planning considerations for using Operations Management Suite to administer Microsoft Teams Rooms devices in your Skype for Business Server implementation.
  
[Operations Management Suite](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview) (OMS) is a collection of management services that were designed in the cloud from the start. Rather than deploying and managing on-premise resources, OMS components are entirely hosted in Azure. Configuration is minimal, and you can be up and running literally in a matter of minutes. With some customization work, it can aid in managing Microsoft Teams Rooms conferencing systems by providing real-time notifications of system health or faults for individual room systems, and it can potentially scale up to managing thousands of Microsoft Teams Rooms conference rooms.
  
This article provides a discussion of the requirements, design/architecture, and implementation best practices needed to implement OMS management of Microsoft Teams Rooms conference devices, and provides links to detailed articles on implementing OMS management for Microsoft Teams Rooms and critical reference information for ongoing OMS management of Microsoft Teams Rooms rooms. 
  
## Functional overview

![diagram of SRS management using OMS](../../media/3f2ae1b8-61ea-4cd6-afb4-4bd75ccc746a.png)
  
The Microsoft Teams Rooms app on the console device writes events to its Windows Event Log. An OMS agent, once installed, passes the information to OMS. 
  
Once properly configured, OMS parses the JSON payload embedded in the event descriptions to describe how each Microsoft Teams Rooms system is functioning and what faults are detected. 
  
An administrator using OMS can get notifications of Microsoft Teams Rooms systems that are offline or are experiencing app, connectivity, or hardware failures as well as knowing if a system needs to be restarted. Each system status is updated every five minutes, so these notifications are close to real-time updates.
  
## OMS requirements

You must have a valid subscription for OMS to use this feature. See [Get started with a Log Analytics workspace](https://docs.microsoft.com/azure/log-analytics/log-analytics-get-started?toc=%2fazure%2foperations-management-suite%2ftoc.json) to create a subscription for your organization.
  
You should familiarize yourself as necessary on how to use the OMS View Designer. See [Views in Operations Management Suite (OMS) management solutions](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-solutions-resources-views) for those details.
  
### Related Tasks

1. Once subscribed to OMS, create custom fields (as described in [Map custom fields](../../deploy/deploy-clients/with-oms.md#Custom_fields)) needed to parse the information that will be sent from Microsoft Teams Rooms consoles. This includes understanding the JSON schema documented in [Understand the log entries](../../manage/skype-room-systems-v2/oms.md#understand-the-log-entries).
    
2. Develop a Microsoft Teams Rooms management view in OMS. You can either [Create a Microsoft Teams Rooms dashboard by using the import method](../../deploy/deploy-clients/with-oms.md#create-a-microsoft-teams-rooms-dashboard-by-using-the-import-method) or [Create a Microsoft Teams Rooms dashboard manually](../../deploy/deploy-clients/with-oms.md#create-a-microsoft-teams-rooms-dashboard-manually).
    
## Individual Microsoft Teams Rooms Console requirements

Each Microsoft Teams Rooms console is an app running on a Surface 4 device in kiosk mode (normally, it's configured to be the only app that can run on the device). As with any Windows app, the Microsoft Teams Rooms app writes events like startup and hardware faults to the Windows Event Log. Adding an OMS agent on your Microsoft Teams Rooms device allows these events to be collected by OMS. (See [Connect Windows computers to the Log Analytics service in Azure](https://docs.microsoft.com/azure/log-analytics/log-analytics-windows-agents) for details.)
  
## Ongoing management

While using OMS to manage your Microsoft Teams Rooms conference devices, you'll need to understand the information contained in the event logs used by OMS. See [Understand the log entries](../../manage/skype-room-systems-v2/oms.md#understand-the-log-entries) for details on these health messages.
  
### Related Tasks

- Understand the Alerts generated by Microsoft Teams Rooms and how to resolve them (see the section titled [Understand the log entries](../../manage/skype-room-systems-v2/oms.md#understand-the-log-entries))
    
## See also

[Deploy Microsoft Teams Rooms management with OMS](../../deploy/deploy-clients/with-oms.md)
  
[Manage Microsoft Teams Rooms devices with OMS](../../manage/skype-room-systems-v2/oms.md)