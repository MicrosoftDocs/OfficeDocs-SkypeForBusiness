---
title: "Certificate Request (Basic)"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/26/2015
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.dep.DeployCertRequestBasics
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 2c6b40d5-207a-4ca9-a090-e43350f4968f
description: "The Name and Security Settings page provides a text box to define a Friendly Name, a drop-down list for the Bit length of the private and public key pair, and a check box that enables you to Mark the certificate's private key as exportable."
---

# Certificate Request (Basic)
 
The **Name and Security Settings** page provides a text box to define a **Friendly Name**, a drop-down list for the **Bit length** of the private and public key pair, and a check box that enables you to **Mark the certificate's private key as exportable**.
  
The friendly, or simple, name on a certificate is an easily recognizable name that makes it easier for the person who views the certificate to identify it.
  
The Bit length of the private and public key pair can be selected as 1024, 2048, or 4096.
  
Selecting the check box for **Mark the certificate's private key as exportable** allows the certificate and private key to be exported and moved to another computer or server. The only time that this is required is when you are creating a pool of Edge Servers for the media relay authentication service (MRAS).
  
> [!CAUTION]
> To help maintain the security of the certificate and the key pair, you should select the Mark the certificate's private key as exportable option only if it is absolutely necessary. 
  

