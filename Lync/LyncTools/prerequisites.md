---
title: Prerequisites
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Prerequisites
ms:assetid: 48016bea-be3b-4ba5-8df8-d8ad4d9243d9
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ945592(v=OCS.15)
ms:contentKeyID: 51541417
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Prerequisites

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-19_

There are various hardware, software, and system configuration requirements that you’ll need to run the Lync Server 2013 Stress and Performance Tool.

<div>

## Client Hardware Requirements

To run the Lync Server 2013 Stress and Performance Tool on your Lync Server 2013 deployment, for every 4,500 users whose load you want to simulate, you’ll need at least one dedicated computer that meets the following minimum hardware requirements:

  - 1 gigabit network adapter

  - 8-GB ram

  - 2 dual-core central processing units (CPUs)

</div>

<div>

## Client Software Requirements

To run the Lync Server 2013 Stress and Performance Tool on your Lync Server 2013 deployment, the supported operating systems are:

  - Windows Server 2012 operating system

  - Windows Server 2008 operating system (64-bit edition)

Your client computer must meet the following software requirements:

  - You must have the [Microsoft .NET Framework 4.5](http://go.microsoft.com/fwlink/?linkid=143212) runtime installed.

  - On Windows Server 2008/Windows Server 2012, the Desktop Experience feature must be enabled.

  - You must have the [Microsoft Visual C++ 2012 redistributable package](http://go.microsoft.com/fwlink/?linkid=143216) (x64) installed.

  - A fully configured Lync Server 2013 deployment.

<div>


> [!IMPORTANT]  
> Microsoft Unified Communications Managed API (UCMA) 4.0 libraries are included in the installation package, so UCMA is not required and should not be installed on client computers.



</div>

</div>

<div>

## Configuration Requirements

The computers that will run the Lync Server 2013 Stress and Performance Tool must be configured according to the following requirements:

1.  You must be logged on as a member of the Domain or Local Admins group.

2.  Lync Server 2013 Stress and Performance Tool (LyncPerfTool.exe) cannot be run on a computer that is also running Lync Server 2013 components.

3.  You must run the Lync Server 2013 User Creation tool (UserProvisioningTool.exe) on the Front End Server or on the Standard Edition server where the user accounts will reside. When the tool is run multiple times, each user who is enabled for Microsoft Unified Communications must have a unique phone number.

4.  The page file size should be system-managed, or should be at least 1.5 times the amount of RAM on the system.

</div>

</div>

<span> </span>

</div>

</div>

</div>

