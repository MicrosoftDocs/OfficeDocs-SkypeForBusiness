---
title: 'Lync Server 2013: Reviewing the Certificates Report'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Reviewing the Certificates Report
ms:assetid: 549cfc9b-3cc5-4483-a93c-fc0738c7f622
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg558651(v=OCS.15)
ms:contentKeyID: 51541477
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Reviewing the Certificates Report in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

The Certificates Report contains all certificates that are required in the recommended Lync Server 2013 deployment. The Planning Tool accounts for the subject names and subject alternative names that are entered. Default text that is left unedited may represent a potential challenge for the team responsible for requesting and issuing the certificates. Certificate information also contains information about where the certificate can typically be issued from. If the infrastructure does not have an internal public key infrastructure (PKI) in place, all certificates can be requested through a public certificate provider. Extended key usages (EKU) and Assign To fields in the report are very helpful in understanding what the purpose and location for each certificate should be.

![Certificates Admin Report](images/Gg558651.63a29335-d9e4-41ae-97ec-3c9d9fd30d8a(OCS.15).jpg "Certificates Admin Report")

Carefully review, and be sure to understand, the use and purpose of each certificate in the deployment. If there is a question about what a certificate does, determine which server or service is talking to what. Certificates in Lync Server 2013 are used for two primary purposes:

  - Mutual Transport Layer Security (MTLS) – The computers involved in the communication each present a certificate that proves their identity to another computer. This is known as server authentication. Communication cannot begin until each computer trusts the other computer’s identity.

  - Encryption – Encryption (Secure Sockets Layer, or SSL, and Transport Layer Security, or TLS) is a critical means to help secure communications, help ensure privacy, and to create a trusted communications and collaboration system.

<div>

## See Also


[Reviewing the Administrator Reports in Lync Server 2013](lync-server-2013-reviewing-the-administrator-reports.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

