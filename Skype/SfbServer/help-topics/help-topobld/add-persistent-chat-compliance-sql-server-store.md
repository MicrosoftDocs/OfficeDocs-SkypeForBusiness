---
title: "Add Persistent Chat Compliance SQL Server Store"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 3/27/2015
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.AddPersistentChatComplianceStorePage
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: b9771b53-e19a-4a12-bf01-24bae6f7e482
description: "You configure the compliance SQL Server stores that will provide databases for the Persistent Chat Server or Persistent Chat Server compliance feature."
---

# Add Persistent Chat Compliance SQL Server Store
 
You configure the compliance SQL Server stores that will provide databases for the Persistent Chat Server or Persistent Chat Server compliance feature.
  
 **SQL Server store**: Select an existing SQL Server and optionally an instance for Persistent Chat.
  
Click **New** to define a new SQL Server and optionally a new instance for the Persistent Chat compliance data.
  
Select the **Enable SQL Server store mirroring** checkbox to configure a SQL Server database and optional instance that will provide a mirrored database for the Persistent Chat compliance data.
  
Select from the list **Mirroring SQL Server store** a SQL Server and optional instance to act as the SQL Server mirror for the Persistent Chat compliance SQL Server.
  
Click **New** to define a new SQL Server and optionally a new instance for the Persistent Chat SQL Server mirroring.
  
Select the list **Use SQL Server mirroring witness to enable automatic failover** a SQL Server that will act as the witness server in failover scenarios. The witness server does not mirror or host data for the Persistent Chat servers, but ensures that only one SQL Server in a mirrored configuration is the active SQL Server at any time.
  
Click **New** to define a new SQL Server witness optionally an instance for the Persistent Chat compliance SQL Server mirroring witness.
  
Click **Back** to go back to the previous pool definition dialog.
  
Click **Next** after you have finished entering the options for this pool's backup SQL Server store configuration and to proceed with the Persistent Chat Server pool definition.
  
Click **Cancel** to discard all changes and end the **Define New Persistent Chat Pool** wizard.
  
Click **Help** to access context sensitive help, such as this page.
  
## See also

[Plan for Persistent Chat Server in Skype for Business Server 2015](../../plan-your-deployment/persistent-chat-server/persistent-chat-server.md)
  
[Server requirements for Skype for Business Server 2015](../../plan-your-deployment/requirements-for-your-environment/server-requirements.md)
  
[Hardware and software requirements for Persistent Chat Server in Skype for Business Server 2015](../../plan-your-deployment/persistent-chat-server/hardware-and-software-requirements.md)
  
[Configure the Compliance service for Persistent Chat Server in Skype for Business Server 2015](../../manage/persistent-chat/configure-compliance.md)
