---
title: "tblServerIdentity"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 3/9/2015
audience: ITPro
ms.topic: article
ms.service: skype-for-business-server
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.assetid: 5411c9bc-b0b3-41fc-8b7e-fa71cccd770b
description: "tblServerIdentity contains the active chat servers in the Persistent Chat Server pool."
---

# tblServerIdentity
 
tblServerIdentity contains the active chat servers in the Persistent Chat Server pool.
  
**Columns**

|**Column**|**Type**|**Description**|
|:-----|:-----|:-----|
|serverID  <br/> |int, not null  <br/> |Server ID. Corresponds to the instance ID from Central Management store.  <br/> |
|serverAddress  <br/> |nvarchar (256), not null  <br/> |Server address using the Windows Communication Foundation address.  <br/> |
|serverLastPingTime  <br/> |datetime  <br/> |The latest time that the Channel Server updated this row to give evidence that it is running.  <br/> |
   
**Key**

|**Column**|**Description**|
|:-----|:-----|
|serverID  <br/> |Primary key.  <br/> |
   

