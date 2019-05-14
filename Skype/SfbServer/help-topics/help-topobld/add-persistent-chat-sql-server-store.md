---
title: "Add Persistent Chat SQL Server Store"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/27/2015
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.AddPersistentChatSqlStorePage
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: c8e6064a-8127-4c25-8685-06f49d8bbfce
description: "You configure the SQL Server stores that will provide databases for the Persistent Chat Server or Persistent Chat Server pool."
---

# Add Persistent Chat SQL Server Store
 
You configure the SQL Server stores that will provide databases for the Persistent Chat Server or Persistent Chat Server pool.
  
 **SQL Server store**: Select an existing SQL Server and optionally an instance for Persistent Chat.
  
Click **New** to define a new SQL Server and optionally a new instance for the Persistent Chat data.
  
Select the **Enable SQL Server store mirroring** checkbox to configure a SQL Server database and optional instance that will provide a mirrored database for the Persistent Chat data.
  
Select from the list **Mirroring SQL Server store** a SQL Server and optional instance to act as the SQL Server mirror for the Persistent Chat SQL Server.
  
Click **New** to define a new SQL Server and optionally a new instance for the Persistent Chat SQL Server mirroring.
  
Select the list **Use SQL Server mirroring witness to enable automatic failover** a SQL Server that will act as the witness server in failover scenarios. The witness server does not mirror or host data for the Persistent Chat servers, but ensures that only one SQL Server in a mirrored configuration is the active SQL Server at any time.
  
Click **New** to define a new SQL Server witness optionally an instance for the Persistent Chat SQL Server mirroring witness.
  
Click **Back** to go back to the previous pool definition dialog.
  
Click **Next** after you have finished entering the options for this pool's SQL Server store configuration and to proceed with the Persistent Chat Server pool definition.
  
Click **Cancel** to discard all changes and end the **Define New Persistent Chat Pool** wizard.
  
Click **Help** to access context sensitive help, such as this page.
  
## See also

[Plan for Persistent Chat Server in Skype for Business Server 2015](../../plan-your-deployment/persistent-chat-server/persistent-chat-server.md)
  
[Add Persistent Chat Server to your Skype for Business Server 2015 topology](../../deploy/deploy-persistent-chat-server/add-persistent-chat-server.md)
  
[Hardware and software requirements for Persistent Chat Server in Skype for Business Server 2015](../../plan-your-deployment/persistent-chat-server/hardware-and-software-requirements.md)
  
[Server requirements for Skype for Business Server 2015](../../plan-your-deployment/requirements-for-your-environment/server-requirements.md)
  
[Topology Basics for Skype for Business Server 2015](../../plan-your-deployment/topology-basics/topology-basics.md)
  
[Configure high availability and disaster recovery for Persistent Chat Server in Skype for Business Server 2015](../../deploy/deploy-persistent-chat-server/configure-hadr-for-persistent-chat.md)
