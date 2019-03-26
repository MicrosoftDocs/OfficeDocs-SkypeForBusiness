---
title: "tblComplianceData"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 05b28f9b-4aba-4b69-ba8d-2ceeb6cbfaac
description: "tblComplianceData contains the compliance events that have not been processed by the compliance adapter yet."
---

# tblComplianceData
 
tblComplianceData contains the compliance events that have not been processed by the compliance adapter yet.
  
**Columns**

|**Column**|**Type**|**Description**|
|:-----|:-----|:-----|
|cmplEventID  <br/> |bigint, not null  <br/> |Event ID.  <br/> |
|entryDate  <br/> |smalldatetime, not null  <br/> |Time of insertion (may be far in the future for cmplType=9 because the entry is just a placeholder in that case).  <br/> |
|cmplType  <br/> |int, not null  <br/> | Type of compliance event: <br/>  1: Chat <br/>  2: Backchat <br/>  3: File download <br/>  4: File upload <br/>  9: Provisional file transfer <br/>  10: Chat deletion (with replace) <br/>  11: Chat purging <br/> |
|cmplTime  <br/> |bigint, not null  <br/> |Time stamp for the event.  <br/> |
|cmplChannelUri  <br/> |nvarchar (255), not null  <br/> |Channel Uniform Resource Identifier (URI).  <br/> |
|cmplChatID  <br/> |bigint  <br/> |Chat ID (corresponding to tblChat.chatId table).  <br/> |
|cmplUserID  <br/> |int, not null  <br/> |Principal ID of the poster (corresponding to tblPrincipal.prinID table).  <br/> |
|cmplUserUri  <br/> |nvarchar (255), not null  <br/> |User URI.  <br/> |
|cmplMessage  <br/> |nvarchar (max)  <br/> |Message (encoding depends on cmplType).  <br/> |
   
**Key**

|**Column**|**Description**|
|:-----|:-----|
|cmplEventID  <br/> |Primary key.  <br/> |
   

