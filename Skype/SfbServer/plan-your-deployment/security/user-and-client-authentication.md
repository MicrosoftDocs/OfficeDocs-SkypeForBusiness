---
title: "User and client authentication for Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 77f4b62a-f75c-424d-8f02-a6519090015d
description: "A trusted user is one whose credentials have been authenticated by a trusted server in Skype for Business Server. This server is usually a Standard Edition server, Enterprise Edition Front End Server, or Director. Skype for Business Server relies on Active Directory Domain Services as the single, trusted back-end repository of user credentials."
---

# User and client authentication for Skype for Business Server
 
A trusted user is one whose credentials have been authenticated by a trusted server in Skype for Business Server. This server is usually a Standard Edition server, Enterprise Edition Front End Server, or Director. Skype for Business Server relies on Active Directory Domain Services as the single, trusted back-end repository of user credentials.
  
Authentication is the provision of user credentials to a trusted server. Skype for Business Server uses the following authentication protocols, depending on the status and location of the user.
  
- **MIT Kerberos version 5 security protocol** for internal users with Active Directory credentials. Kerberos requires client connectivity to Active Directory Domain Services, which is why it cannot be used for authenticating clients outside the corporate firewall.
    
- **NTLM protocol** for users with Active Directory credentials who are connecting from an endpoint outside the corporate firewall. The Access Edge service passes logon requests to a Director, if present, or a Front End Server for authentication. The Access Edge service itself performs no authentication.
    
    > [!NOTE]
    > NTLM protocol offers weaker attack protection than Kerberos, so some organizations minimize usage of NTLM. As a result, access to Skype for Business Server might be restricted to internal or clients connected through a VPN or DirectAccess connection. 
  
- **Digest protocol** for so-called anonymous users. Anonymous users are outside users who do not have recognized Active Directory credentials but who have been invited to an on-premises conference and possess a valid conference key. Digest authentication is not used for other client interactions.
    
Skype for Business Server authentication consists of two phases:
  
1. A security association is established between the client and the server.
    
2. The client and server use the existing security association to sign messages that they send and to verify the messages they receive. Unauthenticated messages from a client are not accepted when authentication is enabled on the server.
    
User trust is attached to each message that originates from a user, not to the user identity itself. The server checks each message for valid user credentials. If the user credentials are valid, the message is unchallenged not only by the first server to receive it but by all other servers in the trusted server cloud.
  
Users with valid credentials issued by a federated partner are trusted but optionally prevented by additional constraints from enjoying the full range of privileges accorded to internal users.
  
The ICE and TURN protocols also use the Digest challenge as described in the IETF TURN RFC.
  
Client certificates provide an alternate way for users to be authenticated by Skype for Business Server. Instead of providing a user name and password, users have a certificate and the private key corresponding to the certificate that is required to resolve a cryptographic challenge. (This certificate must have a subject name or subject alternative name that identifies the user and must be issued by a Root CA that is trusted by servers running Skype for Business Server, be within the certificate's validity period, and not have been revoked.) To be authenticated, users only need to type in a personal identification number (PIN). Certificates are particularly useful for telephones, mobile phones, and other devices where it is difficult to enter a user name and password.
  
### Cryptographic requirements due to ASP .NET 4.5 

As of Skype for Business Server 2015 CU5, AES is not supported for ASP.NET 4.6 and this may cause Skype Meetings App to fail to start. If a client is using AES as the machine key validation value you will need to reset the machine key value to SHA-1 or another supported algorithm on the Skype Meetings App site level on IIS. If necessary, see [IIS 8.0 ASP.NET Configuration Management](https://docs.microsoft.com/iis/get-started/whats-new-in-iis-8/iis-80-aspnet-configuration-management) for instructions.
  
Other supported values are:
  
- HMACSHA256
    
- HMACSHA384
    
- HMACSHA512
    
  The values AES, 3DES, and MD5 are no longer allowed, as they once were in ASP.NET 4. [Cryptographic Improvements in ASP.NET 4.5, pt. 2](https://blogs.msdn.microsoft.com/webdev/2012/10/23/cryptographic-improvements-in-asp-net-4-5-pt-2/) has more details.
  
