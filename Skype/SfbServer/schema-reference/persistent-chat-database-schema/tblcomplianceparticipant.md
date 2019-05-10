---
title: "tblComplianceParticipant"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 5d7e0dea-74f7-46d1-badf-b94abc8f066d
description: "tblComplianceParticipant contains the current participants per channel and per server."
---

# tblComplianceParticipant
 
tblComplianceParticipant contains the current participants per channel and per server.
  
**Columns**

|**Column**|**Type**|**Description**|
|:-----|:-----|:-----|
|channelUri  <br/> |nvarchar (255), not null  <br/> |Channel Uniform Resource Identifier (URI).  <br/> |
|userId  <br/> |int, not null  <br/> |Principal ID of the participant (corresponding to tblPrincipal.prinID table).  <br/> |
|joinedAt  <br/> |bigint, not null  <br/> |Time stamp of the joining event.  <br/> |
|partedAt  <br/> |bigint  <br/> |Null if participant is still joined. The time stamp of the channel leaving event if not null.  <br/> These entries are eventually removed when all translators process the event.  <br/> |
|userUri  <br/> |nvarchar(255), not null  <br/> |User URI.  <br/> |
|serverID  <br/> |int  <br/> |Server identity (as in tblServerIdentity.serverID table).  <br/> |
|sessionId  <br/> |bigint  <br/> |Server session. This is a random number generated each time a Chat service starts. It is used to differentiate sessions for the purpose of identifying orphaned participants.  <br/> |
   
**Key**

|**Column**|**Description**|
|:-----|:-----|
|\<channelUri, userId, joinedAt\>  <br/> |Primary key.  <br/> |
   

