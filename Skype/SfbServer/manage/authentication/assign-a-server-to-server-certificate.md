---
title: "Assign a server-to-server authentication certificate to Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: c7413954-2504-47f4-a073-44548aff1c0c
description: "Summary: Assign a server-to-server authentication certificate for Skype for Business Server."
---

# Assign a server-to-server authentication certificate to Skype for Business Server
**Summary:** Assign a server-to-server authentication certificate for Skype for Business Server.
  
To determine whether or not a server-to-server authentication certificate has already been assigned to Skype for Business Server, run the following command from the Skype for Business Server Management Shell:
  
```
Get-CsCertificate -Type OAuthTokenIssuer
```

If no certificate information is returned you must assign a token issuer certificate before you can use server-to-server authentication. As a general rule, any Skype for Business Server certificate can be used as your OAuthTokenIssuer certificate; for example, your Skype for Business Server default certificate can also be used as the OAuthTokenIssuer certificate. (The OAUthTokenIssuer certificate can also be any Web server certificate that includes the name of your SIP domain in the Subject field.) The primary two requirements for the certificate used for server-to-server authentication are these: 1)the same certificate must be configured as the OAuthTokenIssuer certificate on all of your Front End Servers; and, 2) the certificate must be at least 2048 bits.
  
If you do not have a certificate that can be used for server-to-server authentication you can obtain a new certificate, import the new certificate, and then use that certificate for server-to-server authentication. After you have requested and obtained the new certificate you can then log on to any one of your Front End Servers and use a Windows PowerShell command similar to this one to import and assign that certificate:
  
```
Import-CsCertificate -Identity global -Type OAuthTokenIssuer -Path C:\Certificates\ServerToServerAuth.pfx  -Password "P@ssw0rd"
```

In the preceding command the Path parameter represents the full path to the certificate file, and the Password parameter represents the password that was assigned to the certificate. This procedure should be run just one time: the Skype for Business Server replication service will then automatically create a set of scheduled tasks that will decrypt and deploy the certificate to all your Front End Servers.
  
Alternatively, you can use an existing certificate as your server-to-server authentication certificate. (As noted, the default certificate can be used as the server-to-server authentication certificate.) The following pair of Windows PowerShell commands retrieve the value of the default certificate's Thumbprint property, then use that value to make the default certificate the server-to-server authentication certificate:
  
```
$x = (Get-CsCertificate -Type Default).Thumbprint
Set-CsCertificate -Identity global -Type OAuthTokenIssuer -Thumbprint $x
```

In the preceding command, the retrieved certificate is configured to function as the global server-to-server authentication certificate; that means that the certificate will be replicated to, and used by, all your Front End Servers. Again, this command should only be run one time, and only on one of your Front End Servers. Although all Front End Servers must use the same certificate, you should not configure the OAuthTokenIssuer certificate on each Front End Server. Instead, configure the certificate once, then let the Skype for Business Server replication server take care of copying that certificate to each server.
  
The Set-CsCertificate cmdlet takes the certificate in question and immediately configures that certificate to act as the current OAuthTokenIssuer certificate. (Skype for Business Server keeps two copies of a certificate type: the current certificate and the previous certificate.) If you need the new certificate to immediately begin to act as the OAuthTokenIssuer certificate then you should use the Set-CsCertificate cmdlet.
  
You can also use the Set-CsCertificate cmdlet to "roll" a new certificate. "Rolling" a certificate simply means that you configure a new certificate to become the current OAuthTokenIssuer certificate at a specified point in time. For example, this command retrieves the default certificate and then configure that certificate to take over as the current OAuthTokenIssuer certificate as of July 1, 2015:
  
```
$x = (Get-CsCertificate -Type Default).Thumbprint
Set-CsCertificate -Identity global -Type OAuthTokenIssuer -Thumbprint $x -EffectiveDate "7/1/2015" -Roll
```

On July 1, 2015, the new certificate will be configured as the current OAuthTokenIssuer certificate and the "old" OAuthTokenIssuer certificate will be configured as the previous certificate.
  
If you do not want to use Windows PowerShell you can also use the Certificates MMC console to export a certificate from one Front End Server and then import that same certificate on all your other Front End Servers. If you do this, make sure that you export the private key along with the certificate itself.
  
> [!CAUTION]
> In this case, the procedure must be performed on each Front End Server. When exporting and importing certificates in this manner Skype for Business Server will not replicate that certificate to each Front End Server. 
  
After the certificate has been imported to all your Front End Servers, that certificate can then be assigned by using the Skype for Business Server Deployment Wizard instead of Windows PowerShell. To assign a certificate by using the Deployment Wizard, complete the following steps on a computer where the Deployment Wizard has been installed:
  
1. Click Start, click All Programs, click **Skype for Business Server**, and then click **Skype for Business Server Deployment Wizard**.
    
2. In the Deployment Wizard, click **Install or Update Skype for Business Server System**.
    
3. On the Skype for Business Server page, click the **Run** button under the heading **Step 3: Request, Install or Assign Certificates**. (Note: If you have already installed certificates on this computer then the **Run** button will be labeled **Run Again**.)
    
4. In the Certificate Wizard, select the **OAuthTokenIssuer** certificate and then click **Assign**.
    
5. In the Certificate Assignment wizard, on the **Certificate Assignment** page, click **Next**.
    
6. On the **Certificate Store** page, select the certificate to be used for server-to-server authentication and then click **Next**.
    
7. On the Certificate Assignment Summary page, click **Next**.
    
8. On the Executing Commands page, click **Finish**.
    
9. Close the Certificate Wizard and the Deployment Wizard.
    

