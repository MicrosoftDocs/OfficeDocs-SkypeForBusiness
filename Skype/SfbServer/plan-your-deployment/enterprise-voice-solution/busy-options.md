---
title: "Plan for Busy Options for Skype for Business Server"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- Strat_SB_Admin
ms.custom:
ms.assetid: 5f85c6bc-a962-4283-971c-4380d83b3a66
description: "Read about the Busy Options feature in Skype for Business Server."
---

# Plan for Busy Options for Skype for Business Server
 
Read about the Busy Options feature in Skype for Business Server.
  
Busy Options is a new voice policy introduced in the July 2016 Cumulative Update that allows you to configure how incoming calls are handled when a user is already in a call or conference, or has a call placed on hold. New or incoming calls can be rejected with a busy signal or forwarded to voice mail. 
  
The Busy Options policy is supported for failover and disaster recovery on paired Front End Pools and Survivable Branch Servers (SBS).
  
This topic describes the features of Busy Options. For information about how to install and configure Busy Options, see [Install and configure Busy Options for Skype for Business Server](../../deploy/deploy-enterprise-voice/install-and-configure-busy-options.md).
  
## Configuration options

If Busy Options is enabled for the organization, all users in your organization, both Enterprise Voice and non-Enterprise Voice users, can use the following features:
  
- Busy on Busy - In which new incoming calls will be rejected with a busy signal if the user is busy.
    
- Voicemail on Busy - In which new incoming calls will be forwarded to voice mail if the user is busy.
    
The Busy Options feature provides failover capability. If a problem occurs and users fail over to another Front End Server or to another pool in Skype for Business Server, their Busy Options settings will be preserved.
  
Regardless of how their busy options are configured, users in a call or conference, or those with a call on hold, are not prevented from initiating new calls or conferences. 
  
After configuration, the Busy Options setting is in effect for all the user's Skype for Business call devices and clients. Based on the user's Busy Options settings, the call that is rejected or sent to voice mail would not ring on any of the user's call devices--including Macintosh, Windows Desktop, mobile clients, or IP phones--on which the user is signed in. 
  
Users will see missed-call notifications on their Skype for Business clients and devices, and they will be notified by email as well. Callers whose call was rejected due to Busy on Busy will see a notification in their Skype for Business client stating that the user they attempted to reach is busy on another call.
  
You can configure the Busy Options feature by using Skype for Business PowerShell cmdlets to:
  
- Enable or disable Busy Options Voice policy for the Enterprise.
    
- Administer Busy on Busy or Voicemail on Busy for all the users in the Enterprise.
    
- Administer Busy on Busy or Voicemail on Busy for all the users homed in a particular Front End pool.
    
- Administer Busy on Busy or Voicemail on Busy for a list of users.
    
- Administer Busy on Busy or Voicemail on Busy for a single user.
    
## Interoperability with Voice applications

Busy Options provides interoperability with the following Voice applications in Skype for Business:
  
- Response Groups (RGS)
    
  - Busy Options set on Response Group numbers will be ignored by the system; multiple concurrent calls will be allowed. 
    
  - The current Attendant routing experience in Response Groups will remain unchanged for the Agents with Busy Options settings.
    
  - The calls coming from Response Groups to the users who are Response Groups Agents will not be throttled by Busy Options settings and the current RGS experience will be maintained.
    
  - The non-RGS related calls to the Agents will be honored by their Busy Options settings.
    
- Team Call
    
  - Incoming calls to users who are set up for a Team Call will be prioritized to ignore Busy on Busy and Voicemail on Busy settings.
    
  - The current Team Call experience will remain unchanged with Busy Options set for the users.
    
  - The non-Team Call related calls to such users will be honored by their Busy Options settings.
    
- Boss/Admin Delegation 
    
  - Incoming calls to users who are set up for a Boss/Admin Delegation either as Boss or an Admin will be prioritized to ignore Busy on Busy and Voicemail on Busy settings.
    
  - The current Boss/Admin Delegation experience will remain unchanged with Busy Options set for the Admins or Boss.
    
  - The non-Boss/Admin Delegation related calls to Admins will be honored by their Busy Options settings.
    
- Shared Line Appearance 
    
  - Busy Options settings on user accounts set up for Shared Line Appearance will be ignored. 
    
  - Shared Line Appearance's native Busy on Busy and Voicemail on Busy options will be honored instead.
    
- Call Parking Service 
    
  - Parked calls that were not retrieved and are ringing back due to timing out will be allowed to ring though to the user who parked the call by the Busy Options. 
    
- Call Conferencing
    
  - Users in conference calls are considered Busy and new incoming calls will be rejected with a busy signal or forwarded to voice mail according to their Busy Options settings.
    
  - Users in conferences are not prevented from initiating new calls or conferences by Busy Options.
    
  - Users in conferences are still able to receive new conference invitations, but new peer-to-peer calls will be rejected according to their Busy Options settings.
    
- Simultaneous Ring and Call Forwarding
    
    The Busy on Busy feature is not designed to work with Simultaneous Ring and Call Forwarding.
    

