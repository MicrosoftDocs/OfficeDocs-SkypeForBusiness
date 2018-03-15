---
title: "Planning for remote call control in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 688a0328-1aa7-449f-b5f7-98c876112ed2
description: "In Lync Server 2013, support for remote call control scenarios enables users to control their private branch exchange (PBX) phones by using Lync 2013 on their desktop computers. This section describes remote call control features and requirements for deploying remote call control."
---

# Planning for remote call control in Lync Server 2013
[]
In Lync Server 2013, support for remote call control scenarios enables users to control their private branch exchange (PBX) phones by using Lync 2013 on their desktop computers. This section describes remote call control features and requirements for deploying remote call control.
  
Integration between a PBX and Lync Server 2013 makes it possible for users enabled for remote call control to use the Lync 2013 user interface (UI) to control calls on their PBX phones in the following ways:
  
> [!NOTE]
> Ultimately, the capabilities of the PBX that hosts a user's PBX phone determine the remote call control features that will be available to that user. 
  
- Make an outgoing call
    
- Answer an incoming call
    
- Answer an incoming call with an instant message
    
    > [!NOTE]
    > That is, when the caller's phone number can be associated with an instant message address in your organization's global address list (GAL), in the callee's Lync Contacts list, or in a federated partner's organization. 
  
- Transfer a call
    
- Forward an incoming call
    
- Place calls on hold
    
- Alternate between multiple concurrent calls
    
- Answer a second call while already in a call (that is, call waiting)
    
- Dial dual-tone multifrequency (DTMF) digits
    
- In the Conversation window, type notes in Microsoft Office OneNote note-taking program
    
Additionally, when a user is enabled for remote call control, Lync 2013 provides the user with the following call information:
  
- Identification of a caller by name when the caller's phone number exists in the Contacts list of a remote call control-enabled user's Microsoft Office Outlook messaging and collaboration client, Lync Contacts list, or your organization's GAL.
    
- Past incoming and outgoing calls, which are saved in the Conversation History folder in Outlook.
    
- Missed call notifications, which are sent to the user's Outlook Inbox folder, but are generated only if Lync is running when the incoming call is received.
    
## Remote Call Control and Enterprise Voice

Although remote call control features are separate from Enterprise Voice features and users cannot be enabled for both, Enterprise Voice provides a subset of features that are also available to users who are enabled for remote call control. If Enterprise Voice is deployed, users who are enabled for remote call control can use Lync to access the following Enterprise Voice features:
  
- Make and receive audio calls to another Lync client
    
- Join the audio portion of a conference created by a user who is enabled for Enterprise Voice
    
## In This Section

- [Deployment tasks for remote call control in Lync Server 2013](deployment-tasks-for-remote-call-control.md)
    

