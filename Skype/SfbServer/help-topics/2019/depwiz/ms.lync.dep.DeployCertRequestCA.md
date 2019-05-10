---
title: "Certificate Request (Certificate Authority)"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.dep.DeployCertRequestCA
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: a609f1b0-ae13-44ca-a467-b7fb14ff18a1
ROBOTS: NOINDEX, NOFOLLOW
description: "When making a certificate request to an online certification authority (CA) (typically, these are servers that are on your internal network) on the Choose a Certification Authority (CA) page, you are presented with two options:"
---

# Certificate Request (Certificate Authority)
 
When making a certificate request to an online certification authority (CA) (typically, these are servers that are on your internal network) on the **Choose a Certification Authority (CA)** page, you are presented with two options:
  
1. Select a CA from the list detected in your environment.
    
2. Specify another certification authority.
    
If you select the first option, you'll see a drop-down list that contains all Windows Server-based certification authorities that are detected in your environment. Select the certification authority that is appropriate for your certificate. You may need to consult with your CA administrator to know which CA to choose.
  
If you select the second option, type in the fully qualified domain name (FQDN) and CA instance for the certification authority that you will use for your certificate. This option is appropriate if the CA that you want to use is not a Windows Server-based CA, but will work for Windows Server-based CAs.
  
> [!IMPORTANT]
> Be sure to confirm the group memberships that you need to be successful with the certificate request. Typically, certification authorities have a different permission requirement from the requirements for installing Skype for Business Server on servers. Confirm the requirements for requesting the certificate with your CA administrator. 
  

