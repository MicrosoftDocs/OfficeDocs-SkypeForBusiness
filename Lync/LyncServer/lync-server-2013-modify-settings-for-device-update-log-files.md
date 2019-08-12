---
title: 'Lync Server 2013: Modify settings for Device Update log files'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Modify settings for Device Update log files
ms:assetid: 9b57f126-1853-43b3-bbd4-06401e6498bd
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg182554(v=OCS.15)
ms:contentKeyID: 48184975
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Modify settings for Device Update log files in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-23_

You can change settings for how device update information is logged in your organization by using Lync Server Control Panel or Lync Server Management Shell. The following table shows which settings are modifiable, and which tool(s) you use to modify the settings.

Log settings can be changed and applied globally, or per site.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>To change</th>
<th>Use</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>The maximum size (in bytes) for a log file</p></td>
<td><p>Lync Server Control Panel</p>
<p>-or-</p>
<p>Lync Server Management Shell</p></td>
</tr>
<tr class="even">
<td><p>The maximum amount of information (in bytes) that can be held in the cache</p></td>
<td><p>Lync Server Control Panel</p>
<p>-or-</p>
<p>Lync Server Management Shell</p></td>
</tr>
<tr class="odd">
<td><p>How often (in minutes) to write cached information to the log file</p></td>
<td><p>Lync Server Control Panel</p>
<p>-or-</p>
<p>Lync Server Management Shell</p></td>
</tr>
<tr class="even">
<td><p>How long (in days) to keep log files</p></td>
<td><p>Lync Server Control Panel</p>
<p>-or-</p>
<p>Lync Server Management Shell</p></td>
</tr>
<tr class="odd">
<td><p>When (time of day) to check for expired files that should be deleted</p></td>
<td><p>Lync Server Management Shell</p></td>
</tr>
<tr class="even">
<td><p>What log file extensions to permit</p></td>
<td><p>Lync Server Management Shell</p></td>
</tr>
<tr class="odd">
<td><p>Which log file types to retain</p></td>
<td><p>Lync Server Management Shell</p></td>
</tr>
</tbody>
</table>


<div>

## To change logging settings by using Lync Server Control Panel

1.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

2.  In the left navigation bar, click **Clients**, and then click **Device Log Configuration**.

3.  On the **Device Log Configuration** page, double-click the configuration that you want to change.

4.  In the **Edit Log Setting** dialog box, change any of the following settings:
    
      - **Maximum file size (bytes)**   Specifies the maximum size a log file can become before it is purged. The default is 1,024,000 bytes (1 MB).
    
      - **Maximum cache size (bytes)**   Specifies the maximum amount of information (in bytes) that can be held in the log file cache before that cache must be cleared and the data is written to a log file. The default is 512,000 bytes (0.5 MB).
    
      - **Number of minutes to flush cache (1-60)**   Indicates how often information stored in the log file cache is written to the actual log file. After the data is logged, the cache is cleared. The default is five minutes.
    
      - **Number of days to keep log files (1-365)**   Specifies the number of days the log files are kept before they are purged. The default is 10 days.

5.  Click **Commit**.

</div>

<div>

## Changing Logging Settings by Using Windows PowerShell Cmdlets

Device update log file settings can be modified by using Windows PowerShell and the **Set-CsDeviceUpdateConfiguration** cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell.

<div>


> [!NOTE]  
> For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at <A href="http://go.microsoft.com/fwlink/p/?linkid=255876">http://go.microsoft.com/fwlink/p/?linkId=255876</A>.



</div>

The following examples show a couple of the ways that you can use **Set-CsDeviceUpdateConfiguration** to modify settings.

<div>

## To modify the maximum log file size and the log cleanup interval

  - The following command modifies the device update log settings applied to the Redmond site. In this example, the maximum log file size is set to 204800 bytes and the log cleanup interval is set to 14 days.
    
        Set-CsDeviceUpdateConfiguration -Identity "site:Redmond" -MaxLogFileSize 204800 -LogCleanUpInterval 14.00:00:00

</div>

<div>

## To modify the log cleanup time of day

  - This command sets the log cleanup time for the Redmond site to 3:00 AM.
    
        Set-CsDeviceUpdateConfiguration -Identity "site:Redmond" -LogCleanupTimeOfDay 03:00

</div>

For details, see the Help topic for the [Set-CsDeviceUpdateConfiguration](https://docs.microsoft.com/powershell/module/skype/Set-CsDeviceUpdateConfiguration) cmdlet.

</div>

</div>

<span> </span>

</div>

</div>

</div>

