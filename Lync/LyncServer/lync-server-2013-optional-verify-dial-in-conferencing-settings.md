---
title: 'Lync Server 2013: (Optional) Verify dial-in conferencing settings'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: (Optional) Verify dial-in conferencing settings
ms:assetid: a85efdda-97b0-4f3b-bd26-04416bee8ef5
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412789(v=OCS.15)
ms:contentKeyID: 48185027
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# (Optional) Verify dial-in conferencing settings in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2010-11-02_

As final verification of your dial-in conferencing configuration, you can search for dial plans that have a dial-in conferencing region that is not used by any access number and for access numbers that have not specified a dial-in conferencing region. This step is optional.

<div>

## To find dial plans with a dial-in conferencing region that is not used by an access number

1.  Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the **Cs-ServerAdministrator** or **CsAdministrator** role.

2.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

3.  Run the following at the command prompt:
    
        Get-CsDialinConferencingAccessNumber -EmptyRegion
    
    This cmdlet returns all of the dial plans that have a dial-in conferencing region that is not used by an access number.

</div>

<div>

## To find access numbers without assigned regions

1.  Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the **Cs-ServerAdministrator** or **CsAdministrator** role.

2.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

3.  Run the following at the command prompt:
    
        Get-CsDialinConferencingAccessNumber -Region NULL
    
    This cmdlet returns all the dial-in conferencing access numbers that are not associated with a region.

</div>

</div>

<span> </span>

</div>

</div>

</div>

