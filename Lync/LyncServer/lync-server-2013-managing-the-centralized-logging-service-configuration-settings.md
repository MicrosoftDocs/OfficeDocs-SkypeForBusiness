---
title: 'Managing the Centralized Logging Service configuration settings'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Managing the Centralized Logging Service configuration settings
ms:assetid: f455c3aa-0061-413d-bdfb-a3e78f82723d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ721938(v=OCS.15)
ms:contentKeyID: 49733875
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Managing the Centralized Logging Service configuration settings in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-01_

The Centralized Logging Service is controlled and configured by settings and parameters that are created and used by the Centralized Logging Service Controller (CLSController) to send commands to the individual computer’s Centralized Logging Service Agent (CLSAgent). The agent processes the commands that are sent to it and (in the case of a Start command) uses the configuration of the scenarios, providers, log size, trace duration, and flags to begin collecting trace logs according to the configuration information provided.

<div>


> [!IMPORTANT]
> Not all Windows PowerShell cmdlets listed for the Centralized Logging Service are intended for use with Lync Server 2013 on-premises deployments. Although they may appear to work, the following cmdlets are not designed to function with Lync Server 2013 on-premises deployments: 
> <UL>
> <LI>
> <P><STRONG>CsClsRegion cmdlets:</STRONG> <A href="https://technet.microsoft.com/en-us/library/JJ204879(v=OCS.15)">Get-CsClsRegion</A>, <A href="https://technet.microsoft.com/en-us/library/JJ204746(v=OCS.15)">Set-CsClsRegion</A>, <A href="https://technet.microsoft.com/en-us/library/JJ204658(v=OCS.15)">New-CsClsRegion</A>, and <A href="https://technet.microsoft.com/en-us/library/JJ204971(v=OCS.15)">Remove-CsClsRegion</A>.</P>
> <LI>
> <P><STRONG>CsClsSearchTerm cmdlets:</STRONG> <A href="https://technet.microsoft.com/en-us/library/JJ205061(v=OCS.15)">Get-CsClsSearchTerm</A> and <A href="https://technet.microsoft.com/en-us/library/JJ204911(v=OCS.15)">Set-CsClsSearchTerm</A>.</P>
> <LI>
> <P><STRONG>CsClsSecurityGroup cmdlets:</STRONG> <A href="https://technet.microsoft.com/en-us/library/JJ205285(v=OCS.15)">Get-CsClsSecurityGroup</A>, <A href="https://technet.microsoft.com/en-us/library/JJ204700(v=OCS.15)">Set-CsClsSecurityGroup</A>, <A href="https://technet.microsoft.com/en-us/library/JJ205359(v=OCS.15)">New-CsClsSecurityGroup</A>, and <A href="https://technet.microsoft.com/en-us/library/JJ204958(v=OCS.15)">Remove-CsClsSecurityGroup</A>.</P></LI></UL>The settings defined in these cmdlets will not hinder or cause any adverse behavior, but they are designed for use with Microsoft Office 365 and will not yield the expected results in on-premises deployments. This is not to say that there is no use for these cmdlets in on-premises deployments, but their use is a more advanced topic that is not covered in this documentation.



</div>

<div>

## In This Section

The topics in this section define the configuration options, parameters, and settings for the Centralized Logging Service. Information about how to configure the Centralized Logging Service, how to retrieve the configuration settings, creation of scenarios, management of security groups for Centralized Logging Service, searching, and more is contained in the following topics.

  - [Managing computer, site and global Centralized Logging Service configuration in Lync Server 2013](lync-server-2013-managing-computer-site-and-global-centralized-logging-service-configuration.md)

  - [Configuring providers for Centralized Logging Service in Lync Server 2013](lync-server-2013-configuring-providers-for-centralized-logging-service.md)

  - [Configuring scenarios for the Centralized Logging Service in Lync Server 2013](lync-server-2013-configuring-scenarios-for-the-centralized-logging-service.md)

</div>

<div>

## See Also


[Overview of the Centralized Logging Service in Lync Server 2013](lync-server-2013-overview-of-the-centralized-logging-service.md)  
[Centralized Logging cmdlets in Lync Server 2013](lync-server-2013-centralized-logging-cmdlets.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

