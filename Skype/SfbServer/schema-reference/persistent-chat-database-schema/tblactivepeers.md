---
title: "tblActivePeers"
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
ms.assetid: b50c3f4a-bab6-4cb9-b40e-016cf1a9c607
description: "tblActivePeers contains the current peer-to-peer connections between chat services."
---

# tblActivePeers
 
tblActivePeers contains the current peer-to-peer connections between chat services.
  
**Columns**

|**Column**|**Type**|**Description**|
|:-----|:-----|:-----|
|aplServerID  <br/> |int, not null  <br/> |ID of the server that posted the entry.  <br/> |
|aplPeerID  <br/> |int, not null  <br/> |ID of the peer that the posting server is connected to.  <br/> |
   
**Keys**

|**Column**|**Description**|
|:-----|:-----|
|\<aplServerID, aplPeerID\>  <br/> |Primary key.  <br/> |
|aplServerID  <br/> |Foreign key with lookup in tblServerIdentity.serverID table.  <br/> |
|aplPeerID  <br/> |Foreign key with lookup in tblServerIdentity.serverID table.  <br/> |
   

