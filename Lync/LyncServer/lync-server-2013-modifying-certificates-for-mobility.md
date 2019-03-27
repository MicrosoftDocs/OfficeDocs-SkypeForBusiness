---
title: 'Lync Server 2013: Modifying certificates for mobility'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Modifying certificates for mobility
ms:assetid: 4e9107af-20f4-4c2a-8c98-ca35b39a4e2d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Hh690015(v=OCS.15)
ms:contentKeyID: 48184120
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Modifying certificates for mobility in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-06-20_

To support secure connections between your Lync environment and your mobile clients, the Secure Socket Layer (SSL) certificates for your Director pool, Front End pool, and reverse proxy are going to need to be updated with some additional subject alternative name (SAN) entries. If you need to check out more details about the certificate requirements for mobility, see the Certificate Requirements section in [Technical requirements for mobility in Lync Server 2013](lync-server-2013-technical-requirements-for-mobility.md), but basically you’ll need to get new certificates from the Certificate Authority with the additional SAN entries included, and then add those certificates using this article’s steps.

Of course before you begin, it’s usually a good idea to know what subject alternative names your certificates already have. If you’re not sure what’s already been configured, there are a lot of ways to find out. While the option’s there to run the **Get-CsCertificate** and other PowerShell commands to view this information, (which we walk through below) by default that data will be truncated, so you may not get to see all the properties you need. In order to get a good look at the certificate and all its properties, you can go to the Microsoft Management Console (MMC) and load the Certificates snap-in (which we also walk through below), or you can just check in the Lync Server Deployment Wizard.

As noted above, the following steps will walk you through updating the certificates using the Lync Server Management Shell and the MMC. If you’re interested in using the Certificate Wizard in the Lync Server Deployment Wizard for this instead, you can check [Configure certificates for the Director in Lync Server 2013](lync-server-2013-configure-certificates-for-the-director.md) out for the Director or Director pool, if you configured one (you may not have). For the Front End Server or Front End pool, you’ll want to see [Configure certificates for servers in Lync Server 2013](lync-server-2013-configure-certificates-for-servers.md).

One last thing to keep in mind is that you may have a single Default certificate in your Lync Server 2013 environment, or you may have separate certificates for Default (which is everything but the web services), WebServicesExternal and WebServicesInternal. Whatever your configuration, these steps should help you out.

<div>

## To update certificates with new subject alternative names using the Lync Server Management Shell

1.  You need to log on to your Lync Server 2013 server using an account that has local administrator rights and permissions. Additionally, if you’re running the PowerShell **Request-CsCertificate** in Steps 12 and beyond, the account needs to have rights to the specified Certificate Authority (CA).

2.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

3.  Before you can assign an updated certificate, you’ll need to find out what certificates have been assigned to the server and for which type of use. At the command line, type:
    
        Get-CsCertificate

4.  Review the output from the previous step to see whether a single certificate has been assigned for multiple uses, or whether a different certificate is assigned for each use. Look in the Use parameter to find out how a certificate’s being used. Compare the Thumbprint parameter for the displayed certificates to see if the same certificate has multiple uses. Keep your eye on the Thumbprint parameter.

5.  Update the certificate. At the command line, type:
    
        Set-CsCertificate -Type <type of certificate as displayed in the Use parameter> -Thumbprint <unique identifier>
    
    For example, if the **Get-CsCertificate** cmdlet displayed a certificate with Use of Default, another with a Use of WebServicesInternal, and another with a Use of WebServicesExternal, and they all had the same Thumbprint value, at the command line, you should type:
    
        Set-CsCertificate -Type Default,WebServicesInternal,WebServicesExternal -Thumbprint <Certificate Thumbprint>
    
    **Important:**
    
    If a separate certificate is assigned for each use (so the Thumbprint value you checked above is different for each certificate), it’s vital that you **don’t** run the **Set-CsCertificate** cmdlet with multiple types, as in the example above. In this case, run the **Set-CsCertificate** cmdlet separately for each use. For example:
    
        Set-CsCertificate -Type Default -Thumbprint <Certificate Thumbprint>
        Set-CsCertificate -Type WebServicesInternal -Thumbprint <Certificate Thumbprint>
        Set-CsCertificate -Type WebServicesExternal -Thumbprint <Certificate Thumbprint>

6.  To view the certificate (or certificates), click **Start**, click **Run…**. Type MMC to open the Microsoft Management Console.

7.  From the MMC menu, select **File**, select **Add/Remove snap-in…**, select Certificates. Click **Add**. When prompted, select **Computer account**, then click **Next**.

8.  If this is the server where the certificate’s located, select **Local computer**. If the certificate’s located on another computer, you should select **Another computer**, and then you can either type in the fully qualified domain name of the computer, or click **Browse** in **Enter the object name to select**, and type the name of the computer. Click **Check Names**. When the name of the computer resolves, it’ll be underlined. Click **OK**, then click **Finish**. Click **OK** to commit the selection and close the **Add or Remove Snap-ins** dialog.

