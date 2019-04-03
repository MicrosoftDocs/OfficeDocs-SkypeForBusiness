---
title: 'Lync Server 2013: Integrating Lync Server and Outlook Web App 2013'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Integrating Lync Server 2013 and Outlook Web App 2013
ms:assetid: 513d4cc7-aa87-4f68-b99d-d58b63bdf242
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ688055(v=OCS.15)
ms:contentKeyID: 49733649
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Integrating Microsoft Lync Server 2013 and Microsoft Outlook Web App 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-03_

In addition to integrating with Microsoft Outlook 2013, Microsoft Lync Server 2013 can be fully integrated with Microsoft Outlook Web App 2013; among other things, this adds instant messaging and presence to Outlook Web App, and enables your unified contact list to be shared between Outlook Web App and Microsoft Lync 2013. In order to integrate Lync Server 2013 and Outlook Web App, you must first verify that the Unified Communications Managed API 4.0 Runtime has been installed in your Microsoft Exchange Server 2013 backend server. You can do this by looking for the existence of the following registry value:

HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\MSExchange OWA\\InstantMessaging\\ImplementationDLLPath

The ImplementationDLLPath should point to the folder location for the file Microsoft.Rtc.Internal.Ucweb.dll. If it does not, or if the registry value does not exist, then you should download and install the UCMA Runtime setup program from the Microsoft Download Center at <http://www.microsoft.com/en-us/download/details.aspx?id=34992>. Information on how to install the UCMA Runtime can be found on that same web page.

**Backward Compatibility**

Lync Server 2013 can be integrated with the Microsoft Exchange Server 2010 versions of both unified messaging and Outlook Web App. For more information, see the article Deploying On-Premises Exchange UM to Provide Lync Server 2010 Voice Mail at [http://technet.microsoft.com/en-us/library/gg398768.aspx](lync-server-2013-deploying-on-premises-exchange-um-to-provide-lync-server-2013-voice-mail.md). If you integrate with Exchange 2010 you will not have Lync Server specific features such as the unified contact store and Lync-to-Exchange archiving.

Microsoft Lync 2013 can also be used in conjunction with Exchange 2010 and Outlook 2010. Once again, however, new functionality such as the unified contact store and high-resolution photos will not be available to Lync 2013 users. These new capabilities require both Lync Server 2013 and Exchange 2013.

**Creating a Trusted Application Pool for Outlook Web App**

If you have installed the Microsoft Exchange Unified Messaging Call Router service and the Microsoft Exchange Unified Messaging service on the same computer then there is no need to create a trusted application pool for Outlook Web App. (This assumes that the server in question is hosting a SipName UM dial plan.) If you are using a single computer to host both of these services then you can skip to the section of this document titled **Enabling Instant Messaging on Outlook Web App**.

Lync Server 2013 can autodiscover any Exchange servers that host a SipName UM dial plan; these servers are automatically added to the Lync Server Known Servers List. There is no need to create a trusted application pool and add these servers to the Known Servers List. In fact, doing so will cause Outlook Web App integration to stop working.

<div>


> [!NOTE]  
> This is due to the fact that the Lync Server topology will now have two entries for the same computer: the autodiscovered entry, and the manually-added entry. To fix the problem, and to get Outlook Web App working again, use Windows PowerShell to remove the trusted pool and trusted application entries for the server. See the help topics for the <A href="https://docs.microsoft.com/powershell/module/skype/Remove-CsTrustedApplicationPool">Remove-CsTrustedApplicationPool</A> and <A href="https://docs.microsoft.com/powershell/module/skype/Remove-CsTrustedApplication">Remove-CsTrustedApplication</A> cmdlets for more information.



</div>

If these two services are running on separate computers then, after you have verified that the Unified Communications Managed API 4.0 Runtime has been installed, you must create a Lync Server trusted application pool and a trusted application associated with Outlook Web App; that will add the server to the Known Servers List. To do that, first run a command similar to this from within the Lync Server Management Shell:

    New-CsTrustedApplicationPool -Identity atl-owa-001.litwareinc.com -Registrar atl-cs-001.litwareinc.com -Site Redmond -RequiresReplication $False

In the preceding command, atl-owa-001.litwareinc.com is the fully qualified domain name of the Outlook Web App pool; this must be the same name that appears in the Subject Name and Subject Alternative Name (SAN) fields of the certificate that provides access to Outlook Web App. Likewise, atl-cs-001.litwareinc.com is the fully qualified domain name of the Lync Server 2013 pool that will host the new trusted application pool. Note, too that the specified site, Redmond, represents the SiteID of the Lync Server site. The SiteID is not necessarily the same as the site's DisplayName; you can retrieve SiteIDs for your Lync Server sites by running the following command from the Lync Server Management Shell:

    Get-CsSite | Select-Object DisplayName, SiteID

After creating the trusted application pool, use a command similar to the following to configure an application Identity and a port for Outlook Web App:

    New-CsTrustedApplication -ApplicationId OutlookWebApp -TrustedApplicationPoolFqdn atl-owa-001.litwareinc.com  -Port 5199

In the preceding command, the ApplicationID is simply a friendly identifier used to distinguish trusted applications. The ApplicationID can be any text string that does not include blank spaces or other prohibited characters. (To ensure that you create a valid identifier, it is recommended that you use only letters and numbers when specifying an ApplicationId.) The value assigned to the Port parameter is also left to the administrator's discretion: this can be any available network port.

After creating the trusted application you must run the following command to enable the changes to your Lync Server topology:

    Enable-CsTopology

Note that you must also add your Exchange client access and mailbox server to all of your SIP Uri dial plans. In turn, this will configure the servers as trusted SIP peers with the ExUmRouting topology for Lync Server.

**Enabling Instant Messaging on Outlook Web App**

With Lync Server correctly configured you can then begin to configure Outlook Web App. The first step in that process is to enable instant messaging on all your Outlook Web App virtual directories on your front end servers. (There is no need to enable instant messaging for the virtual directories on your backend servers. In fact, it is recommended that you do not enable instant messaging on your backend servers.) Instant messaging can be enabled on the client access servers by running the following command from within the Exchange Management Shell:

    Get-OwaVirtualDirectory | Set-OwaVirtualDirectory -InstantMessagingEnabled $True -InstantMessagingType OCS

<div>


> [!NOTE]  
> By default, instant messaging is enabled when you install Outlook Web App; that is, the InstantMessagingEnabled property is set to True. However, you must still run the preceding command in order to set the instant messaging type to OCS. By default, InstantMessagingType is set to None.



</div>

Next you must add the following two lines to Outlook Web App Web.config file (this file is typically located in the folder C:\\Program Files\\Microsoft\\Exchange Server\\V15\\ClientAccess\\Owa). These two lines should be added under the \<AppSettings\> node in the Web.config file, and this procedure should be carried out only on the backend servers where Outlook Web App has been installed:

    <add key="IMCertificateThumbprint" value="EA5A332496CC05DA69B75B66111C0F78A110D22d"/>
    <add key="IMServerName" value="atl-cs-001.litwareinc.com"/>

In the preceding example, the value for IMCertificateThumbprint must be the thumbprint for the Exchange 2013 certificate that is installed on your backend servers. You can retrieve that information by running the following command from the Exchange Management Shell:

    Get-ExchangeCertificate

Note, too that the value assigned to IMServerName is the fully qualified domain name of the Lync Server pool where you created the trusted application pool for Outlook Web App.

The certificate that you use for Outlook Web App must be a certificate that is trusted by Lync Server. One way to ensure that the certificate will be trusted by both Lync Server and Exchange is to use your internal certificate authority to create a certificate on the mailbox server, making sure that the server FQDN is used for the subject name and that this FQDN appears in the certificate alternate name field. After the certificate has been created it can then be imported to your backend servers. The net result is that the same certificate is used for two purposes: 1) communication between Exchange unified messaging and Lync Server; and, 2) the integration between Outlook Web App and Lync Server.

