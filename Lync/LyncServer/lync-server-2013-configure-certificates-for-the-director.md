---
title: 'Lync Server 2013: Configure certificates for the Director'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configure certificates for the Director
ms:assetid: 22988186-15ae-43b1-92f4-0adb3b75a7fd
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398296(v=OCS.15)
ms:contentKeyID: 48183612
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure certificates for the Director in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-08_

<div>


> [!IMPORTANT]  
> When you run the Certificate Wizard, ensure that you are logged in using an account that is a member of a group that has been assigned the appropriate permissions for the type of certificate template you will use. By default, a Lync Server 2013 certificate request will use the Web Server certificate template. If you use an account that is a member of the RTCUniversalServerAdmins group to request a certificate using this template, verify that the group has been assigned the Enroll permissions required to use that template.



</div>

Each Director requires a default certificate, a web internal certificate, and a web external certificate. For details about the certificate requirements for Directors, see [Certificate requirements for internal servers in Lync Server 2013](lync-server-2013-certificate-requirements-for-internal-servers.md) in the Planning documentation.

Use the following procedure to configure Director certificates. Repeat the procedure for each Director. The steps of this procedure describe how to configure a certificate from an Internal Enterprise Root certification authority (CA) deployed by your organization and with offline request processing. For details about obtaining certificates from an external CA, contact your support team.

<div>

## To configure certificates for the Director or Director pool

1.  In the Lync Server Deployment Wizard, next to **Step 3: Request, Install or Assign Certificates**, click **Run**.

2.  On the **Certificate Wizard** page, click **Request**.

3.  On the **Certificate Request** page, click **Next**.

4.  On the **Delayed or Immediate Requests** page, accept the default **Send the request immediately to an online certification authority** option, and then click **Next**.

5.  On the **Choose a Certification Authority (CA)** page, click the internal Windows certification authority that you want to use, and then click **Next**.

6.  On the **Certification Authority Account** page, specify alternate credentials to be used if the account you are logged on with does not have sufficient authority to request the certificate, and then click **Next**.

7.  On the **Specify Alternate Certificate Template** page, click **Next**.

8.  On the **Name and Security Settings** page, you can specify a **Friendly Name**, accept the 2048-bit key length, and then click **Next**.

9.  On the **Organization Information** page, optionally specify organization information, and then click **Next**.

10. On the **Geographical Information** page, optionally specify geographical information, and then click **Next**.

11. On the **Subject Name / Subject Alternative Names** page, click **Next**.
    
    <div>
    

    > [!NOTE]  
    > The subject alternative name list should contain the name of the computer on which you are installing the Director (if a single Director) or the Director pool name, and the simple URL names configured for the organization.

    
    </div>

12. On the **SIP Domain Setting on Subject Alternate Names (SANs)** page, select the **Configured SIP Domains** for all domains that you want the Director to handle, and then click **Next**.

13. On the **Configure Additional Subject Alternative Names** page, add any additional required subject alternative names, and then click **Next**.

14. On the **Certificate Request Summary** page, click **Next**.

15. On the **Executing Commands** page, click **Next** after the commands have finished running.

16. On the **Online Certificate Request Status** page, click **Finish**.

17. On the **Certificate Assignment** page, click **Next**.
    
    <div>
    

    > [!NOTE]  
    > if you want to view the certificate, double-click the certificate in the list.

    
    </div>

18. On the **Certificate Assignment Summary** page, click **Next**.

19. On the **Executing Commands** page, click **Finish** after the commands have finished running.

20. On the **Certificate Wizard** page, click **Close**.

</div>

</div>

<span> </span>

</div>

</div>

</div>

