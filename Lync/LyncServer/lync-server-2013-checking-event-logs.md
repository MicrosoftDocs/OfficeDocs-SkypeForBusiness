---
title: 'Lync Server 2013: Checking event logs'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Checking event logs
ms:assetid: 5500720d-c628-4dbd-84bc-a5becc39b99c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn720914(v=OCS.15)
ms:contentKeyID: 63969602
ms.date: 01/27/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Checking event logs in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-08-06_

You can use [Windows Event Viewer](http://go.microsoft.com/fwlink/p/?linkid=314067) to view event logs and obtain information about service failures, replication errors in the AD DS, and warnings about system resources such as virtual memory and disk space. Event Viewer is included with Windows Server 2008 and 2012.

In the Lync Server 2013 Logging Tool, when you end the debug session, click **Analyze Log Files** to view the log files by using the Snooper tool.

Event Viewer maintains logs about application, security, and system events on the computer. Both Lync Server 2013 and Windows report warnings and error conditions to the event logs. Therefore, review event logs daily.

Use Event Viewer to:

  - View and manage event logs.

  - Obtain information about hardware, software, and system issues that must be resolved.

  - Identify trends that require future action.

A server that is running Lync Server on a Windows Server operating system records events in four types of logs:

  - **Application logs**   The Application log contains events logged by applications or programs. Developers determine which events to log. For example, a database program might record a file error in the Application log. Most Lync Server 2013-related events appear in the Application log.

  - **Security logs**   The Security log records events such as valid and not valid logon tries in addition to events related to resource use such as creating, opening, or deleting files or other objects. For example, if logon auditing is enabled, attempts to log on to the system are recorded in the Security log.

  - **System logs**   The System log contains events logged by Windows system components. For example, the failure of a driver or other system component to load during startup is recorded in the System log. The event types logged by system components are predetermined by the server.

  - **Lync Server 2013**   The logging tool records significant events related to authentication, connections, and user actions. After enabling diagnostic logging, you can view the log entries in Event Viewer.

<div>


> [!NOTE]  
> We do not recommend that you use the maximum logging settings unless you are instructed to do this by Microsoft Customer Support Services. Maximum logging drains significant resources and can give many “false positives,” that is, errors that get logged only at maximum logging but are really expected and are not a cause of concern. We also recommend that you do not enable diagnostic logging permanently. Use it only when troubleshooting.



</div>

Within each Event Viewer log, Lync Server 2013 records informational, warning, and error events. Monitor these logs closely to track the types of transactions being conducted on the Lync Server 2013 servers. You should periodically archive the logs or use automatic rollover to avoid running out of space. Because log files can occupy a finite amount of space, increase the log size (for example, to 50 MB) and set it to overwrite so that the Lync Server 2013 Server can continue to write new events.

You can also automate event log administration by using the following tools and technologies:

  - System Center Operations Manager monitors the health and use of Lync Server 2013 servers. Lync Server 2013 Management Pack for Operations Manager extends Operations Manager by providing specialized monitoring for servers that are running Lync Server 2013.

  - The Lync Server 2013 Management Pack for Operations Manager monitors Standard and Enterprise Edition of Lync Server 2013. This release also incorporates the Quality of Experience (QoE) Management Pack which was previously a separate management pack.

Monitored types are event log entries, performance counters and stateful monitoring of QoE. This version of the management pack only monitors Lync Server 2013 and 2010, and cannot be used to monitor Office Communications Server 2007.

The management pack provides the following features:

  - Alerts indicating service affecting events

  - Alerts indicating configuration, and other non-service impacting issues

  - State monitoring of Lync Server services

  - Product knowledge: Cause and resolution of identified issues

For more information about Lync Server 2013 Management Pack, refer to [Monitoring Lync Server 2013 with System Center Operations Manager](lync-server-2013-monitoring-lync-server-with-system-center-operations-manager.md).

**Event Comb**   The Event Comb tool collects specific events from the event logs of several computers to one central location. It lets you report on only the event IDs or event sources it specifies. For more information about Event Comb, see the [Account Lockout and Management Tools](http://go.microsoft.com/fwlink/?linkid=35607) website.

**Event triggers**   In Windows Server 2012 you can "Attach a Task to This Event" within the Windows Event Viewer—where an administrator can either run a program, send an email message or display an on-screen message. For more information about this feature, see the Windows Server 2008 R2 topic [Run a Task in Response to a Given Event](http://technet.microsoft.com/en-us/library/cc748900.aspx). You can also use command-line tools such as ‘Eventtrigger.exe’ to create and query event logs and associate programs with particular logged events. By using Eventtriggers.exe, you can create event triggers that run programs when specific events occur.

<div>

## See Also


[Windows Event Viewer](http://go.microsoft.com/fwlink/p/?linkid=314067)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

