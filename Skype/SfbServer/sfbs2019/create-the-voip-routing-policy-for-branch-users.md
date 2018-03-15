---
title: "Create the VoIP routing policy for branch users in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 10deca9f-f870-4a42-b25d-e4fc53108658
description: "We recommend creating a separate voice over IP (VoIP) policy for users at branch sites. This policy should contain routes to egress from the Survivable Branch Appliance gateway or the Survivable Branch Server external gateway and backup routes to egress from a gateway at the central site. Regardless of where the user is registered, either on the Registrar on the Survivable Branch Appliance or Survivable Branch Server or on the backup Registrar cluster at the central site, the user's VoIP policy is always in effect."
---

# Create the VoIP routing policy for branch users in Lync Server 2013
[]
We recommend creating a separate voice over IP (VoIP) policy for users at branch sites. This policy should contain routes to egress from the Survivable Branch Appliance gateway or the Survivable Branch Server external gateway and backup routes to egress from a gateway at the central site. Regardless of where the user is registered, either on the Registrar on the Survivable Branch Appliance or Survivable Branch Server or on the backup Registrar cluster at the central site, the user's VoIP policy is always in effect.
  
### To configure the VoIP routing policy for branch users

1. Create a user-level dial plan and assign it to branch users. (See [Create a dial plan in Lync Server 2013](create-a-dial-plan.md) in the Operations documentation.) 
    
2. Assign normalization rules corresponding to the dialing habits of users at that site. If the Survivable Branch Appliance or Survivable Branch Server user fails over to the backup Registrar pool at the central site, the same dial plan will be in effect. (See [Create a dial plan in Lync Server 2013](create-a-dial-plan.md) in the Operations documentation.) 
    
3. Configure a voice route that egresses from the Survivable Branch Appliance gateway or the Survivable Branch Server external gateway. (See [Create a voice route in Lync Server 2013](create-a-voice-route.md) in the Operations documentation.) 
    
4. Set a backup call route on the Survivable Branch Appliance or Survivable Branch Server gateway to point to the backup Registrar pool (collocated with Mediation Server) at the central site. (See your Survivable Branch Appliance or Survivable Branch Server vendor documentation.)
    
    > [!NOTE]
    > This backup call route setup helps ensure that inbound calls to the branch user will work when the Survivable Branch Appliance or Survivable Branch Server is not available (for example, if it is down for maintenance). If the Registrar and Mediation Server on the Survivable Branch Appliance or Survivable Branch Server are not available, and the user is registered with the backup Registrar pool at the central site, inbound calls can still be routed to the user. 
  
 **Next step**: [Configure voice mail rerouting settings in Lync Server 2013](configure-voice-mail-rerouting-settings.md)

