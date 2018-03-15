---
title: "Lync PreCall Diagnostics Tool in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 0ff291ec-cfb4-43eb-b5d6-a7a325681e3f
description: "In this articleLync PCD VersionsLync PCD System RequirementsLync PCD FeaturesRunning Lync PCDUninstalling Lync PCD"
---

# Lync PreCall Diagnostics Tool in Lync Server 2013
[]
 **In this article**
  
[Lync PCD Versions](#Version)
  
[Lync PCD System Requirements](#Requirements)
  
[Lync PCD Features](#features)
  
[Running Lync PCD](#running)
  
[Uninstalling Lync PCD](#uninstall)
  
The Lync PreCall Diagnostics Tool (PCD) is a client-based application that allows you to see how the current state of your network might impact the audio quality in an upcoming Enterprise Voice call.
  
PCD is most useful in situations where the last hop of a network is likely to be the weakest (for example, with laptops on a public WiFi network or home users). PCD creates a small packet stream that traverses this final leg of the network. The tool then analyzes the packet stream to estimate how the jitter and loss along this leg might impact call quality, and then provides a report. You can run PCD continuously on the client, even while calls are being placed. The packet stream does not have a significant effect on bandwidth.
  
 **The latest release of the PCD, version 1.1, includes the following enhancements:**
  
- Support for longer passwords, which can now be up to 127 characters
    
- Additional diagnostics for authentication sign-in issues
    
- Better support for Lync hybrid deployments
    
- Updates to credential picker
    
- Stability improvements
    
We appreciate any feedback. Please send all support questions or issues to the [PCD Feedback](mailto:pcdfb@microsoft.com) alias at [pcdfb@microsoft.com](mailto:pcdfb@microsoft.com).
  
This topic includes the following sections:
  
- [Lync PCD Versions](lync-precall-diagnostics-tool.md#Version)
    
- [Lync PCD System Requirements](lync-precall-diagnostics-tool.md#Requirements)
    
- [Lync PCD Features](lync-precall-diagnostics-tool.md#features)
    
- [Running Lync PCD](lync-precall-diagnostics-tool.md#running)
    
- [Uninstalling Lync PCD](lync-precall-diagnostics-tool.md#uninstall)
    
## Lync PCD Versions
<a name="Version"> </a>

This topic describes the following versions of the tool, available for free download:
  
- Windows Desktop App ([http://go.microsoft.com/fwlink/?LinkId=327914](https://go.microsoft.com/fwlink/p/?LinkId=327914))
    
## Lync PCD System Requirements
<a name="Requirements"> </a>

> [!NOTE]
> PCD requires that Unified Communications Web API (UCWA) be installed and configured to support mobile clients in the Lync Server deployment. UCWA is installed with Lync Server. 
  
### Windows Desktop App Requirements

- Any edition of the Windows 7 or Windows 8 operating system
    
- Microsoft .NET Framework 4.5 available at [http://go.microsoft.com/fwlink/?LinkId=327790](https://go.microsoft.com/fwlink/p/?LinkId=327790)
    
## Lync PCD Features
<a name="features"> </a>

 Lync PCD includes the following features: 
  
- Run in default On Demand (2 minute bursts)
    
- Run in Always On (up to 24 hours in snapped view) mode
    
- Historical view of your test runs
    
- Diagnose sign-in failures (Lync PCD for Windows 8 only)
    
![Lync PCD features Sign in progress screen shot](media/lync_pcd_signin-progress.png)
  
- Graphical view of network metrics - Network MOS, Packet Loss and Interarrival Jitter in full screen and snapped view.
    
 **Full screen view**
  
![PreCall Diagnostic Tool test result graphs](media/precall_diag3.png)
  
 **Snapped view**
  
![PreCall Diagnostic Tool Utilization test results](media/utilization.png)
  
## Running Lync PCD
<a name="running"> </a>

### Running Windows Desktop App

1. To start the PCD on a Windows 7 system, select **PreCall Diagnostics** from the **Start** menu. 
    
    To start the PCD on a Windows 8 system, select the icon on your Start screen, or search for "PreCall Diagnostics."
    
     ![PreCall Diagnostic tool icon](media/PCD_logo.png)
  
2. When the tool starts, select your preferred method of providing credentials and select the network operating mode in the **PreCall Diagnostics Tool Options** dialog box, then select **OK**:
    
3. Select the **Start Test** button to start running diagnostics. 
    
    If you selected the **Use network credentials** option, the test begins immediately. 
    
    If you selected the **Let me enter my credentials** option, the **Windows Security** dialog box opens. After you enter your credentials, the test starts. 
    
## Uninstalling Lync PCD
<a name="uninstall"> </a>

To remove Lync PCD, follow the procedure for your operating system:
  
- On a Windows 7 system, open the **Control Panel**, select **Programs and Features**, and double-click **Lync 2013 PreCall Diagnostics**.
    
- On a Windows 8 system, right-click on the PCD tile and click **Uninstall** from the app bar at the bottom of the start screen. 
    

