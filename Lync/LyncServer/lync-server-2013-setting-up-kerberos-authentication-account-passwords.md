---
title: 'Lync Server 2013: Setting up Kerberos authentication account passwords'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Setting up Kerberos authentication account passwords
ms:assetid: b435f88e-4a77-4be7-b7e5-c17484303b74
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412870(v=OCS.15)
ms:contentKeyID: 48185167
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Setting up Kerberos authentication account passwords in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2010-11-03_

After you create the computer object for the Kerberos authentication account, you can set up the password for the account. You run the Windows PowerShell cmdlet for setting the Kerberos account password on one server. You can set the password on the object that you created for the Kerberos authentication. The password can be set to a known value, but by default is a random password. The password is available to all Kerberos authentication sources that use the account. You use Windows PowerShell cmdlets to set up and manage Kerberos account passwords.

<div>


> [!NOTE]  
> The Kerberos account object is a computer object, but uses the UserAccount parameter for operations in the Windows PowerShell cmdlets that are referenced. Note that this is not a mistake, but the intended behavior of the cmdlet when used with the Kerberos account creation and maintenance.



</div>

<div>

## In This Section

  - [Set a Kerberos authentication account password on a server in Lync Server 2013](lync-server-2013-set-a-kerberos-authentication-account-password-on-a-server.md)

  - [Synchronize a Kerberos authentication account password to IIS in Lync Server 2013](lync-server-2013-synchronize-a-kerberos-authentication-account-password-to-iis.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