9.  To view the properties of the certificate, expand **Certificates**, expand **Personal**, and select **Certificates**. Select the certificate to view, right-click on the certificate and select **Open**.

10. In the **Certificate** view, select **Details**. From here, you can select the certificate subject name by selecting **Subject** and the assigned subject name and associated properties are displayed.

11. To view the assigned subject alternative names, select **Subject Alternative Name**. All assigned subject alternative names are displayed here. The subject alternative names found here are of type **DNS Name** by default. You should see the following members (all of which should be fully qualified domain names as represented in DNS host (A or, if IPv6 AAAA) records:
    
      - Pool name for this pool, or the single server name if this isn’t a pool
    
      - Server name that the certificate is assigned to
    
      - Simple URL records, typically meet and dialin
    
      - Web services internal and Web services external names (for example, webpool01.contoso.net, webpool01.contoso.com), based on choices made in Topology Builder and over-ridden web services selections.
    
      - If already assigned, the lyncdiscover.\<sipdomain\> and lyncdiscoverinternal.\<sipdomain\> records.
    
    The last item is what you’re most interested in – if there’s a lyncdiscover and lyncdiscoverinternal SAN entry.
    
    Repeat these steps if you have multiple certificates to check. Once you have this information, you can close the certificate view and the MMC.

12. If an Autodiscover Service subject alternative name is missing, and you are using a single Default certificate for the Default, WebServicesInternal and WebServiceExternal types, do the following:
    
      - At the Lync Server Management Shell command line prompt, type:
        
            Request-CsCertificate -New -Type Default,WebServicesInternal,WebServicesExternal -Ca dc\myca -AllSipDomain -verbose
        
        If you have many SIP domains, you can’t use the new AllSipDomain parameter. Instead, you need to use the DomainName parameter. When you use the DomainName parameter, you’ve got to define the FQDN for the lyncdiscoverinternal and lyncdiscover records. For example:
        
            Request-CsCertificate -New -Type Default,WebServicesInternal,WebServicesExternal -Ca dc\myca -DomainName "LyncdiscoverInternal.contoso.com, LyncdiscoverInternal.contoso.net" -verbose
    
      - To assign the certificate, type the following:
        
            Set-CsCertificate -Type Default,WebServicesInternal,WebServicesExternal -Thumbprint <Certificate Thumbprint>
        
        Where “Thumbprint” is the thumbprint displayed for the newly issued certificate.

13. For a missing internal Autodiscover SAN when using separate certificates for Default, WebServicesInternal, and WebServicesExternal, do the following:
    
      - At the Lync Server Management Shell command line prompt, type:
        
            Request-CsCertificate -New -Type WebServicesInternal -Ca dc\myca -AllSipDomain -verbose
        
        If you have many SIP domains, you can’t use the new AllSipDomain parameter. Instead, you need to use the DomainName parameter. When you use the DomainName parameter, you’ve got to use an appropriate prefix for the SIP domain FQDN. For example:
        
            Request-CsCertificate -New -Type WebServicesInternal -Ca dc\myca -DomainName "LyncdiscoverInternal.contoso.com, LyncdiscoverInternal.contoso.net" -verbose
    
      - For a missing external Autodiscover subject alternative name, at the command line, type:
        
            Request-CsCertificate -New -Type WebServicesExternal -Ca dc\myca -AllSipDomain -verbose
        
        If you have many SIP domains, you can’t use the new AllSipDomain parameter. Instead, you need to use the DomainName parameter. When you use the DomainName parameter, you’ve got to use an appropriate prefix for the SIP domain FQDN. For example:
        
            Request-CsCertificate -New -Type WebServicesExternal -Ca dc\myca -DomainName "Lyncdiscover.contoso.com, Lyncdiscover.contoso.net" -verbose
    
      - To assign the individual certificate types, type the following:
        
            Set-CsCertificate -Type Default -Thumbprint <Certificate Thumbprint>
            Set-CsCertificate -Type WebServicesInternal -Thumbprint <Certificate Thumbprint>
            Set-CsCertificate -Type WebServicesExternal -Thumbprint <Certificate Thumbprint>
        
        Where “Thumbprint” is the thumbprint displayed for the newly issued individual certificates.
    
    <div>
    

    > [!NOTE]  
    > Just to note, Steps 12 and 13 should be run only if the account running them has access to the Certificate Authority with appropriate permissions. If you are unable to log in with an account that’s got those permissions, or if you’re using a public or remote Certificate Authority for your certificates, you would need to request them through the Lync Server Deployment Wizard, which was touched on at the top of the article.

    
    </div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

