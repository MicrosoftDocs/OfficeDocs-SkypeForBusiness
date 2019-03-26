---
title: Enable Exchange 2013 Outlook Web App and IM integration
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Enable Exchange 2013 Outlook Web App and IM integration
ms:assetid: 44d08cf0-b17d-46e1-a4f0-fcc2fe96a958
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204857(v=OCS.15)
ms:contentKeyID: 48184027
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Enable Exchange 2013 Outlook Web App and IM integration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-19_

To enable Exchange 2013 Outlook Web Access (OWA) and instant messaging (IM) integration with Lync Server 2013, you must add the Exchange 2013 Client Access Server (CAS) server to the Lync Server 2013 topology as a trusted application server.

<div>

## To create a trusted application pool

1.  Start the Lync Server 2013 Management Shell.

2.  Run the following cmdlet:
    
        Get-CsSite
    
    This returns the siteID for the siteName in which you are creating the pool. For details, see [Get-CsSite](https://docs.microsoft.com/powershell/module/skype/Get-CsSite) in the Lync Server 2013 Management Shell documentation.

3.  Run the following cmdlet:
    
        New-CsTrustedApplicationPool -Identity <E14 CAS FQDN> -ThrottleAsServer $true -TreatAsAuthenticated $true -ComputerFQDN <E14 CAS FQDN> -Site <Site> -Registrar <Pool FQDN in the site> -RequiresReplication $false
    
    For details, see [New-CsTrustedApplicationPool](https://docs.microsoft.com/powershell/module/skype/New-CsTrustedApplicationPool) in the Lync Server 2013 Management Shell documentation.
    
    The Exchange Server FQDN should be configured as the Exchange OWA certificate Subject Name (SN), or the Subject Alternate Name (SAN).
    
    In Exchange OWA, verify that the pool’s FQDN is trusted as well.
    
    <div>
    

    > [!IMPORTANT]  
    > If your CAS server is <EM>not</EM> collocated on the same server that is running Exchange 2013 Unified Messaging (UM), skip the remaining steps in this procedure and perform the “Create a trusted application for the Exchange 2013 CAS server” procedure later in this topic. If your CAS server is collocated on the same server that is running Exchange 2013 Unified Messaging (UM), complete the steps in this procedure and do not perform the “Create a trusted application for the Exchange 2013 CAS server” procedure later in this topic.

    
    </div>

4.  Run **Enable-CsTopology**.

5.  Open Topology Builder and download the existing topology.

6.  In the left pane, expand the tree until you reach **Trusted application servers**.

7.  Expand the **Trusted application servers** node.

8.  You should now see the Exchange 2013 CAS server listed as a trusted application server.

</div>

<div>

## To create a trusted application for the Exchange 2013 CAS server

1.  Start the Lync Server 2013 Management Shell.

2.  If your CAS server is *not* collocated on the same server that is running Exchange 2013 Unified Messaging (UM), run the following cmdlet:
    
        New-CsTrustedApplication -ApplicationId <AppID String> -TrustedApplicationPoolFqdn <E14 CAS FQDN> -Port <available port number>
    
    For details, see the topic [New-CsTrustedApplication](https://docs.microsoft.com/powershell/module/skype/New-CsTrustedApplication) in the Lync Server 2013 Management Shell documentation.

3.  Run **Enable-CsTopology**.

4.  From Topology Builder, in the left pane, expand the tree until you reach **Trusted application servers**.

5.  Expand the **Trusted application servers** node.

6.  You should now see the Exchange 2013 CAS server listed as a trusted application server.

</div>

</div>

<span> </span>

</div>

</div>

</div>

