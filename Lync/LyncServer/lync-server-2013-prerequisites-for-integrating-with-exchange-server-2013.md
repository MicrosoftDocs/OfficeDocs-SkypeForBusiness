---
title: 'Lync Server 2013: Prerequisites for integrating with Exchange Server 2013'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Prerequisites for integrating Lync Server 2013 and Exchange Server 2013
ms:assetid: ea22beb9-c02e-47cb-836d-97a556969052
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ721919(v=OCS.15)
ms:contentKeyID: 49733853
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Prerequisites for integrating Microsoft Lync Server 2013 and Microsoft Exchange Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-04-22_

Before you can integrate Microsoft Lync Server 2013 and Microsoft Exchange Server 2013 you must ensure that all the prerequisite steps have been completed. As you might expect, integration cannot take place until both Exchange 2013 and Lync Server 2013 are fully installed and up and running. For details about installing Exchange, see the Exchange 2013 Planning and Deployment documentation at [http://go.microsoft.com/fwlink/p/?LinkId=268539](http://go.microsoft.com/fwlink/p/?linkid=268539). For details about installing Lync Server 2013, see the planning and deployment documentation at [http://go.microsoft.com/fwlink/p/?LinkId=254806](http://go.microsoft.com/fwlink/p/?linkid=254806).

After the servers are up and running you must assign server-to-server authentication certificates to both Lync Server 2013 and Exchange 2013; these certificates allow Lync Server and Exchange to exchange information and to communicate with one another. When you install Exchange 2013, a self-signed certificate with the name Microsoft Exchange Server Auth Certificate is created for you. This certificate, which can be found in the local computer certificate store, should be used for server-to-server authentication on Exchange 2013. For details about assigning certificates in Exchange 2013, see "Configure Mail Flow and Client Access" at [http://go.microsoft.com/fwlink/p/?LinkId=268540](http://go.microsoft.com/fwlink/p/?linkid=268540).

For Lync Server 2013 you can use an existing Lync Server certificate as your server-to-server authentication certificate; for example, your default certificate can also be used as the OAuthTokenIssuer certificate. Lync Server 2013 allows you to use any Web server certificate as the certificate for server-to-server authentication provided that:

  - The certificate includes the name of your SIP domain in the Subject field.

  - The same certificate is configured as the OAuthTokenIssuer certificate on all of your Front End Servers.

  - The certificate has a length of at least 2048 bits.

For details about server-to-server authentication certificates for Microsoft Lync Server 2013, see [Assigning a server-to-server authentication certificate to Microsoft Lync Server 2013](lync-server-2013-assigning-a-server-to-server-authentication-certificate-to-lync-server-2013.md).

After the certificates have been assigned you must then configure the autodiscover service on Exchange 2013. In Exchange 2013, the autodiscover service configures user profiles and provides access to Exchange services when users log on to the system. Users present the autodiscover service with their email address and password; in turn, the services provide the user with information such as:

  - Connection information for both internal and external connectivity to Exchange 2013.

  - The location of the user’s Mailbox server.

  - URLs for Outlook features such as free/busy information, Unified Messaging, and the offline address book.

  - Outlook Anywhere server settings.

The autodiscover service must be configured before you can integrate Lync Server 2013 and Exchange 2013. You can verify whether or not the autodiscover service has been configured by running the following command from the Exchange Management Shell and checking the value of the AutoDiscoverServiceInternalUri property:

    Get-ClientAccessServer | Select-Object Name, AutoDiscoverServiceInternalUri | Format-List

If this value is blank, you must assign a URI to the autodiscover service. Typically this URI will look similar to this:

    https://autodiscover.litwareinc.com/autodiscover/autodiscover.xml

You can assign the autodiscover URI by running a command similar to this:

    Get-ClientAccessServer | Set-ClientAccessServer -AutoDiscoverServiceInternalUri "https://autodiscover.litwareinc.com/autodiscover/autodiscover.xml"

For details about the autodiscover service, see "Understanding the Autodiscover Service" at [http://go.microsoft.com/fwlink/p/?LinkId=268542](http://go.microsoft.com/fwlink/p/?linkid=268542).

After the autodiscover service has been configured you must then modify the Lync Server OAuth configuration settings; this ensures that Lync Server knows where to find the autodiscover service. To modify the OAuth configuration settings in Lync Server 2013, run the following command from within the Lync Server Management Shell. When running this command, be sure that you specify the URI to the autodiscover service running on your Exchange server, and that you use **autodiscover.svc** to point to the service location instead of **autodiscover.xml** (which points to the XML file used by the service):

    Set-CsOAuthConfiguration -Identity global -ExchangeAutodiscoverUrl "https://autodiscover.litwareinc.com/autodiscover/autodiscover.svc"

<div>


> [!NOTE]  
> The Identity parameter in the preceding command is optional; that's because Lync Server only allows you to have a single, global collection of OAuth configuration settings. Among other things, that means that you can configure the autodiscover URL by using this slightly-simpler command:<BR>Set-CsOAuthConfiguration–ExchangeAutodiscoverUrl "https://autodiscover.litwareinc.com/autodiscover/autodiscover.svc"<BR>If you are unfamiliar with the technology, OAuth is a standard authorization protocol used by a number of major websites. With OAuth, user credentials and passwords are not passed from one computer to another. Instead, authentication and authorization is based on the exchange of security tokens; these tokens grant access to a specific set of resources for a specific amount of time.



</div>

In addition to configuring the autodiscover service, you must also create a DNS record for the service that points to your Exchange server. For example, if your autodiscover service is located at autodiscover.litwareinc.com you will need to create a DNS record for autodiscover.litwareinc.com that resolves to the fully qualified domain name of your Exchange server (for example, atl-exchange-001.litwareinc.com).

</div>

<span> </span>

</div>

</div>

</div>

