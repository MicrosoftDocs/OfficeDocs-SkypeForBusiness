---
title: 'Lync Server 2013: Deploying Lync clients'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Deploying Lync clients
ms:assetid: 3d10abf2-d484-4fa0-8f10-4a5f9dfba4f5
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204827(v=OCS.15)
ms:contentKeyID: 48183925
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Deploying Lync clients in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-03_

Lync 2013 introduces a different approach to client deployment. In a departure from previous releases, Lync 2013 no longer has its own installer. Instead, Lync is included with the Office 2013 setup program. To deploy Lync 2013 to your users, you can use Office 2013 installation methods and customization tools.

  - **Office 2013 Windows Installer** is a Windows Installer-based installation package that consists of multiple MSI files. A language-neutral core MSI package is combined with one or more language-specific packages to make a complete product. Setup assembles the individual packages and performs customization and maintenance tasks during and after installation of Office on users' computers. The topics in this section describe how to use and customize the Office 2013 Windows Installer to deploy Lync 2013.

  - **Office 2013 Click-to-Run** is an installation program that streams Office setup files to the user from the Microsoft Office 365 portal. Administrators can customize installation by using the Office Deployment Tool for Click-to-Run. Because Office 2013 Click-to-Run is primarily used in the Microsoft Office 365 environment, this installation method is not described in detail in this section. Detailed information about using and customizing Click-to-Run installation is available in the Office 2013 Resource Kit documentation. Administrators can also download the Office 2013 Click-to-Run program and language source files to an on-premises location, which is useful when you want to minimize the demand on the network or prevent users from installing software from the Internet because of corporate security requirements.

The topics in this section focus on how to deploy clients by using the Office 2013 MSI-based installer. Your primary reference should be the Office 2013 Resource Kit documentation, which describes in detail how to prepare your infrastructure, customize setup, and deploy Office 2013. However, you should use the Office documentation in conjunction with topics in this section, which point out deployment considerations that are specific to Lync 2013.

<div>


> [!NOTE]  
> <UL>
> <LI>
> <P>The Online Meeting Add-in for Lync 2013, which supports meeting management from within the Outlook messaging and collaboration client, installs automatically with Lync 2013.</P>
> <LI>
> <P>The Office 2013 setup program does not uninstall previous versions of Lync or Office Communicator. The Lync 2013 client installs side-by-side with other Lync or Office Communicator clients</P></LI></UL>



</div>

<div>

## In This Section

  - [Customizing client installation in Lync Server 2013](lync-server-2013-customizing-client-installation.md)

  - [Customizing Lync behavior and the user interface in Lync Server 2013](lync-server-2013-customizing-lync-behavior-and-the-user-interface.md)

  - [Customizing the Online Meeting Add-in in Lync Server 2013](lync-server-2013-customizing-the-online-meeting-add-in.md)

  - [Configuring the meeting join page in Lync Server 2013](lync-server-2013-configuring-the-meeting-join-page.md)

  - [Configuring supported client versions in Lync Server 2013](lync-server-2013-configuring-supported-client-versions.md)

  - [Configuring enhanced presence privacy mode in Lync Server 2013](lync-server-2013-configuring-enhanced-presence-privacy-mode.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

