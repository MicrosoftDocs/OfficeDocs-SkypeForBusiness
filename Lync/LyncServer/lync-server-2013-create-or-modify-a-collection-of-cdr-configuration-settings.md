---
title: 'Lync Server 2013: Create or modify a collection of CDR configuration settings'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Create or modify a collection of CDR configuration settings
ms:assetid: c830be5a-2a82-468d-9c46-d3fec0f79fd0
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ721878(v=OCS.15)
ms:contentKeyID: 49733812
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Create or modify a collection of CDR configuration settings in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-23_

Call detail recording (CDR) enables you to track usage of such things as peer-to-peer instant messaging sessions, Voice over Internet Protocol (VoIP) phone calls, and conferencing calls. This usage data includes information about who called whom, when they called, and how long they talked.

When you install Microsoft Lync Server 2013 a single, global collection of CDR configuration settings is created for you. Administrators also have the option of creating custom settings at the site scope. Whenever these site-scoped settings are used, they take precedence over the global settings. For example, if you create site-scoped settings for the Redmond site then those settings (rather than the global settings) will be used to manage CDR in Redmond.

You can create CDR configuration settings by using either Lync Server Control Panel or the [New-CsCdrConfiguration](https://docs.microsoft.com/powershell/module/skype/New-CsCdrConfiguration) cmdlet. You can use Lync Server Control Panel or the [Set-CsCdrConfiguration](https://docs.microsoft.com/powershell/module/skype/Set-CsCdrConfiguration) cmdlet to modify existing settings. If you are using Lync Server Control Panel to create or modify settings, the following options will be available to you:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>UI Setting</th>
<th>PowerShell Parameter</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Name</p></td>
<td><p>Identity</p></td>
<td><p>Unique identifier for the CDR configuration settings being created. These settings can only be created at the site scope.</p></td>
</tr>
<tr class="even">
<td><p>Enable monitoring of CDRs</p></td>
<td><p>EnableCDR</p></td>
<td><p>Indicates whether or not CDR is enabled.</p></td>
</tr>
<tr class="odd">
<td><p>Enable purging of CDRs</p></td>
<td><p>EnablePurging</p></td>
<td><p>Indicates whether or not CDR records will periodically be deleted from the CDR database.</p></td>
</tr>
<tr class="even">
<td><p>Keep CDRs for maximum duration (days)</p></td>
<td><p>KeepCallDetailForDays</p></td>
<td><p>Indicates the number of days that CDR records will be kept in the CDR database. Any records older than the specified number of days will automatically be deleted. (Note that purging will take only place if purging has been enabled.)</p></td>
</tr>
<tr class="odd">
<td><p>Keep error report data for maximum duration (days)</p></td>
<td><p>KeepErrorReportForDays</p></td>
<td><p>Indicates the number of days that CDR error reports are kept. Any reports older than the specified number of days will automatically be deleted. CDR error reports are diagnostic reports uploaded by client applications.</p></td>
</tr>
</tbody>
</table>


<div>


> [!NOTE]  
> The New-CsCdrConfiguration and Set-CsCdrConfiguration cmdlets include additional options not available in Lync Server Control Panel. See the <A href="https://docs.microsoft.com/powershell/module/skype/New-CsCdrConfiguration">New-CsCdrConfiguration</A> and the <A href="https://docs.microsoft.com/powershell/module/skype/Set-CsCdrConfiguration">Set-CsCdrConfiguration</A> help topics for more information.



</div>

<div>

## To create CDR configuration settings by using Lync Server Control Panel

1.  In Lync Server Control Panel click **Monitoring and Archiving**.

2.  On the **Call Detail Recording** tab, click **New**.

3.  In the **Select a Site** dialog box, select the site where the new configuration settings are to be created. If the dialog box is empty, that means all of your sites have already been assigned a collection of CDR configuration settings. Each site is limited to a single such collection. In that case you can either delete and then re-create the settings, or simply modify the existing settings.

4.  In the **New Call Detail Recording (CDR) Setting** dialog, make the desired selections and then click **Commit**.

</div>

<div>

## To modify existing CDR configuration settings by using Lync Server Control Panel

1.  In Lync Server Control Panel click **Monitoring and Archiving**.

2.  Double-click the collection of settings to be modified, or select the collection, click **Edit**, and then click **Show Details**. Note that you can only modify a single collection at a time. To make the same changes to multiple collections, use the Lync Server Management Shell instead.

3.  In the **Edit Call Detail Recording (CDR) Setting** dialog, make the desired selections and then click **Commit**.

</div>

<div>

## Creating CDR Configuration Settings by Using Windows PowerShell Cmdlets

You can create CDR configuration settings can also be created by using Windows PowerShell and the **New-CsCdrConfiguration** cmdlet. You can run this cmdlet either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

<div>

## To create a new collection of CDR configuration settings

  - This command creates a new collection of CDR configuration settings applied to the Redmond site:
    
        New-CsCdrConfiguration -Identity "site:Redmond"

</div>

<div>

## To create a collection of CDR configuration settings that disable call detail recording

  - Because no parameters (other than the mandatory Identity parameter) were specified in the preceding command, the new collection of configuration settings will use the default values for all its properties. To create settings that use different property values, simply include the appropriate parameter and parameter value. For example, to create a collection of Call Detail configuration settings that, by default, allow disable Call Detail recording use a command like this:
    
        New-CsCdrConfiguration -Identity "site:Redmond" -EnableCDR $False

</div>

<div>

## To specify multiple property values when creating a new collection of CDR configuration settings

  - You can modify multiple property values by including multiple parameters. For example, this command configures the new settings to keep Call Detail records for 30 days and error reports for 90 days:
    
        New-CsCdrConfiguration -Identity "site:Redmond" -KeepCallDetailForDays 30 -KeepErrorReportForDays 90

</div>

For more information, see the help topic for the [New-CsCdrConfiguration](https://docs.microsoft.com/powershell/module/skype/New-CsCdrConfiguration) cmdlet.

</div>

</div>

<span> </span>

</div>

</div>

</div>

