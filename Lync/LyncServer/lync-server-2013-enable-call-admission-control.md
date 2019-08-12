---
title: 'Lync Server 2013: Enable call admission control'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Enable call admission control
ms:assetid: 80201105-18f7-4c02-9c71-8df5a952f6c7
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398642(v=OCS.15)
ms:contentKeyID: 48184650
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Enable call admission control in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-19_

After you have configured your network settings for call admission control deployment, you must enable CAC to put your bandwidth policies into effect.

For details, see the Lync Server Management Shell documentation for the following cmdlets:

  - [Get-CsNetworkConfiguration](https://docs.microsoft.com/powershell/module/skype/Get-CsNetworkConfiguration)

  - [Set-CsNetworkConfiguration](https://docs.microsoft.com/powershell/module/skype/Set-CsNetworkConfiguration)

  - [Remove-CsNetworkConfiguration](https://docs.microsoft.com/powershell/module/skype/Remove-CsNetworkConfiguration)

<div>

## To enable call admission control by using Management Shell

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

2.  Run the Set-CsNetworkConfiguration cmdlet to enable CAC in your network. For example, run:
    
        Set-CsNetworkConfiguration -EnableBandwidthPolicyCheck 1
    
    If you want to disable CAC in your network, run the following:
    
        Set-CsNetworkConfiguration -EnableBandwidthPolicyCheck 0

</div>

<div>

## To enable call admission control by using Lync Server Control Panel

1.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

2.  In the left navigation bar, click **Network Configuration**.

3.  Click the **Global** navigation button.

4.  Click **Global** in the list, and then select **Show Details** on the **Edit** menu.

5.  On the **Edit Global Settings** page, select the **Enable call admission control** check box.
    
    <div>
    

    > [!NOTE]  
    > If you want to disable call admission control throughout your deployment, clear this check box.

    
    </div>

6.  Click **Commit**.

</div>

</div>

<span> </span>

</div>

</div>

</div>

