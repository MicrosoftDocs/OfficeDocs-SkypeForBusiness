---
title: 'Lync Server 2013: Set up certificates for the internal edge interface'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Set up certificates for the internal edge interface
ms:assetid: a1963cc9-87c5-4935-86c0-6bedc6afd0ac
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412750(v=OCS.15)
ms:contentKeyID: 48184949
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set up certificates for the internal edge interface in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-11-07_

<div>


> [!IMPORTANT]  
> When you run the Certificate Wizard, ensure that you are logged in using an account that is a member of a group that has been assigned the appropriate permissions for the type of certificate template you will use. By default, a Lync Server 2013 certificate request will use the Web Server certificate template. If you use an account that is a member of the RTCUniversalServerAdmins group to request a certificate using this template, verify that the group has been assigned the Enroll permissions required to use that template.



</div>

A single certificate is required on the internal interface of each Edge Server. Certificates for the internal interface can be issued by an internal enterprise certification authority (CA) or a public CA. If your organization has an internal CA deployed you can save on the expense of using public certificates by using the internal CA to issue the certificate for the internal interface. You can use an internal Windows Server 2008 CA or Windows Server 2008 R2 CA to create these certificates.

For details about this and other certificate requirements, see [Certificate requirements for external user access in Lync Server 2013](lync-server-2013-certificate-requirements-for-external-user-access.md).

To set up certificates on the internal edge interface at a site, use the procedures in this section to do the following:

1.  Download the CA certification chain for the internal interface to each Edge Server.

2.  Import the CA certification chain for the internal interface, on each Edge Server.

3.  Create the certificate request for the internal interface, on one Edge Server, called the first Edge Server.

4.  Import the certificate for the internal interface on the first Edge Server.

5.  Import the certificate on the other Edge Servers at this site (or deployed behind this load balancer).

6.  Assign the certificate for the internal interface of every Edge Server.

If you have more than one site with Edge Servers (that is, a multiple-site edge topology), or separate sets of Edge Servers deployed behind different load balancers, you need to follow these steps for each site that has Edge Servers, and for each set of Edge Servers deployed behind a different load balancer.

<div>


> [!NOTE]  
> The steps for procedures in this section are based on using a Windows Server&nbsp;2008 CA, Windows Server&nbsp;2008&nbsp;R2 CA, Windows Server 2012 CA, or Windows Server 2012 R2 CA to create a certificate for each Edge Server. For step-by-step guidance for any other CA, consult the documentation for that CA. By default, all authenticated users have the appropriate user rights to request certificates.<BR>The procedures in this section are based on creating certificate requests on the Edge Server as part of the Edge Server deployment process. It is possible to create certificate requests using the Front End Server. You can do this to complete the certificate request early in the planning and deployment process, before you start deployment of the Edge Servers. To do this, you must ensure that the certificate you request is defined with an exportable private key.<BR>The procedures in this section describe using a .cer and a .p7b file for the certificate. If you use a different type of file, modify these procedures as appropriate.



</div>

<div>

## To download the CA certification chain for the internal interface using certsrv Web site

1.  Log on to an Lync Server 2013 server in the internal network (that is, not the Edge Server) as a member of the **Administrators** group.

2.  Run the following command at a command prompt by clicking **Start**, clicking **Run**, and then typing the following:
    
        https://<name of your Issuing CA Server>/certsrv
    
    For example:
    
        https://ca01.contoso.net/certsrv
    
    <div>
    

    > [!NOTE]  
    > If you are using a Windows Server 2008 or Windows Server 2008 R2 enterprise CA, you must use https, not http.

    
    </div>

3.  On the issuing CA’s certsrv web page, under **Select a task**, click **Download a CA certificate, certificate chain, or CRL**.

4.  Under **Download a CA Certificate, Certificate Chain, or CRL**, click **Download CA certificate chain**.

5.  In the **File Download** dialog box, click **Save**.

6.  Save the .p7b file to the hard disk drive on the server, and then copy it to a folder on each Edge Server.
    
    <div>
    

    > [!NOTE]  
    > The .p7b file contains all of the certificates that are in the certification path. To view the certification path, open the server certificate and click the certification path.

    
    </div>

</div>

<div>

## To export the CA certification chain for the internal interface using MMC

1.  You can export the CA root certificate from any domain joined machine using the Microsoft Management Console (MMC). Click **Start**, click **Run**, and then type **MMC**.

