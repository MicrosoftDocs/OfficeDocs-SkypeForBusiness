---
title: "Move remaining users to Lync Server 2013 [OCS 2007 R2 to W15]"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 0eb990f0-f720-47a7-aaee-437fbd4c4c33
description: "You can move users to the new Lync Server 2013 deployment by using either Lync Server Control Panel or Lync Server Management Shell. You must meet some requirements to ensure a smooth transition to Lync Server 2013. For details about prerequisites to completing the procedures in this topic, see Configure clients for migration [OCS 2007 R2 to W15]. For detailed steps about moving users, see Phase 6: Move users to the pilot pool [OCS 2007 R2 to W15]."
---

# Move remaining users to Lync Server 2013 [OCS 2007 R2 to W15]
[]
You can move users to the new Lync Server 2013 deployment by using either Lync Server Control Panel or Lync Server Management Shell. You must meet some requirements to ensure a smooth transition to Lync Server 2013. For details about prerequisites to completing the procedures in this topic, see [Configure clients for migration [OCS 2007 R2 to W15]](configure-clients-for-migration-ocs-2007-r2-to-w15.md). For detailed steps about moving users, see [Phase 6: Move users to the pilot pool [OCS 2007 R2 to W15]](phase-6-move-users-to-the-pilot-pool-ocs-2007-r2-to-w15.md).
  
> [!IMPORTANT]
> You cannot use the Active Directory Users and Computers snap-in or the Microsoft Office Communications Server 2007 R2 administrative tools to move users from your legacy environment to Lync Server 2013. 
  
> [!IMPORTANT]
> The **Move-CsLegacyUser** cmdlet requires that user names are properly formed and do not have leading or trailing spaces. You cannot move a user account using the **Move-CsLegacyUser** cmdlet if it contains leading or trailing spaces. 
  
When you move a user to an Lync Server 2013 pool, the data for the user is moved to the back-end database that is associated with the new pool. 
  
> [!IMPORTANT]
> This includes the active meetings created by the legacy user. For example, if a legacy user has configured a **my meeting** conference, that conference will still be available in the new Lync Server 2013 pool, after the user has been moved. The details to access that meeting will still be the same **conference URL and conference ID**. The only difference is that the conference is now hosted in the Lync Server 2013 pool, and not in Office Communications Server 2007 R2 pool. 
  
> [!NOTE]
> Homing users on Lync Server 2013 does not require that you deploy upgraded clients at the same time. New functionality will be available to users only when they have upgraded to the new client software. 
  
### Post Migration Task

1. After you move users, verify the conferencing policy that is assigned to them. 
    
2. To ensure that meetings organized by users homed on Lync Server 2013 work seamlessly with federated users who are homed on Office Communications Server 2007 R2, the conferencing policy assigned to the migrated users should allow anonymous participants.
    
3. Conferencing policies that allow anonymous participants have **Allow participants to invite anonymous users** selected in Lync Server 2013 Control Panel and have **AllowAnonymousParticipantsInMeetings** set to **True** in the output from the **Get-CsConferencingPolicy** cmdlet in the Lync Server Management Shell. 
    
4. For details about configuring conferencing policy by using Lync Server Management Shell, see [Set-CsConferencingPolicy](set-csconferencingpolicy.md) in the Lync Server Management Shell documentation. 
    

