---
title: "Plan for dial-in conferencing in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: ea024a26-37b3-410e-961b-83ab85c07540
description: "Summary: Read this topic to learn about planning for dial-in conferencing in Skype for Business Server."
---

# Plan for dial-in conferencing in Skype for Business Server
 
**Summary:** Read this topic to learn about planning for dial-in conferencing in Skype for Business Server.
  
Dial-in conferencing is an optional feature of Skype for Business Server that allows meeting attendees to join the audio portion of a meeting by calling in to the meeting from a phone. Dial-in conferencing is a subset of audio conferencing and requires additional configuration. This topic describes what you need to think about before deploying dial-in conferencing for your organization. 
  
Some of the components required for dial-in conferencing are specific to dial-in conferencing and some are Enterprise Voice components. Although dial-in conferencing uses some of the same components that Enterprise Voice uses, you can deploy dial-in conferencing even if you do not deploy Enterprise Voice. This section describes the components that are needed for dial-in conferencing. For more information about planning a complete Enterprise Voice solution, see [Plan your Enterprise Voice solution in Skype for Business Server](../../plan-your-deployment/enterprise-voice-solution/enterprise-voice-solution.md).
  
Dial-in conferencing requires that you provide connectivity to the public switched telephone network (PSTN) by deploying a Mediation Server. In addition to deploying a Mediation Server, you need to consider the following to allow dial-in conferencing for your organization:
  
- Your plan for connecting to the public switched telephone network (PSTN)
    
- Your plan for dial plans, access numbers, and conferencing regions
    
- Your plan for creating conferencing directories
    
- Your conferencing policy for allowing dial-in access
    
- Support for enterprise and anonymous users
    
> [!NOTE]
> If you deploy dial-in conferencing, you must deploy it in every pool where you deploy Skype for Business Server conferencing. You do not need to assign access numbers--the numbers participants call to join a conference--in every pool, but you must deploy the dial-in feature in every pool. This requirement supports the recorded name feature when a user calls an access number from one pool to join a Skype for Business Server conference in a different pool. 
  
## Plan for PSTN connectivity

Dial-in conferencing requires at least one Mediation Server and at least one public switched telephone network (PSTN) gateway. 
  
You can deploy a Mediation Server in a central site or in a branch site. In a central site, you can collocate a Mediation Server on a Front End pool or Standard Edition server, or you can deploy it on a stand-alone server or pool. In a branch site, you can deploy a Mediation Server on a stand-alone server or as a component of the Survivable Branch Appliance.
  
You can deploy a PSTN gateway in a central site or in a branch site. In a branch site, the PSTN gateway can be stand-alone or a component of the Survivable Branch Appliance.
  
For details about Mediation Server and PSTN gateway requirements, see [Mediation Server component in Skype for Business Server](../../plan-your-deployment/enterprise-voice-solution/mediation-server.md), [Deploy a Mediation Server in Topology Builder in Skype for Business Server](../../deploy/deploy-enterprise-voice/deploy-a-mediation-server.md), and [Define a gateway in Topology Builder in Skype for Business Server](../../deploy/deploy-enterprise-voice/define-a-gateway.md).
  
## Plan for dial plans, access numbers, and conferencing regions

To configure dial-in conferencing, you create dial plans and dial-in conferencing access numbers. You also specify the dial-in regions that associate a dial-in conferencing access number with its dial plans. More specifically:
  
- Dial plans are sets of normalization rules that specify the number and pattern of digits in a phone number, and translate the phone number into the standard E.164 format required for call routing.
    
- Dial-in conferencing access numbers are the numbers participants call to join a conference.
    
- Every dial-in conferencing access number must be associated with at least one dial plan. 
    
- Every dial plan is associated with a conferencing region.
    
When you create a dial plan, you specify the dial-in conferencing region that applies to the dial plan. When you create the dial-in access number, you select the regions that associate the access number with the appropriate dial plans.
  
You also specify the scope of the dial plan: user scope, pool scope, or site scope. Every user is assigned the dial plan from the narrowest scope that applies to the user. For example, a user is assigned a user-level dial plan, if one applies. If a user-level dial plan does not apply, the user is assigned a pool-level dial plan. If a pool-level dial plan does not apply, the user is assigned a site-level dial plan. If a site-level dial plan does not apply, the user is assigned the global dial plan. 
  
Before you configure the dial plans, is it important to plan how you want to name and use regions. The following considerations apply to dial-in conferencing regions:
  
- A region is typically a geographical area that is associated with an office or group of offices.
    
- Languages are associated with dial-in access numbers. If you support geographical areas that have multiple languages, you should decide how you want to define regions to support the multiple languages. For example, you might define multiple regions based on a combination of geography and language, or you might define a single region based on geography and have a different dial-in access numbers for each language.
    
- When a user schedules a meeting, by default the meeting uses the region specified by that user's dial plan.
    
- By default, all of the dial-in access numbers for the region are included in the meeting invitation.
    
- It is important to name regions so that they are clearly recognizable. The user can use the names of the regions to change a meeting's region so that different access numbers are included in the invitation. (When users use Outlook to schedule a meeting, the user uses the Online Meeting Add-in for Skype for Business to change the region).
    
