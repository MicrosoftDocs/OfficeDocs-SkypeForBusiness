---
title: "Capacity planning for Persistent Chat Server in Skype for Business Server 2015"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 2/23/2018
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.assetid: 7a850cd5-c789-4795-a8ff-083be21ae784
description: "Summary: Read this topic to learn about capacity planning for Persistent Chat Server in Skype for Business Server 2015."
---

# Capacity planning for Persistent Chat Server in Skype for Business Server 2015
 
**Summary:** Read this topic to learn about capacity planning for Persistent Chat Server in Skype for Business Server 2015.
  
Persistent Chat Server can perform multi-user, real-time chat that can persist for future retrieval and search. Unlike group instant messaging (IM) that is saved in a user's mailbox if conversation history is configured, a Persistent Chat Server session stays open longer, and the content is saved on a server, along with the messages, files, URLs, and other data that are part of an ongoing conversation.
  
Capacity planning is an important part of preparing to deploy Persistent Chat Server. This topic provides capacity planning tables that you can use to determine the best configuration for your deployment. It also describes how to best manage Persistent Chat Server deployments that require greater capacity at peak times.
  
Before reading this section, you should be familiar with Persistent Chat topologies. For more information, see [Plan Persistent Chat Server topology](topology.md).

> [!NOTE] 
> Persistent chat is available in Skype for Business Server 2015 but is no longer supported in Skype for Business Server 2019. The same functionality is available in Teams. For more information, see [Getting started with your Microsoft Teams upgrade](/microsoftteams/upgrade-start-here). If you need to use Persistent chat, your choices are to either migrate users requiring this functionality to Teams, or to continue using Skype for Business Server 2015. 
  
## Persistent Chat Server capacity planning

The following tables can help you with capacity planning for Persistent Chat Server by modeling how various Persistent Chat Server settings affect capacity.
  
- Plan capacity for number of users
    
- Plan capacity for chat room access
    
- Plan capacity for chat room access by invitation
    
- Plan capacity for performance
    
### Plan capacity for number of users for Persistent Chat Server

Use the following sample table to determine the number of users you will be able to support.
  
**Persistent Chat Server pool maximum capacity sample**

- Active Persistent Chat service instances:  4  <br/> 
- Persistent Chat service instances: 8 (a maximum of 4 can be active; 4 must be inactive)  <br/>
- Active users connected: 80,000  <br/>
- Total provisioned users: 150,000  <br/>
- Number of endpoints: 120,000  <br/>
   
In the preceding sample, the plan is to support the maximum number of users that Persistent Chat Server allows: four servers/instances of the Persistent Chat service (can have four more passive servers running Persistent Chat Server for high availability and disaster recovery) and 20,000 users per server, for a total of 80,000 active users.
  
### Plan capacity for chat room access

The following sample table can help you plan for managing chat room access in a Persistent Chat Server pool.
  
**Managing chat room access sample**

|&nbsp;|Small Chat Rooms|Medium Chat Rooms|Large Chat Rooms|Total|
|:-----|:-----|:-----|:-----|:-----|
|Size of chat rooms (number of users connected)   |30 per room   |150 per room   |16,000 per room   ||
|Chat rooms   |32,000   |1,067   |10   |33,077   |
|% of rooms that are auditorium   |1%   |1%   |50%   ||
|% of rooms that are open   |3%   |3%   |50%   ||
|Open rooms (no explicit membership)   |960   |32   |5   |997   |
|Non-open rooms (regular rooms with explicit membership)   |31,040   |1.035   |5   |32,080   |
|Auditorium rooms (additional presenters entry)   |0   |32   |5   ||
|Rooms managed by direct membership   |50%   |10%   |0%   ||
|Rooms managed by user groups   |50%   |90%   |100%   ||
|User groups in each chat room's membership list for open rooms (not specified explicitly)   |0   |0   |0   ||
|Users in each chat room's membership list for non-open rooms   |30   |150   |16,000   ||
|User groups in each chat room's membership list for non-open rooms   |3   |5   |10   ||
|Users and user groups in each chat room's manager list (for open and non-open rooms)   |6   |6   |6   ||
|Users and user groups in each auditorium chat room's presenters list (for open and non-open rooms)   |6   |6   |6   ||
|User-based membership entities across all non-open rooms   |465,600   |15,520   |-   ||
|User-group-based membership entities across all non-open rooms   |46,560   |4656   |50   ||
|Users and user groups based entities across all auditorium chat rooms   |0   |192   |50   ||
|Users and user groups based manager entities across all chat rooms manager lists   |192,000   |6,400   |60   ||
|Active users per chat room   |30   |150   |16,000   ||
|Chat rooms per user   |12   |2   |2   |16   |
|User groups in each chat room's membership list   |10   |10   |15   ||
|Rooms managed by user groups   |50%   |50%   |50%   ||
|User-group-based membership entities across all chat rooms   |155,200   |5173   |68   ||
|User-based membership entities across all chat rooms   |465,600   |77,600   |72,000   ||
|Users and user groups in each chat room's manager, presenter, and scope lists   |6   |6   |6   ||
|Users and user groups across all chat rooms' manager, presenter, and scope lists   |192,000   |6400   |60   ||
|Access control entries   |704,160   |26,768   |160   |731,088   |
|Maximum access control entries   ||||2,000,000   |
   
In the preceding sample, when you deploy the Persistent Chat Servers according to the recommended guidelines, they can handle up to 80,000 active users across a four-server pool with compliance enabled.
  
