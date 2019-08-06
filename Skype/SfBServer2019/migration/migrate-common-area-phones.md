---
title: "Migrate Common Area Phones"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "Common Area Phones are IP phones that most often reside in a shared workspace or common area, like a lobby, kitchen, or factory floor. Common Area Phones do not need to be connected to a computer to provide Skype for Business Server unified communications (UC) functionality. After migrating a deployment to Skype for Business Server 2019, you must also migrate the contact objects associated with the legacy Common Area Phone. Using Skype for Business Server Management Shell you will first retrieve all contact objects associated with the legacy Common Area Phones, and then move those objects to the Skype for Business Server 2019 pool."
---

# Migrate Common Area Phones

Common Area Phones are IP phones that most often reside in a shared workspace or common area, like a lobby, kitchen, or factory floor. Common Area Phones do not need to be connected to a computer to provide Skype for Business Server unified communications (UC) functionality. After migrating a deployment to Skype for Business Server 2019, you must also migrate the contact objects associated with the legacy Common Area Phone. Using Skype for Business Server Management Shell, you will first retrieve all contact objects associated with the legacy Common Area Phones, and then move those objects to the Skype for Business Server 2019 pool.
  
### Migrate Common Area Phones

1. From the Skype for Business Server 2019 Front End server, open Skype for Business Server Management Shell.
    
2. From the command line, type the following:
    
   ```
   Get-CsCommonAreaPhone -Filter {RegistrarPool -eq "pool01.contoso.net"} | Move-CsCommonAreaPhone -Target pool02.contoso.net
   ```

3. To verify that all contact objects have been moved to the Skype for Business Server 2019 pool, from the Skype for Business Server Management Shell type the following:
    
   ```
   Get-CsCommonAreaPhone -Filter {RegistrarPool -eq "pool02.contoso.net"}
   ```

    Verify that all contact objects are now associated with the Skype for Business Server 2019 pool.
    

