---
title: "Persistent Chat database schema in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 58d7d94f-42f5-4c3e-8fe5-901fbe92152e
description: "This documents the schema of the Persistent Chat database in Lync Server 2013 communications software."
---

# Persistent Chat database schema in Lync Server 2013
[]
This documents the schema of the Persistent Chat database in Lync Server 2013 communications software.
  
The Persistent Chat database refers to the database corresponding to the Lync Server 2013 Back End Server roles **PersistentChatStore** (corresponding to the mgc database) and **PersistentChatComplianceStore** (corresponding to the mgccomp database). The goal of publishing this schema is to enable you to build queries and gain some insights into building useful reporting around chat usage, active rooms, top posters, and so on. 
  
> [!IMPORTANT]
> We reserve the right to evolve this schema. Microsoft does not make any guarantees to maintain full backward compatibility with this published schema. 
  
Follow these best practices:
  
- No SELECT\* // is supported because the column list can grow.
    
- No user-generated schema modifications are supported.
    
- No write operations are supported.
    
- Test any queries that you build on representatively-sized databases to be sure that the queries can perform at a level to meet your needs.
    
## In this section

- [List of Persistent Chat Server tables in Lync Server 2013](list-of-persistent-chat-server-tables.md)
    
- [List of Persistent Chat Server compliance tables in Lync Server 2013](list-of-persistent-chat-server-compliance-tables.md)
    
- [Persistent Chat Server table details in Lync Server 2013](persistent-chat-server-table-details.md)
    
- [Sample Persistent Chat database queries for Lync Server 2013](sample-persistent-chat-database-queries.md)
    

