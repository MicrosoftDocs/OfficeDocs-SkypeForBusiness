---
title: "Enrolling users for smart card authentication in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a6445a83-a94b-423f-ba2a-12b5f84c5d75
description: "There are generally two methods for enrolling users for smart card authentication. The easier method involves having users enroll directly for smart card authentication using web enrollment, while the more complex method involves using an enrollment agent. This topic focuses on self-enrollment for smartcard certificates."
---

# Enrolling users for smart card authentication in Lync Server 2013
[]
There are generally two methods for enrolling users for smart card authentication. The easier method involves having users enroll directly for smart card authentication using web enrollment, while the more complex method involves using an enrollment agent. This topic focuses on self-enrollment for smartcard certificates.
  
For more information on enrolling on behalf of users as an enrollment agent, see Enroll for Certificates on Behalf of Other Users at [https://go.microsoft.com/fwlink/p/?LinkID=313367](https://go.microsoft.com/fwlink/p/?LinkID=313367).
  
## To Enroll Users for Smart Card Authentication

1. Log in to the Windows 8 workstation using the credentials of a Lync-enabled user.
    
2. Launch Internet Explorer.
    
3. Browse to the **Certificate Authority Web Enrollment** page (e.g. https://MyCA.contoso.com/certsrv). 
    
    > [!NOTE]
    > If you are using Internet Explorer 10, you may need to view this website in Compatibility Mode. 
  
4. On the **Welcome** Page, select **Request a certificate**.
    
5. Next, select **Advanced Request**.
    
6. Select **Create and submit a request to this CA**.
    
7. Select **Smartcard User** under the **Certificate Template** section and complete the advanced certificate request with the following values: 
    
  - **Key Options** confirm he following settings: 
    
  - Select the **Create new key set** radio button 
    
  - For **CSP**, select **Microsoft Base Smart Card Crypto Provider**
    
  - For **Key Usage**, select **Exchange** (this is the only option available). 
    
  - For **Key Size**, enter 2048
    
  - Confirm that **Automatic key container name** is selected 
    
  - Leave the other boxes unchecked.
    
  - Under **Additional Options** confirm the following values: 
    
  - For **Request Format** select **CMC**.
    
  - For **Hash Algorithm** select **sha1**.
    
  - For **Friendly Name** enter Smardcard Certificate.
    
8. If you are using a physical smartcard reader, insert the smart card into the device.
    
9. Click **Submit** to submit the certificate request. 
    
10. When prompted, enter the PIN that was used to create the virtual smart card.
    
    > [!NOTE]
    > The default virtual smart card PIN value is '12345678'. 
  
11. Once the certificate has been issued, click **Install this certificate** to complete the enrollment process. 
    
    > [!NOTE]
    >  If your certificate request fails with the error "This Web browser does not support the generation of certificate requests," there are three possible ways to resolve the issue: >  Enable Compatibility View in Internet Explorer >  Enable the Turn on Intranet settings option in Internet Explorer >  Select the Reset all zones to default level setting under the Security tab in the Internet Explorer options menu. 
  

