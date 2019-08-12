---
title: 'Group memberships and user rights requirements for Best Practices Analyzer'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Group memberships and user rights requirements for Best Practices Analyzer
ms:assetid: f812e343-8f75-454e-b7a8-1b404e32071a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg591354(v=OCS.15)
ms:contentKeyID: 48185869
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Group memberships and user rights requirements for Best Practices Analyzer in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-21_

To successfully run Best Practices Analyzer, the user account that you use to log on must be a member of the Administrators group on the local computer. Additionally, to scan your environment, the user account must be a member of the following groups:

  - **Domain Admins**   To enumerate Active Directory Domain Services information and to call the Windows Management Instrumentation (WMI) providers on domain controllers and global catalog servers.

  - **Administrators**   Required on each Lync Server 2013 internal computer and each Edge Server to call the Windows Management Instrumentation (WMI) providers and to access the registry.

  - **RTCUniversalReadOnlyAdmins**   Full or delegated read only Lync Server 2013 administrative rights.

  - **Exchange View Only Administrator**   Full or delegated Exchange View Only Administrator on the Microsoft Exchange organization.

If your user account does not have sufficient user rights, you have two options:

  - At a command prompt, use the **runas** command to run the tool under an account that does have sufficient user rights. The syntax is as follows:
    
        runas /netonly /user:<domain>\<userName> rtcbpa.exe

  - On the **Connect to Active Directory** page, set the credentials for the accounts that you plan to use to run Best Practices Analyzer. Click **Show advanced login options**. You can enter three accounts: one for connecting to Active Directory Domain Services, one for connecting to Lync Server 2013 Edge Servers, and one for connecting to the Exchange Servers. If you do not specify any of these accounts, the user account that you used to log on and run Best Practices Analyzer is used.

</div>

<span> </span>

</div>

</div>

</div>

