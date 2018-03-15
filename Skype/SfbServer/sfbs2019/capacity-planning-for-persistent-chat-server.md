---
title: "Capacity planning for Persistent Chat Server in Lync Server 2013"
ms.author: crowe
author: CarolynRowe
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 7a850cd5-c789-4795-a8ff-083be21ae784
description: "Persistent Chat Server can perform multi-user real-time chat that can persist for future retrieval and search. Unlike group instant messaging (IM) that is saved in a user's mailbox if conversation history is configured, a Persistent Chat Server session stays open longer, and the content is saved on a server, along with the messages, files, URLs, and other data that are part of an ongoing conversation."
---

# Capacity planning for Persistent Chat Server in Lync Server 2013
[]
Persistent Chat Server can perform multi-user real-time chat that can persist for future retrieval and search. Unlike group instant messaging (IM) that is saved in a user's mailbox if conversation history is configured, a Persistent Chat Server session stays open longer, and the content is saved on a server, along with the messages, files, URLs, and other data that are part of an ongoing conversation.
  
Capacity planning is an important part of preparing to deploy Persistent Chat Server. This topic provides details about supported Persistent Chat Server topologies and capacity planning tables that you can use to determine the best configuration for your deployment. It also describes how to best manage Persistent Chat Server deployments that require greater capacity at peak times.
  
