---
title: 'Lync Server 2013: Additional server support and requirements'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Additional server support and requirements
ms:assetid: 7622986b-abd6-4f45-8b5b-d5e2368521e8
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398577(v=OCS.15)
ms:contentKeyID: 48184535
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Additional server support and requirements in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-12-09_

In addition to the software support described in the other sections of this Supportability documentation, Lync Server 2013 has the following support limitations:

  - Lync Server 2013 supports Domain Name System (DNS) and hardware load balancing for specific server roles. It also supports application load balancing for Mediation Servers, where appropriate. For details about when to use each, see the Planning documentation.

  - Lync Server 2013 uses the Distribution List Expansion Protocol (DLX) to expand distribution lists. This protocol also specifies the web service method that is used to get the membership of a distribution list. Microsoft Exchange Server supports dynamic groups that do not have members statically assigned to them. Instead, they store queries that are evaluated when the group is expanded. DLX does not support dynamic distribution lists. This DLX limitation applies to all versions of Lync Server.

  - The Enable User Wizard does not support automatic conversion of non-English characters to a SIP-compliant URI, so you must modify the SIP address manually.

  - For servers running antivirus software, refer to [Antivirus scanning exclusions for Lync Server 2013](lync-server-2013-antivirus-scanning-exclusions.md) for suggested virus exclusions and other security related recommendations.

  - If you use IPsec, we recommend disabling IPsec over the port ranges used for audio and video traffic. For details, see [IPsec exceptions in Lync Server 2013](lync-server-2013-ipsec-exceptions.md) in the Planning documentation.

  - If your organization uses a Quality of Service (QoS) infrastructure, the media subsystem is designed to work within this existing infrastructure. For details about implementing QoS, see [Managing Quality of Service (QoS) in Lync Server 2013](lync-server-2013-managing-quality-of-service-qos.md) in the Operations documentation.

  - Use of the operating system firewall is supported. Lync Server 2013 manages the firewall exceptions for the operating system firewall, except for Microsoft SQL Server database software. For details about SQL Server firewall requirements, see the SQL Server documentation.

  - The external interfaces used to implement support for external user access must be on a separate subnet, *not* on the same network as the internal interfaces.

  - The XMPP capability of Lync Server 2013 is tested and supported by Microsoft for instant messaging federation with Google Talk. For any other XMPP systems contact the third-party vendor to verify that they support federation with Lync Server 2013, and for any deployment or troubleshooting recommendations.

  - With the release of Lync Server 2013 Cumulative Updates: July 2013, Lync Server 2013 now supports two-factor authentication. For more information, see [Two-factor authentication in Lync Server 2013](lync-server-2013-planning-for-and-deploying-two-factor-authentication.md).

  - Most internal servers require a certificate type defined as **Open Authentication** (OAuth). You are required to request and assign an OAuth certificate during the **Request, Install and Assign Certificates** phase of the Lync Server Deployment Wizard. The minimum size for an OAuth certificate key is 1024 bits. A warning may be displayed if you request a certificate with a key length less than 2048 bits in length. To avoid potential problems in the event that a key length of 2048 is enforced instead of warned, it is strongly recommended to always use a key length of 2048 for OAuth certificates.

  - Lync Server 2013 and Microsoft Exchange Server 2010 Service Pack 1 (SP1) operate with support for Federal Information Processing Standard (FIPS) 140-2 algorithms if the Windows Server 2008 R2 operating systems are configured to use the FIPS 140-2 algorithms for system cryptography. To implement FIPS support, you must configure each server running Lync Server 2013 to support it. For details about FIPS-compliant algorithms and how to implement FIPS support, see Microsoft Knowledge Base article 811833, "System cryptography: Use FIPS compliant algorithms for encryption, hashing, and signing security setting in Windows XP and in later versions of Windows at [http://go.microsoft.com/fwlink/p/?linkid=3052\&kbid=811833](http://go.microsoft.com/fwlink/p/?linkid=3052%26kbid=811833). For details about FIPS 140-2 support and limitations in Exchange 2010, see "Exchange 2010 SP1 and Support for FIPS Compliant Algorithms" at [http://go.microsoft.com/fwlink/p/?linkId=205335](http://go.microsoft.com/fwlink/p/?linkid=205335).

Lync Server 2013 requires the installation of other software on specific components prior to or during deployment. This includes software that is available with the operating system, downloadable software, and software that is automatically installed during installation of Lync Server 2013. Following is a list of additional software that can be required:

  - Windows Update

  - Windows Identity Foundation

  - Microsoft .NET 4.5 Framework

  - Microsoft Visual C++ 2012 Redistributable
    
    <div>
    

    > [!NOTE]  
    > Microsoft Visual C++ 2012 Redistributable is automatically installed when you install Lync Server 2013. You should not install and use any other version.

    
    </div>

  - URL Rewrite Module version 2.0 Redistributable

  - Windows Media Format Runtime

  - Windows PowerShell version 3.0

  - Microsoft Silverlight 4 browser plug-in (Silverlight 4.0.50524.0 or the latest version for Lync Server Control Panel)

  - Active Directory Domain Services tools

Some of these software requirements only apply to specific server roles or components. For details about these software requirements, see [Additional software requirements for Lync Server 2013](lync-server-2013-additional-software-requirements.md) in the Planning documentation.

</div>

<span> </span>

</div>

</div>

</div>

