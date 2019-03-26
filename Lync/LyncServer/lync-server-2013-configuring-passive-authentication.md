---
title: 'Lync Server 2013: Configuring passive authentication'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configuring Lync Server passive authentication
ms:assetid: 9a904b8d-9fce-4abf-be73-5c8e48cfb53a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn308569(v=OCS.15)
ms:contentKeyID: 54973690
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring Lync Server 2013 passive authentication

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-11_

The following section describes how to configure Lync Server 2013 with Cumulative Updates: July 2013 to support passive authentication. Once enabled, Lync users who are enabled for two-factor authentication will be required to use a physical or virtual smart card and a valid PIN to sign in using the Lync 2013 with Cumulative Updates: July 2013 client.

<div class="">


> [!NOTE]  
> It is strongly recommended that customers enable passive authentication for Registrar and Web Services at the service level. If passive authentication is enabled for Registrar and Web Services at the global level, it will likely result in organization-wide authentication failures for users who are not signing in with the Lync 2013 with Cumulative Updates: July 2013 client desktop client.



</div>

<div>

## Web Service Configuration

The following steps describe how to create a custom web service configuration for Directors, Enterprise Pools, and Standard Edition servers that will be enabled for passive authentication.

**To create a custom web service configuration**

1.  Log in to your Lync Server 2013 with Cumulative Updates: July 2013 Front End server using a Lync administrator account.

2.  Launch the Lync Server 2013 Management Shell.

3.  From the Lync Server Management Shell command-line, create a new Web Service configuration for each Director, Enterprise Pool, and Standard Edition server that will be enabled for passive authentication by running the following command:
    
        New-CsWebServiceConfiguration -Identity "Service:WebServer:LyncPool01.contoso.com" -UseWsFedPassiveAuth $true -WsFedPassiveMetadataUri https://dc.contoso.com/federationmetadata/2007-06/federationmetadata.xml
    
    <div class="">
    

    > [!WARNING]  
    > The value for the WsFedPassiveMetadataUri FQDN is the Federation Service Name of your AD FS 2.0 server. The Federation Service Name value can be found in the AD FS 2.0 Management Console by right-clicking on <STRONG>Service</STRONG> from the navigation pane and then selecting <STRONG>Edit Federation Service Properties</STRONG>.

    
    </div>

4.  Verify that the UseWsFedPassiveAuth and WsFedPassiveMetadataUri values were set correctly by running the following command:
    
        Get-CsWebServiceConfiguration -identity "Service:WebServer:LyncPool01.contoso.com" | format-list UseWsFedPassiveAuth, WsFedPassiveMetadataUri

5.  For clients, Passive Authentication is the least preferred authentication method for webticket authentication. For all Directors, Enterprise Pools, and Standard Edition servers that will be enabled for passive authentication, all other authentication types must be disabled in Lync Web Services by running the following command:
    
        Set-CsWebServiceConfiguration -Identity "Service:WebServer:LyncPool01.contoso.com" -UseCertificateAuth $false -UsePinAuth $false -UseWindowsAuth NONE

6.  Verify that all other authentication types have been successfully disabled by running the following command:
    
        Get-CsWebServiceConfiguration -Identity "Service:WebServer:LyncPool01.contoso.com" | format-list UseCertificateAuth, UsePinAuth, UseWindowsAuth

</div>

<div>

## Proxy Configuration

When certificate authentication is disabled for Lync Web Services, the Lync client will use a less preferred authentication type, such as Kerberos or NTLM, to authenticate to the Registrar service. Certificate authentication is still needed to allow the Lync client to retrieve a webticket, however, Kerberos and NTLM must be disabled for the Registrar service.

The following steps describe how to create a custom proxy configuration for Edge Pools, Enterprise Pools, and Standard Edition servers that will be enabled for passive authentication.

**To create a custom proxy configuration**

1.  From the Lync Server Management Shell command-line, create a new proxy configuration for each Lync Server 2013 with Cumulative Updates: July 2013 Edge Pool, Enterprise Pool, and Standard Edition server that will be enabled for passive authentication by running the following commands:
    
       ```
        New-CsProxyConfiguration -Identity "Service:EdgeServer:EdgePool01.contoso.com" 
        -UseKerberosForClientToProxyAuth $False -UseNtlmForClientToProxyAuth $False
       ```
    
       ```
        New-CsProxyConfiguration -Identity "Service:Registrar:LyncPool01.contoso.com" 
        -UseKerberosForClientToProxyAuth $False -UseNtlmForClientToProxyAuth $False
       ```

2.  Verify that all other proxy authentication types have been successfully disabled by running the following command:
    
        Get-CsProxyConfiguration -Identity "Service:Registrar:LyncPool01.contoso.com"
         | format-list UseKerberosForClientToProxyAuth, UseNtlmForClientToProxyAuth, UseCertifcateForClientToProxyAuth

</div>

</div>

<span> </span>

</div>

</div>

</div>

