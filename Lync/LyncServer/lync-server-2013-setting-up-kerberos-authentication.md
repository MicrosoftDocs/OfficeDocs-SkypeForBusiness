---
title: 'Lync Server 2013: Setting up Kerberos authentication'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Setting up Kerberos authentication
ms:assetid: dd8009ef-6265-4cc0-b2c7-e474cd1f4b09
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398976(v=OCS.15)
ms:contentKeyID: 48185601
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Setting up Kerberos authentication in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

Lync Server 2013 supports NTLM and Kerberos authentication for Web Services. Office Communications Server 2007 and Office Communications Server 2007 R2 used the default RTCComponentService and RTCService as the user accounts to run the Web Services application pools, allowing for a service principal name (SPN) to be assigned to the user accounts and to act as the authentication principal. Lync Server uses NetworkService to run Web Services and NetworkService cannot have SPNs assigned to it.

To solve the issue of not having Active Directory objects to hold the SPNs, Lync Server Control Panel can use computer account objects for this purpose. The computer account objects can hold the SPNs and are not subject to password expiration, which was an issue with using user accounts in previous versions.

You use Windows PowerShell cmdlets to configure the computer objects to provide Kerberos authentication.

<div>

## In This Section

  - [Prerequisites for enabling Kerberos authentication in Lync Server 2013](lync-server-2013-prerequisites-for-enabling-kerberos-authentication.md)

  - [Create a Kerberos authentication account in Lync Server 2013](lync-server-2013-create-a-kerberos-authentication-account.md)

  - [Assign a Kerberos authentication account to a site in Lync Server 2013](lync-server-2013-assign-a-kerberos-authentication-account-to-a-site.md)

  - [Setting up Kerberos authentication account passwords in Lync Server 2013](lync-server-2013-setting-up-kerberos-authentication-account-passwords.md)

  - [In Lync Server 2013 add Kerberos authentication to other sites](lync-server-2013-add-kerberos-authentication-to-other-sites.md)

  - [In Lync Server 2013 remove Kerberos authentication from a site](lync-server-2013-remove-kerberos-authentication-from-a-site.md)

  - [Testing and reporting the status and assignment of Kerberos authentication in Lync Server 2013](lync-server-2013-testing-and-reporting-the-status-and-assignment-of-kerberos-authentication.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

