---
title: 'Lync Server 2013: Delete Device Update log files'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Delete Device Update log files
ms:assetid: 58d4097f-5bbf-4824-a04d-2a6555cd93c3
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ994039(v=OCS.15)
ms:contentKeyID: 51803949
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Delete Device Update log files in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-23_

The Device Update Web service keeps an extensive collection of log files. This collection includes both audit logs conducted by the service itself and log files uploaded from client devices. To prevent the server from filling up with Device Update Web service logs, you’ll probably want to clear it of log files that have been around for a certain number of days. Set this number of days based on update activity and the number of client devices in your organization, and by using Lync Server Control Panel or Lync Server Management Shell.

<div>

## To clear the device update log by using Lync Server Control Panel

1.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

2.  In the left navigation bar, click **Clients**, and then click **Device Log Configuration**.

3.  On the **Device Log Configuration** page, double-click the configuration that you want to change.

4.  In the **Edit Log Setting** dialog box, in **Number of days to keep log files (1-365)**, specifiy a number of days.

5.  Click **Commit**. All files that have been on the server for more than the specified number of day are deleted. This setting will apply to this configuration until you change it.

</div>

<div>

## Clearing the Device Update Log by Using the Windows PowerShell Cmdlets

You can clear device update logs by using Windows PowerShell and the **Clear-CsDeviceUpdateLog** cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell.

<div>


> [!NOTE]  
> For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at <A href="http://go.microsoft.com/fwlink/p/?linkid=255876">http://go.microsoft.com/fwlink/p/?linkId=255876</A>.



</div>

<div>

## To clear device update logs on one server

  - The following command clears the device update log on the Web server atl-cs-001.litwareinc.com. All log entries more than 10 days old (the value specified by the DaysBack parameter) will be removed from the log.
    
        Clear-CsDeviceUpdateLog -Identity "service:WebServer:atl-cs-001.litwareinc.com" -DaysBack 10

</div>

<div>

## To clear all device update logs

  - This command removes outdated entries (in this example, entries more than 10 days old) from all the device update logs currently in use in your organization.
    
        Get-CsService -WebServer | Foreach-Object {Clear-CsDeviceUpdateLog -Identity $_.Identity -DaysBack 10}

</div>

For details, see the Help topic for the [Clear-CsDeviceUpdateLog](https://docs.microsoft.com/powershell/module/skype/Clear-CsDeviceUpdateLog) cmdlet.

</div>

</div>

<span> </span>

</div>

</div>

</div>

