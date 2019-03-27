---
title: 'Lync Server 2013: Configure a secondary Location Information service'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configure a secondary Location Information service
ms:assetid: 083ffbc6-7c18-4141-85f9-8825b62c3d10
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398138(v=OCS.15)
ms:contentKeyID: 48183334
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure a secondary Location Information service in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-30_

Lync Server 2013 provides a web service interface that you can use to point the Location Information service to a Secondary Location Source (SLS) database. The web service interface that connects to the SLS database must conform to Location Information service WSDL. If both a location database and secondary location database are configured, the Location Information service first queries the location database, and if no match is found, sends the location request from the client to the SLS database. If the location exists in the SLS, the Location Information service then sends the location back to the client.

For details, see the Lync Server Management Shell documentation for the following cmdlet:

  - **Set-CsWebServiceConfiguration**

<div>

## To configure Secondary Location database

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

2.  Run the following cmdlet to configure the URL for the location of the secondary location database.
    
        Set-CsWebServiceConfiguration -SecondaryLocationSourceURL "<web service url>" 

</div>

</div>

<span> </span>

</div>

</div>

</div>

