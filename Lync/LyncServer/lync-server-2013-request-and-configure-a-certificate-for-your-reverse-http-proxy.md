---
title: 'Request and configure a certificate for your reverse HTTP proxy'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Request and configure a certificate for your reverse HTTP proxy
ms:assetid: 4b70991e-5f10-40a3-b069-0b227c3a3a0a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg429704(v=OCS.15)
ms:contentKeyID: 48184085
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Request and configure a certificate for your reverse HTTP proxy in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-02-14_

You need to install the root certification authority (CA) certificate on the server running Microsoft Forefront Threat Management Gateway 2010 or IIS ARR for the CA infrastructure that issued the server certificates to the internal servers running Microsoft Lync Server 2013.

You also must install a public web server certificate on your reverse proxy server. This certificate’s subject alternative names should contain the published external fully qualified domain names (FQDNs) of each pool that is home to users enabled for remote access, and the external FQDNs of all Directors or Director pools that will be used within that Edge infrastructure. The subject alternative name must also contain the meeting simple URL, the dial-in simple URL, and, if you are deploying mobile applications and plan to use automatic discovery, the external Autodiscover Service URL as shown in the following table.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>Value</th>
<th>Example</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Subject name</p></td>
<td><p>Pool FQDN</p></td>
<td><p>webext.contoso.com</p></td>
</tr>
<tr class="even">
<td><p>Subject alternative name</p></td>
<td><p>Pool FQDN</p></td>
<td><p>webext.contoso.com</p>



> [!IMPORTANT]
> The subject name must also be present in the subject alternative name.

</td>
</tr>
<tr class="odd">
<td><p>Subject alternative name</p></td>
<td><p>Optional Director Web Services (if Director is deployed)</p></td>
<td><p>webdirext.contoso.com</p></td>
</tr>
<tr class="even">
<td><p>Subject alternative name</p></td>
<td><p>Meeting simple URL</p>



> [!NOTE]
> All meeting simple URLs must be in the subject alternative name. Each SIP domain must have at least one active meeting simple URL.

</td>
<td><p>meet.contoso.com</p></td>
</tr>
<tr class="odd">
<td><p>Subject alternative name</p></td>
<td><p>Dial-in simple URL</p></td>
<td><p>dialin.contoso.com</p></td>
</tr>
<tr class="even">
<td><p>Subject alternative name</p></td>
<td><p>Office Web Apps Server</p></td>
<td><p>officewebapps01.contoso.com</p></td>
</tr>
<tr class="odd">
<td><p>Subject alternative name</p></td>
<td><p>External Autodiscover Service URL</p></td>
<td><p>lyncdiscover.contoso.com</p>



> [!NOTE]
> If you are also using Microsoft Exchange Server you will also need to configure reverse proxy rules for the Exchange autodiscover and web services URLs.

</td>
</tr>
</tbody>
</table>


<div>


> [!NOTE]
> If your internal deployment consists of more than one Standard Edition server or Front End pool, you must configure web publishing rules for each external web farm FQDN and you will either need a certificate and web listener for each, or you must obtain a certificate whose subject alternative name contains the names used by all of the pools, assign it to a web listener, and share it among multiple web publishing rules.



</div>

<div>

## Create a Certificate Request

You create a certificate request on the reverse proxy. You create a request on another computer, but you must export the signed certificate with the private key and import it onto the reverse proxy once you have received it from the public certification authority.

<div>


> [!NOTE]
> A certificate request or a certificate signing request (CSR) is a request to a trusted public certification authority (CA) to validate and sign the requesting computer’s public key. When a certificate is generated, a public key and a private key are created. Only the public key is shared and signed. As the name implies, the public key is made available to any public request. The public key is for use by clients, servers and other requesters that need to exchange information securely and validate a computer’s identity. The private key is kept secured and is used only by the computer that created the key pair to decrypt messages encrypted with its public key. The private key can be used for other purposes. For reverse proxy purposes, data encipherment is the primary use. Secondarily, the certificate authentication at the certificate key level is another use, and is limited only to validation that a requester has the computer’s public key, or that the computer that you have a public key for is actually the computer that it claims to be.



</div>

<div>


> [!TIP]
> If you plan your Edge Server certificates and your reverse proxy certificates at the same time, you should notice that there is a great deal of similarity between the two certificate requirements. When you configure and request your Edge Server certificate, combine the Edge Server and the reverse proxy subject alternative names. You can use the same certificate for your reverse proxy if you export the certificate and the private key and copy the exported file to the reverse proxy and then import the certificate/key pair and assign it as needed in the upcoming procedures. Refer to the certificate requirements for the Edge Server&nbsp;<A href="lync-server-2013-plan-for-edge-server-certificates.md">Plan for Edge Server certificates in Lync Server 2013</A> and the reverse proxy <A href="lync-server-2013-certificate-summary-reverse-proxy.md">Certificate summary - Reverse proxy in Lync Server 2013</A>. Make sure that you create the certificate with an exportable private key. Creating the certificate and certificate request with an exportable private key is required for pooled Edge Servers, so this is a normal practice and the Certificate Wizard in the Lync Server Deployment Wizard for the Edge Server will allow you to set the <STRONG>Make private key exportable</STRONG> flag. Once you receive the certificate request back from the public certification authority, you will export the certificate and the private key. See the section “To export the certificate with the private key for Edge Servers in a pool” in the topic <A href="lync-server-2013-set-up-certificates-for-the-external-edge-interface.md">Set up certificates for the external edge interface for Lync Server 2013</A> for details on how to create and export your certificate with a private key. The extension of the certificate should be of type <STRONG>.pfx</STRONG>.



