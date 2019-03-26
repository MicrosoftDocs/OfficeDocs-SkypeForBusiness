---
title: "Security framework for Skype for Business Server"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 01131e28-b38e-40d9-8524-06725b9c6608
description: "This section provides an overview of the fundamental elements that form the security framework for Skype for Business Server. Understanding how these elements work together is essential to making informed decisions about securing your particular Skype for Business Server deployment."
---

# Security framework for Skype for Business Server
 
This section provides an overview of the fundamental elements that form the security framework for Skype for Business Server. Understanding how these elements work together is essential to making informed decisions about securing your particular Skype for Business Server deployment.
  
These elements are as follows:
  
- Active Directory Domain Services (AD DS) provides a single trusted back-end repository for user accounts and network resources.
    
- Role-Based Access Control (RBAC) enables you to delegate administrative tasks while maintaining high standards for security.
    
- Public Key Infrastructure (PKI) uses certificates issued by trusted certification authorities (CAs) to authenticate servers and ensure data integrity.
    
- Transport Layer Security (TLS), HTTPS over SSL (HTTPS), and mutual TLS (MTLS) enable endpoint authentication and IM encryption. Point-to-point audio, video, and application sharing streams are encrypted using Secure Real-Time Transport Protocol (SRTP).
    
- Industry-standard protocols for user authentication, where possible.
    
- Windows PowerShell provides security features that are enabled by default so that users cannot easily or unknowingly run scripts.
    
These fundamental security elements work together to define trusted users, servers, connections, and operations to help ensure a secure foundation for Skype for Business Server.
  
## In this section

The topics in this section describe how each of these fundamental elements works to enhance the security of your Skype for Business Server infrastructure.
  
- [Active Directory Domain Services for Skype for Business Server](active-directory-domain-services.md)
    
- [Role-based access control (RBAC) for Skype for Business Server](role-based-access-control-rbac.md)
    
- [Public Key Infrastructure for Skype for Business Server](public-key-infrastructure-for-skype.md)
    
- [TLS and MTLS for Skype for Business Server](tls-and-mtls.md)
    
- [Encryption for Skype for Business Server](encryption.md)
    
- [User and client authentication for Skype for Business Server](user-and-client-authentication.md)
    
- [Windows PowerShell and Skype for Business Server management tools](management-tools.md)
    

