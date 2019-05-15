---
title: 'Lync Server 2013: Enable Group Call Pickup for users'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Enable Group Call Pickup for users
ms:assetid: 20ec5f41-6ba2-4156-82ed-b91d05b62a6d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ945620(v=OCS.15)
ms:contentKeyID: 51541457
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Enable Group Call Pickup for users in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-01-30_

Use the SEFAUtil resource kit tool to enable Group Call Pickup for users. Users must be assigned a group number with type GroupPickup in the call park orbit table to have Group Call Pickup enabled. You assign a call pickup group number and enable Group Call Pickup at the same time by using the /enablegrouppickup parameter when you run SEFAUtil.exe.

<div>

## To enable Group Call Pickup for a user

1.  Log on to the computer where you installed the SEFAUtil tool with administrator rights.

2.  At the command line, run:
    
        SEFAUtil.exe sip:<sip address of user> /server:<pool FQDN> /enablegrouppickup:<group number>
    
    For example:
    
        SEFAUtil.exe katarina@contoso.com /server:pool01.contoso.com /enablegrouppickup:199

</div>

<div>

## See Also


[Assign Group Call Pickup numbers to users in Lync Server 2013](lync-server-2013-assign-group-call-pickup-numbers-to-users.md)  
[Disable Group Call Pickup for users in Lync Server 2013](lync-server-2013-disable-group-call-pickup-for-users.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