After you have updated the Web.config file you should then run the following command on the Exchange backend server in order to recycle the Outlook Web App pool:

    C:\Windows\System32\Inetsrv\Appcmd.exe recycle apppool /apppool.name:"MSExchangeOWAAppPool"

If the recycle operation succeeds you will see the following message in the Exchange Management Shell:

    "MSExchangeOWAAppPool" successfully recycled

**Configuring Outlook Web App Mailbox Policies**

At this point you can use the following command to configure instant messaging on the appropriate Outlook Web App mailbox policy (or policies). For example, this command, run on one of your mailbox servers, enables instant messaging on the Default policy:

    Set-OwaMailboxPolicy -Identity "Default" -InstantMessagingEnabled $True -InstantMessagingType "OCS"

And this command enables instant messaging for all your Outlook Web App mailbox policies:

    Get-OwaMailboxPolicy | Set-OwaMailboxPolicy -InstantMessagingEnabled $True -InstantMessagingType "OCS"

After the mailbox policy has been enabled then all users managed by that policy will have full integration between Lync Server and Outlook Web App, provided that:

  - The user has a mailbox on Exchange 2013.

  - The user has been enabled for Lync Server 2013.

  - The user has a valid SIP proxy address.

**Disabling Instant Messaging in Outlook Web App**

As noted previously, instant messaging is enabled by default in Outlook Web App. That means that, if you do not integrate Outlook Web App with Lync Server, users will see blank presence icons and an error message each time they log on to Outlook Web App. To prevent this problem, use the following Exchange Management Shell command to disable instant messaging in Outlook web App:

    Get-OwaVirtualDirectory | Set-OwaVirtualDirectory -InstantMessagingEnabled $False

**Verifying Integration With Outlook Web App**

To verify that instant messaging and presence have been integrated with Outlook Web App, sign on to Outlook Web App 2013. In the upper right-hand corner of the screen, you will see your Exchange display name. If there is a presence icon next to your name (for example, a green icon indicating that your current status is Available) that indicates that you have successfully integrated Lync Server and Outlook Web App.

After the initial sign-on to Outlook Web App, check to see if an event with the Event ID 112 (and the source MSExchange OWA) has been written to the event log on the mailbox server. This event indicates that the Instant Messaging Endpoint Manager was successfully initialized. If instant messaging does not appear to be working then, on the mailbox server, look for log files in the folder C:\\Program Files\\Microsoft\\Exchange server\\V15\\Logging\\OWA\\InstantMessaging. If either the Logging or the InstantMessaging folders do not exist that indicates that integration has failed. In that case, you can use SIPStack tracing on Lync Server (All Levels and All Flags) to try and determine why integration failed.

</div>

<span> </span>

</div>

</div>

</div>

