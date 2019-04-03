---
title: "Capacity planning for Persistent Chat Server in Skype for Business Server 2015"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 2/23/2018
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 7a850cd5-c789-4795-a8ff-083be21ae784
description: "Summary: Read this topic to learn about capacity planning for Persistent Chat Server in Skype for Business Server 2015."
---

# Capacity planning for Persistent Chat Server in Skype for Business Server 2015
 
**Summary:** Read this topic to learn about capacity planning for Persistent Chat Server in Skype for Business Server 2015.
  
Persistent Chat Server can perform multi-user, real-time chat that can persist for future retrieval and search. Unlike group instant messaging (IM) that is saved in a user's mailbox if conversation history is configured, a Persistent Chat Server session stays open longer, and the content is saved on a server, along with the messages, files, URLs, and other data that are part of an ongoing conversation.
  
Capacity planning is an important part of preparing to deploy Persistent Chat Server. This topic provides capacity planning tables that you can use to determine the best configuration for your deployment. It also describes how to best manage Persistent Chat Server deployments that require greater capacity at peak times.
  
Before reading this section, you should be familiar with Persistent Chat topologies. For more information, see [Plan Persistent Chat Server topology](topology.md).

> [!NOTE] 
> Persistent chat is available in Skype for Business Server 2015 but is no longer supported in Skype for Business Server 2019. The same functionality is available in Teams. For more information, see [Journey from Skype for Business to Microsoft Teams](/microsoftteams/journey-skypeforbusiness-teams). If you need to use Persistent chat, your choices are to either migrate users requiring this functionality to Teams, or to continue using Skype for Business Server 2015. 
  
## Persistent Chat Server capacity planning

The following tables can help you with capacity planning for Persistent Chat Server by modeling how various Persistent Chat Server settings affect capacity.
  
- Plan capacity for number of users
    
- Plan capacity for chat room access
    
- Plan capacity for chat room access by invitation
    
- Plan capacity for performance
    
### Plan capacity for number of users for Persistent Chat Server

Use the following sample table to determine the number of users you will be able to support.
  
**Persistent Chat Server pool maximum capacity sample**

|||
|:-----|:-----|
|Active Persistent Chat service instances  <br/> |4  <br/> |
|Persistent Chat service instances  <br/> |8 (only a maximum of 4 can be active; 4 must be inactive)  <br/> |
|Active users connected  <br/> |80,000  <br/> |
|Total provisioned users  <br/> |150,000  <br/> |
|Number of endpoints  <br/> |120,000  <br/> |
   
In the preceding sample, the plan is to support the maximum number of users that Persistent Chat Server allows: four servers/instances of the Persistent Chat service (can have four more passive servers running Persistent Chat Server for high availability and disaster recovery) and 20,000 users per server, for a total of 80,000 active users.
  
### Plan capacity for chat room access

The following sample table can help you plan for managing chat room access in a Persistent Chat Server pool.
  
**Managing chat room access sample**

||**Small Chat Rooms**|**Medium Chat Rooms**|**Large Chat Rooms**|**Total**|
|:-----|:-----|:-----|:-----|:-----|
|Size of chat rooms (number of users connected)  <br/> |30 per room  <br/> |150 per room  <br/> |16,000 per room  <br/> ||
|Chat rooms  <br/> |32,000  <br/> |1,067  <br/> |10  <br/> |33,077  <br/> |
|% of rooms that are auditorium  <br/> |1%  <br/> |1%  <br/> |50%  <br/> ||
|% of rooms that are open  <br/> |3%  <br/> |3%  <br/> |50%  <br/> ||
|Open rooms (no explicit membership)  <br/> |960  <br/> |32  <br/> |5  <br/> |997  <br/> |
|Non-open rooms (regular rooms with explicit membership)  <br/> |31,040  <br/> |1.035  <br/> |5  <br/> |32,080  <br/> |
|Auditorium rooms (additional presenters entry)  <br/> |0  <br/> |32  <br/> |5  <br/> ||
|Rooms managed by direct membership  <br/> |50%  <br/> |10%  <br/> |0%  <br/> ||
|Rooms managed by user groups  <br/> |50%  <br/> |90%  <br/> |100%  <br/> ||
|User groups in each chat room's membership list for open rooms (not specified explicitly)  <br/> |0  <br/> |0  <br/> |0  <br/> ||
|Users in each chat room's membership list for non-open rooms  <br/> |30  <br/> |150  <br/> |16,000  <br/> ||
|User groups in each chat room's membership list for non-open rooms  <br/> |3  <br/> |5  <br/> |10  <br/> ||
|Users and user groups in each chat room's manager list (for open and non-open rooms)  <br/> |6  <br/> |6  <br/> |6  <br/> ||
|Users and user groups in each auditorium chat room's presenters list (for open and non-open rooms)  <br/> |6  <br/> |6  <br/> |6  <br/> ||
|User-based membership entities across all non-open rooms  <br/> |465,600  <br/> |15,520  <br/> |-  <br/> ||
|User-group-based membership entities across all non-open rooms  <br/> |46,560  <br/> |4656  <br/> |50  <br/> ||
|Users and user groups based entities across all auditorium chat rooms  <br/> |0  <br/> |192  <br/> |50  <br/> ||
|Users and user groups based manager entities across all chat rooms manager lists  <br/> |192,000  <br/> |6,400  <br/> |60  <br/> ||
|Active users per chat room  <br/> |30  <br/> |150  <br/> |16,000  <br/> ||
|Chat rooms per user  <br/> |12  <br/> |2  <br/> |2  <br/> |16  <br/> |
|User groups in each chat room's membership list  <br/> |10  <br/> |10  <br/> |15  <br/> ||
|Rooms managed by user groups  <br/> |50%  <br/> |50%  <br/> |50%  <br/> ||
|User-group-based membership entities across all chat rooms  <br/> |155,200  <br/> |5173  <br/> |68  <br/> ||
|User-based membership entities across all chat rooms  <br/> |465,600  <br/> |77,600  <br/> |72,000  <br/> ||
|Users and user groups in each chat room's manager, presenter, and scope lists  <br/> |6  <br/> |6  <br/> |6  <br/> ||
|Users and user groups across all chat rooms' manager, presenter, and scope lists  <br/> |192,000  <br/> |6400  <br/> |60  <br/> ||
|Access control entries  <br/> |704,160  <br/> |26,768  <br/> |160  <br/> |731,088  <br/> |
|Maximum access control entries  <br/> ||||2,000,000  <br/> |
   
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

