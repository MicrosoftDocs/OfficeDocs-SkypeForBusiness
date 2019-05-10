---
title: "SIPResponseMetaData table"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 10/20/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: cf723737-4a75-4352-829b-f4954aa59716
description: "The SIPResponseMetaDataTable contains a list of SIP response codes and the classification and definition of each of those codes. These codes are generated in response to events affecting SIP devices and SIP communication sessions; for example, the response code 403 is generated when a SIP device makes a request, but the server declines to honor that request."
---

# SIPResponseMetaData table
 
The SIPResponseMetaDataTable contains a list of SIP response codes and the classification and definition of each of those codes. These codes are generated in response to events affecting SIP devices and SIP communication sessions; for example, the response code 403 is generated when a SIP device makes a request, but the server declines to honor that request.
  
This table was introduced in Skype for Business Server 2015.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**ResponseCode** <br/> |int  <br/> |Primary  <br/> |Numeric value that represents the SIP response code.  <br/> |
|**Class** <br/> |int  <br/> || General classification for the response code. Classifications include: <br/>  1 - Informational Responses <br/>  2 - Successful Responses <br/>  3 - Redirection Responses <br/>  4 - Client Failure Responses <br/>  5 -- Server Failure Responses <br/>  6 - Global Failure Response <br/> |
|**Description** <br/> |nvarchar(256)  <br/> ||Description of the SIP response code. For example, response code 181 has the following description:  <br/> Call Is Being Forwarded  <br/> |
   