This sample shows chat rooms categorized as small (30 active users at any given time), medium (150 active users), and large (16,000 active users). The supported number of chat rooms of a certain size in the table above is computed based on the total number of:
  
- Active users in the system
    
- Active users in chat rooms of the given size
    
- Chat rooms of the given size that a single user joins
    
For each chat room, the preceding capacity planning table specifies the number of access control entries that are associated with the chat room, including entries that are assigned directly to the chat room. You can control access to individual chat rooms by using access control lists (ACLs). You can also control access at the category level. In an ACL, an individual access control entry can be either a user group—for example, a security group, a distribution list, or a single user. You can define access control entries for chat room managers, presenters, and members.
  
> [!IMPORTANT]
> In planning your strategy for managing chat rooms, keep in mind that the total number of allowed access control entries is 2 million. If the calculated access control entries exceed 2 million, server performance could degrade significantly. To avoid this issue, whenever possible, be sure that your access control entries are user groups instead of individual users. 
  
### Plan capacity for managing chat room access by invitation

You can use the following capacity planning table to understand the number of invitations that Persistent Chat Server creates and stores in the Persistent Chat database when it is configured to send invitations. You manage invitations on the Category by using the **Chat Room Category settings** page in the Skype for Business Server Control Panel, or by using the Windows PowerShell cmdlet, **set-csPersistentChatCategory**. You can manage invitations on a chat room (in line with what the category allows) by using the **Room Management** page launched from the Skype for Business client, or by using a Windows PowerShell cmdlet, **set-csPersistentChatRoom**.
  
The sample data in the following table assumes that, on the **Chat room settings** page for 50 percent of all chat rooms, the **Invitations** option is set to **Yes**.
  
> [!IMPORTANT]
> If the calculated value for the number of invitations that is generated by the server exceeds 1 million, server performance could degrade significantly. To avoid this issue, be sure that you minimize the number of chat rooms that are configured to send invitations or restrict the number of users who can join chat rooms that have been configured to send invitations. 
  
**Chat room access by invitation sample**

|&nbsp;|Small Chat Rooms|Medium Chat Rooms|Large Chat Rooms|Total|
|:-----|:-----|:-----|:-----|:-----|
|Users who can access chat room   |30 per room   |150 per room   |16,000 per room   ||
|Percentage of rooms that have invitations   |50%   |50%   |50%   ||
|Chat rooms configured to send invitations   |16,000   |533   |5   ||
|Users who can access the chat room   |60   |225   |16,000   ||
|Invitations generated by Persistent Chat Server   |960,000   |120,000   |80,000   |1,160,000   |
|Maximum allowable number of invitations   ||||2,000,000   |
|Model 1 - Start with expected number of messages per room per day   |||||
|Chat Rate Per Room (per day)   |50   |500   |100   |650   |
|Chat rate (per second) across all rooms   |55.56   |18.52   |0.03   |74   |
|Model 2 - Start with number of messages posted per user per day   |||||
|Chat rate per user per day   |15   |5   |0.1   |20   |
|Chat rate per room (per day)   |38   |375   |800   |1,213   |
|Chat rate (per second) across all rooms   |41.67   |13.89   |0.28   |56   |
   
### Plan capacity for Persistent Chat Server performance

The following table describes the user model for Persistent Chat Server. It provides the basis for the capacity planning requirements and represents a typical organization with 80,000 concurrent users on four servers.
  
**Persistent Chat Server performance user model**

- Number of active users connected: 80,000  <br/>
- Number of Persistent Chat Server service instances: 4  <br/>
- Size of small chat rooms: 30 users  <br/> 
- Size of medium chat rooms: 150 users  <br/>
- Size of large chat rooms: 16,000 users  <br/>
- Total number of chat rooms: 33,077  <br/> 
- Number of small chat rooms: 32,000  <br/> 
- Number of medium chat rooms: 1,067  <br/> 
- Number of large chat rooms: 10  <br/> 
- Total number of chat rooms per user: 16  <br/> 
- Number of small chat rooms per user: 12  <br/> 
- Number of medium chat rooms per user: 2  <br/> 
- Number of large chat rooms per user: 2  <br/> 
- Number of rooms joined per user: 24  <br/>
- Peak join rate: 10/second  <br/> 
- Total chat rate: 24/second  <br/> 
- Chat rate for small chat rooms: 22.22/second  <br/> 
- Chat rate for medium chat rooms: 1.67/second  <br/> 
- Chat rate for large chat rooms: ~0.15/second  <br/> 
- Percentage of chat rooms configured for invitations: 50%  <br/>
- Percentage of direct memberships: 50%  <br/>
- Percentage of group memberships: 50%  <br/> 
- Average number of ancestor affiliations in Active Directory Domain Services: 100 - 200  <br/>
- Number of subscribed contacts per user: 80  <br/> 
- Average number of endpoints per user: 1.5  <br/> 
- Average number of visible chat rooms per endpoint: 1.5  <br/> 
- Average number of visible chat rooms per user: 2.25 (50% for 1 room and 50% for 2 rooms); Up to 6 rooms open, one per monitor  <br/> 
- Number of participants polled per interval: 25 per visible chat room  <br/> 
- Length of polling interval: 5 minutes  <br/> 
- Number of participants polled per second: 15,000  <br/>
- Number of presence changes per hour per user: 6  <br/> 
- Number of presence changes per second: 133.33  
   

