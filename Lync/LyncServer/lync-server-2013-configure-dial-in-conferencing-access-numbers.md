---
title: 'Lync Server 2013: Configure dial-in conferencing access numbers'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configure dial-in conferencing access numbers
ms:assetid: d8a18030-f318-43dd-834d-70e5014b5e8a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398952(v=OCS.15)
ms:contentKeyID: 48185623
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure dial-in conferencing access numbers in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2011-07-17_

When you deploy dial-in conferencing, you need to set up phone numbers that users can dial from the public switched telephone network (PSTN) to join the audio portion of conferences. These dial-in access numbers appear in meeting invitations and on the Dial-in Conferencing Settings webpage.

Before you can create dial-in access numbers, you must first plan your dial-in conferencing regions and then configure dial plans with the regions. For details about regions, see [Dial-in conferencing requirements in Lync Server 2013](lync-server-2013-dial-in-conferencing-requirements.md) in the Planning documentation. For details about configuring dial plans for dial-in conferencing, see [Configure dial plans for dial-in conferencing in Lync Server 2013](lync-server-2013-configure-dial-plans-for-dial-in-conferencing.md).

<div>


> [!NOTE]  
> You cannot use a new dial-in access number until Active Directory Domain Services (AD&nbsp;DS) replication of that access number is complete. Replication can take several hours to complete.



</div>

<div>


> [!NOTE]  
> After you create dial-in access numbers, you can modify the display name for the Active Directory contact objects so that users can more easily identify the correct access number. Use the <STRONG>Set-CsDialInConferencingAccessNumber</STRONG> cmdlet to modify the display name. You should not modify Active Directory objects manually. For details about modifying an access number, see Lync Server Management Shell documentation for the <STRONG>Set-CsDialInConferencingAccessNumber</STRONG> cmdlet.



</div>

<div>

## In This Section

[Create or modify a dial-in conferencing access number in Lync Server 2013](lync-server-2013-create-or-modify-a-dial-in-conferencing-access-number.md)

</div>

<div>

## See Also


[Dial-in conferencing requirements in Lync Server 2013](lync-server-2013-dial-in-conferencing-requirements.md)  


[Configure dial plans for dial-in conferencing in Lync Server 2013](lync-server-2013-configure-dial-plans-for-dial-in-conferencing.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

