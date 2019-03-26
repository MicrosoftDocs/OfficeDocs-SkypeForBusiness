---
title: Move remaining users to Lync Server 2013
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Move remaining users to Lync Server 2013
ms:assetid: 72025e1b-97d1-40e9-8a98-28c018942b48
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ688090(v=OCS.15)
ms:contentKeyID: 49733689
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Move remaining users to Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-29_

You can move users to the new Lync Server 2013 deployment by using either Lync Server Control Panel or Lync Server Management Shell. You must meet some requirements to ensure a smooth transition to Lync Server 2013. For details about prerequisites to completing the procedures in this topic, see [Configure clients for migration](configure-clients-for-migration.md). For detailed steps about moving users, see [Phase 4: Move test users to the pilot pool](phase-4-move-test-users-to-the-pilot-pool.md).

<div>


> [!IMPORTANT]  
> You cannot use the Active Directory Users and Computers snap-in or the Lync Server 2010 administrative tools to move users from your legacy environment to Lync Server 2013.



</div>

When you move a user to an Lync Server 2013 pool, the data for the user is moved to the back-end database that is associated with the new pool.

<div>


> [!IMPORTANT]  
> This includes the active meetings created by the legacy user. For example, if a legacy user has configured a <STRONG>my meeting</STRONG> conference, that conference will still be available in the new Lync Server 2013 pool after the user has been moved. The details to access that meeting will still be the same <STRONG>conference URL and conference ID</STRONG>. The only difference is that the conference is now hosted in the Lync Server 2013 pool, and not in the Lync Server 2010 pool.



</div>

<div>


> [!NOTE]  
> Homing users on Lync Server 2013 does not require that you deploy upgraded clients at the same time. New functionality will be available to users only when they have upgraded to the new client software.



</div>

<div>

## Post Migration Task

1.  After you move users, verify the conferencing policy that is assigned to them.

2.  To ensure that meetings organized by users homed on Lync Server 2013 work seamlessly with federated users who are homed on Lync Server 2010, the conferencing policy assigned to the migrated users should allow anonymous participants.

3.  Conferencing policies that allow anonymous participants have **Allow participants to invite anonymous users** selected in Lync Server 2013 Control Panel and have **AllowAnonymousParticipantsInMeetings** set to **True** in the output from the **Get-CsConferencingPolicy** cmdlet in the Lync Server Management Shell.

4.  For details about configuring conferencing policy by using Lync Server Management Shell, see [Set-CsConferencingPolicy](https://docs.microsoft.com/powershell/module/skype/Set-CsConferencingPolicy) in the Lync Server Management Shell documentation.

</div>

</div>

<span> </span>

</div>

</div>

</div>

