---
title: 'Lync Server 2013: Migrate users to unified contact store'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Migrate users to unified contact store
ms:assetid: 215a8ec1-d63e-4fdf-b73d-75aeb9dddb43
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204737(v=OCS.15)
ms:contentKeyID: 48183600
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Migrate users to unified contact store in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-15_

A user's contacts are automatically migrated to the Exchange 2013 server when the user:

  - Has been assigned a user services policy that has UcsAllowed set to True.

  - Has been provisioned with an Exchange 2013 mailbox and has signed into the mailbox at least once.

  - Logs in by using a Lync 2013 rich client.

If the user logs in with a Lync 2010 or earlier client, or if the user is not connected to an Exchange 2013 server, the user services policy is ignored and the user's contacts remain in Lync Server.

You can determine whether a user's contacts have been migrated by using either of the following methods:

  - Check the following registry key on the client computer:
    
    HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\15.0\\Lync\\\<SIP URL\>\\UCS
    
    If the user's contacts are stored in Exchange 2013, this key contains a value of InUCSMode with a value of 2165.

  - Run the **Test-CsUnifiedContactStore** cmdlet. At the Lync Server Management Shell command line, type:
    
        Test-CsUnifiedContactStore -UserSipAddress "sip:kenmyer@litwareinc.com" -TargetFqdn "atl-cs-001.litwareinc.com"
    
    If **Test-CsUnifiedContactStore** succeeds, the user's contacts were migrated to unified contact store.

</div>

<span> </span>

</div>

</div>

</div>