</div>

To generate a certificate signing request on the computer where the certificate and private key will be assigned, you do the following:

**Creating a certificate signing request**

1.  Open the Microsoft Management Console (MMC) and add the Certificates snap-in and select **Computers**, then expand **Personal**. For details on how to create a certificates console in the Microsoft Management Console (MMC), see [http://go.microsoft.com/fwlink/?LinkId=282616](http://go.microsoft.com/fwlink/?linkid=282616).

2.  Right-click **Certificates**, click **All Tasks**, click **Advanced Operations**, click **Create Custom Request**.

3.  On the **Certificate Enrollment** page, click **Next**.

4.  On the **Select Certificate Enrollment Policy** page under **Custom Request**, select **Proceed without enrollment policy**. Click **Next**.

5.  On the **Custom Request** page, for **Template** select **(No template) Legacy key**. Unless otherwise directed by your certificate provider, leave **Suppress default extensions** unchecked and the **Request format** selection on **PKCS \#10**. Click **Next**.

6.  On the **Certificate Information** page, click **Details**, then click **Properties**.

7.  On the **Certificate Properties** page on the **General** tab in the **Friendly Name** field, type a name for this certificate. Optionally, type a description in the **Description** field. The Friendly Name and description are typically used by the Administrator to identify what the certificate purpose is, such as **Reverse Proxy Listener for Lync Server**.

8.  Select the **Subject** tab. Under **Subject name** for the **Type**, select **Common name** for the Subject name type. For the **Value**, type the subject name that you will use for the reverse proxy, and then click **Add**. In the example provided in the table in this topic, the subject name is webext.contoso.com and would be typed into the Value field for the Subject name.

9.  On the **Subject** tab under **Alternative name**, select **DNS** from the drop down for **Type**. For each defined subject alternative name that you require on the certificate, type the fully qualified domain name, then click **Add**. For example, in the table there are three subject alternative names, meet.contoso.com, dialin.contoso.com, and lyncdiscover.contoso.com. In the **Value** field, type meet.contoso.com, then click **Add**. Repeat for each subject alternative names that you need to define.

10. On the **Certificate Properties** page, click the **Extensions** tab. On this page, you will define the cryptographic key purposes in **Key usage** and the extended key usage in **Extended Key Usage (application policies)**.

11. Click the **Key usage** arrow to show the **Available options**. Under Available options, click **Digital signature**, then click **Add**. Click **Key encipherment**, then click **Add**. If the checkbox for **Make these key usages critical** is unchecked, select the checkbox.

12. Click the **Extended Key Usage (application policies)** arrow to show the **Available options**. Under Available options, click **Server Authentication**, then click **Add**. Click **Client Authentication**, then click **Add**. If the check box for **Make the Extended Key Usages critical** is checked, unselect the checkbox. Contrary to the Key usage checkbox (which must be checked) you must be sure that the Extended Key Usage checkbox is not checked.

13. On the **Certificate Properties** page, click the **Private Key** tab. Click the **Key options** arrow. For **Key size**, select **2048** from the drop down. If you are generating this key pair and CSR on a computer other than the reverse proxy that this certificate is intended for, select **Make private key exportable**.
    
    <div>
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398321.security(OCS.15).gif" title="security" alt="security" />Security Note:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Selecting <strong>Make a private key exportable</strong> is generally advised when you have more than one reverse proxy in a farm because you will copy the certificate and the private key to each machine in the farm. If you do allow for an exportable private key, you must take extra care with the certificate and the computer that it is generated on. The private key, if compromised, will render the certificate useless as well as potentially expose the computer or computers to external access and other security vulnerabilities.</td>
    </tr>
    </tbody>
    </table>
    
    </div>

14. On the **Private Key** tab, click the **Key type** arrow. Select the **Exchange** option.

15. Click **OK** to save the **Certificate Properties** that you have set.

16. On the **Certificate Enrollment** page, click **Next**.

17. On the **Where do you want to save the offline request?** page, you are prompted for a **File Name** and a **File Format** for saving the certificate signing request.

18. In the **File Name** entry field, type a path and filename for the request, or click **Browse** to select a location for the file and type the filename for the request.

19. For **File format**, click either **Base 64** or **Binary**. Select **Base 64** unless you are instructed otherwise by the vendor for your certificates.

20. Locate the request file that you saved in the previous step. Submit to your public certification authority.
    
    <div>
    

    > [!IMPORTANT]
    > Microsoft has identified Public CAs that meets the requirements for Unified Communications purposes. A list is maintained in the following knowledge base article. <A href="http://go.microsoft.com/fwlink/?linkid=282625">http://go.microsoft.com/fwlink/?LinkId=282625</A>

    
    </div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

