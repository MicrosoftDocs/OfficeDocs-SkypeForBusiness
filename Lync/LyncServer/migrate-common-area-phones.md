---
title: Migrate Common Area Phones
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Migrate Common Area Phones
ms:assetid: 31bd26fc-861b-45c6-8221-18df16e575de
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ688015(v=OCS.15)
ms:contentKeyID: 49733604
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Migrate Common Area Phones

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-29_

Common Area Phones are IP phones that most often reside in a shared workspace or common area, like a lobby, kitchen, or factory floor. Common Area Phones do not need to be connected to a computer to provide Lync Server UC functionality. After migrating an Lync Server 2010 deployment to Lync Server 2013, you must also migrate the contact objects associated with the legacy Common Area Phone. Using Lync Server Management Shell you will first retrieve all contact objects associated with the Lync Server 2010 Common Area Phones, and then move those objects to the Lync Server 2013 pool.

**Migrate Common Area Phones**

1.  From the Lync Server 2013 Front End server, open Lync Server Management Shell.

2.  From the command line, type the following:
    
        Get-CsCommonAreaPhone -Filter {RegistrarPool -eq "pool01.contoso.net"} | Move-CsCommonAreaPhone -Target pool02.contoso.net

3.  To verify all contact objects have been moved to the Lync Server 2013 pool, from the Lync Server Management Shell type the following:
    
        Get-CsCommonAreaPhone -Filter {RegistrarPool -eq "pool02.contoso.net"}
    
    Verify all contact objects are now associated with the Lync Server 2013 pool.

</div>

<span> </span>

</div>

</div>

</div>