2.  In the MMC console, click **File**, click **Add/Remove**.

3.  From the **Add or Remove Snap-ins** dialog list, select **Certificates**, then click **Add**. When prompted, select **Computer Account**. On the **Select Computer** dialog, select **Local Computer**. Click **Finish**. Click **OK**.

4.  Expand **Certificates (Local Computer)**. Expand **Trusted Root Certification Authorities**, select **Certificates**.

5.  Click the root certificate issued by your CA. Right click the certificate, select **All Tasks**, select **Export**. The **Certificate Export Wizard** will open.

6.  In the **Certificate Export Wizard**, click **Next**.

7.  On the **Export File Format** dialog, select a format to export to. We recommend the **Cryptographic Message Syntax Standard – PKCS \#7 Certificates (.P7B)**. If you select the **Cryptographic Message Syntax Standard – PKCS \#7 Certificates (.P7B)**, select the **Include all certificates in the certification path if possible** checkbox to export the certificate chain, including the root CA certificate and any Intermediate CA certificates. Click **Next**.

8.  On the **File to Export** dialog in the file name entry, type a path and file name (default extension is .p7b) for the exported certificate. Optionally, click **Browse**, locate a directory to place the exported certificate in and provide a name for the exported certificate. Click **Save**. Click **Next**.

9.  Review the summary of actions, and click **Finish** to complete the export of the certificate. Click **OK** to confirm the successful export.

</div>

<div>

## To import the CA certification chain for the internal interface

1.  On each Edge Server, open the Microsoft Management Console (MMC) by clicking **Start**, clicking **Run**, typing **mmc** in the **Open** box, and then clicking **OK**.

2.  On the **File** menu, click **Add/Remove Snap-in**, and then click **Add**.

3.  In the **Add Standalone Snap-ins** box, click **Certificates**, and then click **Add**.

4.  In the **Certificate snap-in** dialog box, click **Computer account**, and then click **Next**.

5.  In the **Select Computer** dialog box, ensure that the **Local computer: (the computer this console is running on)** check box is selected, and then click **Finish**.

6.  Click **Close**, and then click **OK**.

7.  In the console tree, expand **Certificates (Local Computer)**, right-click **Trusted Root Certification Authorities**, point to **All Tasks**, and then click **Import**.

8.  In the wizard, in **File to Import**, specify the file name of the certificate (that is, the name of that you specified when you downloaded the CA certification chain for the internal interface in the previous procedure).

9.  Repeat this procedure on each Edge Server.

</div>

<div>

## To create the certificate request for the internal interface

1.  On one of the Edge Servers, start the Deployment Wizard, and next to **Step 3: Request, Install, or Assign Certificates**, click **Run**.
    
    <div>
    

    > [!NOTE]  
    > If you have multiple Edge Servers in one location in a pool, you can run the Certificate Wizard on any one of the Edge Servers.<BR>After you run Step 3 the first time, the button changes to <STRONG>Run again</STRONG>, and a green check mark that indicates successful completion of the task is not displayed until all require certificates have been requested, installed, and assigned.

    
    </div>

2.  On the **Available Certificate Tasks** page, click **Create a new certificate request**.

3.  On the **Certificate Request** page, click **Next**.

4.  On the **Delayed or Immediate Requests** page, click **Prepare the request now, but send it later**.

5.  On the **Certificate Request File** page, type the full path and file name to which the request is to be saved (for example, **c:\\cert\_internal\_edge.cer**).

6.  On the **Specify Alternate Certificate Template** page, to use a template other than the default WebServer template, select the **Use alternative certificate template for the selected Certificate Authority** check box.

7.  On the **Name and Security Settings** page, do the following:
    
      - In **Friendly name**, type a display name for the certificate (for example, Internal Edge).
    
      - In **Bit length**, specify the bit length (typically, the default of **2048**).
        
        <div>
        

        > [!NOTE]  
        > Higher bit lengths offer more security, but they have a negative impact on speed.

        
        </div>
    
      - If the certificate needs to be exportable, select the **Mark certificate private key as exportable** check box.

8.  On the **Organization Information** page, type the name for the organization and the organizational unit (OU) (for example, a division or department).

9.  On the **Geographical Information** page, specify the location information.

10. On the **Subject Name/Subject Alternate Names** page, the information to be automatically populated by the wizard is displayed.

11. On the **Configure Additional Subject Alternate Names** page, specify any additional subject alternative names that are required.

