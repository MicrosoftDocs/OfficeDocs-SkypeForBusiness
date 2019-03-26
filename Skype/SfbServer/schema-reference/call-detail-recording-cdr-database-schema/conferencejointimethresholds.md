---
title: "ConferenceJoinTimeThresholds table in Skype for Business Server 2015"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 3944d724-bdd8-4d1c-a2af-933ee8141529
description: "The ConferenceJoinTimeThresholds table contains the classification boundaries used by the Conference Join Time Summary Report. The Conference Join Time Summary Report summarizes the amount time required for users to successfully join a conference; these time values are reported both as an average and in one of the following categories:"
---

# ConferenceJoinTimeThresholds table in Skype for Business Server 2015
 
The ConferenceJoinTimeThresholds table contains the classification boundaries used by the Conference Join Time Summary Report. The Conference Join Time Summary Report summarizes the amount time required for users to successfully join a conference; these time values are reported both as an average and in one of the following categories:
  
- Less than 2 seconds.
    
- Between 2 second and 5 seconds.
    
- Between 5 seconds and 10 seconds.
    
- More than 10 seconds.
    
The ConferenceJoinTimeThresholds table contains the classification values 2 seconds, 5 seconds, and 10 seconds.
  
This table was introduced in Microsoft Lync Server 2013.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**ThresholdId** <br/> |int  <br/> |Primary  <br/> |Unique identifier for the classification.  <br/> |
|**ThresholdValue** <br/> |int  <br/> || Upper limit for the classification. Allowed values are: <br/>  2 <br/>  5 <br/>  10 <br/> |
   

