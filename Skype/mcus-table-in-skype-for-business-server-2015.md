---
title: Mcus table in Skype for Business Server 2015
ms.prod: SKYPEFORBUSINESS
ms.assetid: 271b7963-8fd8-4d92-a701-1a62aaf895ee
---


# Mcus table in Skype for Business Server 2015
[]
The Mcus table is a supporting table. Each record stores information about one conferencing service. These can include the IM Conferencing service and the Telephony Conferencing service (which run as processes on front-end servers), and the Web Conferencing service and A/V Conferencing service. 
  
    
    



|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**McuId** <br/> |int  <br/> |Primary  <br/> |Unique number identifying this conferencing server.  <br/> |
|**McuUri** <br/> |nvarchar(450)  <br/> | <br/> | <br/> |
|**McuTypeId** <br/> |inyint  <br/> | Foreign <br/> |Conferencing server type, such as conf:chat (for IMs) or conf:audio-video. See the  [UriTypes table](uritypes-table.md) for more information. <br/> |
   

