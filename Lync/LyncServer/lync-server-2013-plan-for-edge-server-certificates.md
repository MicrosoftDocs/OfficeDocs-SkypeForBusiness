---
title: 'Lync Server 2013: Plan for Edge Server certificates'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Plan for Edge Server certificates
ms:assetid: f1dfe220-2398-4ac8-ba4c-206c8c0cbc50
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg413010(v=OCS.15)
ms:contentKeyID: 48185798
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Plan for Edge Server certificates in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-05_

Certificate creation for Edge is simplified in Lync Server 2013.

**Certificates Flow Chart for Edge Server**

![a5fc20db-7ced-4364-b577-6a709a8367cd](images/Gg413010.a5fc20db-7ced-4364-b577-6a709a8367cd(OCS.15).jpg "a5fc20db-7ced-4364-b577-6a709a8367cd")

Create a single public certificate, ensure that you have an exportable private key defined for the certificate, and assign it to the following Edge Server external interfaces using the certificate wizard:

<div>


> [!IMPORTANT]  
> Wildcard certificates are not supported in Lync Server, except where used to summarize the Simple URLs through the reverse proxy. You must define distinct subject alternate names (SANs) for each SIP domain name, Web Conferencing Edge service, A/V Edge service and XMPP domain offered by your deployment.



</div>

<div>


> [!NOTE]  
> Introduced in Lync Server 2013, staging Audio/Video Authentication certificates in advance of the expiration time of the current certificate requires some additional planning. Instead of one certificate with multiple purposes for the external Edge interface, you will require two certificates, one assigned to the Access Edge service and Web Conferencing Edge service, and one certificate for the A/V Edge service. For additional details, see <A href="lync-server-2013-staging-av-and-oauth-certificates-using-roll-in-https://docs.microsoft.com/powershell/module/skype/Set-CsCertificate">Staging AV and OAuth certificates in Lync Server 2013 using -Roll in Set-CsCertificate</A>



</div>

<div>


> [!IMPORTANT]  
> In the event of a pool of Edge Servers, you export the certificate with the private key to each Edge Server and assign the certificate to each Edge Server service. Do the same for the internal Edge Server certificate, exporting the certificate with the private key and assigning to each internal Edge interface.



</div>

  - Ensure that you have an exportable private key assigned for the certificate

  - Access Edge service (referred to as **SIP Access Edge External** in the certificate wizard)

  - Web Conferencing Edge service (referred to as **Web Conferencing Edge External** in the certificate wizard)

  - A/V Authentication service (referred to as **A/V Edge External** in the certificate wizard)

Create a single internal certificate with exportable private key, copy and assign it to each of the Edge Server internal interfaces:

  - Edge Server (referred to as **Edge Internal** in the certificate wizard)

<div>


> [!IMPORTANT]  
> It is possible to use separate and distinct certificates for each Edge Server service. A good reason to choose separate certificates is if you want to use the new rolling certificate feature for the A/V Edge service certificate. In the case of this feature, decoupling the A/V Edge service certificate from the Access Edge service and Web Conferencing Edge service is recommended. If you choose to request, acquire and assign separate certificates for each service, you must request that the private key be exportable for the A/V Edge service (again, this is in actuality the A/V Authentication service) and assign the same certificate to the A/V Edge External interface on each Edge Server.



</div>

<div>

## See Also


[Staging AV and OAuth certificates in Lync Server 2013 using -Roll in Set-CsCertificate](lync-server-2013-staging-av-and-oauth-certificates-using-roll-in-https://docs.microsoft.com/powershell/module/skype/Set-CsCertificate)  


[Changes in Lync Server 2013 that affect Edge Server planning](lync-server-2013-changes-in-lync-server-that-affect-edge-server-planning.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

