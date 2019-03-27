---
title: 'Lync Server 2013: Enrolling users for smart card authentication'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Enrolling users for smart card authentication
ms:assetid: a6445a83-a94b-423f-ba2a-12b5f84c5d75
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn308570(v=OCS.15)
ms:contentKeyID: 54973691
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Enrolling users for smart card authentication in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-03_

There are generally two methods for enrolling users for smart card authentication. The easier method involves having users enroll directly for smart card authentication using web enrollment, while the more complex method involves using an enrollment agent. This topic focuses on self-enrollment for smartcard certificates.

For more information on enrolling on behalf of users as an enrollment agent, see Enroll for Certificates on Behalf of Other Users at [http://go.microsoft.com/fwlink/p/?LinkID=313367](http://go.microsoft.com/fwlink/p/?linkid=313367).

<div>

## To Enroll Users for Smart Card Authentication

1.  Log in to the Windows 8 workstation using the credentials of a Lync-enabled user.

2.  Launch Internet Explorer.

3.  Browse to the **Certificate Authority Web Enrollment** page (e.g. https://MyCA.contoso.com/certsrv).
    
    <div>
    

    > [!NOTE]  
    > If you are using Internet Explorer 10, you may need to view this website in Compatibility Mode.

    
    </div>

4.  On the **Welcome** Page, select **Request a certificate**.

5.  Next, select **Advanced Request**.

6.  Select **Create and submit a request to this CA**.

7.  Select **Smartcard User** under the **Certificate Template** section and complete the advanced certificate request with the following values:
    
      - **Key Options** confirm he following settings:
        
          - Select the **Create new key set** radio button
        
          - For **CSP**, select **Microsoft Base Smart Card Crypto Provider**
        
          - For **Key Usage**, select **Exchange** (this is the only option available).
        
          - For **Key Size**, enter **2048**
        
          - Confirm that **Automatic key container name** is selected
        
          - Leave the other boxes unchecked.
    
      - Under **Additional Options** confirm the following values:
        
          - For **Request Format** select **CMC**.
        
          - For **Hash Algorithm** select **sha1**.
        
          - For **Friendly Name** enter **Smardcard Certificate**.

8.  If you are using a physical smartcard reader, insert the smart card into the device.

9.  Click **Submit** to submit the certificate request.

10. When prompted, enter the PIN that was used to create the virtual smart card.
    
    <div>
    

    > [!NOTE]  
    > The default virtual smart card PIN value is ‘12345678’.

    
    </div>

11. Once the certificate has been issued, click **Install this certificate** to complete the enrollment process.
    
    <div>
    

    > [!NOTE]  
    > If your certificate request fails with the error “This Web browser does not support the generation of certificate requests,” there are three possible ways to resolve the issue: 
    > <OL>
    > <LI>
    > <P>Enable Compatibility View in Internet Explorer</P>
    > <LI>
    > <P>Enable the Turn on Intranet settings option in Internet Explorer</P>
    > <LI>
    > <P>Select the Reset all zones to default level setting under the Security tab in the Internet Explorer options menu.</P></LI></OL>

    
    </div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

