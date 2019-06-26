---
title: "Skype for Business on Mac client requirements"
ms.author: v-lanac
author: lanachin
ms.reviewer: PhillipGarding
manager: serdars
ms.date: 2/16/2018
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- Strat_SB_Admin
ms.custom: 
ms.assetid: 790d3e89-2b68-411b-b282-38de5d34dd10
description: "Read this topic to learn about hardware, software, and infrastructure requirements for running Skype for Business on a Mac."
---

# Skype for Business on Mac client requirements
 
Read this topic to learn about hardware, software, and infrastructure requirements for running Skype for Business on a Mac.
  
The [Skype for Business on Mac Client](https://products.office.com/en-us/skype-for-business/download-app?tab=tabs-3#Mac) is available for download.
  
## Hardware and software requirements for Skype for Business on Mac

The Skype for Business on Mac client requires Mac OS X El Capitan and higher, and uses at least 100MB of disk space. We support the use of all built-in audio and video devices. External devices must be in the [Skype for Business Solutions Catalog](https://partnersolutions.skypeforbusiness.com/solutionscatalog). 
  
> [!NOTE]
> This list is preliminary and some devices may be qualified for Lync, but not supported on Skype for Business on the Mac. 
> Refer to the [System requirements](https://products.office.com/en-us/office-system-requirements) for the minimum hardware required.
  
### Legacy Mac clients

Skype for Business Server 2015 also supports the following legacy clients on computers that are running Mac OS 10.5.8 or latest service pack or release (Intel-based) operating systems (Mac OS 10.9 operating system is not currently supported). For details about supported features, see [Desktop client feature comparison for Skype for Business](desktop-feature-comparison.md).
  
- Microsoft Lync for Mac 2011 (see [Lync for Mac 2011 Deployment Guide](https://go.microsoft.com/fwlink/p/?LinkId=268786))
    
- Microsoft Communicator for Mac 2011 (see [Communicator for Mac 2011 Deployment Guide](https://go.microsoft.com/fwlink/p/?LinkId=268787))
 
These clients are not supported by Skype for Business Server 2019.
   
## Infrastructure requirements for Skype for Business on Mac
<a name="Infrastructure"> </a>

The Skype for Business on Mac client leverages both the Unified Communications Management Platform (UCMP) as well as the Unified Communications Web API (UCWA) that our mobility clients use.
  
The client has the same requirements as our mobility clients in that you must have an Access Edge Server and Reverse Proxy deployed in a supported configuration. 
  
### Authentication

The Skype for Business on Mac client supports Cert-based authentication, Microsoft Modern Authentication, and Multi-Factor Authentication when deployed and enabled.
  
> [!NOTE]
> Due to a current limitation, the user's Exchange credentials must be the same as their Skype for Business credentials. 
  
### Certificates

Certificates in use on the Access Edge, Reverse Proxy and Front End servers must not use the SHA-512 hash algorithm.
  
The HTTP Certificate Revocation List must be defined and accessible by the client. For example, we don't support an LDAP entry in the certificate as your Certificate Revocation List.
  
### DNS

Mobility must be properly deployed for the Skype for Business on the Mac client to function properly. A common failure scenario is to have both of the following DNS entries resolvable on the internal network:
  
- lyncdiscoverinternal.\<sipdomain\>
    
- lyncdiscover.\<sipdomain\>
    
For more information, refer to: [Deploying Mobility in Lync Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=798224), and the [Microsoft Lync Server 2010 Mobility Guide](https://go.microsoft.com/fwlink//p/?LinkId=798226).
  
## See also
<a name="Infrastructure"> </a>

[DNS requirements for Skype for Business Server](../../plan-your-deployment/network-requirements/dns.md)

[Frequently Asked Questions](https://go.microsoft.com/fwlink/p/?LinkId=798227)
  
[Known issues](https://go.microsoft.com/fwlink/p/?LinkId=798228)
