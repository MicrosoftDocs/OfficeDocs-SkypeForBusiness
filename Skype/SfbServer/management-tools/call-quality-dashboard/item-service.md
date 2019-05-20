---
title: "Item Service for Call Quality Dashboard (CQD)"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: b6d7b02a-a34e-4fef-986c-ca442e18fa0c
description: "Summary: Learn about the Item Service, which is part of the Repository API for Call Quality Dashboard. Call Quality Dashboard is a tool for Skype for Business Server."
---

# Item Service for Call Quality Dashboard (CQD)
 
**Summary:** Learn about the Item Service, which is part of the Repository API for Call Quality Dashboard. Call Quality Dashboard is a tool for Skype for Business Server.
  
The Item Service is part of the Repository API for Call Quality Dashboard.
  
## Item Service

Repository API offers a simple content management service, known as item service, that can be used for storing any application-defined contents for users. 
  
The system contents are owned by the system user and shared by all users with read-only access. Dedicated user contents are owned by regular users, and only the owners can modify or delete them, but all users still have read-only access to them.
  
> [!NOTE]
> This API documentation covers read-only operations of Repository API. 
  
Call Quality Dashboard saves Reports and Queries as Items in the repository database. An Item can have optional sub-Items, and Call Quality Dashboard organizes Reports and Queries in an hierarchical structure using sub-Items feature.
  
Item service includes the following concepts:
  
- **Item** - the basic element of repository. Each Item is owned by exactly one User.
    
- **Sub-Item** - the basic organizational mechanics of repository. Item can have zero, one, or more subordinate Items.
    
- **Item Ancestors** - the list of Items, beginning from the top-most Item, which is the default Item of the User, leading to a given Item.
    
- **Item Content** - the application-specific content stored in Items. Call Quality Dashboard saves JSON representations of Reports and Queries in Contents.
    
The REST operations are included in the following table.
  

|**Operation**|**Description**|
|:-----|:-----|
|[Get Items](get-items.md) <br/> |Get Items returns all Items in the repository.  <br/> |
|[Get Item](get-item.md) <br/> |Get Item returns a specific Item.  <br/> |
|[Get Sub-Items](get-sub-items.md) <br/> |Get Sub-Items returns a specific Item's sub-Items.  <br/> |
|[Get Item Ancestors](get-item-ancestors.md) <br/> |Get Item Ancestors returns a specific Item's ancestors.  <br/> |
|[Update Item](update-item.md) <br/> |Update a specific item in the repository.  <br/> |
   

