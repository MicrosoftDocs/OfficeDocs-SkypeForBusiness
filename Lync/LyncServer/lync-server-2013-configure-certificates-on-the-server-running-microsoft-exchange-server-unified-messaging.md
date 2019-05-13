---
title: 'Lync Server 2013: Configure certificates on the server running Microsoft Exchange Server Unified Messaging'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configure certificates on the server running Microsoft Exchange Server Unified Messaging
ms:assetid: 74c883b4-cef6-41a9-b2eb-7212be32fea4
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398564(v=OCS.15)
ms:contentKeyID: 48184521
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure certificates on the server running Microsoft Exchange Server Unified Messaging

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-26_

If you have deployed Exchange Unified Messaging (UM), as described in [Planning for Exchange Unified Messaging integration in Lync Server 2013](lync-server-2013-planning-for-exchange-unified-messaging-integration.md) in the Planning documentation, and you want to provide Exchange UM features to Enterprise Voice users in your organization, you can use the following procedures to configure the certificate on the server running Exchange UM.

<div>


> [!IMPORTANT]  
> For internal certificates, both the servers running Lync Server 2013 and the servers running Microsoft Exchange must have trusted root authority certificates that are mutually trusted. The certification authority (CA) can either be the same, or a different certification authority, as long as the servers have the certification authority’s root certificate registered in their trusted root authority certificate store.



</div>

The Exchange Server must be configured with a server certificate in order to connect to Lync Server 2013:

1.  Download the CA certificate for the Exchange Server.

2.  Install the CA certificate for the Exchange Server.

3.  Verify that the CA is in the list of trusted root CAs of the Exchange Server.

4.  Create a certificate request for the Exchange Server and install the certificate.

5.  Assign the certificate for the Exchange Server.

<div>

## To download the CA certificate

1.  On the server running Exchange UM, click **Start**, click **Run**, type **http://\<name of your Issuing CA Server\>/certsrv**, and then click **OK**.

2.  Under **Select a task**, click **Download a CA certificate, certificate chain, or CRL**.

3.  Under **Download a CA Certificate, Certificate Chain, or CRL**, select **Encoding Method to Base 64**, and then click **Download CA certificate**.
    
    <div>
    

    > [!NOTE]  
    > You can also specify Distinguished Encoding Rules (DER) encoding at this step. If you select DER encoding, the file type in the next step of this procedure and in step 10 of <STRONG>To Install the CA certificate</STRONG> is .p7b rather than .cer.

    
    </div>

4.  In the **File Download** dialog box, click **Save**, and then save the file to the hard disk on the server. (The file will have either a .cer or a .p7b file extension, depending on the encoding that you selected in the previous step.)

</div>

<div>

## To install the CA certificate

1.  On the server running Exchange UM, open Microsoft Management Console (MMC) by clicking **Start**, clicking **Run**, typing **mmc** in the **Open** box, and then clicking **OK**.

2.  On the **File** menu, click **Add/Remove Snap-in**, and then click **Add**.

3.  In the **Add Standalone Snap-ins** box, click **Certificates**, and then click **Add**.

4.  In the **Certificate snap-in** dialog box, click **Computer account**, and then click **Next**.

5.  In the **Select Computer** dialog box, verify that the **Local computer: (the computer this console is running on)** check box is selected, and then click **Finish**.

6.  Click **Close**, and then click **OK**.

7.  In the console tree, expand **Certificates (Local Computer)**, expand **Trusted Root Certification Authorities**, and then click **Certificates**.

8.  Right-click **Certificates**, click **All Tasks**, and click **Import**.

9.  Click **Next**.

