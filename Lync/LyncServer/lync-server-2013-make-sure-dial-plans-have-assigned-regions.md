---
title: 'Lync Server 2013: Make sure dial plans have assigned regions'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Make sure dial plans have assigned regions
ms:assetid: 3da3a907-0dbf-4440-b12f-370f94dd4c17
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425903(v=OCS.15)
ms:contentKeyID: 48183937
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Make sure dial plans Lync Server 2013 have assigned regions

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2010-11-02_

Dial plans that are used for dial-in conferencing need to have a **Dial-in conferencing region** specified to associate dial-in conferencing access numbers with the appropriate dial plan. When you set up a dial plan, you specify the dial-in conferencing region that applies to that dial plan. Then, when you create the dial-in access number, you select the regions that associate the access number with the appropriate dial plans.

Because it important to specify a region for all dial plans, we recommend that you use this procedure to verify that all dial plans have regions. This step is optional.

Use the **Get-CsDialPlan** cmdlet to verify whether the region is set for all dial-in conferencing dial plans. If the region is missing from dial plans, you can use the **Set-CsDialPlan** cmdlet to set the region. You can also use Lync Server Control Panel to update the region in existing dial plans. For details about using Lync Server Control Panel, see [Modify a dial plan in Lync Server 2013](lync-server-2013-modify-a-dial-plan.md).

<div>

## To verify whether dial plans have the region property set

1.  Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the **Cs-VoiceAdministrator**, **Cs-ServerAdministrator**, or **CsAdministrator** role.

2.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

3.  Run the following at the command prompt:
    
        Get-CsDialPlan [-Identity <Identifier of the dial plans to be retrieved>]
    
    For example:
    
        Get-CsDialPlan
    
    In this example, all the dial plans configured for your organization are returned.

4.  Review the returned dial plans to identify any that are missing the dial-in conferencing region. For details, see the Lync Server Management Shell documentation.

</div>

<div>

## To set the region property for a dial plan

1.  Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the **Cs-VoiceAdministrator**, **Cs-ServerAdministrator**, or **CsAdministrator** role.

2.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

3.  For any dial plans that are missing the dial-in conferencing region, run:
    
        Set-CsDialPlan [-Identity <Identity of the dial plan to be modified>] -DialinConferencingRegion "<new region>"
    
    For example:
    
        Set-CsDialPlan -Identity Redmond -DialinConferencingRegion "US West Coast"
    
    In this example, the dial plan with the Identity of Redmond is modified to set the DialinConferencingRegion property to "US West Coast". For details, see the Lync Server Management Shell documentation.

</div>

</div>

<span> </span>

</div>

</div>

</div>

