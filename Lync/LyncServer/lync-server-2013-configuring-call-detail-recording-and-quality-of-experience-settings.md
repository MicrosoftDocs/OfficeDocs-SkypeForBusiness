---
title: 'Configuring call detail recording and Quality of Experience settings'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configuring call detail recording and Quality of Experience settings
ms:assetid: 009a0499-4f8c-450d-9c72-a565a08e9f7a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204621(v=OCS.15)
ms:contentKeyID: 48183223
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring call detail recording and Quality of Experience settings in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-17_

After you have associated a monitoring store with a Front End pool, set up the monitoring store, and then installed and configured SQL Server Reporting Services and Monitoring Reports you can manage Call Detail Recording (CDR) and Quality of Experience (QoE) monitoring by using Lync Server Management Shell. Lync Server Management Shell cmdlets allow you to enable and disable CDR and/or QoE monitoring for a particular site or for your entire Lync Server deployment; that can be done with a command as simple as this:

    Set-CsQoEConfiguration -Identity "global" -EnableQoE $False

When you install Microsoft Lync Server 2013, you will also install a predefined collection of global configuration settings for both CDR and QoE. Default values for some of the more commonly-used settings used by Call Detail Recording are shown in the following table:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
<th>Default Value</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>EnableCDR</p></td>
<td><p>Indicates whether or not CDR is enabled. If True, all CDR records will be collected and written to the monitoring database.</p></td>
<td><p>True</p></td>
</tr>
<tr class="even">
<td><p>EnablePurging</p></td>
<td><p>Indicates whether or not CDR records will periodically be deleted from the database. If True, records will be deleted after the time period specified by the properties KeepCallDetailForDays (for CDR records) and KeepErrorReportForDays (for CDR errors). If False, CDR records will be maintained indefinitely.</p></td>
<td><p>True</p></td>
</tr>
<tr class="odd">
<td><p>KeepCallDetailForDays</p></td>
<td><p>Indicates the number of days that CDR records will be kept in the database; any records older than the specified number of days will automatically be deleted. However, this will occur only if purging has been enabled.</p>
<p>KeepCallDetailForDays can be set to any integer value between 1 and 2562 days (approximately 7 years).</p></td>
<td><p>60 days</p></td>
</tr>
<tr class="even">
<td><p>KeepErrorReportForDays</p></td>
<td><p>Indicates the number of days that CDR error reports are kept; any reports older than the specified number of days will automatically be deleted. CDR error reports are diagnostic reports uploaded by client applications such as Microsoft Lync 2013.</p>
<p>You can set this property to any integer value between 1 and 2562 days.</p></td>
<td><p>60 days</p></td>
</tr>
</tbody>
</table>


Similarly, default values for selected QoE settings are shown in this table:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
<th>Default Value</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>EnableQoE</p></td>
<td><p>Indicates whether or not QoE monitoring is enabled. If True, all QoE records will be collected and written to the monitoring database.</p></td>
<td><p>True</p></td>
</tr>
<tr class="even">
<td><p>EnablePurging</p></td>
<td><p>Indicates whether or not QoE records will periodically be deleted from the database. If True, records will be deleted after the time period specified by the KeepQoEDataForDays property. If False, QoE records will be maintained indefinitely.</p></td>
<td><p>True</p></td>
</tr>
<tr class="odd">
<td><p>KeepQoEDataForDays</p></td>
<td><p>Indicates the number of days that QoE records will be kept in the database; any records older than the specified number of days will automatically be deleted. However, this will occur only if purging has been enabled.</p>
<p>KeepCallDetailForDays can be set to any integer value between 1 and 2562 days.</p></td>
<td><p>60 days</p></td>
</tr>
</tbody>
</table>


If you need to modify these global settings you can do so by using the Set-CsCdrConfiguration and the Set-CsQoEConfiguration cmdlets. For example, this command (run from within the Lync Server Management Shell) disables CDR monitoring at the global scope; that's done by setting the EnableCDR property to False ($False):

    Set-CsCdrConfiguration -Identity "global" -EnableCDR $False

Note that disabling monitoring does not dissociate the monitoring store from the Front End pool, nor does it uninstall or otherwise affect the backend monitoring database. When you use Lync Server Management Shell to disable either CDR or QoE monitoring all you really do is temporarily stop Lync Server from collecting and archiving monitoring data. If you want to resume, in this case, the collection and archiving of CDR data, all you need to do is set the EnableCDR property back to True ($True):

    Set-CsCdrConfiguration -Identity "global" -EnableCDR $True

Similarly, this command disables the purging of QoE records at the global scope:

    Set-CsQoEConfiguration -Identity "global" -EnablePurging $False

In addition to the global settings, CDR and QoE configurations settings can be assigned to the site scope. This provides additional management flexibility when it comes to monitoring; for example, an administrator can enable CDR monitoring for the Redmond site but disable CDR monitoring for the Dublin site. To create new CDR configuration settings at the site scope, use a command similar to this:

    New-CsCdrConfiguration -Identity "site:Redmond" -EnableCDR $False

Keep in mind that settings configured at the site scope take precedence over settings configured at the global scope. For example, suppose CDR monitoring is enabled at the global scope, but disabled at the site scope (for the Redmond site). That means that call detail recording information will not be archived for users in the Redmond site. However, users in other sites (that is, users managed by the global settings instead of the Redmond site settings) will have their call detail recording information archived.

New QoE configuration settings can be created at the site scope by using a command like this one:

    New-CsQoEConfiguration -Identity "site:Redmond" -KeepQoEDataForDays 15

For more information, type the following commands from within the Lync Server Management Shell:

    Get-Help New-CsCdrConfiguration | more
    Get-Help Set-CsCdrConfiguration | more
    Get-Help New-CsQoEConfiguration | more
    Get-Help Set-CsQoEConfiguration | more

</div>

<span> </span>

</div>

</div>

</div>

