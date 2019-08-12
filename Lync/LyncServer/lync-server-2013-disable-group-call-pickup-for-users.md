---
title: 'Lync Server 2013: Disable Group Call Pickup for users'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Disable Group Call Pickup for users
ms:assetid: 91b06f9e-2840-45a2-bbb3-6a29179b9a9f
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ945638(v=OCS.15)
ms:contentKeyID: 51541492
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Disable Group Call Pickup for users in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-01-30_

Use the following procedure to disable Group Call Pickup for a user.

<div>


> [!NOTE]  
> When you disable Group Call Pickup for a user, the call pickup group number that was assigned to the user is not retained. If you subsequently want to re-enable Group Call Pickup for that user, you must assign the call pickup group number again with the /enablegrouppickup parameter.



</div>

<div>

## To disable Group Call Pickup for a user

1.  Log on to the computer where you installed the SEFAUtil tool with administrator rights.

2.  At the command line, run:
    
        SEFAUtil.exe sip:<sip address of user> /server:<pool FQDN> /disablegrouppickup
    
    For example:
    
        SEFAUtil.exe katarina@contoso.com /server:pool01.contoso.com /disablegrouppickup

</div>

<div>

## See Also


[Assign Group Call Pickup numbers to users in Lync Server 2013](lync-server-2013-assign-group-call-pickup-numbers-to-users.md)  
[Enable Group Call Pickup for users in Lync Server 2013](lync-server-2013-enable-group-call-pickup-for-users.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

