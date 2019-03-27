---
title: 'Lync Server 2013: Troubleshooting Lync Server 2013 Control Panel'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Troubleshooting Lync Server 2013 Control Panel
ms:assetid: 54e7ab57-34ce-4a07-bcc9-643379eb4eb7
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg195689(v=OCS.15)
ms:contentKeyID: 48184145
ms.date: 07/28/2016
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Troubleshooting Lync Server 2013 Control Panel

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2016-07-28_

This topic provides information and procedures that can help you troubleshoot access to Lync Server 2013 Control Panel.

<div>

## Internet Browser Requirements

Lync Server Control Panel requires that Microsoft Silverlight browser plug-in version 4.0.50524.0 or latest version is installed. If Silverlight is not installed or if an earlier version is installed, follow the instructions in the message to install the required version.

<div>


> [!NOTE]  
> Other software requirements for Lync Server Control Panel pertain to the operating system on which Lync Server Control Panel and all other Lync Server 2013 administrative tools can be installed. For details, see <A href="lync-server-2013-server-and-tools-operating-system-support.md">Server and tools operating system support in Lync Server 2013</A> in the Supportability documentation.



</div>

If your Internet browser blocks installation of Silverlight due to security considerations, add the Uniform Resource Locator (URL) that opens Lync Server Control Panel to the list of trusted sites. In Internet Explorer security settings, ensure that **Run ActiveX controls and plug-ins** is set to **Enabled**. For details, see [http://go.microsoft.com/fwlink/p/?linkId=214060](http://go.microsoft.com/fwlink/p/?linkid=214060). Furthermore, ensure that the browser is configured to use SSL 3.0.

If the Internet browser is configured to use a proxy server, verify that the browser is configured to bypass the proxy server for sites that are automatically detected as internal sites. Or, add the address to the browser's exception list in the proxy server configuration settings.

</div>

<div>

## DNS Record and Certificate Requirements for the Administrative Access URL

If you configured a simple URL to access Lync Server Control Panel, ensure that you also configured the static Domain Name System (DNS) host (A) resource record and certificate necessary to use that administrative access URL. If you change the base URL at any time, ensure that the change is reflected in the appropriate DNS record and certificate and that you run the *Enable-CsComputer* on each Director and Front End Server to register the change. For details, see the following topics in the Planning documentation:

  - [Planning for simple URLs in Lync Server 2013](lync-server-2013-planning-for-simple-urls.md)

  - [DNS requirements for simple URLs in Lync Server 2013](lync-server-2013-dns-requirements-for-simple-urls.md)

  - [Certificate requirements for internal servers in Lync Server 2013](lync-server-2013-certificate-requirements-for-internal-servers.md)

For step-by-step procedures to configure the administrative access URL, see [Edit or configure simple URLs in Lync Server 2013](lync-server-2013-edit-or-configure-simple-urls.md) in the Deployment documentation.

</div>

<div>

## Internet Information Services (IIS) Requirements

Lync Server Control Panel is one of the components of Lync Server 2013 that requires Internet Information Services (IIS). In particular, ensure that HTTP redirection and Windows authentication features are enabled, and that the World Wide Web Publishing Service (W3SVC) is running.

<div>

## World Wide Publishing Service (Windows Service) Dependency

When the World Wide Web Publishing Service is stopped, you cannot access Lync Server Control Panel. You can restart the service by using the Windows Services Microsoft Management Console (MMC).

**To start the World Wide Web Publishing Service**

1.  Log on to the computer where the World Wide Web Publishing Service is installed as part of Internet Information Services (IIS).

2.  Click **Start**, click **Administrative Tools**, and then click **Services**.

3.  Right-click **World Wide Web Publishing Service**, and then click **Start**.

</div>

<div>

## Application Pool Mode

Configure IIS so that the CsManagementAppPool application pool uses the Network Service account as its process model identity.

</div>

</div>

<div>

## User Rights and Permissions

You must sign in to Lync Server Control Panel either by using a domain account that is a member of the CsAdministrator group or by using an account to which you have delegated user rights and permissions. You cannot sign in to Lync Server Control Panel by using a local machine account. For details about delegating administrative tasks through role-based access control (RBAC), see [Planning for role-based access control in Lync Server 2013](lync-server-2013-planning-for-role-based-access-control.md) in the Planning documentation.

If you use a simple URL to access Lync Server Control Panel, ensure that web servers are added to the RTCUniversalServerAdmins and RTCUniversalUserAdmins groups.

</div>

<div>

## See Also


[Lync Server 2013 administrative tools](lync-server-2013-lync-server-administrative-tools.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

