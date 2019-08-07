---
title: "Migrate analog devices"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "Skype for Business Server provides support for analog devices. Specifically, the supported analog devices are analog audio phones and analog fax machines. You can configure the qualified gateways to support the use of analog devices in your Skype for Business Server environment. After you migrate to Skype for Business Server 2019, you must also migrate the contact objects associated with the analog devices. Use Skype for Business Server Management Shell to first retrieve all contact objects associated with the legacy analog devices, and then move those objects to the Skype for Business Server 2019 pool."
---

# Migrate analog devices

Skype for Business Server provides support for analog devices. Specifically, the supported analog devices are analog audio phones and analog fax machines. You can configure the qualified gateways to support the use of analog devices in your Skype for Business Server environment. After you migrate to Skype for Business Server 2019, you must also migrate the contact objects associated with the analog devices. Use Skype for Business Server Management Shell to first retrieve all contact objects associated with the legacy analog devices, and then move those objects to the Skype for Business Server 2019 pool.

### To migrate analog devices

1. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Skype for Business Server 2019**, and then click **Skype for Business Server Management Shell**.

2. At the command line, type:

   ```
   Get-CsAnalogDevice -Filter {RegistrarPool -eq "pool01.contoso.net"} | Move-CsAnalogDevice -Target pool02.contoso.net
   ```

3. Verify that all contact objects have been moved to the Skype for Business Server 2019 pool. At the command line, type:

   ```
   Get-CsAnalogDevice -Filter {RegistrarPool -eq "pool02.contoso.net"}
   ```

4. Verify that all the contact objects are now associated with the Skype for Business Server 2019 pool.


