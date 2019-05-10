---
title: 'Lync Server 2013: Overview of Best Practices Analyzer'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Overview of Best Practices Analyzer
ms:assetid: c5fcaa05-eb1c-4092-90ad-177b127e795b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg591349(v=OCS.15)
ms:contentKeyID: 48185364
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Overview of Best Practices Analyzer in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-19_

You can use Lync Server 2013, Best Practices Analyzer to identify and resolve problems with your Lync Server 2013 deployment. The Lync Server 2013, Best Practices Analyzer gathers configuration information from Lync Server 2013 components.

With the proper network access, the Best Practices Analyzer can examine servers running Active Directory Domain Services, Exchange Server Unified Messaging (UM), and Lync Server 2013. You can use Best Practices Analyzer to do the following:

  - Proactively perform checks, verifying that the configuration is set according to recommended best practices.

  - Automatically detect required updates to Lync Server 2013.

  - Generate a list of issues, such as suboptimal configuration settings, unsupported options, missing updates, or practices that we do not recommend.

  - Help you troubleshoot and fix specific problems.

Best Practices Analyzer provides the following features:

  - Minimal installation prerequisites.

  - Online documentation about reported issues, including troubleshooting tips.

  - Configuration information that you can save for later review.

  - State-of-the-art system analysis.

Best Practices Analyzer uses a set of XML configuration files to determine the information to gather from your Lync Server 2013 environment. In addition to checking Active Directory Domain Services, it checks sources such as the Windows Server operating system registry and settings in Windows Management Instrumentation (WMI).

Best Practices Analyzer compares the data it gathers with a set of predefined rules for the settings and configurations of Lync Server 2013 deployments.

After comparing the collected data with the predefined rules, the tool reports issues. For every issue that it reports, Best Practices Analyzer provides information about what was found in the scanned Lync Server 2013 environment and the recommended configuration. Best Practices Analyzer also provides links to more detailed information about the specific issues.

<div>


> [!NOTE]  
> The Lync Server 2013, Best Practices Analyzer gathers configuration information only from Lync Server 2013 components. You can use the previous versions of the tool to scan previous environments. For details, see <A href="lync-server-2013-requirements-for-running-best-practices-analyzer.md">Requirements for running Best Practices Analyzer in Lync Server 2013</A>.



</div>

</div>

<span> </span>

</div>

</div>

</div>