10. Click **Browse** to locate the file, and then click **Next**. (The file will have either a .cer or a .p7b file extension, depending on the encoding that you selected in step 3 of **To download the CA certificate**.

11. Click **Place All Certificates in the following store**.

12. Click **Browse**, and then select **Trusted Root Certification Authorities**.

13. Click **Next** to verify the settings, and then click **Finish**.

</div>

<div>

## To verify that the CA is in the list of trusted root CAs

1.  On the server running Exchange UM, in MMC expand **Certificates (Local Computer)**, expand **Trusted Root Certification Authorities**, and then click **Certificates**.

2.  In the details pane, verify that your CA is on the list of trusted CAs.

</div>

<div>

## To configure Exchange Server 2013 UM with Lync Server

1.  For details, see "Integrate Exchange 2013 UM with Lync Server" in the Exchange Server documentation at [http://go.microsoft.com/fwlink/p/?LinkId=265372](http://go.microsoft.com/fwlink/p/?linkid=265372).

</div>

<div>

## To create a certificate request and install the certificate on Exchange Server 2007 (SP1)

1.  On the server running Exchange UM, click **Start**, click **Run**, type **http://\<**name of your Issuing CA Server**\>/certsrv**, and then click **OK**.

2.  Under **Select a task**, click **Request a Certificate**.

3.  Under **Request a Certificate**, click **Advanced certificate request**.

4.  Under **Advanced Certificate Request**, click **Create and submit a request to this CA**.

5.  Under **Advanced Certificate Request**, select **Web server** or another server certificate template configured for server authentication.

6.  Under **Identifying Information for Offline Template**, in the **Name** box, type the fully qualified domain name (FQDN) of the Exchange Server.
    
    <div>
    

    > [!NOTE]  
    > You must enter the FQDN of the Exchange Server for communications to work.

    
    </div>

7.  Under **Key Options**, click the **Store certificate in the local computer certificate store** check box.

8.  Click the **Submit** button in the bottom of the webpage.

9.  In the dialog box that opens asking for confirmation, click **Yes**.

10. On the Certificate Issued page, under **Certificate Issued**, click **Install this certificate**.

11. In the dialog box that opens asking for confirmation, click **Yes**.

12. Verify that the message "Your new certificate has been successfully installed" appears.

</div>

<div>

## To create a certificate on Exchange Server 2010

1.  Log on to the server running Exchange UM with appropriate user rights. For details, see "Client Access Permissions" at [http://go.microsoft.com/fwlink/p/?linkId=195499](http://go.microsoft.com/fwlink/p/?linkid=195499).

2.  Refer to the following procedures to create the certificate:
    
    1.  "Create a New Exchange Certificate" at [http://go.microsoft.com/fwlink/p/?linkId=195494](http://go.microsoft.com/fwlink/p/?linkid=195494)
    
    2.  "Import an Exchange Certificate" at [http://go.microsoft.com/fwlink/p/?linkId=195496](http://go.microsoft.com/fwlink/p/?linkid=195496)
    
    <div>
    

    > [!NOTE]  
    > For the certificate <STRONG>Subject Name</STRONG>, you must enter the FQDN of the Exchange Server for communications to work.

    
    </div>

</div>

<div>

## To assign the certificate on Exchange Server 2007 (SP1)

1.  On the server running Exchange UM, open MMC.

2.  In the console tree, expand **Personal** and then click **Certificates**.

3.  In the details pane, verify that personal certificate is displayed.

4.  Double-click the certificate to read its details and verify that it is valid.
    
    <div>
    

    > [!NOTE]  
    > It may take a few minutes before the certificate displays as valid.

    
    </div>

5.  Restart the Microsoft Exchange Unified Messaging service.
    
    <div>
    

    > [!NOTE]  
    > The server running Exchange Server 2007 SP1 Unified Messaging automatically retrieves the correct certificate.

    
    </div>

6.  Open Event Viewer and look for Event ID 1112, which specifies what certificate the server running Exchange Server 2007 SP1 Unified Messaging has retrieved.

</div>

<div>

## To assign the certificate on Exchange Server 2010

1.  Log on to the server running Exchange UM with appropriate user rights. For details, see "Client Access Permissions" at [http://go.microsoft.com/fwlink/p/?linkId=195499](http://go.microsoft.com/fwlink/p/?linkid=195499).

2.  For the procedure to assign the certificate, see "Assign Services to a Certificate" at [http://go.microsoft.com/fwlink/p/?linkId=195497](http://go.microsoft.com/fwlink/p/?linkid=195497).

</div>

</div>

<span> </span>

</div>

</div>

</div>

