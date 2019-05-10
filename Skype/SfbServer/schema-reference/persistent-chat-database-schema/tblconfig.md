---
title: "tblConfig"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 7445e7db-c574-46fa-b964-8640d77047a8
description: "tblConfig contains some Persistent Chat Server unsupported configuration, in one row."
---

# tblConfig
 
tblConfig contains some Persistent Chat Server unsupported configuration, in one row.
  
**Columns**

|**Column**|**Type**|**Description**|
|:-----|:-----|:-----|
|configLabel  <br/> |nvarchar (255), not null  <br/> |Contains "pool."  <br/> |
|configContent  <br/> |nvarchar (max)  <br/> |Configuration content.  <br/> |
|configPoolID  <br/> |GUID, not null  <br/> |Unique ID of the database instance.  <br/> |
   
**Key**

|**Column**|**Description**|
|:-----|:-----|
|configLabel  <br/> |Primary key.  <br/> |
   

