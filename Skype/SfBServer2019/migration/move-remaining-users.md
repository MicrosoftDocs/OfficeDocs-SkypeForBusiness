---
title: "Move remaining users"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "You can move users to the new Skype for Business Server 2019 deployment by using either Skype for Business Server Control Panel or Skype for Business Server Management Shell. You must meet some requirements to ensure a smooth transition to Skype for Business Server 2019. For details about prerequisites to completing the procedures in this topic, see Configure clients for migration. For detailed steps about moving users, see Phase 4: Move test users to the pilot pool."
---

# Move remaining users to Skype for Business Server 2019

You can move users to the new Skype for Business Server 2019 deployment by using either Skype for Business Server Control Panel or Skype for Business Server Management Shell. You must meet some requirements to ensure a smooth transition to Skype for Business Server 2019. For details about prerequisites to completing the procedures in this topic, see [Configure clients for migration](configure-clients-for-migration.md). For detailed steps about moving users, see [Phase 4: Move test users to the pilot pool](phase-4-move-test-users-to-the-pilot-pool.md).
  
> [!IMPORTANT]
> You cannot use the Active Directory Users and Computers snap-in or the legacy administrative tools to move users from your legacy environment to Skype for Business Server 2019. 
  
When you move a user to a Skype for Business Server 2019 pool, the data for the user is moved to the back-end database that is associated with the new pool. 
  
> [!IMPORTANT]
> This includes the active meetings created by the legacy user. For example, if a legacy user has configured a **my meeting** conference, that conference will still be available in the new Skype for Business Server 2019 pool after the user has been moved. The details to access that meeting will still be the same **conference URL and conference ID**. The only difference is that the conference is now hosted in the Skype for Business Server 2019 pool, and not in the legacy pool. 
  
> [!NOTE]
> Homing users on Skype for Business Server 2019 does not require that you deploy upgraded clients at the same time. New functionality will be available to users only when they have upgraded to the new client software. 
  
### Post migration task

1. After you move users, verify the conferencing policy that is assigned to them. 
    
2. To ensure that meetings organized by users homed on Skype for Business Server 2019 work seamlessly with federated users who are homed on legacy install, the conferencing policy assigned to the migrated users should allow anonymous participants.
    
3. Conferencing policies that allow anonymous participants have **Allow participants to invite anonymous users** selected in Skype for Business Server 2019 Control Panel and have **AllowAnonymousParticipantsInMeetings** set to **True** in the output from the **Get-CsConferencingPolicy** cmdlet in the Skype for Business Server Management Shell. 
    
<!-- 4. For details about configuring conferencing policy by using Skype for Business Server Management Shell, see 
 [Set-CsConferencingPolicy](../../lync-server-management-shell/lync-server-2013-cmdlets-by-category/set-csconferencingpolicy.md) in the Skype for Business Server Management Shell documentation.  -->
    

