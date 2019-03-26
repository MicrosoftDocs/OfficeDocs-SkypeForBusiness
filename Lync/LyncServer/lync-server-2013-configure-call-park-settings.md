---
title: 'Lync Server 2013: Configure Call Park settings'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configure Call Park settings
ms:assetid: 3bed9d09-8363-4fff-a220-f0f6d3a81241
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425886(v=OCS.15)
ms:contentKeyID: 48183922
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure Call Park settings in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-01_

If you don't want to use default Call Park settings, you can customize them. When you install the Call Park application, global settings are configured by default. You can modify the global settings, and you can also specify site-specific settings. Use the **New-CsCpsConfiguration** cmdlet to create new site-specific settings. Use the **Set-CsCpsConfiguration** cmdlet to modify existing settings.

<div>


> [!NOTE]  
> At a minimum, we recommend that you configure the <STRONG>OnTimeoutURI</STRONG> option for the fallback destination to use when a parked call times out and ringback fails.



</div>

Use **New-CsCpsConfiguration** cmdlet or the **Set-CsCpsConfiguration** cmdlet to configure any of the following settings:


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>This option:</th>
<th>Specifies this:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>CallPickupTimeoutThreshold</strong></p></td>
<td><p>The amount of time that elapses after a call has been parked before it rings back to the phone where the call was answered.</p>
<p>The value must be entered in the format hh:mm:ss to specify the hours, minutes, and seconds. The minimum value is 10 seconds, and the maximum value is 10 minutes. The default is 00:01:30.</p></td>
</tr>
<tr class="even">
<td><p><strong>EnableMusicOnHold</strong></p></td>
<td><p>Whether music plays for a caller while a call is parked.</p>
<p>Values are True or False. The default is True.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MaxCallPickupAttempts</strong></p></td>
<td><p>The number of times a parked call rings back to the answering phone before it is forwarded to the fallback Uniform Resource Identifier (URI) that is specified for <strong>OnTimeoutURI</strong>. The default is 1.</p></td>
</tr>
<tr class="even">
<td><p><strong>OnTimeoutURI</strong></p></td>
<td><p>The SIP address of the user or response group to which an unanswered parked call is routed when <strong>MaxCallPickupAttempts</strong> is exceeded.</p>
<p>Value must be a SIP URI beginning with the string sip:. For example, sip:bob@contoso.com. The default is no forwarding address.</p></td>
</tr>
</tbody>
</table>


<div>

## To configure Call Park settings

1.  Log on to the computer where Lync Server Management Shell is installed as a member of the RTCUniversalServerAdmins group or with the necessary user rights as described in [Delegate setup permissions in Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

3.  Run:
    
        New-CsCpsConfiguration -Identity site:<sitename to apply settings> [-CallPickupTimeoutThreshold <hh:mm:ss>] -[EnableMusicOnHold <$true | $false>] [-MaxCallPickupAttempts <number of rings>] [-OnTimeoutURI sip:<sip URI for routing unanswered call>]
    
    <div>
    

    > [!TIP]  
    > Use the <STRONG>Get-CsSite</STRONG> cmdlet to identify the site. For details, see Lync Server Management Shell documentation.

    
    </div>
    
    For example:
    
        New-CsCpsConfiguration -Identity site:Redmond1 -CallPickupTimeoutThreshold 00:01:00 -EnableMusicOnHold $false -MaxCallPickupAttempts 2 -OnTimeoutURI sip:bob@contoso.com

</div>

<div>

## See Also


[Customize Call Park music on hold in Lync Server 2013](lync-server-2013-customize-call-park-music-on-hold.md)  


[New-CsCpsConfiguration](https://docs.microsoft.com/powershell/module/skype/New-CsCpsConfiguration)  
[Set-CsCpsConfiguration](https://docs.microsoft.com/powershell/module/skype/Set-CsCpsConfiguration)  
[Get-CsSite](https://docs.microsoft.com/powershell/module/skype/Get-CsSite)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

