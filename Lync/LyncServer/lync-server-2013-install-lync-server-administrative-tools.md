---
title: 'Lync Server 2013: Install Lync Server administrative tools'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Install Lync Server administrative tools
ms:assetid: 842b85e4-2eeb-464f-b1c1-ceb8cc04f8d5
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398665(v=OCS.15)
ms:contentKeyID: 48184695
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Install Lync Server 2013 administrative tools

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

This topic describes how to install the administrative tools you need to use to deploy and manage Lync Server 2013. The administrative tools are installed by default on each server running Lync Server 2013. Additionally, you can install the administrative tools on other computers, such as dedicated administrative consoles. We strongly recommend that you install the administrative tools on a computer that is in the same domain or forest as the Lync Server 2013 deployment you are creating because by doing so you make sure that Active Directory Domain Services preparation steps are already complete, which enables you to use the administrative tools on that computer later to publish your topology.

Make sure that you review infrastructure, operating system, software, and administrator rights requirements before you install or use the Lync Server 2013 administrative tools. For details about infrastructure requirements, see [Administrative tools infrastructure requirements in Lync Server 2013](lync-server-2013-administrative-tools-infrastructure-requirements.md). For details about operating system and software requirements to install the Lync Server 2013 administrative tools, see [Server and tools operating system support in Lync Server 2013](lync-server-2013-server-and-tools-operating-system-support.md), [Additional software requirements for Lync Server 2013](lync-server-2013-additional-software-requirements.md), and [Additional server support and requirements in Lync Server 2013](lync-server-2013-additional-server-support-and-requirements.md). For details about the user rights and permissions required to install and use the tools, see [Administrator rights and permissions required for setup and administration of Lync Server 2013](lync-server-2013-administrator-rights-and-permissions-required-for-setup-and-administration.md).

<div>


> [!IMPORTANT]  
> If your organization requires that you locate Internet Information Services (IIS) and all Web Services on a drive other than the system drive, you can change the installation location path for the Lync Server files in the Setup dialog box. If you install the Setup files to this path, including OCSCore.msi, the rest of the Lync Server 2013 files will be deployed to this drive as well.



</div>

<div>

## To install the Lync Server 2013 administrative tools

1.  Log on as a local administrator (minimum requirement) to the computer where you want to install the administrative tools. If you are logged on as an a standard user on the Windows Vista or Windows 7 operating systems, and User Account Control (UAC) is enabled, you will be prompted for the local administrator or a domain equivalent user name and password.

2.  Locate the installation media on your computer, and then double-click \\Setup\\amd64\\Setup.exe.

3.  If you are prompted to install the Microsoft Visual C++ 2008 distributable, click **Yes**.

4.  On the **Microsoft Lync Server 2013 Installation Location** page, click **OK**. Change this path to another location or drive if you need to have the files installed to another location.
    
    <div>
    

    > [!IMPORTANT]  
    > If your organization requires that you locate Internet Information Services (IIS) and all Web Services on a drive other than the system drive, you can change the installation location path for the Lync Server 2013 files in the Setup dialog box. If you install the Setup files to this path, including OCSCore.msi, the rest of the Lync Server 2013 files will be deployed to this drive too.

    
    </div>

5.  On the **End User License Agreement** page, review the license terms, click **I accept**, and then click **OK**. This step is required before you can continue.

6.  On the **Microsoft Lync Server 2013 – Deployment Wizard** page, click **Install Administrator Tools**.

7.  When the installation successfully completes, click **Exit**.

</div>

<div>

## See Also


[Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md)  


[Lync Server 2013 administrative tools](lync-server-2013-lync-server-administrative-tools.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

