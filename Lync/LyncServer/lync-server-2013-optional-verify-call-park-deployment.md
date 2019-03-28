---
title: 'Lync Server 2013: (Optional) Verify Call Park deployment'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: (Optional) Verify Call Park deployment
ms:assetid: fcfe0962-1a9c-4cbd-847c-fed40e3b1480
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg413076(v=OCS.15)
ms:contentKeyID: 48185952
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# (Optional) Verify Call Park deployment in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-11_

After you install and configure Call Park, you need to verify the configuration to make sure that parking and retrieving calls works as expected. At minimum, verify the following:

  - Call a user who has Call Park enabled and have the user park the call.
    
    <div>
    

    > [!NOTE]  
    > If you enabled Call Park in voice policy just before performing this test, the user who is parking the call needs to sign out of Lync Server, and then sign back in, to be able to see the Call Park option in the transfer call list.

    
    </div>

  - Dial the orbit number to retrieve the call.

  - Park another call, let the parked call time out, and do not pick up the ringback. Verify that the timed-out call is correctly routed to the fallback destination that is specified for **OnTimeoutURI**.

</div>

<span> </span>

</div>

</div>

</div>

