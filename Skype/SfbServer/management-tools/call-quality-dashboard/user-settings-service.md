---
title: "User Settings Service for Call Quality Dashboard (CQD)"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: eafeb54a-2574-415b-b991-a0ff0470d8c3
description: "Summary: Learn about the User Settings Service, which is part of the Repository API for Call Quality Dashboard. Call Quality Dashboard is a tool for Skype for Business Server."
---

# User Settings Service for Call Quality Dashboard (CQD)
 
**Summary:** Learn about the User Settings Service, which is part of the Repository API for Call Quality Dashboard. Call Quality Dashboard is a tool for Skype for Business Server.
  
The User Settings Service is part of the Repository API for Call Quality Dashboard.
  
## User Settings Service

User settings are key-value pairs that applications can use to store metadata for various purposes including customization of application behaviors per-user basis. Each user receives a storage for user settings. Only the owners can add, modify, and remove user settings.
  
 **Global Settings**
  
Global settings are the user settings owned by the system user, and all users have read-only access to them. Global settings are constants: they are created during the repository creation, and they never change.
  
Each user can override global settings by creating user settings with the same keys. When application requests the effective user settings, the API returns a set of global settings merged with the user settings, with each user setting superseding the respective global setting if keys are the same. The API can also return just the user settings so that applications can find out which settings are overridden. 
  
The REST operations are included in the following table.

|**Operation**|**Description**|
|:-----|:-----|
|[Get User Settings](get-user-settings.md) <br/> |Get User Settings returns a list of settings for a specified user.  <br/> |
|[Get User Setting](get-user-setting.md) <br/> |Get User Setting returns a single user setting.  <br/> |
   

