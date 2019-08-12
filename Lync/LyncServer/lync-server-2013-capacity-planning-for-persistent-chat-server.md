---
title: 'Lync Server 2013: Capacity planning for Persistent Chat Server'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Capacity planning for Persistent Chat Server
ms:assetid: 7a850cd5-c789-4795-a8ff-083be21ae784
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg615006(v=OCS.15)
ms:contentKeyID: 48184580
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Capacity planning for Persistent Chat Server in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-05_

Persistent Chat Server can perform multi-user real-time chat that can persist for future retrieval and search. Unlike group instant messaging (IM) that is saved in a user’s mailbox if conversation history is configured, a Persistent Chat Server session stays open longer, and the content is saved on a server, along with the messages, files, URLs, and other data that are part of an ongoing conversation.

Capacity planning is an important part of preparing to deploy Persistent Chat Server. This topic provides details about supported Persistent Chat Server topologies and capacity planning tables that you can use to determine the best configuration for your deployment. It also describes how to best manage Persistent Chat Server deployments that require greater capacity at peak times.

To download Persistent Chat Server, see "Microsoft Lync Server 13 Persistent Chat Server" at [http://go.microsoft.com/fwlink/p/?linkId=209539](http://go.microsoft.com/fwlink/p/?linkid=209539).

For details about installing Persistent Chat Server, see [Installing Persistent Chat Server in Lync Server 2013](lync-server-2013-installing-persistent-chat-server.md) and [Configuring Persistent Chat Server in Lync Server 2013](lync-server-2013-configuring-persistent-chat-server.md) in the Deployment documentation.

Support tools, such as Lync Server Planning Tool, can further assist you with capacity planning. For details about the Planning Tool, see [Beginning the planning process for Lync Server 2013](lync-server-2013-beginning-the-planning-process.md) in the Planning documentation.

<div>

## Persistent Chat Server Supported Topologies

You can deploy Persistent Chat Server in single-server or multiple-server pools, and with single-pool or multiple-pool topology.

We now also support Persistent Chat Server on Standard Edition server for new Lync Server 2013 deployments. However, performance and scale will be affected, and because there is no high availability option for this new deployment, we expect you to use this primarily for the purposes of proof of concept, evaluation, and so on.

<div>


> [!NOTE]  
> For additional details about both topologies, see <A href="lync-server-2013-planning-for-persistent-chat-server.md">Planning for Persistent Chat Server in Lync Server 2013</A> in this documentation set and <A href="lync-server-2013-deploying-persistent-chat-server.md">Deploying Persistent Chat Server in Lync Server 2013</A> in the Deployment documentation.



</div>

<div>

## Single-Server Topology

The minimum configuration and simplest deployment for Persistent Chat Server is a single Persistent Chat Server Front End Server topology. This deployment requires a single server that runs Persistent Chat Server (which optionally runs the Compliance service, if compliance is enabled), a server that hosts both the SQL Server database, and if compliance is required, the SQL Server database to store the compliance data.

<div>


> [!IMPORTANT]  
> You cannot add additional servers to a Persistent Chat Server pool that is started as a single-server deployment in Topology Builder. We recommend using the multiple-server pool topology, even if you’re using a single server. This is so that you’ll be able to add more servers later, if it's necessary. 


</div>

The following figure shows all required and optional components of a topology for a single Persistent Chat Server Front End Server with compliance.

**Single Persistent Chat Server**

![Single server topology with Compliance service](images/Gg398500.9168fa52-61e0-4d17-a14d-45fd32e81456(OCS.15).jpg "Single server topology with Compliance service")

</div>

<div>

## Multiple-Server Topology

To provide greater capacity and reliability, you can deploy a multiple-server topology, as described in [Planning for Persistent Chat Server in Lync Server 2013](lync-server-2013-planning-for-persistent-chat-server.md). The multiple-server topology can include as many as four active computers running Persistent Chat Server (high availability and disaster recovery configurations will allow up to eight, but only four can be active and the remaining four on standby). Each server can support as many as 20,000 concurrent users, for a total of 80,000 concurrent users connected to a Persistent Chat Server pool with 4 servers. A multiple-server topology is the same as the single-server topology except that multiple servers host Persistent Chat Server, and can scale higher. Multiple computers running Persistent Chat Server should reside in the same Active Directory Domain Services domain as Lync Server and the Compliance service.

The following figure shows all the components of a multiple-server topology with multiple computers running Persistent Chat Server, the optional Compliance service, and a separate compliance database.

**Multiple Persistent Chat Servers**

![Multiple server topology](images/Gg398500.19aea898-28df-4d9b-903c-f72ef062d919(OCS.15).jpg "Multiple server topology")

In a four-server Persistent Chat Server deployment, where 80,000 users can be simultaneously signed in to and using Persistent Chat, the load is distributed evenly at 20,000 users per server. If one server becomes unavailable, the users who are connected to that server will lose their access to Persistent Chat Server. The disconnected users will be automatically transferred to the remaining servers until the unavailable server is restored. Depending on the amount of Persistent Chat traffic on the network, this transfer can take a few minutes or longer. Because each of the remaining servers might be hosting as many as 30,000 users, we recommend that you restore the unavailable server as quickly as possible to avoid performance issues. Otherwise, you can make another Persistent Chat Server available by using the Topology Builder or the Windows PowerShell cmdlet, **set-CsPersistentChatActiveServer**.

</div>

</div>

<div>

## Persistent Chat Server Capacity Planning

The following tables can help you with capacity planning for Persistent Chat Server. They model how changing various Persistent Chat Server settings affect capacity capabilities.

<div>

## Planning Your Maximum Capacity for Persistent Chat Server

Use the following sample table to determine the number of users you will be able to support.

### Persistent Chat Server pool Maximum Capacity Sample

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Active Persistent Chat service instances</p></td>
<td><p><em>4</em></p></td>
</tr>
<tr class="even">
<td><p>Persistent Chat service instances</p></td>
<td><p><em>8 (4 must be inactive; only a maximum of 4 can be active)</em></p></td>
</tr>
<tr class="odd">
<td><p>Active users connected</p></td>
<td><p><em>80,000</em></p></td>
</tr>
<tr class="even">
<td><p>Total provisioned users</p></td>
<td><p>150,000</p></td>
</tr>
<tr class="odd">
<td><p>Number of endpoints</p></td>
<td><p>120,000</p></td>
</tr>
</tbody>
</table>


In the preceding sample, the plan is to support the maximum number of users that Persistent Chat Server allows: four servers/instances of the Persistent Chat service (can have four more passive servers running Persistent Chat Server for high availability and disaster recovery) and 20,000 users per server, for a total of 80,000 active users.

</div>

<div>

## Capacity Planning for Managing Persistent Chat Room Access

The following sample table can help you plan for managing Persistent Chat room access in a Persistent Chat Server pool.

### Managing Chat Room Access Sample

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>Small Chat Rooms</th>
<th>Medium Chat Rooms</th>
<th>Large Chat Rooms</th>
<th>Total</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Size of chat rooms (number of users connected)</p></td>
<td><p>30 per room</p></td>
<td><p>150 per room</p></td>
<td><p>16,000 per room</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Chat rooms</p></td>
<td><p>32,000</p></td>
<td><p>1,067</p></td>
<td><p>10</p></td>
<td><p>33,077</p></td>
</tr>
<tr class="odd">
<td><p>% of rooms that are auditorium</p></td>
<td><p>1%</p></td>
<td><p>1%</p></td>
<td><p>50%</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>% of rooms that are open</p></td>
<td><p>3%</p></td>
<td><p>3%</p></td>
<td><p>50%</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Open rooms (no explicit membership)</p></td>
<td><p>960</p></td>
<td><p>32</p></td>
<td><p>5</p></td>
<td><p>997</p></td>
</tr>
<tr class="even">
<td><p>Non-open rooms (regular rooms with explicit membership)</p></td>
<td><p>31,040</p></td>
<td><p>1.035</p></td>
<td><p>5</p></td>
<td><p>32,080</p></td>
</tr>
<tr class="odd">
<td><p>Auditorium rooms (additional presenters entry)</p></td>
<td><p>0</p></td>
<td><p>32</p></td>
<td><p>5</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Rooms managed by direct membership</p></td>
<td><p>50%</p></td>
<td><p>10%</p></td>
<td><p>0%</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Rooms managed by user groups</p></td>
<td><p>50%</p></td>
<td><p>90%</p></td>
<td><p>100%</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>User groups in each chat room's membership list for open rooms (not specified explicitly)</p></td>
<td><p>0</p></td>
<td><p>0</p></td>
<td><p>0</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Users in each chat room's membership list for non-open rooms</p></td>
<td><p>30</p></td>
<td><p>150</p></td>
<td><p>16,000</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>User groups in each chat room's membership list for non-open rooms</p></td>
<td><p>3</p></td>
<td><p>5</p></td>
<td><p>10</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Users and user groups in each chat room's manager list (for open and non-open rooms)</p></td>
<td><p>6</p></td>
<td><p>6</p></td>
<td><p>6</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Users and user groups in each auditorium chat room's presenters list (for open and non-open rooms)</p></td>
<td><p>6</p></td>
<td><p>6</p></td>
<td><p>6</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>User-based membership entities across all non-open rooms</p></td>
<td><p>465,600</p></td>
<td><p>15,520</p></td>
<td><p>-</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>User-group-based membership entities across all non-open rooms</p></td>
<td><p>46,560</p></td>
<td><p>4656</p></td>
<td><p>50</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Users and user groups based entities across all auditorium chat rooms</p></td>
<td><p>0</p></td>
<td><p>192</p></td>
<td><p>50</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Users and user groups based manager entities across all chat rooms manager lists</p></td>
<td><p>192,000</p></td>
<td><p>6,400</p></td>
<td><p>60</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Active users per chat room</p></td>
<td><p><em>30</em></p></td>
<td><p><em>150</em></p></td>
<td><p><em>16,000</em></p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Chat rooms per user</p></td>
<td><p><em>12</em></p></td>
<td><p><em>2</em></p></td>
<td><p><em>2</em></p></td>
<td><p><em>16</em></p></td>
</tr>
<tr class="odd">
<td><p>User groups in each chat room’s membership list</p></td>
<td><p><em>10</em></p></td>
<td><p><em>10</em></p></td>
<td><p><em>15</em></p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Rooms managed by user groups</p></td>
<td><p><em>50%</em></p></td>
<td><p><em>50%</em></p></td>
<td><p><em>50%</em></p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>User-group-based membership entities across all chat rooms</p></td>
<td><p>155,200</p></td>
<td><p>5173</p></td>
<td><p>68</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>User-based membership entities across all chat rooms</p></td>
<td><p>465,600</p></td>
<td><p>77,600</p></td>
<td><p>72,000</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Users and user groups in each chat room's manager, presenter, and scope lists</p></td>
<td><p>6</p></td>
<td><p>6</p></td>
<td><p>6</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Users and user groups across all chat rooms' manager, presenter, and scope lists</p></td>
<td><p>192,000</p></td>
<td><p>6400</p></td>
<td><p>60</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Access control entries</p></td>
<td><p>704,160</p></td>
<td><p>26,768</p></td>
<td><p>160</p></td>
<td><p>731,088</p></td>
</tr>
<tr class="even">
<td><p>Maximum access control entries</p></td>
<td></td>
<td></td>
<td></td>
<td><p>2,000,000</p></td>
</tr>
</tbody>
</table>


In the preceding sample, when you deploy the Persistent Chat Servers according to the recommended guidelines, they can handle up to 80,000 active users across a four-server pool with compliance enabled.

This sample shows chat rooms categorized as small (30 active users at any given time), medium (150 active users), and large (16,000 active users). The number of chat rooms of a certain size is computed based on the total number of:

  - Active users in the system

  - Active users in chat rooms of the given size

  - Chat rooms of the given size that a single user joins

For each chat room, the preceding capacity planning table specifies the number of access control entries that are associated with the chat room, including entries that are assigned directly to the chat room. You can control access to individual chat rooms by using access control lists (ACLs). You can also control access at the category level. In an ACL, an individual access control entry can be either a user group—for example, a security group, a distribution list, or a single user. You can define access control entries for chat room managers, presenters, and members.

<div>


> [!IMPORTANT]  
> In planning your strategy for managing chat rooms, keep in mind that the total number of allowed access control entries is 2 million. If the calculated access control entries exceed 2 million, server performance could degrade significantly. To avoid this issue, whenever possible, be sure that your access control entries are user groups instead of individual users.



</div>

</div>

<div>

## Capacity Planning for Managing Chat Room Access by Invitation

You can use the following capacity planning table to understand the number of invitations that Persistent Chat Server creates and stores in the Persistent Chat database when it is configured to send invitations. You manage invitations on the Category by using the **Chat Room Category settings** page in the Lync Server Control Panel, or by using the Windows PowerShell cmdlet, **set-csPersistentChatCategory**. You can manage invitations on a chat room (in line with what the category allows) by using the **Room Management** page launched from the Lync client, or by using a Windows PowerShell cmdlet, **set-csPersistentChatRoom**.

The sample data in the following table assumes that, on the **Chat room settings** page for 50 percent of all chat rooms, the **Invitations** option is set to **Yes**.

<div>


> [!IMPORTANT]  
> If the calculated value for the number of invitations that is generated by the server exceeds 1 million, server performance could degrade significantly. To avoid this issue, be sure that you minimize the number of chat rooms that are configured to send invitations or restrict the number of users who can join chat rooms that have been configured to send invitations.



</div>

### Chat Room Access by Invitation Sample

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>Small Chat Rooms</th>
<th>Medium Chat Rooms</th>
<th>Large Chat Rooms</th>
<th>Total</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Users who can access chat room</p></td>
<td><p>30 per room</p></td>
<td><p>150 per room</p></td>
<td><p>16,000 per room</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Percentage of rooms that have invitations</p></td>
<td><p>50%</p></td>
<td><p>50%</p></td>
<td><p>50%</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Chat rooms configured to send invitations</p></td>
<td><p><em>16,000</em></p></td>
<td><p><em>533</em></p></td>
<td><p><em>5</em></p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Users who can access the chat room</p></td>
<td><p><em>60</em></p></td>
<td><p><em>225</em></p></td>
<td><p><em>16,000</em></p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Invitations generated by Persistent Chat Server</p></td>
<td><p>960,000</p></td>
<td><p>120,000</p></td>
<td><p>80,000</p></td>
<td><p>1,160,000</p></td>
</tr>
<tr class="even">
<td><p>Maximum allowable number of invitations</p></td>
<td></td>
<td></td>
<td></td>
<td><p>2,000,000</p></td>
</tr>
<tr class="odd">
<td><p>Model 1 - Start with expected number of messages per room per day</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Chat Rate Per Room (per day)</p></td>
<td><p>50</p></td>
<td><p>500</p></td>
<td><p>100</p></td>
<td><p>650</p></td>
</tr>
<tr class="odd">
<td><p>Chat rate (per second) across all rooms</p></td>
<td><p>55.56</p></td>
<td><p>18.52</p></td>
<td><p>0.03</p></td>
<td><p>74</p></td>
</tr>
<tr class="even">
<td><p>Model 2 - Start with number of messages posted per user per day</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Chat rate per user per day</p></td>
<td><p>15</p></td>
<td><p>5</p></td>
<td><p>0.1</p></td>
<td><p>20</p></td>
</tr>
<tr class="even">
<td><p>Chat rate per room (per day)</p></td>
<td><p>38</p></td>
<td><p>375</p></td>
<td><p>800</p></td>
<td><p>1,213</p></td>
</tr>
<tr class="odd">
<td><p>Chat rate (per second) across all rooms</p></td>
<td><p>41.67</p></td>
<td><p>13.89</p></td>
<td><p>0.28</p></td>
<td><p>56</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Persistent Chat Server Performance User Model

The following table describes the user model for Persistent Chat Server. It provides the basis for the capacity planning requirements and represents a typical organization with 80,000 concurrent users on four servers.

### Persistent Chat Server Performance User Model

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Number of active users connected</p></td>
<td><p>80,000</p></td>
</tr>
<tr class="even">
<td><p>Number of Persistent Chat Server service instances</p></td>
<td><p>4</p></td>
</tr>
<tr class="odd">
<td><p>Size of small chat rooms</p></td>
<td><p>30 users</p></td>
</tr>
<tr class="even">
<td><p>Size of medium chat rooms</p></td>
<td><p>150 users</p></td>
</tr>
<tr class="odd">
<td><p>Size of large chat rooms</p></td>
<td><p>16,000 users</p></td>
</tr>
<tr class="even">
<td><p>Total number of chat rooms</p></td>
<td><p>33,077</p></td>
</tr>
<tr class="odd">
<td><p>Number of small chat rooms</p></td>
<td><p>32,000</p></td>
</tr>
<tr class="even">
<td><p>Number of medium chat rooms</p></td>
<td><p>1,067</p></td>
</tr>
<tr class="odd">
<td><p>Number of large chat rooms</p></td>
<td><p>10</p></td>
</tr>
<tr class="even">
<td><p>Total number of chat rooms per user</p></td>
<td><p>16</p></td>
</tr>
<tr class="odd">
<td><p>Number of small chat rooms per user</p></td>
<td><p>12</p></td>
</tr>
<tr class="even">
<td><p>Number of medium chat rooms per user</p></td>
<td><p>2</p></td>
</tr>
<tr class="odd">
<td><p>Number of large chat rooms per user</p></td>
<td><p>2</p></td>
</tr>
<tr class="even">
<td><p>Number of rooms joined per user</p></td>
<td><p>24</p></td>
</tr>
<tr class="odd">
<td><p>Peak join rate</p></td>
<td><p>10/second</p></td>
</tr>
<tr class="even">
<td><p>Total chat rate</p></td>
<td><p>24/second</p></td>
</tr>
<tr class="odd">
<td><p>Chat rate for small chat rooms</p></td>
<td><p>22.22/second</p></td>
</tr>
<tr class="even">
<td><p>Chat rate for medium chat rooms</p></td>
<td><p>1.67/second</p></td>
</tr>
<tr class="odd">
<td><p>Chat rate for large chat rooms</p></td>
<td><p>~0.15/second</p></td>
</tr>
<tr class="even">
<td><p>Percentage of chat rooms configured for invitations</p></td>
<td><p>50%</p></td>
</tr>
<tr class="odd">
<td><p>Percentage of direct memberships</p></td>
<td><p>50%</p></td>
</tr>
<tr class="even">
<td><p>Percentage of group memberships</p></td>
<td><p>50%</p></td>
</tr>
<tr class="odd">
<td><p>Average number of ancestor affiliations in Active Directory Domain Services</p></td>
<td><p>100 - 200</p></td>
</tr>
<tr class="even">
<td><p>Number of subscribed contacts per user</p></td>
<td><p>80</p></td>
</tr>
<tr class="odd">
<td><p>Average number of endpoints per user</p></td>
<td><p>1.5</p></td>
</tr>
<tr class="even">
<td><p>Average number of visible chat rooms per endpoint</p></td>
<td><p>1.5</p></td>
</tr>
<tr class="odd">
<td><p>Average number of visible chat rooms per user</p></td>
<td><p>2.25 (50% for 1 room and 50% for 2 rooms); Up to 6 rooms open, one per monitor</p></td>
</tr>
<tr class="even">
<td><p>Number of participants polled per interval</p></td>
<td><p>25 per visible chat room</p></td>
</tr>
<tr class="odd">
<td><p>Length of polling interval</p></td>
<td><p>5 minutes</p></td>
</tr>
<tr class="even">
<td><p>Number of participants polled per second</p></td>
<td><p>15,000</p></td>
</tr>
<tr class="odd">
<td><p>Number of presence changes per hour per user</p></td>
<td><p>6</p></td>
</tr>
<tr class="even">
<td><p>Number of presence changes per second</p></td>
<td><p>133.33</p></td>
</tr>
</tbody>
</table>


</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

