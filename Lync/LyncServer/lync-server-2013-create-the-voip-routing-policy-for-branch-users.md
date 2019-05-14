---
title: 'Lync Server 2013: Create the VoIP routing policy for branch users'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Create the VoIP routing policy for branch users
ms:assetid: 10deca9f-f870-4a42-b25d-e4fc53108658
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398196(v=OCS.15)
ms:contentKeyID: 48183435
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Create the VoIP routing policy for branch users in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-23_

We recommend creating a separate voice over IP (VoIP) policy for users at branch sites. This policy should contain routes to egress from the Survivable Branch Appliance gateway or the Survivable Branch Server external gateway and backup routes to egress from a gateway at the central site. Regardless of where the user is registered, either on the Registrar on the Survivable Branch Appliance or Survivable Branch Server or on the backup Registrar cluster at the central site, the user’s VoIP policy is always in effect.

<div>

## To configure the VoIP routing policy for branch users

1.  Create a user-level dial plan and assign it to branch users. (See [Create a dial plan in Lync Server 2013](lync-server-2013-create-a-dial-plan.md) in the Operations documentation.)

2.  Assign normalization rules corresponding to the dialing habits of users at that site. If the Survivable Branch Appliance or Survivable Branch Server user fails over to the backup Registrar pool at the central site, the same dial plan will be in effect. (See [Create a dial plan in Lync Server 2013](lync-server-2013-create-a-dial-plan.md) in the Operations documentation.)

3.  Configure a voice route that egresses from the Survivable Branch Appliance gateway or the Survivable Branch Server external gateway. (See [Create a voice route in Lync Server 2013](lync-server-2013-create-a-voice-route.md) in the Operations documentation.)

4.  Set a backup call route on the Survivable Branch Appliance or Survivable Branch Server gateway to point to the backup Registrar pool (collocated with Mediation Server) at the central site. (See your Survivable Branch Appliance or Survivable Branch Server vendor documentation.)
    
    <div>
    

    > [!NOTE]  
    > This backup call route setup helps ensure that inbound calls to the branch user will work when the Survivable Branch Appliance or Survivable Branch Server is not available (for example, if it is down for maintenance). If the Registrar and Mediation Server on the Survivable Branch Appliance or Survivable Branch Server are not available, and the user is registered with the backup Registrar pool at the central site, inbound calls can still be routed to the user.

    
    </div>

**Next step**: [Configure voice mail rerouting settings in Lync Server 2013](lync-server-2013-configure-voice-mail-rerouting-settings.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

