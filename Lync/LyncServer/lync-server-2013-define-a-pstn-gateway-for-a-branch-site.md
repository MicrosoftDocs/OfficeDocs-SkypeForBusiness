---
title: 'Lync Server 2013: Define a PSTN gateway for a branch site'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Define a PSTN gateway for a branch site
ms:assetid: 87be2fe2-1d56-4062-b430-439d4536414c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398689(v=OCS.15)
ms:contentKeyID: 48184724
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Define a PSTN gateway for a branch site in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-21_

Perform this procedure at the central site, which contains at least one Front End pool or Standard Edition server.

<div>


> [!IMPORTANT]  
> Before you perform the procedure, the following conditions must be in place: 
> <UL>
> <LI>
> <P>Lync Server 2013&nbsp;communications software must be set up at the central site.</P>
> <LI>
> <P>Mediation Server must be deployed at the central site.</P></LI></UL>



</div>

<div>

## To define a PSTN gateway

1.  Click **Start**, click **All Programs**, click **Microsoft Lync Server**, and then click **Lync Server Topology Builder**.

2.  In the console tree, expand the central site, expand **Branch Office Sites**, expand name of the branch site that you want to define a public switched telephone network (PSTN) gateway for, and then expand **Shared Components**.

3.  Right-click **PSTN gateways**, and then click **New IP/PSTN Gateway**.

4.  In the **Define New IP/PSTN Gateway** dialog box, click **Gateway FQDN or IP Address**, and then type the fully qualified domain name (FQDN) or IP address of the gateway that you are deploying at the branch site.

5.  Click **Listening Port for IP/PSTN Gateway**, and then accept the default values.

6.  In the **SIP Transport Protocol** list, click the transport protocol the gateway uses, and then click **OK**.
    
    <div>
    

    > [!NOTE]  
    > For security reasons, we strongly recommend that you use a PSTN gateway that supports Transport Layer Security (TLS).

    
    </div>

<div>


> [!TIP]  
> Use the cmdlet <STRONG>Set-CsPstnGateway</STRONG> to modify properties of a PSTN gateway. For details, see <A href="https://docs.microsoft.com/powershell/module/skype/Set-CsPstnGateway">Set-CsPstnGateway</A>, in the Lync Server Management Shell Help.



</div>

**Next step** for branch-site resiliency: [Configuring users for branch site resiliency in Lync Server 2013](lync-server-2013-configuring-users-for-branch-site-resiliency.md)

</div>

<div>

## See Also


[PSTN gateway deployment options in Lync Server 2013](lync-server-2013-pstn-gateway-deployment-options.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

