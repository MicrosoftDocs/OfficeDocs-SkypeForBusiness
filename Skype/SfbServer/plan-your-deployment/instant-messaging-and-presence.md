---
title: "Plan for instant messaging and presence in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 70d2151e-9382-485d-ab14-758597571a74
description: "Summary: Learn how to plan for instant messaging and presence in Skype for Business Server."
---

# Plan for instant messaging and presence in Skype for Business Server
 
**Summary:** Learn how to plan for instant messaging and presence in Skype for Business Server.
  
Plan for instant messaging and presence in Skype for Business Server. To learn about specific deployment options, such as enabling or disabling Offline Instant Messaging (IM), see [Deploy instant messaging and presence in Skype for Business Server](../deploy/im-and-presence/im-and-presence.md).
  
## Plan for instant messaging and presence in Skype for Business Server

Front End Servers provide core Skype for Business Server functionality such as instant messaging (IM) and presence and are included in every Skype for Business Server deployment. There are two editions available: Skype for Business Server Enterprise Edition, which is designed primarily for larger organizations, and Skype for Business Server Standard Edition, which is designed primarily for smaller organizations which want a smaller hardware investment and do not require full high availability options. Both editions support all Skype for Business Server workloads including IM, presence, conferencing, and Enterprise Voice.
  
Instant messaging (IM) enables your users to communicate with each other in real time on their computers using text-based messages. Both two-party and multiparty IM sessions are supported. A participant in a two-party IM conversation can add a third participant to the conversation at any time. When this happens, the Conversation window changes to support conferencing features.
  
Presence provides information to users about the status of others on the network. A user's presence status provides information to help others decide whether they should try to contact the user and whether to use instant messaging, phone, or email. Presence encourages instant communication when possible, but it also provides information about whether a user is in a meeting or out of the office, indicating that instant communication is not possible. This presence status is displayed as a presence icon in Skype for Business and other presence-aware applications, including the Microsoft Outlook messaging and collaboration client, Microsoft SharePoint technologies, and Microsoft Office. The presence icon represents the user's current availability and willingness to communicate. 
  
### Technical requirements

Instant messaging (IM) and presence always run on Enterprise Edition Front End pools and Standard Edition servers. For information on supported hardware, operating systems, and database software, see  [Certified Gateways](../../SfbPartnerCertification/certification/infra-gateways.md),  [Requirements for your Skype for Business 2015 environment](requirements-for-your-environment/requirements-for-your-environment.md), and [Infrastructure requirements for Skype for Business Server 2019](../../SfBServer2019/plan/system-requirements.md).
  
### Enabling communication with external users

You can greatly increase the benefits of your investment in Skype for Business Server by enabling your users to communicate with external users. External users can include:
  
- Remote users: Your organization's own users, when they are working outside your firewalls and are using their laptops or other Skype for Business Server devices.
    
- Federated users: Users from companies you work with who also run Skype for Business Server. To enable your users to easily contact these users, you create federated relationships with these companies. 
    
- Skype users: Skype for Business users can reach the hundreds of millions of users on Skype with IM, voice and video.
    
> [!NOTE]
> AOL, Yahoo, and Google Talk are no longer supported. 
  
> [!NOTE]
> To enable any or all of these scenarios, you need to deploy an Edge Server to help enable secure communications between your Skype for Business Server deployment and external users. Your organization's remote users and users at federated organizations will be able to see each other's presence and communicate using IM. 
  
> [!NOTE]
> Extensible Messaging and Presence Protocol (XMPP) is only supported for Unified Capabilities Collaboration Platform (UCCP) Joint Interoperability Test Command (JITC) certification scenarios. 
  
### Archiving IM content

Skype for Business Server provides features you can use if your organization must follow compliance regulations. You can use Archiving to archive the content of IM messages for all users in your organization or for only certain users that you specify. For details, see [Plan for archiving in Skype for Business Server](archiving/archiving.md). 
  
If you also have Microsoft Exchange Server 2013 deployed, you can integrate the archiving of Exchange data with the archiving of Skype for Business Server data, and use a single tool to search both types of archived data. For more information, see [Configure Skype for Business Server to use Exchange Server archiving](../deploy/integrate-with-exchange-server/use-exchange-archiving.md).
  
### Topologies and components

The only components required for instant messaging (IM) and presence are:
  
- Your organization's Front End servers (known as a pool) or a Standard Edition server. IM and presence capabilities are always enabled on these servers. For more information on Front End pool topologies and management, see [Front End Pool high availability and management](high-availability-and-disaster-recovery/high-availability.md).
    
- A load balancer, if you have an Enterprise Edition Front End pool.
    
### Supported collocation

Collocation is defined as having a single server, or group of servers, with multiple roles installed. For details on collocation, see [Topology Basics for Skype for Business Server](topology-basics/topology-basics.md). 
  

