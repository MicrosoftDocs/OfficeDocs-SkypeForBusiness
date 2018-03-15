---
title: "Enable Exchange 2013 Outlook Web App and IM integration [OCS 2007 R2 to W15]"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 44d08cf0-b17d-46e1-a4f0-fcc2fe96a958
description: "To enable Exchange 2013 Outlook Web Access (OWA) and instant messaging (IM) integration with Lync Server 2013, you must add the Exchange 2013 Client Access Server (CAS) server to the Lync Server 2013 topology as a trusted application server."
---

# Enable Exchange 2013 Outlook Web App and IM integration [OCS 2007 R2 to W15]
[]
To enable Exchange 2013 Outlook Web Access (OWA) and instant messaging (IM) integration with Lync Server 2013, you must add the Exchange 2013 Client Access Server (CAS) server to the Lync Server 2013 topology as a trusted application server.
  
## To create a trusted application pool

1. Start the Lync Server 2013 Management Shell. 
    
2. Run the following cmdlet:
    
  ```
  Get-CsSite
  ```

    This returns the siteID for the siteName in which you are creating the pool. For details, see [Get-CsSite](get-cssite.md) in the Lync Server 2013 Management Shell documentation. 
    
3. Run the following cmdlet:
    
  ```
  New-CsTrustedApplicationPool -Identity <E14 CAS FQDN> -ThrottleAsServer $true -TreatAsAuthenticated $true -ComputerFQDN <E14 CAS FQDN> -Site <Site> -Registrar <Pool FQDN in the site> -RequiresReplication $false
  ```

    For details, see [New-CsTrustedApplicationPool](new-cstrustedapplicationpool.md) in the Lync Server 2013 Management Shell documentation. 
    
    The Exchange Server FQDN should be configured as the Exchange OWA certificate Subject Name (SN), or the Subject Alternate Name (SAN).
    
    In Exchange OWA, verify that the pool's FQDN is trusted as well. 
    
    > [!IMPORTANT]
    > If your CAS server is  *not*  collocated on the same server that is running Exchange 2013 Unified Messaging (UM), skip the remaining steps in this procedure and perform the "Create a trusted application for the Exchange 2013 CAS server" procedure later in this topic. If your CAS server is collocated on the same server that is running Exchange 2013 Unified Messaging (UM), complete the steps in this procedure and do not perform the "Create a trusted application for the Exchange 2013 CAS server" procedure later in this topic. 
  
4. Run **Enable-CsTopology**.
    
5. Open Topology Builder and download the existing topology.
    
6. In the left pane, expand the tree until you reach **Trusted application servers**.
    
7. Expand the **Trusted application servers** node. 
    
8. You should now see the Exchange 2013 CAS server listed as a trusted application server.
    
## To create a trusted application for the Exchange 2013 CAS server

1. Start the Lync Server 2013 Management Shell. 
    
2. If your CAS server is  *not*  collocated on the same server that is running Exchange 2013 Unified Messaging (UM), run the following cmdlet: 
    
  ```
  New-CsTrustedApplication -ApplicationId <AppID String> -TrustedApplicationPoolFqdn <E14 CAS FQDN> -Port <available port number>
  ```

    For details, see the topic [New-CsTrustedApplication](new-cstrustedapplication.md) in the Lync Server 2013 Management Shell documentation. 
    
3. Run **Enable-CsTopology**.
    
4. From Topology Builder, in the left pane, expand the tree until you reach **Trusted application servers**.
    
5. Expand the **Trusted application servers** node. 
    
6. You should now see the Exchange 2013 CAS server listed as a trusted application server.
    

