---
title: 'Lync Server 2013: Security framework for Lync Server'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Security framework for Lync Server 2013
ms:assetid: 01131e28-b38e-40d9-8524-06725b9c6608
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn481316(v=OCS.15)
ms:contentKeyID: 59893866
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Security framework for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-11-08_

This section provides an overview of the fundamental elements that form the security framework for Microsoft Lync Server 2013. Understanding how these elements work together is essential to making informed decisions about securing your particular Lync Server 2013 deployment.

These elements are as follows:

  - Active Directory Domain Services (AD DS) provides a single trusted back-end repository for user accounts and network resources.

  - Role-Based Access Control (RBAC) enables you to delegate administrative tasks while maintaining high standards for security.

  - Public Key Infrastructure (PKI) uses certificates issued by trusted certification authorities (CAs) to authenticate servers and ensure data integrity.

  - Transport Layer Security (TLS), HTTPS over SSL (HTTPS), and mutual TLS (MTLS) enable endpoint authentication and IM encryption. Point-to-point audio, video, and application sharing streams are encrypted using Secure Real-Time Transport Protocol (SRTP).

  - Industry-standard protocols for user authentication, where possible.

  - Windows PowerShell provides security features that are enabled by default so that users cannot easily or unknowingly run scripts.

These fundamental security elements work together to define trusted users, servers, connections, and operations to help ensure a secure foundation for Lync Server 2013.

<div>

## In This Section

The topics in this section describe how each of these fundamental elements works to enhance the security of your Lync Server infrastructure.

  - [Active Directory Domain Services for Lync Server 2013](lync-server-2013-active-directory-domain-services-for-lync-server.md)

  - [Role-based access control (RBAC) for Lync Server 2013](lync-server-2013-role-based-access-control-rbac.md)

  - [Public Key Infrastructure for Lync Server 2013](lync-server-2013-public-key-infrastructure.md)

  - [TLS and MTLS for Lync Server 2013](lync-server-2013-tls-and-mtls.md)

  - [Encryption for Lync Server 2013](lync-server-2013-encryption.md)

  - [User and client authentication for Lync Server 2013](lync-server-2013-user-and-client-authentication.md)

  - [Windows PowerShell and Lync Server 2013 management tools](lync-server-2013-windows-powershell-and-lync-server-management-tools.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

