---
title: 'Lync Server 2013: Enable users for unified contact store'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Enable users for unified contact store
ms:assetid: 7b46a01f-beb5-4a33-adb0-35f0502b168d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205024(v=OCS.15)
ms:contentKeyID: 48184599
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Enable users for unified contact store in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-07_

When you deploy Lync Server 2013 and publish the topology, unified contact store is enabled for all users by default. You do not need to take any additional action to enable unified contact store after you deploy Lync Server 2013. However, you can use the **Set-CsUserServicesPolicy** cmdlet to customize which users have unified contact store available. You can enable this feature globally, by site, by tenant, or by individuals or groups of individuals.

<div>

## To enable users for unified contact store

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

2.  Do any of the following:
    
      - To enable unified contact store globally for all Lync Server users, at the command line, type:
        
            Set-CsUserServicesPolicy -Identity global -UcsAllowed $True
    
      - To enable unified contact store for the users at a specific site, at the command line, type:
        
            New-CsUserServicesPolicy -Identity site:<site name> -UcsAllowed $True
        
        For example:
        
            New-CsUserServicesPolicy -Identity site:Redmond -UcsAllowed $True
    
      - To enable unified contact store by tenant, at the command line, type:
        
            Set-CsUserServicesPolicy -Tenant <tenantId> -UcsAllowed $True
        
        For example:
        
            Set-CsUserServicesPolicy -Tenant "38aad667-af54-4397-aaa7-e94c79ec2308" -UcsAllowed $True
    
      - To enable unified contact store for specific users, at the command line, type:
        
            New-CsUserServicesPolicy -Identity "<policy name>" -UcsAllowed $True
            Grant-CsUserServicesPolicy -Identity "<user display name>" -PolicyName <"policy name">
        
        <div>
        

        > [!NOTE]  
        > You can also use user alias or SIP URI instead of the user display name.

        
        </div>
        
        For example:
        
            New-CsUserServicesPolicy -Identity "UCS Enabled Users" -UcsAllowed $True
            Grant-CsUserServicesPolicy -Identity "Ken Myer" -PolicyName "UCS Enabled Users"
        
        <div>
        

        > [!NOTE]  
        > In the preceding example, the first command creates a new per-user policy named <EM>UCS Enabled Users</EM> with the UcsAllowed flag set to True. The second command assigns the policy to the user with the display name Ken Myer, which means that Ken Myer is now enabled for unified contact store.

        
        </div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

