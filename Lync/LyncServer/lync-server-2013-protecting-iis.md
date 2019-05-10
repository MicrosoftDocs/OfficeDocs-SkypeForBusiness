---
title: 'Lync Server 2013: Protecting IIS'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Protecting IIS in Lync Server 2013
ms:assetid: a67171a6-6703-4e09-abb3-35d335bb674e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn518332(v=OCS.15)
ms:contentKeyID: 62625492
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Protecting IIS in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-12-05_

In Microsoft Office Communications Server 2007 and Microsoft Office Communications Server 2007 R2, Internet Information Services (IIS) ran under a standard user account. This had the potential to cause issues: if that password expired you could lose your Web Services, an issue that was often difficult to diagnose. To help avoid the issue of expiring passwords, Microsoft Lync Server 2013 enables you to create a computer account (for a computer that doesn’t actually exist) that can serve as the authentication principal for all the computers in a site that are running IIS. Because these accounts use the Kerberos authentication protocol, the accounts are referred to as Kerberos accounts, and the new authentication process is known as Kerberos web authentication. This enables you to manage all your IIS servers by using a single account.

To run your servers under this authentication principal, you must first create a computer account by using the New-CsKerberosAccount cmdlet; this account is then assigned to one or more sites. After the assignment has been made, the association between the account and the Lync Server 2013 site is enabled by running the Enable-CsTopology cmdlet. Among other things, this creates the required service principal name (SPN) in Active Directory Domain Services (AD DS). SPNs provide a way for client applications to locate a particular service. For details, see [New-CsKerberosAccount](https://docs.microsoft.com/powershell/module/skype/New-CsKerberosAccount) in the Operations documentation.

<div>

## Best Practices

To help increase security of IIS, we recommend that you implement a Kerberos account for IIS. If you do not implement a Kerberos account, IIS runs under a standard user account.

</div>

</div>

<span> </span>

</div>

</div>

</div>

