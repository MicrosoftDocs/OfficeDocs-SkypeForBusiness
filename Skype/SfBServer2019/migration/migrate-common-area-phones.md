---
title: "Migrate Common Area Phones"
ms.author: kenwith
author: kenwith
manager: serdars
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 31bd26fc-861b-45c6-8221-18df16e575de
description: "Common Area Phones are IP phones that most often reside in a shared workspace or common area, like a lobby, kitchen, or factory floor. Common Area Phones do not need to be connected to a computer to provide Lync Server UC functionality. After migrating an Lync Server 2010 deployment to Lync Server 2013, you must also migrate the contact objects associated with the legacy Common Area Phone. Using Lync Server Management Shell you will first retrieve all contact objects associated with the Lync Server 2010 Common Area Phones, and then move those objects to the Lync Server 2013 pool."
---

# Migrate Common Area Phones
[]
Common Area Phones are IP phones that most often reside in a shared workspace or common area, like a lobby, kitchen, or factory floor. Common Area Phones do not need to be connected to a computer to provide Lync Server UC functionality. After migrating an Lync Server 2010 deployment to Lync Server 2013, you must also migrate the contact objects associated with the legacy Common Area Phone. Using Lync Server Management Shell you will first retrieve all contact objects associated with the Lync Server 2010 Common Area Phones, and then move those objects to the Lync Server 2013 pool.
  
### Migrate Common Area Phones

1. From the Lync Server 2013 Front End server, open Lync Server Management Shell.
    
2. From the command line, type the following:
    
  ```
  Get-CsCommonAreaPhone -Filter {RegistrarPool -eq "pool01.contoso.net"} | Move-CsCommonAreaPhone -Target pool02.contoso.net
  ```

3. To verify all contact objects have been moved to the Lync Server 2013 pool, from the Lync Server Management Shell type the following:
    
  ```
  Get-CsCommonAreaPhone -Filter {RegistrarPool -eq "pool02.contoso.net"}
  ```

    Verify all contact objects are now associated with the Lync Server 2013 pool.
    

