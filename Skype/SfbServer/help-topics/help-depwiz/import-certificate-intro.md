---
title: "Import Certificate (Intro)"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 11/17/2018
audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.dep.DeployCertImportBasics
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 474fac52-0b11-45dd-a211-fd2f1727238b
description: "To import a certificate, you must provide a path to the certificate file. In the Select Certificate file text box, you can either type the full path and file name, or click the Browse button and navigate to the path location and the file name (typically, a .p7b, .pfx, or .cer file)."
---

# Import Certificate (Intro)
 
To import a certificate, you must provide a path to the certificate file. In the **Select Certificate file** text box, you can either type the full path and file name, or click the **Browse** button and navigate to the path location and the file name (typically, a .p7b, .pfx, or .cer file).
  
If the certificate contains a private key, select the check box **Certificate file contains certificate's private key**. When this check box is selected, the **Password** text input is enabled. If you have a certificate with a private key associated with it, a password is usually placed on the private key when the certificate is created. You input the password for the private key to allow the certificate and the private key to be imported into the certificate store. When you have provided the information for the certificate file path, and optionally the private key password, if required, click **Next**.
  
> [!IMPORTANT]
> If you do not know the password for the private key, the import will fail. 
  

