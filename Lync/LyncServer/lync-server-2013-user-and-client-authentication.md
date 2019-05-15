---
title: 'Lync Server 2013: User and client authentication'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: User and client authentication for Lync Server 2013
ms:assetid: 77f4b62a-f75c-424d-8f02-a6519090015d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn481132(v=OCS.15)
ms:contentKeyID: 59893868
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# User and client authentication for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-11-11_

A trusted user is one whose credentials have been authenticated by a trusted server in Microsoft Lync Server 2013. This server is usually a Standard Edition server, Enterprise Edition Front End Server, or Director. Lync Server 2013 relies on Active Directory Domain Services as the single, trusted back-end repository of user credentials.

Authentication is the provision of user credentials to a trusted server. Lync Server 2013 uses the following authentication protocols, depending on the status and location of the user.

  - **MIT Kerberos version 5 security protocol** for internal users with Active Directory credentials. Kerberos requires client connectivity to Active Directory Domain Services, which is why it cannot be used for authenticating clients outside the corporate firewall.

  - **NTLM protocol** for users with Active Directory credentials who are connecting from an endpoint outside the corporate firewall. The Access Edge service passes logon requests to a Director, if present, or a Front End Server for authentication. The Access Edge service itself performs no authentication.
    
    <div>
    

    > [!NOTE]  
    > NTLM protocol offers weaker attack protection than Kerberos, so some organizations minimize usage of NTLM. As a result, access to Lync Server 2013 might be restricted to internal or clients connected through a VPN or DirectAccess connection.

    
    </div>

  - **Digest protocol** for so-called anonymous users. Anonymous users are outside users who do not have recognized Active Directory credentials but who have been invited to an on-premises conference and possess a valid conference key. Digest authentication is not used for other client interactions.

Lync Server 2013 authentication consists of two phases:

1.  A security association is established between the client and the server.

2.  The client and server use the existing security association to sign messages that they send and to verify the messages they receive. Unauthenticated messages from a client are not accepted when authentication is enabled on the server.

User trust is attached to each message that originates from a user, not to the user identity itself. The server checks each message for valid user credentials. If the user credentials are valid, the message is unchallenged not only by the first server to receive it but by all other servers in the trusted server cloud.

Users with valid credentials issued by a federated partner are trusted but optionally prevented by additional constraints from enjoying the full range of privileges accorded to internal users.

The ICE and TURN protocols also use the Digest challenge as described in the IETF TURN RFC.

Client certificates provide an alternate way for users to be authenticated by Lync Server 2013. Instead of providing a user name and password, users have a certificate and the private key corresponding to the certificate that is required to resolve a cryptographic challenge. (This certificate must have a subject name or subject alternative name that identifies the user and must be issued by a Root CA that is trusted by servers running Lync Server 2013, be within the certificate’s validity period, and not have been revoked.) To be authenticated, users only need to type in a personal identification number (PIN). Certificates are particularly useful for telephones and other devices running Microsoft Lync 2013 Phone Edition where it is difficult to enter a user name and/or password.

</div>

<span> </span>

</div>

</div>

</div>

