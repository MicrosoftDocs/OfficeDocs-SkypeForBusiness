---
title: 'Lync Server 2013: Set up certificates for the external edge interface'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Set up certificates for the external edge interface
ms:assetid: 5d78182c-88d8-4483-95ad-74b17f2d5fac
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398409(v=OCS.15)
ms:contentKeyID: 48184287
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set up certificates for the external edge interface for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-08_

<div>


> [!IMPORTANT]  
> When you run the Certificate Wizard, ensure that you are logged in using an account that is a member of a group that has been assigned the appropriate permissions for the type of certificate template you will use. By default, a Lync Server certificate request will use the Web Server certificate template. If you use an account that is a member of the RTCUniversalServerAdmins group to request a certificate using this template, verify that the group has been assigned the Enroll permissions required to use that template.



</div>

Each Edge Server requires a public certificate on the interface between the perimeter network and the Internet, and the certificate’s subject alternative name must contain the external names of the Access Edge service and Web Conferencing Edge service fully qualified domain names (FQDNs).

For details about this and other certificate requirements, see [Certificate requirements for external user access in Lync Server 2013](lync-server-2013-certificate-requirements-for-external-user-access.md).

For a list of public certification authorities (CAs) that provide certificates that comply with specific requirements for unified communications certificates and have partnered with Microsoft to ensure they work with the Lync Server 2013 Certificate Wizard, see Microsoft Knowledge Base article 929395, "Unified Communications Certificate Partners for Exchange Server and for Communications Server," at [http://go.microsoft.com/fwlink/p/?linkId=202834](http://go.microsoft.com/fwlink/p/?linkid=202834).

<div>

## Configuring Certificates on the External Interfaces

To set up a certificate on the external edge interface at a site, use the procedures in this section to do the following:

  - Create the certificate request for the external interface of the Edge Server.

  - Submit the request to your public CA.

  - Import the certificate for the external interface of each Edge Server.

  - Assign the certificate for the external interface of each Edge Server.

  - If your deployment includes multiple Edge Servers, export the certificate along with its private key, and then copy it to the other Edge Servers. Then, for each Edge Server, import it and assign it as previously described. Repeat this procedure for each Edge Server.

You can request public certificates directly from a public certification authority (CA) (such as from the website of a public CA). The procedures in this section use the Certificate Wizard for most certificate tasks. If you chose to request a certificate directly from a public CA, then you will need to modify each procedure as appropriate to request, transport, and import the certificate and also to import the certificate chain.

When you request a certificate from an External CA, the credentials provided must have rights to request a certificate from that CA. Each CA has a security policy that defines which credentials (that is, specific user and group names) are allowed to request, issue, manage, or read certificates.

If you decide to use the Certificates Microsoft Management Console (MMC) to import the certificate chain and certificate, you must import them to the certificate store for the computer. If you import them to the user or service certificate store, the certificate will not be available for assignment in the Lync Server 2013 Certificate Wizard.

<div>

## To create the certificate request for the external interface of the Edge Server

1.  On the Edge Server, in the Deployment Wizard, next to **Step 3: Request, Install, or Assign Certificates**, click **Run again**.
    
    <div>
    

    > [!NOTE]  
    > If your organization wants to support public instant messaging (IM) connectivity with AOL, you cannot use the Lync Server Deployment Wizard to request the certificate. Instead, perform the steps in the “To create a certificate request for the external interface of the Edge Server to support public IM connectivity with AOL” procedure later in this topic.<BR>If you have multiple Edge Servers in one location in a pool, you can run the Lync Server 2013 Certificate Wizard on any one of the Edge Servers.

    
    </div>

2.  On the **Available Certificate Tasks** page, click **Create a new certificate request**.

3.  On the **Certificate Request** page, click **External Edge Certificate**.

4.  On the **Delayed or Immediate Request** page, select the **Prepare the request now, but send it later** check box.

5.  On the **Certificate Request File** page, type the full path and file name of the file to which the request is to be saved (for example, c:\\cert\_exernal\_edge.cer).

6.  On the **Specify Alternate Certificate Template** page, to use a template other than the default WebServer template, select the **Use alternative certificate template for the selected certification authority** check box.

7.  On the **Name and Security Settings** page, do the following:
    
      - In **Friendly name**, type a display name for the certificate.
    
      - In **Bit length**, specify the bit length (typically, the default of **2048**).
    
      - Verify that the **Mark certificate private key as exportable** check box is selected.

8.  On the **Organization Information** page, type the name for the organization and the organizational unit (for example, a division or department).

9.  On the **Geographical Information** page, specify the location information.

10. On the **Subject Name/Subject Alternate Names** page, the information to be automatically populated by the wizard is displayed. If additional subject alternative names are needed, you specify them in the next two steps.

11. On the **SIP Domain Setting on Subject Alternate Names (SANs)** page, select the domain check box to add a sip.\<sipdomain\> entry to the subject alternative names list.

12. On the **Configure Additional Subject Alternate Names** page, specify any additional subject alternative names that are required.

13. On the **Request Summary** page, review the certificate information to be used to generate the request.

14. After the commands finish running, do the following:
    
      - To view the log for the certificate request, click **View Log**.
    
      - To complete the certificate request, click **Next**.

15. On the **Certificate Request File** page, do the following:
    
      - To view the generated certificate signing request (CSR) file, click **View**.
    
      - To close the wizard, click **Finish**.

16. Copy the output file to a location where you can submit it to the public CA.

</div>

<div>

## To create a certificate request for the external interface of the Edge Server to support public IM connectivity with AOL

1.  When the required template is available to the CA, use the following Windows PowerShell cmdlet from at the Edge Server to request the certificate:
    
        Request-CsCertificate -New -Type AccessEdgeExternal  -Output C:\ <certfilename.txt or certfilename.csr>  -ClientEku $true -Template <template name>
    
    The default certificate name of the template provided in Lync Server 2013 is Web Server. Only specify the \<template name\> if you need to use a template that is different from the default template.
    
    <div>
    

    > [!NOTE]  
    > If your organization wants to support public IM connectivity with AOL, you must use Windows PowerShell instead of the Certificate Wizard to request the certificate to be assigned to the external edge for the Access Edge service. This is because the Lync Server 2013 Web Server template that the Certificate Wizard uses to request a certificate does not support client EKU configuration. Before using Windows PowerShell to create the certificate, the CA administrator must create and deploy a new template that supports client EKU.

    
    </div>

</div>

<div>

## To submit a request to a public certification authority

1.  Open the output file.

2.  Copy and paste the contents of the Certificate Signing Request (CSR).

3.  If prompted, specify the following:
    
      - **Microsoft** as the server platform.
    
      - **IIS** as the version.
    
      - **Web Server** as the usage type.
    
      - **PKCS7** as the response format.

4.  When the public CA has verified your information, you will receive an email message containing text required for your certificate.

5.  Copy the text from the email message and save the contents in a text file (.txt) on your local computer.

</div>

<div>

## To import the certificate for the external interface of the Edge Server

1.  Log on as a member of the Administrators group to the same Edge Server on which you created the certificate request.

2.  In the Deployment Wizard, on the **Deploy Edge Server** page, next to **Step 3: Request, Install, or Assign Certificates**, click **Run again**.

3.  On the **Available Certificate Tasks** page, click **Import a certificate from a .p7b, pfx or .cer file**.

4.  On the **Import Certificate** page, click **Browse** to locate and select the certificate that you requested for the external interface of the Edge Server (or, you can type the full path and file name). If the certificate contains a private key, select **Certificate file contains certificate’s private key** and type the password for the private key. Click **Next**.

5.  On **Import Certificate Summary** page, review the summary and then click **Next**.

6.  On **Executing Commands**, review the results of the import, click **View Log** for more information as needed, and then click **Finish** to complete the certificate import.

7.  If you are configuring an Edge Server pool, export the certificate with its private key as outlined in the “To export the certificate with the private key for Edge Servers in a pool” procedure later in this topic. Copy the exported certificate file to the other Edge Servers, and import it into the computer store on each Edge Server.

</div>

<div>

## To export the certificate with the private key for Edge Servers in a pool

1.  Log on as a member of the Administrators group to the same Edge Server on which you imported the certificate.

2.  Click **Start**, click **Run**, and type **MMC**.

3.  In the Microsoft Management Console (MMC) console, click **File**, and then click **Add/Remove Snap-in**.

4.  In **Add or Remove Snap-ins**, click **Certificates**, and then click **Add**.

5.  In the **Certificates** dialog box, select **Computer account**, click **Next**, select **Local computer: (the computer this console is running on)** in **Select Computer**, click **Finish** and then click **OK** to complete configuration of the MMC console.

6.  Double-click **Certificates (Local Computer)** to expand the certificate stores, double-click **Personal**, and then double-click **Certificates**.
    
    <div>
    

    > [!IMPORTANT]  
    > If there are no certificates in the Certificates Personal store for the local computer, there is no private key associated with the certificate that was imported. Review the request and import steps. If the problem persists, contact your certification authority administrator or provider.

    
    </div>

7.  In the **Certificates Personal store for the local computer**, right-click the certificate that you are exporting, click **All Tasks**, and then click **Export**.

8.  In the Certificate Export Wizard, click **Next**, select **Yes, export the private key**, and then click **Next**.
    
    <div>
    

    > [!NOTE]  
    > If the selection <STRONG>Yes, export the private key</STRONG> is not available, the private key associated with this certificate was not marked for export. You will need to request the certificate again, ensuring that the certificate is marked to allow for the export of the private key before you can continue with the export. Contact your certification authority administrator or provider.

    
    </div>

9.  On the Export File Formats dialog, select **Personal Information Exchange – PKCS\#12 (.PFX)** and then select the following:
    
      - Include all certificates in the certification path if possible
    
      - Export all extended properties
        
        <div>
        

        > [!WARNING]  
        > When exporting the certificate from an Edge server, do not select <STRONG>Delete the private key if the export is successful</STRONG>. Selecting this option will require that you import the certificate and the private key to this Edge server.

        
        </div>

10. Click **Next**.

11. Type a password for the private key, type the password again to confirm, and then click **Next**.

12. Type a path and file name for the exported certificate, using a file extension of .pfx. The path must either be accessible to all other Edge servers in the pool or available to transport by means of removable media - for example, a USB flash drive. Click **Next**.

13. Review the summary in **Completing the Certificate Export Wizard**, and then click **Finish**.

14. In the successful export dialog box, click **OK**.

15. Import the exported certificate file to the other Edge servers following the steps outlined in the “To import the certificate for the external interface of the Edge Server” procedure earlier in this topic.

</div>

<div>

## To assign the certificate for the external interface of the Edge Server

1.  On each Edge Server, in the Deployment Wizard, next to **Step 3: Request, Install, or Assign Certificates**, click **Run again**.

2.  On the **Available Certificate Tasks** page, click **Assign an existing certificate**.

3.  On the **Certificate Assignment** page, click **External Edge Certificate** and select the **Advanced Certificate Usages** check box.

4.  On the **Advanced Certificate Usages** page, select all check boxes to assign the certificate for all usages.

5.  On the **Certificate Store** page, select the public certificate that you requested and imported for the external interface of the Edge Server.
    
    <div>
    

    > [!NOTE]  
    > If the certificate you requested and imported is not in the list, one of the trouble shooting methods is to verify that subject name and subject alternative names of the certificate meet all requirements for the certificate and, if you manually imported the certificate and certificate chain instead of using the preceding procedures, that the certificate is in the correct certificate store (the computer certificate store, not the user or service certificate store).

    
    </div>

6.  On the **Certificate Assignment Summary** page, review your settings, and then click **Next** to assign the certificates.

7.  On the wizard completion page, click **Finish**.

8.  After using this procedure to assign the edge certificate, open the Certificate snap-in on each server, expand **Certificates (Local computer)**, expand **Personal**, click **Certificates**, and then verify in the details pane that the certificate is listed.

9.  If your deployment includes multiple Edge Servers, repeat this procedure for each Edge Server.

</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

