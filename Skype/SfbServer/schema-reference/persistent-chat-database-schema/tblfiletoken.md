---
title: "tblFileToken"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 49e7dd79-1607-443c-818a-88c160e4ed06
description: "tblFileToken contains temporary tokens for file transfer purposes."
---

# tblFileToken
 
tblFileToken contains temporary tokens for file transfer purposes.
  
**Columns**

|**Column**|**Type**|**Description**|
|:-----|:-----|:-----|
|fileToken  <br/> |nvarchar (50), not null  <br/> |Unique token (a GUID).  <br/> |
|fileTokenUserID  <br/> |int, not null  <br/> |ID of the principal that is transferring the file.  <br/> |
|fileTokenChannelID  <br/> |GUID, not null  <br/> |GUID of the chat room node.  <br/> |
|fileTokenExpireDate  <br/> |datetime, not null  <br/> |Expiration time. (Tokens expire after 30 minutes, unless pinned (see the following descriptions in this column).  <br/> |
|fileTokenComplianceFileUrl  <br/> |nvarchar(256)  <br/> |URL of the transferred file (for Compliance service use).  <br/> |
|fileTokenComplianceThumbnailUrl  <br/> |nvarchar(256)  <br/> |URL of the thumbnail for the transferred file (for Compliance service use).  <br/> |
|fileTokenComplianceTime  <br/> |datetime2  <br/> |Timestamp for the actual file transfer operation (for Compliance service use).  <br/> |
|fileTokenComplianceIsUpload  <br/> |bit  <br/> |True if upload; False if download (for Compliance service use).  <br/> |
|fileTokenCompliancePinned  <br/> |bit, not null  <br/> |True if token is pinned. It's used to keep the token in the table until Compliance service has a chance to retrieve the relevant fields from it.  <br/> |
   
**Keys**

|**Column**|**Description**|
|:-----|:-----|
|fileToken  <br/> |Primary key.  <br/> |
|fileTokenChannelID  <br/> |Foreign key with lookup in tblNode.nodeGuid table.  <br/> |
   

