---
title: 'Lync Server 2013: Deploying Lync Windows Store app'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Deploying Lync Windows Store app
ms:assetid: 9e00aaf4-15f9-4356-9ed7-5a58a2bfa043
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ822971(v=OCS.15)
ms:contentKeyID: 50117635
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Deploying Lync Windows Store app in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-12-03_

Before making Lync Windows Store app available to users, make sure that your deployment meets the [Lync Windows Store app requirements for Lync Server 2013](lync-server-2013-lync-windows-store-app-requirements.md). For details about configuring Lync Server 2013 to support Lync Windows Store app, see the NextHop Blog article, "Lync Server Autodiscover and the Lync Windows Store App," at [http://go.microsoft.com/fwlink/?LinkId=271966](http://go.microsoft.com/fwlink/?linkid=271966). After your server environment is configured correctly, you can direct users to download the Lync app from the Windows Store by searching for "Lync."

<div>

## Enabling Multi-Factor Authentication for Lync Windows Store app

Cumulative Updates for Lync Server 2013: June 2013 adds support for multi-factor authentication for Lync Windows Store app clients. In addition to user name and password, you can require additional authentication methods, such as smart cards or PINs, to authenticate external users when they sign in to Lync meetings. To enable multi-factor authentication, you deploy Active Directory Federation Service (AD FS) federation server and enable passive authentication in Lync Server 2013. After AD FS is configured, external users who attempt to join Lync meetings are presented with an AD FS multi-factor authentication webpage that contains the user name and password challenge along with any additional authentication methods that you have configured.

<div class=" ">


> [!IMPORTANT]  
> The following are important considerations if you plan to configure AD FS for multi-factor authentication for Lync Windows Store app: 
> <UL>
> <LI>
> <P>Lync Server 2013 with Cumulative Updates for Lync Server 2013: June 2013 is required at a minimum. Lync 2013 desktop clients do not require Cumulative Updates for Lync Server 2013: June 2013, so it might appear that passive authentication is working because Lync 2013 clients are able to authenticate. However, the authentication process for Lync Windows Store app clients will fail to complete and no notification or error message will display.</P>
> <LI>
> <P>The server must be configured so that passive authentication is the only authentication type offered.</P>
> <LI>
> <P>If you use hardware load balancers, enable cookie persistence on the load balancers so that all requests from the Lync Windows Store app client are handled by the same Front End Server.</P>
> <LI>
> <P>When you establish a relying party trust between Lync Server and AD FS servers, assign a token life that is long enough to span the maximum length of your Lync meetings. Typically, a token life of 240 minutes is sufficient.</P></LI></UL>



</div>

**To Configure Multi-Factor Authentication**

1.  Install an AD FS federation server role. For details, see the Active Directory Federation Services 2.0 Deployment Guide at <http://go.microsoft.com/fwlink/p/?linkid=267511>.

2.  Create certificates for AD FS. For more information, see the "Federation server certificates" section of the Plan for and deploy AD FS for use with single sign-on topic at [http://go.microsoft.com/fwlink/p/?LinkId=285376](http://go.microsoft.com/fwlink/p/?linkid=285376).

3.  From the Windows PowerShell command-line interface, run the following command:
    
        add-pssnapin Microsoft.Adfs.powershell

4.  Establish a partnership by running the following command:
    
        Add-ADFSRelyingPartyTrust -Name ContosoApp -MetadataURL https://lyncpool.contoso.com/passiveauth/federationmetadata/2007-06/federationmetadata.xml

5.  Set the following relying party rules:
    
       ```
        $IssuanceAuthorizationRules = '@RuleTemplate = "AllowAllAuthzRule" => issue(Type = "http://schemas.contoso.com/authorization/claims/permit", Value = "true");'$IssuanceTransformRules = '@RuleTemplate = "PassThroughClaims" @RuleName = "Sid" c:[Type == "http://schemas.contoso.com/ws/2008/06/identity/claims/primarysid"]=> issue(claim = c);'
       ```
    
       ```
        Set-ADFSRelyingPartyTrust -TargetName ContosoApp -IssuanceAuthorizationRules $IssuanceAuthorizationRules -IssuanceTransformRules $IssuanceTransformRules
       ```
    
       ```
        Set-CsWebServiceConfiguration -UseWsFedPassiveAuth $true -WsFedPassiveMetadataUri https://dc.contoso.com/federationmetadata/2007-06/federationmetadata.xml
       ```

</div>

<div>

## Known Issues that Can Prevent Sign-in

<div>

## The time and date are not set accurately on the device running Lync Windows Store app

The time setting on the device must be synchronized with the time setting on the server. This is particularly important for devices such as Microsoft Surface, and other devices running Windows RT that are not joined to a domain. To set the time on these devices automatically from a time server, run the following command from an elevated command prompt on the device:

    w32tm /resync

</div>

<div>

## Lync Windows Store app cannot access the Lync server or services

Lync Windows Store app may not be able to access the Lync server or services through network adapters, such as 4G LTE USB modems, that do not register with Windows 8 as physical devices. Lync Windows Store app may have this issue even when the desktop apps and browsers are able to access other servers and web sites.

</div>

<div>

## Lync Windows Store app cannot sign in with Lync Server 2010 and Office Communications Server 2007 R2 Edge Server

If your topology consists of Lync Server 2010 with Office Communications Server 2007 R2 Edge Server, you will need to run the updated version of Topology Builder available in the cumulative update for Lync Server 2010: July 2013. Earlier versions of Topology Builder do not create the required mapping to Office Communications Server 2007 Edge Server, so Lync Windows Store app clients are unable to sign in. The following steps are required:

1.  Install the cumulative update for Lync Server 2010: July 2013 on Lync Server 2010 pools and Lync Server 2010 Directors.

2.  Update the Lync AutoDiscover configuration to indicate that the external SIP entry point is the Edge server address by doing the following:
    
    1.  Open Lync Server Management Shell.
    
    2.  Run the following command:
        
            Set-CsAutodiscoverConfiguration -ExternalSipClientAccessFqdn <FQDN of server used for external client access> -ExternalSipClientAccessPort 443

</div>

<div>

## Lync Windows Store App cannot sign in due to a certificate name validation failure

A sign-in issue can occur for Office 365 users who are not running the latest version of Lync Windows Store app. This issue generally occurs when using multiple domains (for example, when the SIP URI is **userA@domainZ.com** but the Edge Server is **sip.domainX.com**). To fix the issue, users should install the latest version of Lync Windows Store app, which also requires Windows 8.1.

</div>

</div>

<div>

## Use Lync Windows Store app logs to troubleshoot issues

You can use the logs generated on the device to troubleshoot issues. The logs are stored in the following folder:

%LocalAppData%\\Packages\\Microsoft.LyncMX\_8wekyb3d8bbwe\\LocalState\\Tracing

Before you get the logs from a user, make sure that logging is turned on, and then ask the user to save the logs so that all the information stored in memory is also saved to files on the hard drive.

**To turn on logging**

1.  Open Lync Windows Store app on the device.

2.  Swipe from the right side of the screen. If you’re using a mouse, point to the upper-right corner of the screen and then move the mouse pointer down the screen.

3.  Select **Settings**, select **Options**, and then set **Diagnostic Logs** to **On**.

4.  If **Diagnostic Logs** was off previously, you must restart Lync. To restart Lync, do one of the following:
    
      - Restart the device.
    
      - End the Lync task and launch the app again. To end the task, open the Windows Task Manager, select **Lync**, and then tap **End task**. If Lync is not listed, tap **More details** and look for Lync under **Background processes**.

**To save the logs**

1.  Open Lync Windows Store app on the device.

2.  Try signing in.

3.  Swipe from the right side of the screen. If you’re using a mouse, point to the upper-right corner of the screen and then move the mouse pointer down the screen.

4.  Select **Settings**, select **About**, and then select **Save logs**.

</div>

</div>

<span> </span>

</div>

</div>

</div>

