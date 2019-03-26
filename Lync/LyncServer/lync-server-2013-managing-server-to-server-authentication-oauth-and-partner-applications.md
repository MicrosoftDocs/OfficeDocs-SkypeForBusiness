---
title: 'Managing server-to-server authentication (OAuth) and partner applications'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Managing server-to-server authentication (OAuth) and partner applications
ms:assetid: 38848373-c8c6-4097-bf7f-699fe471348d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204817(v=OCS.15)
ms:contentKeyID: 48183894
ms.date: 05/15/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Managing server-to-server authentication (OAuth) and partner applications in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2015-05-14_

Microsoft Lync Server 2013 must be able to securely, and seamlessly, communicate with other applications and server products. For example, you can configure Lync Server 2013 so that contact data and/or archiving data is stored in Microsoft Exchange Server 2013; however, this can only be done if Lync Server and Exchange are able to securely communicate with one another. Likewise, you can schedule a Lync Server conference from within Microsoft SharePoint Server; again, however, this can only be done if the two servers (SharePoint and Lync Server) trust one another. Although it's possible to use one authentication mechanism for Lync-to-Exchange communication and a separate mechanism for Lync-to-SharePoint communication, a better and more efficient approach is to use a standardized method for all server-to-server authentication and authorization.

Using a single, standardized method for server-to-server authentication is the approach taken by Lync Server 2013. For the 2013 release, Lync Server 2013 (as well as other Microsoft Server products, including Exchange 2013 and Microsoft SharePoint Server) support the OAuth (Open Authorization) protocol for server-to-server authentication and authorization. With OAuth, a standard authorization protocol used by a number of major websites, user credentials and passwords are not passed from one computer to another. Instead, authentication and authorization is based on the exchange of security tokens; these tokens grant access to a specific set of resources for a specific amount of time.

OAuth authentication typically involves three parties: a single authorization server and the two realms that need to communicate with one another. (You can also do server-to-server authentication without using an authorization server, a process that will be discussed later in this document.) Security tokens are issued by the authorization server (also known as a security token server) to the two realms that need to communicate; these tokens verify that communications originating from one realm should be trusted by the other realm. For example, the authorization server might issue tokens that verify that users from a specific Lync Server 2013 realm are able to access a specified Exchange 2013 realm, and vice-versa.

<div>


> [!NOTE]
> A realm is simply a security container. By default, Lync Server 2013 uses your default SIP domain as its OAuth realm. Additional SIP namespaces are added to the Subject Alternate Name list in the OAuth certificate.



</div>

Lync Server 2013 supports three server-to-server authentication scenarios. With Lync Server 2013 you can:

  - Configure server-to-server authentication between an on-premise installation of Lync Server 2013 and an on-premises installation of Exchange 2013 and/or Microsoft SharePoint Server.

  - Configure server-to-server authentication between a pair of Office 365 components (for example, between Microsoft Exchange and Microsoft Lync Server, or between Microsoft Lync Server and Microsoft SharePoint).

  - Configure server-to-server authentication in a cross-premises environment (that is, server-to-server authentication between an on-premises server and an Office 365 component).

Note that, at this point in time, only Exchange 2013, SharePoint Server, and Lync Server 2013 support server-to-server authentication; if you are not running one of these servers then you will not be able to fully implement OAuth authentication.

It should also be pointed out that you do not need to use server-to-server authentication: server-to-server authentication is not required in order to deploy Lync Server 2013. If Lync Server 2013 does not need to communicate with other servers (such as Exchange 2013) then server-to-server authentication is not needed.

However, server-to-server authentication is required if you want to use some of Lync Server's new features, such as the "unified contact store." With unified contact store, Lync Server 2013 contact information is stored in Exchange 2013 instead of in Lync Server; this enables users to have a single set of contacts that is readily accessible from within Lync, Microsoft Outlook, or Microsoft Outlook Web Access. Because the unified contact store requires Lync Server 2013 to share information with Exchange 2013, you must use server-to-server authentication in order to deploy the feature. Server-to-server authentication is also required if you choose to use Exchange archiving, in which the transcripts of instant messaging sessions are saved as Exchange 2013 emails rather than as individual database records.

For the Office 365 version of Lync Server to communicate with its Exchange counterpart, Lync Server 2013 must first obtain a security token from the authorization server. Lync Server then uses that security token to identify itself to Exchange. The Office 365 version of Exchange must go through the same process in order to communicate with Lync Server 2013.

However, for on-premises server-to-server authentication between two Microsoft servers there is no need to use a third-party token server. Server products such as Lync Server 2013 and Exchange 2013 have a built-in token server that can be used for authentication purposes with other Microsoft servers (such as SharePoint server) that support server-to-server authentication. For example, Lync Server 2013 can issue and sign a security token by itself, then use that token to communicate with Exchange 2013. In a case like this, there is no need for a third-party token server.

In order to configure server-to-server authentication for an on-premises implementation of Lync Server 2013 you must do two things:

  - Assign a certificate to Lync Server's built-in token issuer.

  - Configure the server that Lync Server 2013 will communicate with to be a "partner application." For example, if Lync Server 2013 needs to communicate with Exchange 2013 then you will need to configure Exchange to be a partner application.

<div>


> [!NOTE]
> A "partner application" is any application that Lync Server 2013 can directly exchange security tokens with, without having to go through a third-party security token server.



</div>

Note that OAuth is a core part of the product and cannot be disabled or removed.

<div>

## See Also


[Assigning a server-to-server authentication certificate to Microsoft Lync Server 2013](lync-server-2013-assigning-a-server-to-server-authentication-certificate-to-lync-server-2013.md)  
[Configuring Microsoft Lync Server 2013 in a cross-premises environment](lync-server-2013-configuring-lync-server-in-a-cross-premises-environment.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

