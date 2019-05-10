---
title: "Persistent Chat database schema"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 10/20/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 58d7d94f-42f5-4c3e-8fe5-901fbe92152e
description: "This documents the schema of the Persistent Chat database in Skype for Business Server."
---

# Persistent Chat database schema
 
This documents the schema of the Persistent Chat database in Skype for Business Server.
  
The Persistent Chat database refers to the database corresponding to the Skype for Business Server Back End Server roles **PersistentChatStore** (corresponding to the mgc database) and **PersistentChatComplianceStore** (corresponding to the mgccomp database). The goal of publishing this schema is to enable you to build queries and gain some insights into building useful reporting around chat usage, active rooms, top posters, and so on.
  
> [!IMPORTANT]
> We reserve the right to evolve this schema. Microsoft does not make any guarantees to maintain full backward compatibility with this published schema. 
  
Follow these best practices:
  
- No SELECT\* // is supported because the column list can grow.
    
- No user-generated schema modifications are supported.
    
- No write operations are supported.
    
- Test any queries that you build on representatively-sized databases to be sure that the queries can perform at a level to meet your needs.
    
## In this section

- [List of Persistent Chat Server tables](list-of-persistent-chat-server-tables.md)
    
- [List of Persistent Chat Server compliance tables in Skype for Business Server](list-of-persistent-chat-server-compliance-tables.md)
    
- [Persistent Chat Server table details](persistent-chat-server-table-details.md)
    
- [Sample Persistent Chat database queries](sample-persistent-chat-database-queries.md)
    