- Regions should be designed so that any invitee who wants to dial into a conference can see a local access number in the conference invitation.
    
- You can configure the order in which access numbers within a region appear on the Dial-in Conferencing Settings page (and, therefore, the order in which they appear in the conference invitation) by using Skype for Business Server Management Shell cmdlets.
    
- Any user from any location can call any dial-in access number to join a conference.
    
For more information about creating a dial plan, see [Create or modify a dial plan in Skype for Business Server](../../deploy/deploy-enterprise-voice/dial-plans.md) and [Create or modify a normalization rule in Skype for Business](../../deploy/deploy-enterprise-voice/normalization-rules.md). 
  
## Plan for conference directories

Conference directories maintain a mapping between the alphanumeric meeting ID that a participant uses to join a conference when using Skype for Business, and the numeric-only conference ID that a dial-in conferencing participant uses to join the conference. The format of the conference ID is as follows:
  
```
<housekeeping digit (1 digit)><conference directory (usually 1-2 digits)><conference number (variable number of digits><check digit (1 digit)>
```

Creating multiple conference directories will ensure that conference IDs will stay short until a significant amount of conferences have been created. In an organization with a typical number of conferences per user, we recommend that you create one conference directory for every 999 users in the pool. Using this guideline, the conference IDs can generally be kept small. However, once the number of conference directories (across the pools) exceed 9, the Conference ID number will grow to support additional conferences.
  
## Plan for a conferencing policy that allows dial-in access

Conferences must be enabled for dial-in access when you configure conferencing policies. By default, conferences that are enabled for dial-in access include the following information in the conference invitation:
  
- A numeric conference ID that identifies the conference
    
- One or more PSTN access numbers
    
- A link to a Dial-in Conferencing Settings page, which contains a complete list of access numbers with their associated languages; a place to create, reset, or unblock personal identification numbers (PINs); and other information, such as dual-tone multi-frequency (DTMF) controls
    
For more information about conferencing policies, see [Configure dial-in conferencing in Skype for Business Server](../../deploy/deploy-conferencing/dial-in-conferencing.md) and [Manage conferencing policies in Skype for Business Server](../../manage/conferencing/conferencing-policies.md).  

## Support for enterprise and anonymous users

Dial-in conferencing supports both enterprise and anonymous users. Enterprise users have Active Directory Domain Services credentials and Skype for Business Server accounts within their organization. Anonymous users do not have enterprise credentials within your organization. In the dial-in conferencing context, a user in a federated partner's organization who uses the PSTN to connect to a conference is treated like an anonymous user. For dial-in conferencing, unlike other contexts, federated users are not authenticated.
  
Enterprise users or conference leaders who join a conference that is enabled for dial-in access dial one of the conference access numbers and then are prompted to enter the conference ID. If a leader has not yet joined the meeting, users can either enter their unified communications (UC) extension (or full phone number) and PIN or wait to be admitted by a leader. The Meeting organizer can join the meeting as a leader by entering just their PIN. The Front End Server uses the combination of full phone number or extension, and PIN, to uniquely map enterprise users to their Active Directory credentials. As a result, enterprise users are authenticated and identified by name in the conference. Enterprise users can also assume a conference role predefined by the organizer.
  
> [!NOTE]
> Enterprise users who dial in from an office IP phone or from Skype for Business Server Attendant are not prompted for their phone number because they are already authenticated. 
  
Anonymous users who want to join a dial-in conference dial one of the conference access numbers and then they are prompted to enter the conference ID. Unauthenticated anonymous users are also prompted to record their name. The recorded name identifies unauthenticated users in the conference. Anonymous users are not admitted to the conference until at least one leader or authenticated user has joined, and they cannot be assigned a predefined role.
  
> [!NOTE]
> Enterprise users who choose not to enter their phone number and PIN are not authenticated. They are prompted to record their name and are treated as anonymous users in the conference. 
  
When scheduling a meeting, the meeting organizer can choose to restrict access to the meeting by making the meeting closed or locked. In this case, dial-in users are requested to authenticate. 
  
- If dial-in users fail or choose not to authenticate, they are transferred to the lobby where they until a leader accepts or rejects them, or they time out and are disconnected.
    
- After they are admitted to a conference, dial-in users can participate in the audio portion of the conference and can exercise dual-tone multi-frequency (DTMF) commands by using the phone keypad.
    
- Dial-in leaders can exercise DTMF commands to turn participants' ability to unmute on or off, lock or unlock the conference, admit people from the lobby, and turn entry and exit announcements on or off.
    
- Leaders can also use a DTMF command to admit everyone from the lobby, which changes the permissions of the meeting to allow anyone who subsequently joins. 
    
- All dial-in participants can exercise DTMF commands to hear Help, listen to the conference roster, and mute themselves.
    
- Dial-in participants (that is, whether or not they dial from the PSTN) hear personal announcements during the conference, such as whether they have been muted or unmuted, whether the meeting is being recorded, or whether someone is waiting in the lobby.
    
    > [!NOTE]
    > Participants who join the conference by clicking a link instead of dialing in do not hear personal announcements. 
  

