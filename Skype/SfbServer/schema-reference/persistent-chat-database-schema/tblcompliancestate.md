---
title: "tblComplianceState"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: ea82e56c-3cca-4d89-b4e6-6bcaeb1f2830
description: "tblComplianceState contains pool-wide compliance state information."
---

# tblComplianceState
 
tblComplianceState contains pool-wide compliance state information.
  
**Columns**

|**Column**|**Type**|**Description**|
|:-----|:-----|:-----|
|lastProcessedEntryID  <br/> |bigint, not null  <br/> |ID of the latest processed compliance event.  <br/> |
|activeServerID  <br/> |int, not null  <br/> |ID of the Compliance server holding the exclusive lock on the database, or -1 if none.  <br/> |
|lockExpirationTime  <br/> |datetime2, not null  <br/> |Lock expiration time (if activeServerID is not -1).  <br/> |
   