12. On the **Request Summary** page, review the certificate information that is going to be used to generate the request.

13. After the commands complete, do the following:
    
      - To view the log for the certificate request, click **View Log**.
    
      - To complete the certificate request, click **Next**.

14. On the **Certificate Request File** page, do the following:
    
      - To view the generated certificate signing request (CSR) file, click **View**.
    
      - To close the wizard, click **Finish**.

15. Submit this file to your CA (by email or other method supported by your organization for your enterprise CA) and, when you receive the response file, copy the new certificate to this computer so that it is available for import.

</div>

<div>

## To import the certificate for the internal interface

1.  Log on to the Edge Server on which you created the certificate request as a member of the local Administrators group.

2.  In the Deployment Wizard, next to **Step 3: Request, Install, or Assign Certificates**, click **Run again**.
    
    After you run Step 3 the first time, the button changes to **Run again**, but a green check mark (indicating successful completion of the task) is not displayed until all require certificates have been requested, installed, and assigned.

3.  On the **Available Certificate Tasks** page, click **Import a certificate from a .P7b, .pfx or .cer file**.

4.  On the **Import Certificate** page, type the full path and file name of the certificate that you requested and received for the internal interface of this Edge Server (or, click **Browse** to locate and select the file).

5.  If you are importing certificates for other members of the pool a certificate containing a private key, select the **Certificate file contains certifcate’s private key** check box and specify the password.

</div>

<div>

## To export the certificate with the private key for Edge Servers in a pool

1.  Log on as a member of the Administrators group to the same Edge Server on which you imported the certificate.

2.  Click **Start**, click **Run**, and type **MMC**.

3.  From the MMC console, click **File**, click **Add/Remove Snap-in**.

4.  From Add or Remove Snap-ins page, click **Certificates**, click **Add**.

5.  In the Certificates snap-in dialog, select **Computer account**. Click **Next**. In Select Computer, select **Local computer: (the computer this console is running on)**. Click **Finish**. Click **OK** to complete configuration of the MMC console.

6.  Double-click **Certificates (Local Computer)** to expand the certificate stores. Double-click **Personal**, then double-click **Certificates**.
    
    <div>
    

    > [!IMPORTANT]  
    > If there are no certificates in the Certificates Personal store for the local computer, there is no private key associated with the certificate that was imported. Review the request and import steps. If the problem persists, contact your certification authority administrator or provider.

    
    </div>

7.  In the Certificates Personal store for the local computer, right-click the certificate that you are exporting. Click **All Tasks**, click **Export**.

8.  In the Certificate Export Wizard, click **Next**. Select **Yes, export the private key**. Click **Next**.
    
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
    
    Click **Next** to continue.

10. If you want to assign password to protect the private key, type a password for the private key. Re-enter the password to confirm. Click **Next**.

11. Type a path and file name for the exported certificate, using a file extension of .pfx. The path must either be accessible to all other Edge servers in the pool or available to transport by means of removable media - for example, a USB flash drive. Click **Next**.

12. Review the summary on the Completing the Certificate Export Wizard dialog. Click **Finish**.

13. Click **OK** in the successful export dialog.

14. Import the exported certificate file to the other Edge servers following the steps outlined in the [Set up certificates for the external edge interface for Lync Server 2013](lync-server-2013-set-up-certificates-for-the-external-edge-interface.md) procedures.

</div>

<div>

## To assign the internal certificate on the Edge Servers

1.  On each Edge Server, in the Deployment Wizard, next to **Step 3: Request, Install, or Assign Certificates**, click **Run again**.

2.  On the **Available Certificate Tasks** page, click **Assign an existing certificate**.

3.  On the **Certificate Assignment** page, select **Edge Internal** in the list.

4.  On the **Certificate Store** page, select the certificate that you imported for the internal edge (from the previous procedure).

5.  On the **Certificate Assignment Summary** page, review your settings, and then click **Next** to assign the certificates.

6.  On the wizard completion page, click **Finish**.

7.  After using this procedure to assign the internal edge certificate, open the Certificate snap-in on each server, expand **Certificates (Local computer)**, expand **Personal**, click **Certificates**, and then verify in the details pane that the internal edge certificate is listed.

8.  If your deployment includes multiple Edge Servers, repeat this procedure for each Edge Server.

</div>

</div>

<span> </span>

</div>

</div>

</div>

