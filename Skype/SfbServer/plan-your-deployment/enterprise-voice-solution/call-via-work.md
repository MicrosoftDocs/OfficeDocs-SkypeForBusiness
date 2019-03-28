---
title: "Plan for Call Via Work in Skype for Business Server"
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom:
ms.assetid: a33ec637-9ac8-4cb7-b3b2-88d432efc078
description: "Planning for Call Via Work in Skype for Business Server, which enables integration between Skype for Business and your PBX phone system, so that users can use Skype for Business to control their PBX phones."
---

# Plan for Call Via Work in Skype for Business Server
 
Planning for Call Via Work in Skype for Business Server, which enables integration between Skype for Business and your PBX phone system, so that users can use Skype for Business to control their PBX phones.
  
 **Call Via Work** is a new feature in Skype for Business Server which enables you to integrate your Skype for Business solution with your existing PBX phone systems. A user enabled for Call Via Work can click in Skype for Business to call another user, either within your deployment or an external user. The call is completed using the user's PBX phone. This enables a user with a PBX phone to include audio in their rich Skype for Business conversations. In previous versions of Lync Server remote call control was a feature which enabled users to control their PBX phones with Lync Server. In Skype for Business Server, this feature has been replaced with Call Via Work.
  
Call Via Work enables the following for PBX phone users
  
- Click-to-call experience, with the audio provided through the PBX phone.
    
- Presence, user search, and IM integration-- for example, two Call Via Work users in an IM session can add audio to their session, with the audio provided through the PBX phones.
    
- The ability to add IM, application sharing, and file transfer to a Call Via Work call.
    
- One-click meeting join capability
    
## How it works

Call Via Work uses Unified Communications Web API (UCWA) as the back-to-back user agent (B2BUA) between the PBX system and your Skype for Business Server deployment, so that no computer-supported telecommunications application (CSTA) gateway is needed to connect Skype for Business Server with your PBX system. UCWA is a service introduced in previous versions of Lync Server to enable connectivity with mobile and web clients, and is automatically installed on every Front End Server.
  
### Call workflow for a Call Via Work call

The following illustrates how a user enabled for Call Via Work can use the Skype for Business Server to make a call:
  
![Shows the steps during a Call Via Work call; first the caller clicks to call someone in the Skype for Business client; then the UCWA rings the caller's phone. When the caller picks up the phone, the recipient is called](../../media/050e88ed-e18e-40c0-84d5-b17fe40c305a.jpg)
  
1. The user selects a user in their Skype for Business client, and clicks the phone icon to call them. Or, during an IM conversation, the user clicks to call the user they are having the session with.
    
2. The PBX phone of the user who placed the call starts to ring. The caller ID for this phone shows a global phone number which you have set up to show in the caller ID of all users placing Call Via Work calls. This global phone number is not an actual phone number that corresponds to any one person's phone. Instead, it is a visual signal to let a user know that this is their own outgoing call, and not an incoming call happening at the same time. When you deploy Call Via Work, you should educate those users about this global phone number and what it means.
    
3. The user who placed the call picks up their PBX phone. Skype for Business then initiates the voice call to the callee. 
    
4. When the callee answers, the voice call begins. If the two users already had an IM session going, it can continue.
    
### Joining a Conference With Call Via Work

A Call Via Work user can join a scheduled meeting by clicking the meeting URL. Skype for Business then shows a **Dialing out to** message until the meeting service dials the user's PBX phone. The Call Via Work user then picks up the PBX phone and joins the meeting.
  
A Call Via Work user can also use the **Meet Now** option in Skype for Business to create Meet Now meetings. The user then sees the **Dialing out to** message, and the PBX phone rings.
  
A Call Via Work user can also dial in to a meeting by calling the Conference Bridge number from within Skype for Business. If a conference PIN is required, the user must use their PBX phone to input the PIN.
  
### Incoming Calls

When a user enabled for Call Via Work receives a Skype for Business call, the PBX phone and the user's Skype for Business clients all ring simultaneously (if the user has set up simultaneous ring). The user can accept the call either by picking up the PBX phone or clicking **Accept** on the Skype for Business notification. If the user accepts the call using Skype for Business, the Skype for Business window for the call stays open. But if the user accepts the call by picking up the PBX phone, then the Skype for Business notification window closes and there is no Skype for Business session, only the voice call over the PBX phone.
  
When a user enabled for Call Via Work receives a PBX call, only the PBX phone rings.
  
## Limitations of Call Via Work

Call Via Work is a voice solution that requires little hardware setup, but has limitations compared to the features available in full Enterprise Voice or remote call control. Call Via Work has the following limitations:
  
- If a Call Via Work user has set up call forwarding to the Call Via Work callback number, and someone tries to invite this user to a meeting by the user's phone number, the invitation will not reach the user. You should educate your users to invite participants to meetings by clicking the name, not the phone number. 
    
- Enhanced 911 capability and malicious call tracing are not available during Call Via Work calls.
    
- Users enabled for Call Via Work cannot use the delegation, team call, or response group features.
    
- Users of Call Via Work cannot use Skype for Business to record a meeting, mute or unmute the call, hold or transfer the call, or use call park.
    
- Users cannot use Call Via Work to access their PBX voicemail messages.
    
- Users of Call Via Work cannot escalate a session that started as a voice call to a collaborative meeting that includes communications such as video, Powerpoint, whiteboard, or One Note.
    
- Users of Call Via Work cannot add more users to a 2-person call.
    
- No support for deskphone pairing or VDI plugin pairing.
    
- If a user makes or answers a call using the PBX phone (and not using the Skype for Business window), there will be no log of the call.
    
- If your PBX system does not support **REFER with Replaces**, the following behavior will happen. While on a Call Via Work call, if the user transfers the ongoing call from the PBX Phone, the call window will not disappear from their Skype for Business window. If the user then closes the call window, the call between the transfer target and the transferee will end. 
    
## Prerequisites for Call Via Work

To enable any users for Call Via Work, you must have some pre-requisites in place. For more information on these prerequisites, and for steps on how to enable users for Call Via Work, see [Deploy Call Via Work in Skype for Business Server 2015](../../deploy/deploy-call-via-work.md). 
  
## See also

[Plan for remote call control in Skype for Business](remote-call-control.md)
  
[Deploy Call Via Work in Skype for Business Server 2015](../../deploy/deploy-call-via-work.md)