To download Persistent Chat Server, see "Microsoft Lync Server 13 Persistent Chat Server" at [https://go.microsoft.com/fwlink/p/?linkId=209539](https://go.microsoft.com/fwlink/p/?linkId=209539).
  
For details about installing Persistent Chat Server, see [Installing Persistent Chat Server in Lync Server 2013](installing-persistent-chat-server.md) and [Configuring Persistent Chat Server in Lync Server 2013](configuring-persistent-chat-server.md) in the Deployment documentation. 
  
Support tools, such as Lync Server Planning Tool, can further assist you with capacity planning. For details about the Planning Tool, see [Beginning the planning process for Lync Server 2013](beginning-the-planning-process.md) in the Planning documentation. 
  
## Persistent Chat Server Supported Topologies

You can deploy Persistent Chat Server in single-server or multiple-server pools, and with single-pool or multiple-pool topology.
  
We now also support Persistent Chat Server on Standard Edition server for new Lync Server 2013 deployments. However, performance and scale will be affected, and because there is no high availability option for this new deployment, we expect you to use this primarily for the purposes of proof of concept, evaluation, and so on.
  
> [!NOTE]
> For additional details about both topologies, see [Planning for Persistent Chat Server in Lync Server 2013](planning-for-persistent-chat-server.md) in this documentation set and [Deploying Persistent Chat Server in Lync Server 2013](deploying-persistent-chat-server.md) in the Deployment documentation. 
  
### Single-Server Topology

The minimum configuration and simplest deployment for Persistent Chat Server is a single Persistent Chat Server Front End Server topology. This deployment requires a single server that runs Persistent Chat Server (which optionally runs the Compliance service, if compliance is enabled), a server that hosts both the SQL Server database, and if compliance is required, the SQL Server database to store the compliance data.
  
> [!IMPORTANT]
> You cannot add additional servers to a Persistent Chat Server pool that is started as a single-server deployment in Topology Builder. We recommend using the multiple-server pool topology, even if you're using a single server, so that you'll be able to add more servers later, if needed. 
  
The following figure shows all required and optional components of a topology for a single Persistent Chat Server Front End Server with compliance.
  
**Single Persistent Chat Server**

![Single server topology with Compliance service](media/Persistent_Chat_Server_ChatRoomSingleServerTopology.jpg)
  
### Multiple-Server Topology

To provide greater capacity and reliability, you can deploy a multiple-server topology, as described in [Planning for Persistent Chat Server in Lync Server 2013](planning-for-persistent-chat-server.md). The multiple-server topology can include as many as four active computers running Persistent Chat Server (high availability and disaster recovery configurations will allow up to eight, but only four can be active and the remaining four on standby). Each server can support as many as 20,000 concurrent users, for a total of 80,000 concurrent users connected to a Persistent Chat Server pool with 4 servers. A multiple-server topology is the same as the single-server topology except that multiple servers host Persistent Chat Server, and can scale higher. Multiple computers running Persistent Chat Server should reside in the same Active Directory Domain Services domain as Lync Server and the Compliance service.
  
The following figure shows all the components of a multiple-server topology with multiple computers running Persistent Chat Server, the optional Compliance service, and a separate compliance database.
  
**Multiple Persistent Chat Servers**

![Multiple server topology](media/Persistent_Chat_Server_ChatRoomMultiServerTopology.jpg)
  
In a four-server Persistent Chat Server deployment, where 80,000 users can be simultaneously signed in to and using Persistent Chat, the load is distributed evenly at 20,000 users per server. If one server becomes unavailable, the users who are connected to that server will lose their access to Persistent Chat Server. The disconnected users will be automatically transferred to the remaining servers until the unavailable server is restored. Depending on the amount of Persistent Chat traffic on the network, this transfer can take a few minutes or longer. Because each of the remaining servers might be hosting as many as 30,000 users, we recommend that you restore the unavailable server as quickly as possible to avoid performance issues. Otherwise, you can make another Persistent Chat Server available by using the Topology Builder or the Windows PowerShell cmdlet, **set-CsPersistentChatActiveServer**. 
  
## Persistent Chat Server Capacity Planning

The following tables can help you with capacity planning for Persistent Chat Server. They model how changing various Persistent Chat Server settings affect capacity capabilities.
  
### Planning Your Maximum Capacity for Persistent Chat Server

Use the following sample table to determine the number of users you will be able to support.
  
**Persistent Chat Server pool Maximum Capacity Sample**

|||
|:-----|:-----|
|Active Persistent Chat service instances  <br/> | _4_ <br/> |
|Persistent Chat service instances  <br/> | _8 (4 must be inactive; only a maximum of 4 can be active)_ <br/> |
|Active users connected  <br/> | _80,000_ <br/> |
|Total provisioned users  <br/> |150,000  <br/> |
|Number of endpoints  <br/> |120,000  <br/> |
   
In the preceding sample, the plan is to support the maximum number of users that Persistent Chat Server allows: four servers/instances of the Persistent Chat service (can have four more passive servers running Persistent Chat Server for high availability and disaster recovery) and 20,000 users per server, for a total of 80,000 active users.
  
### Capacity Planning for Managing Persistent Chat Room Access

The following sample table can help you plan for managing Persistent Chat room access in a Persistent Chat Server pool.
  
**Managing Chat Room Access Sample**

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
|Active users per chat room  <br/> | _30_ <br/> | _150_ <br/> | _16,000_ <br/> ||
|Chat rooms per user  <br/> | _12_ <br/> | _2_ <br/> | _2_ <br/> | _16_ <br/> |
|User groups in each chat room's membership list  <br/> | _10_ <br/> | _10_ <br/> | _15_ <br/> ||
|Rooms managed by user groups  <br/> | _50%_ <br/> | _50%_ <br/> | _50%_ <br/> ||
|User-group-based membership entities across all chat rooms  <br/> |155,200  <br/> |5173  <br/> |68  <br/> ||
|User-based membership entities across all chat rooms  <br/> |465,600  <br/> |77,600  <br/> |72,000  <br/> ||
|Users and user groups in each chat room's manager, presenter, and scope lists  <br/> |6  <br/> |6  <br/> |6  <br/> ||
|Users and user groups across all chat rooms' manager, presenter, and scope lists  <br/> |192,000  <br/> |6400  <br/> |60  <br/> ||
|Access control entries  <br/> |704,160  <br/> |26,768  <br/> |160  <br/> |731,088  <br/> |
|Maximum access control entries  <br/> ||||2,000,000  <br/> |
   
In the preceding sample, when you deploy the Persistent Chat Servers according to the recommended guidelines, they can handle up to 80,000 active users across a four-server pool with compliance enabled.
  
This sample shows chat rooms categorized as small (30 active users at any given time), medium (150 active users), and large (16,000 active users). The number of chat rooms of a certain size is computed based on the total number of:
  
- Active users in the system
    
- Active users in chat rooms of the given size
    
- Chat rooms of the given size that a single user joins
    
For each chat room, the preceding capacity planning table specifies the number of access control entries that are associated with the chat room, including entries that are assigned directly to the chat room. You can control access to individual chat rooms by using access control lists (ACLs). You can also control access at the category level. In an ACL, an individual access control entry can be either a user group—for example, a security group, a distribution list, or a single user. You can define access control entries for chat room managers, presenters, and members.
  
> [!IMPORTANT]
> In planning your strategy for managing chat rooms, keep in mind that the total number of allowed access control entries is 2 million. If the calculated access control entries exceed 2 million, server performance could degrade significantly. To avoid this issue, whenever possible, be sure that your access control entries are user groups instead of individual users. 
  
### Capacity Planning for Managing Chat Room Access by Invitation

You can use the following capacity planning table to understand the number of invitations that Persistent Chat Server creates and stores in the Persistent Chat database when it is configured to send invitations. You manage invitations on the Category by using the **Chat Room Category settings** page in the Lync Server Control Panel, or by using the Windows PowerShell cmdlet, **set-csPersistentChatCategory**. You can manage invitations on a chat room (in line with what the category allows) by using the **Room Management** page launched from the Lync client, or by using a Windows PowerShell cmdlet, **set-csPersistentChatRoom**. 
  
The sample data in the following table assumes that, on the **Chat room settings** page for 50 percent of all chat rooms, the **Invitations** option is set to **Yes**.
  
> [!IMPORTANT]
> If the calculated value for the number of invitations that is generated by the server exceeds 1 million, server performance could degrade significantly. To avoid this issue, be sure that you minimize the number of chat rooms that are configured to send invitations or restrict the number of users who can join chat rooms that have been configured to send invitations. 
  
**Chat Room Access by Invitation Sample**

||**Small Chat Rooms**|**Medium Chat Rooms**|**Large Chat Rooms**|**Total**|
|:-----|:-----|:-----|:-----|:-----|
|Users who can access chat room  <br/> |30 per room  <br/> |150 per room  <br/> |16,000 per room  <br/> ||
|Percentage of rooms that have invitations  <br/> |50%  <br/> |50%  <br/> |50%  <br/> ||
|Chat rooms configured to send invitations  <br/> | _16,000_ <br/> | _533_ <br/> | _5_ <br/> ||
|Users who can access the chat room  <br/> | _60_ <br/> | _225_ <br/> | _16,000_ <br/> ||
|Invitations generated by Persistent Chat Server  <br/> |960,000  <br/> |120,000  <br/> |80,000  <br/> |1,160,000  <br/> |
|Maximum allowable number of invitations  <br/> ||||2,000,000  <br/> |
|Model 1 - Start with expected number of messages per room per day  <br/> |||||
|Chat Rate Per Room (per day)  <br/> |50  <br/> |500  <br/> |100  <br/> |650  <br/> |
|Chat rate (per second) across all rooms  <br/> |55.56  <br/> |18.52  <br/> |0.03  <br/> |74  <br/> |
|Model 2 - Start with number of messages posted per user per day  <br/> |||||
|Chat rate per user per day  <br/> |15  <br/> |5  <br/> |0.1  <br/> |20  <br/> |
|Chat rate per room (per day)  <br/> |38  <br/> |375  <br/> |800  <br/> |1,213  <br/> |
|Chat rate (per second) across all rooms  <br/> |41.67  <br/> |13.89  <br/> |0.28  <br/> |56  <br/> |
   
### Persistent Chat Server Performance User Model

The following table describes the user model for Persistent Chat Server. It provides the basis for the capacity planning requirements and represents a typical organization with 80,000 concurrent users on four servers.
  
**Persistent Chat Server Performance User Model**

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
   

