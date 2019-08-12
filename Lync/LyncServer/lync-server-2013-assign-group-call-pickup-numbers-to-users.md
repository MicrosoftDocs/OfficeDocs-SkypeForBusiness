---
title: 'Lync Server 2013: Assign Group Call Pickup numbers to users'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Assign Group Call Pickup numbers to users
ms:assetid: b8e79275-8e7e-4799-b908-f34f61df22f0
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ945647(v=OCS.15)
ms:contentKeyID: 51541508
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Assign Group Call Pickup numbers to users in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-01-30_

After you add Group Call Pickup group numbers to the call park orbit table, you can assign the groups to users. Use the secondary extension feature activation (SEFAUtil ) resource kit tool to assign call pickup groups to users.

<div>


> [!NOTE]  
> In a hybrid deployment, do not assign a Group Call Pickup group to users who are homed online. Users who are homed online cannot participate in Group Call Pickup. That is, their calls cannot be answered by other users, and they cannot answer calls to other users.



</div>

<div>

## To assign a Group Call Pickup group to a user

1.  Log on to the computer where you installed the SEFAUtil tool with administrator rights.

2.  At the command line, run:
    
        SEFAUtil.exe sip:<sip address of user> /server:<pool FQDN> /enablegrouppickup:<group number>
    
    For example:
    
        SEFAUtil.exe katarina@contoso.com /server:pool01.contoso.com /enablegrouppickup:199

</div>

<div>

## See Also


[Enable Group Call Pickup for users in Lync Server 2013](lync-server-2013-enable-group-call-pickup-for-users.md)  
[Disable Group Call Pickup for users in Lync Server 2013](lync-server-2013-disable-group-call-pickup-for-users.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

