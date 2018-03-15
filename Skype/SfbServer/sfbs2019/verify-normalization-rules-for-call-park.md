---
title: "Verify normalization rules for Call Park in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: deaa170f-041e-45cb-8eab-f02931ab541e
description: "Call Park orbits must not be normalized. Check your dial plans to be sure that your orbit numbers are not normalized. If you must create an additional normalization rule to prevent your orbits from being normalized, follow the procedure in Create a dial plan in Lync Server 2013 to define a new normalization rule, so that Pattern to match identifies the orbit range and Translation pattern is $1 . For example, if your Call Park orbit range is 7000 - 7999, the Pattern to match is ^(7\d{3})$ and Translation pattern is $1 ."
---

# Verify normalization rules for Call Park in Lync Server 2013
[]
Call Park orbits must not be normalized. Check your dial plans to be sure that your orbit numbers are not normalized. If you must create an additional normalization rule to prevent your orbits from being normalized, follow the procedure in [Create a dial plan in Lync Server 2013](create-a-dial-plan.md) to define a new normalization rule, so that **Pattern to match** identifies the orbit range and **Translation pattern** is **$1**. For example, if your Call Park orbit range is 7000 - 7999, the **Pattern to match** is **^(7\d{3})$** and **Translation pattern** is **$1**. 
  
> [!IMPORTANT]
> Be sure that the default normalization rule in your dial plans does not contain **^(\d\*)**. Otherwise, your Call Park normalization rule will never run. 
  
## See also

#### 

[Create a dial plan in Lync Server 2013](create-a-dial-plan.md)

