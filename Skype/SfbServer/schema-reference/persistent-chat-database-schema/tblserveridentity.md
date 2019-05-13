---
title: "tblServerIdentity"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
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
   

