---
title: 'Lync Server 2013: Using cmdlets to reverse domain preparation'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Using cmdlets to reverse domain preparation
ms:assetid: 014dba5d-fcb3-44c9-9d63-ae0755276dac
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398071(v=OCS.15)
ms:contentKeyID: 48183227
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Using cmdlets to reverse domain preparation for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-29_

Use the **Disable-CsAdDomain** cmdlet to reverse the domain preparation step.

<div>

## To use cmdlets to reverse domain preparation

1.  Log on to any server in the domain as a member of the Domain Admins group.

2.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

3.  Run:
    
        Disable-CsAdDomain [-Domain <Fqdn>] [-DomainController <Fqdn>] [-Force <SwitchParameter>] 
        [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] 
    
    For example:
    
        Disable-CsAdDomain -Domain domain1.contoso.net -GlobalSettingsDomainController dc01.domain1.contoso.net -Force
    
    If the Force parameter is present, domain preparation is rolled back, even if one or more Front End Servers or A/V Conferencing Servers in the domain are activated. If the Force parameter is not present, domain preparation rollback is terminated if any Front End Servers or A/V Conferencing Servers in the domain are activated.
    
    <div>
    

    > [!NOTE]  
    > The parameter GlobalSettingsDomainController allows you to indicate where global settings are stored. If your settings are stored in the System container (which is typical with upgrade deployments that have not had the global setting migrated to the Configuration container), you define a domain controller in the root of your Active Directory forest. If the global settings are in the Configuration container (which is typical with new deployments or upgrade deployments where the settings have been migrated to the Configuration container), you define any domain controller in the forest. If you do not specify this parameter, the cmdlet assumes that the settings are stored in the Configuration container and refers to any domain controller in AD&nbsp;DS.

    
    </div>

</div>

<div>

## See Also


[Running domain preparation for Lync Server 2013](lync-server-2013-running-domain-preparation.md)  


[Preparing domains for Lync Server 2013](lync-server-2013-preparing-domains.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

