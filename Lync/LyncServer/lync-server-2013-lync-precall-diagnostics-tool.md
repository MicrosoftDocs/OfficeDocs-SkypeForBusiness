---
title: 'Lync Server 2013: Lync PreCall Diagnostics Tool'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Lync PreCall Diagnostics Tool
ms:assetid: 0ff291ec-cfb4-43eb-b5d6-a7a325681e3f
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn451255(v=OCS.15)
ms:contentKeyID: 56708404
ms.date: 11/04/2016
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Lync PreCall Diagnostics Tool in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2016-11-04_

The Lync PreCall Diagnostics Tool (PCD) is a client-based application that allows you to see how the current state of your network might impact the audio quality in an upcoming Enterprise Voice call.

PCD is most useful in situations where the last hop of a network is likely to be the weakest (for example, with laptops on a public WiFi network or home users). PCD creates a small packet stream that traverses this final leg of the network. The tool then analyzes the packet stream to estimate how the jitter and loss along this leg might impact call quality, and then provides a report. You can run PCD continuously on the client, even while calls are being placed. The packet stream does not have a significant effect on bandwidth.

**The latest release of the PCD, version 1.1, includes the following enhancements:**

  - Support for longer passwords, which can now be up to 127 characters

  - Additional diagnostics for authentication sign-in issues

  - Better support for Lync hybrid deployments

  - Updates to credential picker

  - Stability improvements

We appreciate any feedback. Please send all support questions or issues to the [PCD Feedback](mailto:pcdfb@microsoft.com) alias at <pcdfb@microsoft.com>.

This topic includes the following sections:

  - Lync PCD Versions

  - Lync PCD System Requirements

  - Lync PCD Features

  - Running Lync PCD

  - Uninstalling Lync PCD

<span id="Version"></span>

<div>

## Lync PCD Versions

This topic describes the following versions of the tool, available for free download:

  - Windows Desktop App ([http://go.microsoft.com/fwlink/?LinkId=327914](http://go.microsoft.com/fwlink/p/?linkid=327914))

</div>

<span id="Requirements"></span>

<div>

## Lync PCD System Requirements

<div>


> [!NOTE]  
> PCD requires that Unified Communications Web API (UCWA) be installed and configured to support mobile clients in the Lync Server deployment. UCWA is installed with Lync Server.



</div>

<div>

## Windows Desktop App Requirements

  - Any edition of the Windows 7 or Windows 8 operating system

  - Microsoft .NET Framework 4.5 available at [http://go.microsoft.com/fwlink/?LinkId=327790](http://go.microsoft.com/fwlink/p/?linkid=327790)

</div>

</div>

<span id="features"></span>

<div>

## Lync PCD Features

Lync PCD includes the following features:

  - Run in default On Demand (2 minute bursts)

  - Run in Always On (up to 24 hours in snapped view) mode

  - Historical view of your test runs

  - Diagnose sign-in failures (Lync PCD for Windows 8 only)

![Lync PCD features Sign in progress screen shot](images/Dn451255.7e0eb891-1481-47ae-8d63-164468f69c96(OCS.15).png "Lync PCD features Sign in progress screen shot")

  - Graphical view of network metrics – Network MOS, Packet Loss and Interarrival Jitter in full screen and snapped view.

**Full screen view**

![PreCall Diagnostic Tool test result graphs](images/Dn451255.5d01fd94-9e59-4823-96c7-7a1c83dd7d31(OCS.15).png "PreCall Diagnostic Tool test result graphs")

**Snapped view**

![PreCall Diagnostic Tool Utilization test results](images/Dn451255.30501ba7-22d1-4db1-9297-56cf7dc6721c(OCS.15).png "PreCall Diagnostic Tool Utilization test results")

</div>

<span id="running"></span>

<div>

## Running Lync PCD

<div>

## Running Windows Desktop App

1.  To start the PCD on a Windows 7 system, select **PreCall Diagnostics** from the **Start** menu.
    
    To start the PCD on a Windows 8 system, select the icon on your Start screen, or search for “PreCall Diagnostics.”
    
    ![PreCall Diagnostic tool icon](images/Dn451255.c9800fde-54f6-4efe-bb35-1a38064ec380(OCS.15).png "PreCall Diagnostic tool icon")

2.  When the tool starts, select your preferred method of providing credentials and select the network operating mode in the **PreCall Diagnostics Tool Options** dialog box, then select **OK**:

3.  Select the **Start Test** button to start running diagnostics.
    
    If you selected the **Use network credentials** option, the test begins immediately.
    
    If you selected the **Let me enter my credentials** option, the **Windows Security** dialog box opens. After you enter your credentials, the test starts.

</div>

</div>

<span id="uninstall"></span>

<div>

## Uninstalling Lync PCD

To remove Lync PCD, follow the procedure for your operating system:

  - On a Windows 7 system, open the **Control Panel**, select **Programs and Features**, and double-click **Lync 2013 PreCall Diagnostics**.

  - On a Windows 8 system, right-click on the PCD tile and click **Uninstall** from the app bar at the bottom of the start screen.

</div>

</div>

<span> </span>

</div>

</div>

</div>

