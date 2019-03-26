---
title: "Verify normalization rules for Call Park in Skype for Business"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom: 
ms.assetid: deaa170f-041e-45cb-8eab-f02931ab541e
description: "Learn about normalization rules for Call Park in Skype for Business Server Enterprise Voice."
---

# Verify normalization rules for Call Park in Skype for Business
 
Learn about normalization rules for Call Park in Skype for Business Server Enterprise Voice.
  
Call Park orbits must not be normalized. Check your dial plans to be sure that your orbit numbers are not normalized. If you must create an additional normalization rule to prevent your orbits from being normalized, follow the procedure in [Create or modify a dial plan in Skype for Business Server](dial-plans.md) to define a new normalization rule, so that **Pattern to match** identifies the orbit range and **Translation pattern** is **$1**. For example, if your Call Park orbit range is 7000 - 7999, the **Pattern to match** is **^(7\d{3})$** and **Translation pattern** is **$1**.
  
> [!IMPORTANT]
> Be sure that the default normalization rule in your dial plans does not contain **^(\d\*)**. Otherwise, your Call Park normalization rule will never run.
  
## See also

[Create or modify a dial plan in Skype for Business Server](dial-plans.md)

