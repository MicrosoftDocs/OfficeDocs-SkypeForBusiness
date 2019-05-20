---
title: "Manage server-to-server authentication (OAuth) and partner applications in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 38848373-c8c6-4097-bf7f-699fe471348d
description: "Summary: Manage OAuth and partner applications in Skype for Business Server."
---

# Manage server-to-server authentication (OAuth) and partner applications in Skype for Business Server
 
**Summary:** Manage OAuth and partner applications in Skype for Business Server.
  
Skype for Business Server must be able to securely, and seamlessly, communicate with other applications and server products. For example, you can configure Skype for Business Server so that contact data and/or archiving data is stored in Microsoft Exchange Server 2013; however, this can only be done if Skype for Business Server and Exchange are able to securely communicate with one another. Likewise, you can schedule a Skype for Business Server conference from within Office Web Apps Server; again, this can only be done if the two servers (SharePoint and Skype for Business Server) trust one another. Although it's possible to use one authentication mechanism for communication between Skype for Business Server and Exchange but a separate mechanism for Skype for Business Server and SharePoint communication, a better and more efficient approach is to use a standardized method for all server-to-server authentication and authorization.
  
Using a single, standardized method for server-to-server authentication is the approach taken by Skype for Business Server. Started with Office Servers 2013 release, Skype for Business Server (as well as other Microsoft Server products, including Exchange Server and SharePoint Server) supported the OAuth (Open Authorization) protocol for server-to-server authentication and authorization. With OAuth, a standard authorization protocol used by a number of major websites, user credentials and passwords are not passed from one computer to another. Instead, authentication and authorization is based on the exchange of security tokens; these tokens grant access to a specific set of resources for a specific amount of time.
  
OAuth authentication typically involves three parties: a single authorization server and the two realms that need to communicate with one another. (You can also do server-to-server authentication without using an authorization server, a process that will be discussed later in this document.) Security tokens are issued by the authorization server (also known as a security token server) to the two realms that need to communicate; these tokens verify that communications originating from one realm should be trusted by the other realm. For example, the authorization server might issue tokens that verify that users from a specific Skype for Business Server realm are able to access a specified Exchange realm, and vice-versa.
  
> [!NOTE]
> A realm is simply a security container. By default, Skype for Business Server uses your default SIP domain as its OAuth realm. Additional SIP namespaces are added to the Subject Alternate Name list in the OAuth certificate. 
  
Skype for Business Server supports three server-to-server authentication scenarios. With Skype for Business Server, you can:
  
- Configure server-to-server authentication between an on-premises installation of Skype for Business Server and an on-premises installation of Exchange and/or SharePoint Server.
    
- Configure server-to-server authentication between a pair of Office 365 components (for example, between Microsoft Exchange Server and Skype for Business Server, or between Skype for Business Server and SharePoint).
    
- Configure server-to-server authentication in a cross-premises environment (that is, server-to-server authentication between an on-premises server and an Office 365 component).
    
Note that, at this point in time, only Exchange 2013, SharePoint Server, Lync Server 2013, Skype for Business Server 2015, and Skype for Business 2019 support server-to-server authentication; if you are not running one of these servers, you will not be able to fully implement OAuth authentication.
  
It should also be pointed out that server-to-server authentication is optional: If Skype for Business Server does not need to communicate with other servers (such as Exchange) then server-to-server authentication can be skipped altogether. If server-to-server authentication is already configured for Lync Server 2013 and other applications, there's no need to re-do it for Skype for Business Server. 
  
However, server-to-server authentication is required if you want to use some of the features in Skype for Business Server, such as the "unified contact store." With unified contact store, Skype for Business Server contact information is stored in Exchange instead of in Skype for Business Server; this enables users to have a single set of contacts that is readily accessible from within Skype for Business, Outlook, or Outlook Web Access. Because the unified contact store requires Skype for Business Server to share information with Exchange, you must use server-to-server authentication in order to deploy the feature. Server-to-server authentication is also required if you choose to use Exchange archiving, in which the transcripts of instant messaging sessions are saved as Exchange emails rather than as individual database records.
  
For the Office 365 version of Skype for Business Server to communicate with its Exchange counterpart, Skype for Business Server must first obtain a security token from the authorization server. Skype for Business Server then uses that security token to identify itself to Exchange. The Office 365 version of Exchange must go through the same process in order to communicate with Skype for Business Server.
  
However, for on-premises server-to-server authentication between two Microsoft servers there is no need to use a third-party token server. Server products such as Skype for Business Server and Exchange have a built-in token server that can be used for authentication purposes with other Microsoft servers (such as SharePoint Server) that support server-to-server authentication. For example, Skype for Business Server can issue and sign a security token by itself, then use that token to communicate with Exchange. In a case like this, there is no need for a third-party token server.
  
In order to configure server-to-server authentication for an on-premises implementation of Skype for Business Server, you must do two things:
  
- Assign a certificate to the built-in Skype for Business Server token issuer.
    
- Configure the server that Skype for Business Server will communicate with to be a "partner application." For example, if Skype for Business Server needs to communicate with Exchange, you will need to configure Exchange to be a partner application.
    
> [!NOTE]
> A "partner application" is any application that Skype for Business Server can directly exchange security tokens with, without having to go through a third-party security token server. 
  
Note that OAuth is a core part of the product and cannot be disabled or removed.
  
## See also

[Assign a server-to-server authentication certificate to Skype for Business Server](assign-a-server-to-server-certificate.md)
  
[Configure a hybrid environment in Skype for Business Server](configure-a-hybrid-environment.md)
