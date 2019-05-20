---
title: "User Service for CQD"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: abd5c828-42dd-4f48-bf87-29993193cb3a
description: "Summary: Learn about the User Service, which is part of the Repository API for Call Quality Dashboard. Call Quality Dashboard is a tool for Skype for Business Server."
---

# User Service for CQD
 
**Summary:** Learn about the User Service, which is part of the Repository API for Call Quality Dashboard. Call Quality Dashboard is a tool for Skype for Business Server.
  
The User Service is part of the Repository API for Call Quality Dashboard.
  
## User Service

Repository API provides a simplified user management model where user provisioning (creating new user accounts) is automatic and implicit. When a user make a request against Repository API for the first time, the repository creates a new User record. 
  
Call Quality Dashboard also automatically creates a user dedicated items for the new user. The new user dedicated items are complete clones of system user's items. This way, users start with their own copies of Reports and Queries that they can immediately start customizing. 
  
> [!NOTE]
> Using Call Quality Dashboard, users can reset their dedicated items anytime. 
  
 **Special User IDs**
  
Repository API includes REST API URIs that expects an integer value to specify a particular user. Example:  `https://<portal>/QoERepositoryService/repository/user/{userId}`. Here, {userId} should be replaced by an integer value such as 0, 1, etc.
  
Moreover, Repository API will accept two special user IDs at {userId} in URIs.
  
-  *default*  - represents the user who is currently interacting with the API. This allows applications to access current user's contents without keeping track of the actual user ID value. Example: ` https://<portal>/QoERepositoryService/repository/user/default`.
    
-  *system*  - represents the system user. This allows applications to access the system user's contents without knowing the actual user ID value. Example: `https://<portal>/QoERepositoryService/repository/user/system`.
    
Unless otherwise noted, the special user IDs can be used at {userId} in URIs. 
  
The REST operations are included in the following table.
  
|**Operation**|**Description**|
|:-----|:-----|
|[Get Users](get-users.md) <br/> |Returns a list of users in the repository.  <br/> |
|[Get User](get-user.md) <br/> |Returns a user record.  <br/> |
   

