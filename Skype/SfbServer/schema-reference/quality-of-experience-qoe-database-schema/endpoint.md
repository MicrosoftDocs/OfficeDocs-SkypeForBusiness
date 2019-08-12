---
title: "Endpoint table"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 2/1/2018
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 500f330d-4d7d-4e88-b1cc-fef9a9de6b5c
description: "The Endpoint table is a supporting table that stores information about the endpoints that have participated in sessions recorded in the database. Each record in the table represents one endpoint."
---

# Endpoint table
 
The Endpoint table is a supporting table that stores information about the endpoints that have participated in sessions recorded in the database. Each record in the table represents one endpoint.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**EndpointKey** <br/> |int  <br/> |Primary  <br/> |Unique number identifying this endpoint.  <br/> |
|**Name** <br/> |nvarchar(256)  <br/> |Unique  <br/> |Endpoint name.  <br/> |
|**OS** <br/> |nvarchar(128)  <br/> | <br/> |Operating system (OS) of the endpoint.  <br/> |
|**CPUName** <br/> |nvarchar(128)  <br/> ||CPU name of the endpoint.  <br/> |
|**CPUNumberOfCores** <br/> |smallint  <br/> ||Number of CPU cores of the endpoint.  <br/> |
|**CPUProcessorSpeed** <br/> |int  <br/> ||CPU processor speed of the endpoint.  <br/> |
|**VirtualizationFlag** <br/> |tinyint  <br/> || Bit flag that indicates if the system is running in a virtualized environment: <br/>  0x0000 - None <br/>  0x0001 - HyperV <br/>  0x0002 - VMWare <br/>  0x0004 - Virtual PC <br/>  0x0008 - Xen PC <br/> |
   

