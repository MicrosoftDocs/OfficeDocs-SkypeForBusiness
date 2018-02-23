---
title: "Plan for Edge Server deployments in Skype for Business Server 2015"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 8/17/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.collection: IT_Skype16
ms.custom: Strat_SB_Hybrid
ms.assetid: 9cdc3e23-3f6a-4e4d-9e04-f038596b6700
description: "Summary: Plan for your Skype for Business Server 2015 Server Edge environment. This topic introduces you to Edge concepts and lets you get organized with our more in-depth topics."
---

# Plan for Edge Server deployments in Skype for Business Server 2015
[]
 **Summary:** Plan for your Skype for Business Server 2015 Server Edge environment. This topic introduces you to Edge concepts and lets you get organized with our more in-depth topics.
  
When you have a Skype for Business Server 2015 environment that's working well internally, the next step for you might be to introduce an Edge Server or an Edge pool to the environment. This role would be vital if you want the services provided by Skype for Business Server 2015 to be used by people who are outside your internal network. These can potentially include:
  
- Remote Users: Employees who are offsite, either temporarily or in an ongoing way.
    
- Federated Users: Your partner organizations' employees.
    
- Mobile Users.
    
- Potential customers, partners and even anonymous users you want to invite to meetings and presentations.
    
External User Access, which is what Edge Servers provide, allow all this to happen. Your internal users will be able to enjoy the following services that are hosted by your Skype for Business Server 2015 deployment:
  
- IM and presence for communication: Authorized external users can join in IM conversations and conferences. They can get presence information for other users (who get their presence info too). You won't be able to do multiparty conferences if you're using a public IM provider, that's strictly peer-to-peer communication. But both SIP and XMPP protocols are supported.
    
- Audio/video (A/V) conferencing: Authorized external users can participate in your Skype for Business Server 2015 audio and video conferences.
    
- Web conferencing: Your authorized external users can participate in your Skype for Business conferences. You can also enable participation for remote users, federated users, and anonymous users if you'd like. Public IM users can't participate in conferences. There are also options to let these users participate in application and desktop sharing, and even act as meeting organizers or presenters.
    
Mobile device access is supported, as is Enterprise Voice. You can invite external users to those meetings you wish them to attend, even anonymous users, if you want to give permissions to them.
  
If this sounds like something your organization needs, then planning for an Edge environment's going to be a big help in deploying it. For further reading, we have the topics listed below.
  
## Planning topics:

The planning articles are:
  
- [Edge Server system requirements in Skype for Business Server 2015](system-requirements.md)
    
- [Edge Server environmental requirements in Skype for Business Server 2015](edge-environmental-requirements.md)
    
- [Edge Server scenarios in Skype for Business Server 2015](scenarios-0.md)
    

