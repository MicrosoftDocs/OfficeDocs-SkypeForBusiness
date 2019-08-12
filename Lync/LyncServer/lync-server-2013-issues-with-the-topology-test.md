---
title: 'Lync Server 2013: Issues with the topology test'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Issues with the topology test
ms:assetid: 821e8916-7b5d-4f64-8fb0-e5cc392ec1bb
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205045(v=OCS.15)
ms:contentKeyID: 48184670
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Issues with the topology test in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-21_

Like the **Test-CsTopology** cmdlet, Best Practice Analyzer provides a way for you to verify that Lync Server 2013 is functioning correctly at a global level. By default, Best Practice Analyzer, like the cmdlet, checks your entire Lync Server 2013 infrastructure, verifying that the required services are running, and that the appropriate user rights and permissions have been set for these services and for the universal security groups created when you install Lync Server 2013.

In addition to verifying the validity of Lync Server as a whole, **Test-CsTopology** also checks the validity of a specific service. For details about using the cmdlet to test specific services, see [Test-CsTopology](https://docs.microsoft.com/powershell/module/skype/Test-CsTopology) in the Lync Server Management Shell documentation. Use the following information to help resolve issues with your topology.

<div>


> [!NOTE]  
> Depending on the configuration of your Edge Servers and any related perimeter network settings, including firewall settings and permissions, Best Practices Analyzer might not be able to access and scan your Edge Servers. If you include Edge Servers in your scan and the reports indicate that there is an issue accessing Edge Servers, clear the <STRONG>Edge Servers</STRONG> check box and run the scan again to prevent the issue from showing up in reports.



</div>

<div>

## Resolving Issues with Your Topology

If the topology test found issues with your topology, these issues are probably caused by issues that occurred when you published or enabled your topology.

When you make changes to your topology, the changes take effect only when they have been both published and enabled. You must use Topology Builder to make topology changes. After you make changes, you can then publish and enable those changes by using Topology Builder.

When you publish the changes, the new information (for example, a new site or a new server role) is written to the Central Management store. However, these new (or the newly modified) objects do not immediately join your topology. Objects join your topology only when you enable the updated topology. If you select the Publish option in Topology Builder both of these steps occur: the changes are published (that is, they are written to the Central Management store) and then the new topology is enabled.

By default, members of the RTCUniversalServerAdmins group are authorized to run the **Publish-CsTopology** cmdlet and the **Enable-CsTopology** cmdlet. However, if setup permissions have not been delegated, you must be logged on as a domain administrator to run **Publish-CsTopology**. To give RTCUniversalServerAdmins the right to actually use the **Publish-CsTopology** cmdlet, you must run the **Grant-CsSetupPermission** cmdlet on every Active Directory container that contains computers running Lync Server services. To give RTCUniversalServerAdmins the right to use the **Enable-CsTopology** cmdlet, you must run the **Set-CsSetupPermission** cmdlet against every Active Directory Domain Services container that contains computers running Lync Server services. Note that this applies to enabling and publishing a topology by using Topology Builder. If you have not delegated permissions by using **Set-CsSetupPermission**, only a domain administrator can enable and publish a topology through Topology Builder.

</div>

</div>

<span> </span>

</div>

</div>

</div>

