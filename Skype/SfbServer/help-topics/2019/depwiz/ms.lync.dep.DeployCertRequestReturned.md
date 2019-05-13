---
title: "Certificate Request (Returned)"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.dep.DeployCertRequestReturned
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 4ada9045-0fdf-4470-8574-2fa08bab9392
ROBOTS: NOINDEX, NOFOLLOW
description: "The Online Certificate Request Status page presents you with important information that results from the successful creation and issuing of the online certificate request. This page provides the certificate thumbprint that uniquely identifies the certificate. By default, the check box Assign this certificate to Skype for Business Server certificate usages is selected. If you click Finish, the certificate will be automatically assigned to Skype for Business Server for the purposes that you defined during the creation steps of the certificate request. By default, the purposes that the certificate will be assigned are:"
---

# Certificate Request (Returned)
 
The **Online Certificate Request Status** page presents you with important information that results from the successful creation and issuing of the online certificate request. This page provides the certificate thumbprint that uniquely identifies the certificate. By default, the check box **Assign this certificate to Skype for Business Server certificate usages** is selected. If you click **Finish**, the certificate will be automatically assigned to Skype for Business Server for the purposes that you defined during the creation steps of the certificate request. By default, the purposes that the certificate will be assigned are:
  
- Server Default for Mutual Transport Layer Security (MTLS) - Connections to clients and other servers
    
- Web services internal - Client and server connections on the internal Web services site for Transport Layer Security/Secure Sockets Layer (TLS/SSL)
    
- Web services external - Client and server connections on the external Web services site for TLS/SSL
    
Click the **View Certificate Details** to view the certificate to confirm that the properties of the certificate are what you intended, and that the certificate is ready to be applied and put into use on the server.
  
Click **Finish** to complete the online certificate request process. If you selected the check box **Assign this certificate to Skype for Business Server certificate usages**, the certificate will be automatically assigned. If you chose to clear this check box, you must assign the certificate in a separate step. 
  
> [!IMPORTANT]
> If the issuing certification authority (CA) root certificate is not in the computer's Trusted Root Certification Authority store, or if intermediate CA certificates are not in the proper store, you will see the summary status, as illustrated in the following image. You do not have the option to assign the certificate. To complete the certificate assignment process, you must import the issuing CA root certificate and any intermediate CA certificates, and then assign the certificate by clicking **Assign** on the main Certificate Wizard page.
  

