---
title: 'Lync Server 2013: Create Quality of Experience configuration settings'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Create Quality of Experience configuration settings
ms:assetid: 64f05569-07c7-4f76-a96b-ea4125a510d5
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg521006(v=OCS.15)
ms:contentKeyID: 48184357
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Create Quality of Experience configuration settings in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-23_

Quality of Experience (QoE) metrics track the quality of audio and video calls made in your organization, including such things as the number of network packets lost, background noise, and the amount of "jitter" (differences in packet delay). These metrics are stored in a database apart from other data (such as call detail records), which allows you to enable and disable QoE independent of other data recording.

When you install Microsoft Lync Server 2013, a single, global collection of QoE configuration settings is created for you. Administrators also have the option of creating custom settings at the site scope. Whenever these site-scoped settings are used, they take precedence over the global settings. For example, if you create site-scoped settings for the Redmond site then those settings (rather than the global settings) will be used to manage QoE in Redmond.

QoE configuration settings can be created by using either Lync Server Control Panel or the [New-CsQoEConfiguration](https://docs.microsoft.com/powershell/module/skype/New-CsQoEConfiguration) cmdlet. If you are using Lync Server Control Panel to create new settings the following options will be available to you:


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
<td><p>Unique identifier for the settings to be created. QoE configuration settings can only be created at the site scope.</p></td>
</tr>
<tr class="even">
<td><p>Enable monitoring of QoE data</p></td>
<td><p>EnableQoE</p></td>
<td><p>Specifies whether QoE records will be collected and saved to the monitoring database.</p></td>
</tr>
<tr class="odd">
<td><p>Enable purging of QoE data</p></td>
<td><p>EnablePurging</p></td>
<td><p>Specifies whether records will be purged after the duration defined in the <strong>Keep QoE data for a maximum duration (days)</strong> property has elapsed.</p></td>
</tr>
<tr class="even">
<td><p>Keep QoE data for maximum duration (days)</p></td>
<td><p>KeepQoEDataForDays</p></td>
<td><p>Number of days QoE data will be stored before being purged from the database. This value is ignored if purging is disabled.</p></td>
</tr>
</tbody>
</table>


<div>


> [!NOTE]  
> The New-CsQoEConfiguration cmdlet includes additional options not available in Lync Server Control Panel. For more information, see the <A href="https://docs.microsoft.com/powershell/module/skype/New-CsQoEConfiguration">New-CsQoEConfiguration</A> help topic.



</div>

<div>

## To create QoE configuration settings by using Lync Server Control Panel

1.  Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role. For details, see [Delegate setup permissions in Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Monitoring and Archiving**, and then click **Quality of Experience Data**.

4.  On the **Quality of Experience Data** page, click **New**.

5.  In **Select a Site**, click the site to which the policy is to be applied, and click **OK**.

6.  In **New Quality of Experience Setting**, do the following:
    
      - Select **Enable monitoring of QoE data** to turn on monitoring.
    
      - Select **Enable purging of QoE data** to turn on purging.
    
      - In **Keep QoE for maximum duration (days)**, select the maximum number of days that QoE records should be retained.

7.  Click **Commit**.

</div>

<div>

## Creating QoE Configuration Settings by Using Windows PowerShell Cmdlets

You can create QoE configuration settings by using Windows PowerShell and the New-CsQoEConfiguration cmdlet. You can run this cmdlet either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

<div>

## To create a new collection of QoE configuration settings

  - This command creates a new collection of QoE configuration settings applied to the Redmond site:
    
        New-CsQoEConfiguration -Identity "site:Redmond"

</div>

<div>

## To create a new collection of QoE configuration settings where QoE monitoring is disabled

  - Because no parameters (other than the mandatory Identity parameter) were specified in the preceding command, the new collection of configuration settings will use the default values for all its properties. To create settings that use different property values, simply include the appropriate parameter and parameter value. For example, to create a collection of Quality of Experience configuration settings that, by default, allow disable QoE recording use a command like this:
    
        New-CsQoEConfiguration -Identity "site:Redmond" -EnableQoE $False

</div>

<div>

## To specify multiple property values when creating a new collection of QoE configuration settings

  - You can multiple property values by including multiple parameters. For example, this command configures the new settings to keep QoE data for 30 days and to purge old data at 3:00 AM:
    
        New-CsQoEConfiguration -Identity "site:Redmond" -KeepQoEDataForDays 30 -PurgeHourOfDay 3

</div>

For more information, see the help topic for the [New-CsQoEConfiguration](https://docs.microsoft.com/powershell/module/skype/New-CsQoEConfiguration) cmdlet.

</div>

</div>

<span> </span>

</div>

</div>

</div>