||**Small Chat Rooms**|**Medium Chat Rooms**|**Large Chat Rooms**|**Total**|
|:-----|:-----|:-----|:-----|:-----|
|Users who can access chat room  <br/> |30 per room  <br/> |150 per room  <br/> |16,000 per room  <br/> ||
|Percentage of rooms that have invitations  <br/> |50%  <br/> |50%  <br/> |50%  <br/> ||
|Chat rooms configured to send invitations  <br/> |16,000  <br/> |533  <br/> |5  <br/> ||
|Users who can access the chat room  <br/> |60  <br/> |225  <br/> |16,000  <br/> ||
|Invitations generated by Persistent Chat Server  <br/> |960,000  <br/> |120,000  <br/> |80,000  <br/> |1,160,000  <br/> |
|Maximum allowable number of invitations  <br/> ||||2,000,000  <br/> |
|Model 1 - Start with expected number of messages per room per day  <br/> |||||
|Chat Rate Per Room (per day)  <br/> |50  <br/> |500  <br/> |100  <br/> |650  <br/> |
|Chat rate (per second) across all rooms  <br/> |55.56  <br/> |18.52  <br/> |0.03  <br/> |74  <br/> |
|Model 2 - Start with number of messages posted per user per day  <br/> |||||
|Chat rate per user per day  <br/> |15  <br/> |5  <br/> |0.1  <br/> |20  <br/> |
|Chat rate per room (per day)  <br/> |38  <br/> |375  <br/> |800  <br/> |1,213  <br/> |
|Chat rate (per second) across all rooms  <br/> |41.67  <br/> |13.89  <br/> |0.28  <br/> |56  <br/> |
   
### Plan capacity for Persistent Chat Server performance

The following table describes the user model for Persistent Chat Server. It provides the basis for the capacity planning requirements and represents a typical organization with 80,000 concurrent users on four servers.
  
**Persistent Chat Server performance user model**

|||
|:-----|:-----|
|Number of active users connected  <br/> |80,000  <br/> |
|Number of Persistent Chat Server service instances  <br/> |4  <br/> |
|Size of small chat rooms  <br/> |30 users  <br/> |
|Size of medium chat rooms  <br/> |150 users  <br/> |
|Size of large chat rooms  <br/> |16,000 users  <br/> |
|Total number of chat rooms  <br/> |33,077  <br/> |
|Number of small chat rooms  <br/> |32,000  <br/> |
|Number of medium chat rooms  <br/> |1,067  <br/> |
|Number of large chat rooms  <br/> |10  <br/> |
|Total number of chat rooms per user  <br/> |16  <br/> |
|Number of small chat rooms per user  <br/> |12  <br/> |
|Number of medium chat rooms per user  <br/> |2  <br/> |
|Number of large chat rooms per user  <br/> |2  <br/> |
|Number of rooms joined per user  <br/> |24  <br/> |
|Peak join rate  <br/> |10/second  <br/> |
|Total chat rate  <br/> |24/second  <br/> |
|Chat rate for small chat rooms  <br/> |22.22/second  <br/> |
|Chat rate for medium chat rooms  <br/> |1.67/second  <br/> |
|Chat rate for large chat rooms  <br/> |~0.15/second  <br/> |
|Percentage of chat rooms configured for invitations  <br/> |50%  <br/> |
|Percentage of direct memberships  <br/> |50%  <br/> |
|Percentage of group memberships  <br/> |50%  <br/> |
|Average number of ancestor affiliations in Active Directory Domain Services  <br/> |100 - 200  <br/> |
|Number of subscribed contacts per user  <br/> |80  <br/> |
|Average number of endpoints per user  <br/> |1.5  <br/> |
|Average number of visible chat rooms per endpoint  <br/> |1.5  <br/> |
|Average number of visible chat rooms per user  <br/> |2.25 (50% for 1 room and 50% for 2 rooms); Up to 6 rooms open, one per monitor  <br/> |
|Number of participants polled per interval  <br/> |25 per visible chat room  <br/> |
|Length of polling interval  <br/> |5 minutes  <br/> |
|Number of participants polled per second  <br/> |15,000  <br/> |
|Number of presence changes per hour per user  <br/> |6  <br/> |
|Number of presence changes per second  <br/> |133.33  <br/> |
   

