---
title: "Reviewing the Certificates Report in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 549cfc9b-3cc5-4483-a93c-fc0738c7f622
description: "The Certificates Report contains all certificates that are required in the recommended Lync Server 2013 deployment. The Planning Tool accounts for the subject names and subject alternative names that are entered. Default text that is left unedited may represent a potential challenge for the team responsible for requesting and issuing the certificates. Certificate information also contains information about where the certificate can typically be issued from. If the infrastructure does not have an internal public key infrastructure (PKI) in place, all certificates can be requested through a public certificate provider. Extended key usages (EKU) and Assign To fields in the report are very helpful in understanding what the purpose and location for each certificate should be."
---

# Reviewing the Certificates Report in Lync Server 2013
[]
The Certificates Report contains all certificates that are required in the recommended Lync Server 2013 deployment. The Planning Tool accounts for the subject names and subject alternative names that are entered. Default text that is left unedited may represent a potential challenge for the team responsible for requesting and issuing the certificates. Certificate information also contains information about where the certificate can typically be issued from. If the infrastructure does not have an internal public key infrastructure (PKI) in place, all certificates can be requested through a public certificate provider. Extended key usages (EKU) and Assign To fields in the report are very helpful in understanding what the purpose and location for each certificate should be. 
  
![Certificates Admin Report](media/Certificates_Report_Admin_Report.jpg)
  
Carefully review, and be sure to understand, the use and purpose of each certificate in the deployment. If there is a question about what a certificate does, determine which server or service is talking to what. Certificates in Lync Server 2013 are used for two primary purposes:
  
- Mutual Transport Layer Security (MTLS) - The computers involved in the communication each present a certificate that proves their identity to another computer. This is known as server authentication. Communication cannot begin until each computer trusts the other computer's identity.
    
- Encryption - Encryption (Secure Sockets Layer, or SSL, and Transport Layer Security, or TLS) is a critical means to help secure communications, help ensure privacy, and to create a trusted communications and collaboration system.
    
## See also

#### 

[Reviewing the Administrator Reports in Lync Server 2013](reviewing-the-administrator-reports.md)

