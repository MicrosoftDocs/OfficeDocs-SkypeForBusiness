---
title: "Certificate Wizard"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/26/2015
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.dep.DeployCertsMain
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 6ab661d7-5741-4cad-bbe4-62cf862ded85
description: "To Request, Assign, Remove, or View certificates, you use the Certificate Wizard. You must be logged in as a member of the RTCUniversalServerAdmins group. To request a certificate from a public certification authority (CA), you do not need any additional group memberships. To request a certificate from your organization's public key infrastructure (PKI), you need to confirm what additional—if any—group memberships you will need. During the Request task, you can enter alternate credentials that will be used to request the certificate from your PKI's issuing CA."
---

# Certificate Wizard
 
To **Request**, **Assign**, **Remove**, or **View** certificates, you use the Certificate Wizard. You must be logged in as a member of the RTCUniversalServerAdmins group. To request a certificate from a public certification authority (CA), you do not need any additional group memberships. To request a certificate from your organization's public key infrastructure (PKI), you need to confirm what additional—if any—group memberships you will need. During the Request task, you can enter alternate credentials that will be used to request the certificate from your PKI's issuing CA.
  
To request a new certificate, click **Request**.
  
To assign a certificate that has not been assigned yet, click **Assign**.
  
To remove a certificate that you have previously assigned, click **Remove**.
  
> [!NOTE]
> The **Remove** button will be available only if a certificate has been previously assigned. If the **Remove** button is unavailable (dimmed), there is no certificate assigned.
  
To view an assigned certificate, click **View**.
  
> [!NOTE]
> The **View** button will be available only if a certificate has been previously assigned. If the **View** button is greyed out, there is no certificate assigned.
  
To refresh the current certificate assignment screen, click **Refresh**.
  
To import a certificate that is not present in the certificate store, click **Import Certificate**.
  
> [!NOTE]
> **Import Certificate** is typically used to process a certificate that is received through a process other than a request from the Certificate Wizard. For example, your PKI administrator creates a certificate and makes it available to you. Use **Import Certificate** to import the certificate into the computer's certificate store and make it available to Skype for Business Server to assign.
  
To complete the process of requesting a certificate request from a CA in your organization that requires CA administrator approval, click **Process Pending Request**. The certificate request will have returned a status of pending, and also displays the identification number of the pending request. To continue processing a certificate with a pending status, click **Refresh** to enable the **Process Pending Request** button. The **Process Pending Request** button will no longer be unavailable (dimmed). You can then attempt to retrieve the pending request, but the status of the request will remain pending until the certificate is issued or denied by the CA administrator. The button will be unavailable if there are no valid pending requests that have been created by the Certificate Wizard.
  

