---
title: "Monitor, start, and stop the Persistent Chat services in Skype for Business Server 2015"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 3/28/2016
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.assetid: b6b28595-f702-4ecf-8115-e4104b87da89
description: "Summary: Learn how to start, stop, and monitor the Persistent Chat services in Skype for Business Server 2015."
---

# Monitor, start, and stop the Persistent Chat services in Skype for Business Server 2015
 
**Summary:** Learn how to start, stop, and monitor the Persistent Chat services in Skype for Business Server 2015.
  
The Persistent Chat services and Persistent Chat Compliance services are part of the Skype for Business Server topology and can therefore be monitored, stopped, and started by using the following cmdlets:
  
|Cmdlet|Function|
|:-----|:-----|
|get-CsWindowsService  <br/> |Returns detailed information about Skype for Business Server 2015 components that run as Windows services.  <br/> |
|start-CsWindowsService  <br/> |Starts the service.  <br/> |
|stop-CsWindowsService  <br/> |Stops the service.  <br/> |
   
> [!NOTE]
> Persistent chat is available in Skype for Business Server 2015 but is no longer supported in Skype for Business Server 2019. The same functionality is available in Teams. For more information, see [Getting started with your Microsoft Teams upgrade](/microsoftteams/upgrade-start-here). If you need to use Persistent chat, your choices are to either migrate users requiring this functionality to Teams, or to continue using Skype for Business Server 2015. 

For detailed information about how to use the cmdlets, see [Skype for Business Server 2015 Management Shell](../management-shell.md).
  

