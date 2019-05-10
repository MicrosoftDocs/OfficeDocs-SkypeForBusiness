---
title: 'Lync Server 2013: Preparing for and installing Best Practices Analyzer'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Preparing for and installing Best Practices Analyzer
ms:assetid: 550613dd-dc08-482e-9980-a3fe187cd162
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg591347(v=OCS.15)
ms:contentKeyID: 48184149
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Preparing for and installing Best Practices Analyzer in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-11-07_

You must be logged on as a member of the Administrators group to perform the tasks that are described in this topic.

<div>

## System Requirements for Best Practices Analyzer Installation

To run Lync Server 2013, Best Practices Analyzer to scan your environment, the computer must be running a 64-bit edition of one of the following operating systems:

  - Windows Server 2008 R2 with Service Pack 1 (SP1) Standard operating system

  - Windows Server 2008 R2 with SP1 Enterprise operating system

  - Windows Server 2008 R2 with SP1 Datacenter operating system

  - Windows Server 2012 Datacenter operating system

  - Windows Server 2012 Standard operating system

  - Windows Server 2012 Enterprise operating system

  - Windows Server 2012 R2 Datacenter operating system

  - Windows Server 2012 R2 Standard operating system

  - Windows Server 2012 R2 Enterprise operating system

  - Windows 8 operating system

  - Windows 7 operating system

The computer must also be running the following:

  - Microsoft .NET Framework 4.5. For Lync Server 2013, you must manually install the 64-bit edition of Microsoft .NET Framework 4.5 on the server prior to installing Lync Server 2013.

  - Lync Server 2013, Core Components.

  - WMI Backward Compatibility Package. For details, see [Install WMI Backward Compatibility package](install-wmi-backward-compatibility-package.md) in the Migration documentation.

  - Windows PowerShell 3.0. For details, see [Installing Windows PowerShell 3.0 for Lync Server 2013](lync-server-2013-installing-windows-powershell-3-0.md) in the Deployment documentation.

You can install Best Practices Analyzer on computers with a supported operating system that are not running Lync Server 2013, Core Components or WMI Backward Compatibility Package, but you can use Best Practices Analyzer on those computers only to view reports, not to run scans.

</div>

<div>

## Choosing a Computer for Installation

We recommend that you install Lync Server 2013, Best Practices Analyzer on a computer that is dedicated to Lync Server 2013 management. You can install the tool on a server running Lync Server 2013 or an administrative computer running Lync Server 2013 administrative tools. If you install the tool on a server that is running Lync Server, we recommend that you use the tool to scan only that server.

</div>

<div>

## Installing Best Practices Analyzer

You can download the Best Practices Analyzer for Lync Server 2013 at [http://go.microsoft.com/fwlink/p/?linkId=266539](http://go.microsoft.com/fwlink/p/?linkid=266539).

To install Best Practices Analyzer, start the Microsoft Installer file RtcBPA.msi on the computer where you want to install the tool, and then follow the instructions on the screen. The default location for installing the program files is \<system drive\>\\Program Files\\Lync Server 2013\\BPA.

</div>

</div>

<span> </span>

</div>

</div>

</div>

