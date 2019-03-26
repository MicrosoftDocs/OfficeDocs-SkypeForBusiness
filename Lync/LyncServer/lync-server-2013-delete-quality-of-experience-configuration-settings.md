---
title: 'Lync Server 2013: Delete Quality of Experience configuration settings'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Delete Quality of Experience configuration settings
ms:assetid: fd0c4c2f-3bfb-42cb-9b6a-f0f8d5aa9e81
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg182613(v=OCS.15)
ms:contentKeyID: 48185954
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Delete Quality of Experience configuration settings in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-23_

Quality of Experience (QoE) metrics track the quality of audio and video calls made in your organization, including such things as the number of network packets lost, background noise, and the amount of "jitter" (differences in packet delay). These metrics are stored in a database apart from other data (such as call detail records), which allows you to enable and disable QoE independent of other data recording.

When you install Microsoft Lync Server 2013, a single, global collection of QoE configuration settings is created for you. Administrators also have the option of creating custom setting collections that can be applied to individual sites. By design, settings configured at the site scope take precedence over settings configured at the global scope. If you delete site-scoped settings, then QoE will be managed in that site by using the global settings.

Note that you can also “delete” the global settings. However, the global settings will not actually be removed. Instead, all the properties in that collection will be reset to their default values. For example, by default purging is enabled in a collection of QoE configuration settings. Suppose you modify the global collection so that purging is disabled. If you later delete the global settings, all the properties will be reset to their default values. In this case, that means that purging will once again be enabled.

You can remove QoE configuration settings by using the Lync Server Control Panel or by using the [Remove-CsQoEConfiguration](https://docs.microsoft.com/powershell/module/skype/Remove-CsQoEConfiguration) cmdlet.

<div>

## To delete QoE configuration settings by using Lync Server Control Panel

1.  Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role. For details, see [Delegate setup permissions in Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Monitoring and Archiving**, and then click **Quality of Experience Data**.

4.  On the **Quality of Experience Data** page, click the policy that you want, click **Edit**, and then click **Delete**.

5.  Click **OK**.

</div>

<div>

## Removing QoE Configuration Settings by Using Windows PowerShell Cmdlets

You can delete QoE configuration settings by using Windows PowerShell and the **Remove-CsQoEConfiguration** cmdlet. You can run this cmdlet either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

<div>

## To remove a specified collection of QoE configuration settings

  - This command removes the QoE configuration settings applied to the Redmond site:
    
        Remove-CsQoEConfiguration -Identity "site:Redmond"

</div>

<div>

## To remove all of the QoE configuration settings applied to the site scope

  - This command removes all the QoE configuration settings applied to the site scope:
    
        Get-CsQoEConfiguration -Filter "site:*" | Remove-CsQoEConfiguration

</div>

<div>

## To remove all of the QoE configuration settings where QoE monitoring is disabled

  - This command removes all the QoE configuration settings where QoE monitoring has been disabled:
    
        Get-CsQoEConfiguration | Where-Object {$_.EnableQoE -eq $False} | Remove-CsQoEConfiguration

</div>

For details, see [Remove-CsQoEConfiguration](https://docs.microsoft.com/powershell/module/skype/Remove-CsQoEConfiguration).

</div>

</div>

<span> </span>

</div>

</div>

</div>

