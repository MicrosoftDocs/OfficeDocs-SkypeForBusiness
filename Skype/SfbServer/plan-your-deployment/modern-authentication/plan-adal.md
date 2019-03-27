---
title: "Planning for Modern Authentication (ADAL) with Skype for Business"
ms.reviewer: 
ms.author: heidip
author: microsoftheidi
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
description: "This article explains what Modern Authentication (which is based on the Active Directory Authentication Library (ADAL) and OAuth 2.0) is."
---

# How to use Modern Authentication (ADAL) with Skype for Business
 
This article introduces Modern Authentication (which is based on the Active Directory Authentication Library (ADAL) and OAuth 2.0) that can be found in the March 2016 Cumulative Update for Skype for Business for Skype for Business Server 2015, or from initial release for Skype for Business Server 2019.
  
## What is ADAL?

ADAL is the acronym for the 'Active Directory Authentication Library', and, along with OAuth 2.0, it is an underpinning of Modern Authentication. This code library is designed to make secured resources in your directory available to client applications (like Skype for Business) via security tokens. ADAL works with OAuth 2.0 to enable more authentication and authorization scenarios, like Multi-factor Authentication (MFA), and more forms of SAML Auth.
  
A variety of apps that act as clients can leverage Modern Authentication for help in getting to secured resources. In Skype for Business Server, this technology is used between on-premises clients and on-premises servers in order to give users a proper level of authorization to resources.
  
Modern Authentication conversations (which are based on ADAL and OAuth 2.0) have some elements in common.
  
- There is a client making a request for a resource, in this case, the client is Skype for Business.
    
- There is a resource to which the client needs a specific level of access, and this resource is secured by a directory service, in this case the resource is Skype for Business Server.
    
- There is an OAuth connection, in other words, a connection that is dedicated to  *authorizing*  a user to access a resource. (OAuth is also known by the more descriptive name, 'Server-to-Server' auth, and is often abbreviated as S2S.)
    
In Skype for Business Server Modern Authentication (ADAL) conversations, Skype for Business Server communicates through ADFS (ADFS 3.0 in Windows Server 2012 R2). The authentication may happen using some other Identity Provider (IdP), but Skype for Business server needs to be configured to communicate with ADFS, directly. If you haven't configured ADFS to work with Skype for Business Server please complete the [ADFS installation](https://technet.microsoft.com/en-us/library/adfs2-step-by-step-guides%28v=ws.10%29.aspx).
  
ADAL is included in the March 2016 Cumulative Update for Skype for Business Server 2015, and the March 2016 Cumulative Update for Skype for Business **must** be installed and is needed for successful configuration. For Skype for Business Server 2019, it is available from initial release of the product.
  
> [!NOTE]
> During the initial release, Modern Authentication in an on-premises environment is supported only if there is no mixed Skype topology involved. For example, if the environment is purely Skype for Business Server. This statement may be subject to change. 
  
A PowerShell package including .ps1 files with the commands used by ADAL must be downloaded for successful configuration.

For information on how to implement Modern Authentication in Skype for Business, please refer to: [How to use Modern Authentication (ADAL) with Skype for Business](../../manage/authentication/use-adal.md)
