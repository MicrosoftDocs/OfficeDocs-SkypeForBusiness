---
title: 'Lync Server 2013: View PSTN usage records'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: View PSTN usage records
ms:assetid: 65025c78-c263-472c-9ff9-e170588f10b5
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398458(v=OCS.15)
ms:contentKeyID: 48184361
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# View PSTN usage records in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

A public switched telephone network (PSTN) usage record specifies a class of call (such as internal, local, or long distance) that can be made by various users or groups of users in an organization. For details, see [PSTN usage records in Lync Server 2013](lync-server-2013-pstn-usage-records.md) in the Planning documentation.

<div>

## To view a PSTN usage record by using Lync Server Control Panel

1.  Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role. For details, see [Delegate setup permissions in Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Voice Routing** and then click **PSTN Usage**.

4.  On the **PSTN Usage** page, highlight the PSTN usage record you want to view, click **Edit** and then click **Show details**.
    
    <div>
    

    > [!NOTE]  
    > A read-only page of the selected PSTN usage record shows the associated routes and associated voice policies.

    
    </div>

</div>

<div>

## Viewing PSTN Usage Information by Using Windows PowerShell Cmdlets

You can also view PSTN usages by using Windows PowerShell and the **Get-CsPstnUsage** cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

<div>

## To view PSTN usage information by using Windows PowerShell cmdlets

  - To view information about all of your PSTN usages, type the following command in the Lync Server Management Shell, and then press ENTER:
    
        Get-CsPstnUsage
    
    This command returns information similar to the following:
    
        Identity : Global
        Usage    : {Internal, Local, Long Distance}

</div>

For details, see [Get-CsPstnUsage](https://docs.microsoft.com/powershell/module/skype/Get-CsPstnUsage).

</div>

<div>

## See Also


[Create a voice policy and configure PSTN usage records in Lync Server 2013](lync-server-2013-create-a-voice-policy-and-configure-pstn-usage-records.md)  
[Modify a voice policy and configure PSTN usage records in Lync Server 2013](lync-server-2013-modify-a-voice-policy-and-configure-pstn-usage-records.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

