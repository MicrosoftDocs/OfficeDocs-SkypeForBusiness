---
title: "<topic title>"
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
description: "A Discussion of the available hybrid solutions in Skype for Business Server 2019."
---

# <Topic title>

[!INCLUDE [disclaimer](../disclaimer.md)]

PLACEHOLDER TOPIC FOR HYBRID SOLUTIONS 

IN PROGRESS...


You might also be familiar with the term "hybrid voice"—which refers to on-premises voice trunks that provide functionality to users homed in the cloud. Hybrid voice enables migration to the cloud while preserving on-premises voice configuration. If you already have a Skype for Business Server deployment, the first step to enable hybrid voice is to configure a split domain environment. 
  
For example, assume your company has a large mobile field support organization that requires minimal PBX voice, but extensive smart phone use. You might choose to move these users to the cloud to take advantage of Microsoft's Phone System in Office 365 (Cloud PBX). If your company also has a large on-premises call center that requires advanced, complex contact center software as part of your on-premises PBX, you might choose to leave these users on premises. Users homed online and on premises both have PSTN connectivity through your on-premises deployment.
  
The following diagram shows a Skype for Business hybrid voice deployment:
  
![SfB split domain with Cloud PBX](../../sfbserver/media/5e755772-269e-45ce-8b48-2e06ababfe6c.png)
  
For more information about setting up a hybrid voice solution with your Skype for Business Server deployment, see [Plan Phone System in Office 365 with on-premises PSTN connectivity in Skype for Business Server](../../sfbserver/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-phone-system-with-on-premises-pstn-connectivity.md). 
  
You can also configure hybrid deployments for integration with on-premises Exchange and SharePoint, or with Microsoft Office 365 applications, including Exchange Online and SharePoint Online. You can also configure a hybrid voice solution that does not require a full Skype for Business Server deployment by using Cloud Connector Edition. For more information about all Skype for Business hybrid solutions and planning your move to the cloud, see [Skype for Business hybrid solutions](hybrid-solutions.md).


## Exchange co-existence
<a name="BKMK_Exchange"> </a>

To support co-existence with Exchange, keep the following in mind:
  
- The best practice is to move the user's mailbox to Exchange Online before moving the user's Skype for Business home.
    
- Users with Exchange mailboxes on premises are supported with following known limitations:
    
  - Client sign on: Users may need to sign on twice during SfB client sign on
    
  - Server side conversation history, Archiving, Unified Contact Store, HighRes Photo requires Exchange 2013 or later, and you must enable OAuth Server to Server communication. For more information, see [Manage server-to-server authentication (OAuth) and partner applications in Skype for Business Server 2015](https://technet.microsoft.com/en-us/library/jj204817.aspx).
    
For details on co-existence with Exchange Server, including support criteria and limitations in various combinations of on-premises and online, see [Feature support](../../sfbserver/plan-your-deployment/integrate-with-exchange/integrate-with-exchange.md#feature_support) in [Plan to integrate Skype for Business and Exchange](../../sfbserver/plan-your-deployment/integrate-with-exchange/integrate-with-exchange.md).



**TERMINOLOGY**

ou'll learn more about Active Directory configuration in the sections that follow. But first, an overview of the terminology and acronyms used in the diagrams below, and in many of the hybrid connectivity topics:
  
- PSTN - Public Switched Telephone Network
    
- PBX - Private Branch Exchange phone system
    
- Phone System - Microsoft's Cloud PBX phone system offering
    
- Trunk - Telephony line that connects PBXs to the PSTN—A trunk might use Session Initiation Protocol (SIP)—A Voice over Internet Protocol (VoIP)—or the older Time-Division Multiplexing (TDM) technology 
    
- SBC - Session Border Controller - Device that serves as a firewall and router in telephony networks. For example, provides security, connectivity, interoperability, and Quality of Services. 
    
- PSTN gateway - A device that serves as a router in telephony networks, capable of doing most of what an SBC can do except security and NAT traversal.
    
The following diagram shows a Skype for Business "split domain" hybrid configuration. Users A and B are homed online but are discoverable by on-premises users; users C and D are homed on premises, but are discoverable by online users.
  

