---
title: "Dialogs table in Skype for Business Server 2015"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 487a430b-af66-4ea6-b28e-4e33cfdb7f9e
description: "The Dialogs table is a supporting table that stores the information about DialogIDs for peer-to-peer sessions."
---

# Dialogs table in Skype for Business Server 2015
 
The Dialogs table is a supporting table that stores the information about DialogIDs for peer-to-peer sessions.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**SessionIdTime** <br/> |datetime  <br/> |Primary  <br/> |Time of session request; used in conjunction with SessionIDSeq to uniquely identify a session.  <br/> |
|**SessionIdSeq** <br/> |int  <br/> |Primary  <br/> |ID number to identify the session. Used in conjunction with SessionIDTime to uniquely identify a session.  <br/> |
|**ExternalChecksum** <br/> |int  <br/> | <br/> |Checksum of the ExternalID. This field is used to increase the speed of database searches.  <br/> |
|**ExternalId** <br/> |varbinary(775)  <br/> | <br/> |SIP dialog ID, stored as a binary. The format of the binary is:  <br/> dialog;from-tag;to-tag  <br/> This data can be converted to text format by using this syntax:  <br/>  `cast(cast(ExternalId as varbinary(max)) as varchar(max))` <br/> |
   

