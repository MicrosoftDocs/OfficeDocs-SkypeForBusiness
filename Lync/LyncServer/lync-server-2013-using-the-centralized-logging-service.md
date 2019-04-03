---
title: 'Lync Server 2013: Using the Centralized Logging Service'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Using the Centralized Logging Service
ms:assetid: 7b05aaef-f0ea-4649-ba8a-02e68b0cdf23
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ688101(v=OCS.15)
ms:contentKeyID: 49733700
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Using the Centralized Logging Service in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-01_

The Centralized Logging Service is a new feature in Lync Server 2013. It is an enhanced replacement for the **OCSLogger** and **OCSTracer** tools that were provided in previous releases. You can use the Centralized Logging Service to perform the following tasks:

  - Start logging on one or more computers and pools from a single location and command.

  - Stop logging on one or more computers and pools from a single location and command.

  - Search logs on one or more computers and pools for a single location and command. You can tailor the search command to return the entire aggregation of logs that were captured and stored on all machines, or return a trimmed-down result that captures specific data.

  - Configure logging sessions as follows:
    
      - Define a **Scenario**, or use a default scenario. A *scenario* in Centralized Logging Service is made up of scope (global or site), a scenario name to identify the purpose of the scenario, and one or more providers. You can run two scenarios at any given time on a computer.
    
      - Use an existing *provider* or create a new provider. A *provider* defines what the logging session collects, what level of detail, what components to trace, and what flags are applied.
        
        <div>
        

        > [!TIP]  
        > If you are familiar with OCSLogger, the term <EM>providers</EM> refers to the collection of <STRONG>components</STRONG> (for example, S4, SIPStack), a <STRONG>logging type</STRONG> (for example, WPP, EventLog, or IIS logfile), a <STRONG>tracing level</STRONG> (for example, All, verbose, debug), and <STRONG>flags</STRONG> (for example, TF_COMPONENT, TF_DIAG). These items are defined in the provider (a Windows PowerShell variable) and passed into the Centralized Logging Service command.

        
        </div>
    
      - Configure the computers and pools that you want to collect logs from.
    
      - Define the scope for the logging session from the options **Site** (run logging captures on computers in that site only), or **Global** (run logging capture on all computers in the deployment).

The Centralized Logging Service is extremely powerful and can meet nearly all of the needs for troubleshooting problems—large or small. From root cause analysis to performance problems, the Centralized Logging Service can be an important tool for any administrator. All examples are shown using the Lync Server Management Shell. There is a command-line component for the Centralized Logging Service called **CLSController.exe**. Help is provided for the command-line tool through the tool itself. However, there is a limited set of functions that you can execute from the command line. By using Lync Server Management Shell, you have access to a much larger and much more configurable set of features. You should always consider Lync Server Management Shell as the first and foremost method when using the Centralized Logging Service.

The topics in this section explain how to use the Centralized Logging Service and examples of how to use its many features.

<div>

## In This Section

  - [Overview of the Centralized Logging Service in Lync Server 2013](lync-server-2013-overview-of-the-centralized-logging-service.md)

  - [Managing the Centralized Logging Service configuration settings in Lync Server 2013](lync-server-2013-managing-the-centralized-logging-service-configuration-settings.md)

  - [Understanding Centralized Logging Service configuration settings in Lync Server 2013](lync-server-2013-understanding-centralized-logging-service-configuration-settings.md)

  - [Using Start for the Centralized Logging Service to capture logs in Lync Server 2013](lync-server-2013-using-start-for-the-centralized-logging-service-to-capture-logs.md)

  - [Using Stop for the Centralized Logging Service in Lync Server 2013](lync-server-2013-using-stop-for-the-centralized-logging-service.md)

  - [Using search on capture logs created by the Centralized Logging Service in Lync Server 2013](lync-server-2013-using-search-on-capture-logs-created-by-the-centralized-logging-service.md)

  - [Reading capture logs from the Centralized Logging Service in Lync Server 2013](lync-server-2013-reading-capture-logs-from-the-centralized-logging-service.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

