---
title: Coexistence with Skype for Business  
author: jambirk
ms.author: francoid
manager: Serdars
ms.date: 11/7/2018
ms.topic: article
ms.service: msteams
ms.reviewer: francoid
description: Prepare your organization's network for Quality of Service (QoS) in Microsoft Teams.
localization_priority: Normal
search.appverid: MET150
MS.collection: Teams_ITAdmin_PracticalGuidance
appliesto:
- Microsoft Teams
description: "This document describes the behavior of chat, call routing and presence between users of Teams and Skype for Business, both in-tenant and federated, based on assigned TeamsUpgrade modes. It includes routing optimizations,  presence behavior, as well as the change of default TeamsUpgrade mode from *Legacy* to *Islands* and the impending retirement of *Legacy*."
---

# Coexistence with Skype for Business

Coexistence and interoperability between Skype for Business and Teams is defined by TeamsUpgrade modes, described in [Migration and interoperability guidance for organizations using Teams together with Skype for Business](migration-interop-guidance-for-teams-with-skype.md).

Any given user will always be assigned a TeamsUpgrade mode, either by default or explicitly by the administrator. The default value is *Islands*. Users upgraded to Teams have the mode of *TeamsOnly*.

> [!NOTE]
> *Legacy* mode has been deprecated; users remaining on *Legacy* mode will be converted to *Islands* mode after November 15, 2018.

## Routing parameters

The TeamsUpgrade mode of the recipient is key in determining the behavior of chats, calls, and presence, both within a tenant and across federated tenants.

If the sender is using Teams, the routing decision is made when creating a new conversation thread. Existing conversation threads in Teams always retain the routing method determined when the thread was created. Teams supports persistent threads.

 Thread routing methods are:  
* *native* for a Teams to Teams conversation in-tenant
* *interop* for a Teams to Skype for business conversation in-tenant
* *federated* for a federated conversation across tenants.

The parameters that determine the thread routing method are:
* The TeamsUpgrade mode of the recipient
* The client used by the sender
* Whether the conversation is new, or part of an existing thread
* Whether the conversation is in-tenant or federated
* Whether the conversation is possible
    * In-tenant interoperability and federation from Teams requires that the originator’s tenant is either pure online or Skype for Business hybrid. Purely on-premise tenants can't have in-tenant interoperability or federation to Teams.
    * If the Skype for Business account of the originator is homed on-premise, that user can't use the Teams client for in-tenant interoperability and for federation. That user must use the Skype for Business client instead for interoperability and federation.
    * Teams to Teams communication is always possible in-tenant.

# Chat and call routing

## In-tenant routing for new chats or calls 

The table below captures current practice for in-tenant chat and call routing. This table is valid for new calls or chats that are not started from a preexisting existing thread. It describes to which client a new call (or chat) will be routed, if originated by a user on the left, to an in-tenant target user on the right.

Messages sent to TeamsOnly users will always land in Teams. Messages sent to SfB* users will always land in Skype for Business, if the conversation is possible as described above. Messages sent to Islands users will always land in the client from which they were originated.

**Table 1: in-tenant new chat or call routing**

| <br/> Mode   | From&nbsp;originator <br/> Client | <br/> SfB&nbsp;homed | | <br/> Islands  | To&nbsp;Target <br/> SfB\*   | <br/> TeamsOnly  |
|--- |--- |--- |--- |--- |--- |--- |
| Islands <br/>Islands <br/>Islands <br/>Islands<br/> SfB\*<br/> SfB\* <br/> TeamsOnly |Teams<br/>SfB <br/>Teams <br/>SfB <br/>SfB <br/>SfB <br/>Teams|Online<br/> Online<br/> On-prem<br/> On-prem<br/> Online<br/> On-prem<br/> Online| &boxv;<br/>&boxv;<br/>&boxv;<br/>&boxv;<br/>&boxv;<br/>&boxv;<br/>&boxv;<br/>|Teams <br/> SfB <br/> Teams <br/> SfB <br/>  SfB <br/> SfB <br/> Teams | *SfB* <br/> SfB <br/> **NA** <br/>SfB <br/> SfB <br/>SfB <br/>*SfB* <br/>  | Teams <br/>*Teams* <br/>Teams <br/>*Teams* <br/> *Teams*  <br/>*Teams* <br/>Teams <br/> |
|  | | | | | | |

In the table, SfB* represents any of the following modes: *SfBOnly*, *SfBWithTeamsCollab*, *SfBWithTeamsCollabAndMeetings*.

*Italic text*  in the table indicates an interop conversation.

**Bolding** in the table represents a situation in which the chat or call is not possible. That’s because the interoperability infrastructure is only available online and requires the Skype for Business account associated with the Teams account to be an online account. The originator must use Skype for Business instead in these cases. This is one of the reasons why Microsoft’s prescriptive guidance to on-prem/hybrid customers is to use another mode than Islands (typically *SfBWithTeamsCollab*) as the starting point of their upgrade journey to Teams.

## Federated routing for new chats or calls
  
The table below captures current federated call (and chat) routing practices. This table is valid for new calls or chats. It describes to which client a new call (or chat) will be routed, if originated by a user on the left, to a federated target user on the right.

In summary, if the conversation is possible as described above, messages sent to TeamsOnly users will always land in Teams; messages sent to SfB* users will always land in Skype for Business; messages sent to Islands users will always land in Skype for Business regardless of the client from which they were originated. Routing for federated chats and calls differs from in-tenant routing in that Islands users will always receive a federated communication in Skype for Business.

The reason for this last point is that we cannot assume that a federated Skype for Business partner already uses Teams if they are in Islands mode. Islands is the default mode, however we can't assume all Islands users run Teams. By routing to Skype for Business we ensure that no communication to an Islands user fails. If we routed to Teams, that communication could be missed if the target did not use Teams. Routing to Skype for Business ensures the message will always be received.  

> [!NOTE]
> Current implementation of Teams federation is based upon Skype for Business federation, therefore it leverages the interoperability infrastructure (which requires the tenant of the originator to be either pure online or SfB hybrid) and provides a reduced set of capabilities compared to a native thread. We expect to provide native Teams to Teams federation in the future, at which point the thread will be native and provide full capabilities.

**Table 2: federated new chat or call routing**

| <br/>Mode   | From originator<br/> Client| <br/>SfB homed| | <br/> Islands | To Target<br/> SfB\* | <br/> TeamsOnly  |
|--- |--- |--- |--- |--- |--- |---|
| Islands <br/>Islands <br/>Islands <br/>Islands<br/> SfB\*<br/> SfB\* <br/> TeamsOnly |Teams<br/>SfB <br/>Teams <br/>SfB <br/>SfB <br/>SfB <br/>Teams|Online<br/> Online<br/> On-prem<br/> On-prem<br/> Online<br/> On-prem<br/> Online| &boxv;<br/>&boxv;<br/>&boxv;<br/>&boxv;<br/>&boxv;<br/>&boxv;<br/>&boxv;<br/>| *SfB* <br/> SfB <br/> **NA** <br/>SfB <br/> SfB <br/>SfB <br/>SfB <br/> | *SfB* <br/> SfB <br/> **NA** <br/>SfB <br/> SfB <br/>SfB <br/>SfB <br/>  | Teams <br/>Teams <br/>**NA** <br/>*Teams <br/>Teams <br/>Teams* <br/>Teams <br/> |
|  | | | | | |

In the table, SfB* represents any of the following modes: *SfBOnly*, *SfBWithTeamsCollab*, *SfBWithTeamsCollabAndMeetings*.

*Italic text*  highlights an interop conversation.

**Bolding** represents a situation in which the chat or call is not possible. The originator must use Skype for Business instead in these cases. This is one of the reasons why Microsoft’s prescriptive guidance to on-prem/hybrid customers is to use another mode than Islands (typically SfBWithTeamsCollab) as the starting point of their upgrade journey to Teams.

## Chats and calls from pre-existing threads

### From Teams

Calls or chats started from a pre-existing persistent thread in Teams will be routed in the same manner as that thread, if that routing option is still available. 

If the pre-existing persistent thread in Teams was a native thread (i.e. routed to Teams), additional chat messages and calls from that thread will go to Teams. If it was an interop thread (i.e. routed to Skype for Business), additional chat messages and calls will go to Skype for Business (again assuming routing options are available).

> [!NOTE]
> Pre-existing threads in Teams may no longer be routable. This can happen for example if the thread was an interop thread to a user that is now upgraded to Teams. Since it’s an interop thread, the thread would route to Skype for Business but that user no longer can use Skype for Business for chat and calling. In that case, the thread will be disabled and not permit further communication.

### From Skype for Business

Skype for Business does not have thread persistence beyond the SIP session timeout (10 min). Chats and calls from an existing thread in Skype for Business prior to expiration of the SIP session will be routed in the same manner as the thread. Calls and chats from an existing thread in Skype for Business beyond the SIP session timeout will be routed to the remote party’s Skype for Business, regardless of which client the original thread came from on the other party’s side.

## Availability

The in-tenant behavior described above is available in production today.

The federated behavior described above is mostly available in production today. The following elements are still being rolled out and are only available to tenants on early adopters: 
* Federation with an on-premises tenant with presence visibility
* Display of the migrated federated contacts in the Teams client contact list
* Ability to use either SIP URI or SMTP address to discover a federated contact.

Roll-out for these has begun, and general availability is expected prior to the end of November 2018.

# Presence

When you have a situation where some of your users are using the Teams client and others are still using the Skype for Business client, you may have a number of users who are using both clients. You still want presence states to be shared with all users without regard to what client an individual user has. When this is shared across the organization, users can better determine whether it's appropriate to initiate a chat or make a call.

For example, if an originator’s chat or call should land on the target’s Skype for Business client, then it’s the Skype for Business client’s presence that should be shown to the originator. If it should land on the target’s Teams client, then it’s the Teams client’s presence that should be shown.

In order to know what behavior to expect, you'll need to understand that Presence is shared based on a user’s coexistence mode:

* If a user is in TeamsOnly mode, then any other user (whether in Teams or Skype for Business) will see that TeamsOnly user’s Teams presence
* If a user is in any of the SfB\* modes (SfbOnly, SfbWithTeamsCollab, SfbWithTeamsCollabAndMeetings), then any other user (whether in Teams or Skype for Business) will see that SfB\* user’s Skype for Business presence
* If a user is in Islands (or Legacy) mode, presence in Teams and presence in Skype for Business are independent (the values need not match) and other users will see one or the other presence of the Islands user, depending on whether they are in the same tenant or in a federated tenant and which client they use
    * From Teams, any other user within the same tenant will see the Islands user’s Teams presence; this is aligned with the in-tenant routing table above
    * From Teams, any other user in a federated tenant will see the Islands user’s Skype for Business presence; this is aligned with the federated routing table above
    * From Skype for Business, any other user will see the Islands user’s Skype for Business presence (both in-tenant and federated); this is aligned with the routing tables above

> [!NOTE]
> This is a recent change from the previous implementation (called Unified Presence) which showed a combined, aggregated presence of the target’s Teams and Skype for Business clients. That previous approach turned out to be confusing to users as it would frequently result in displaying in accurate presence,  i.e. a user not being reachable even though their presence showed them online.

## In-tenant presence

Messages sent to TeamsOnly users will always land in Teams. Messages sent to SfB\* users will always land in Skype for Business, if the conversation is possible as described above. Messages sent to Islands users will always land in the client from which they were originated.

The table describes the Publisher’s presence that will be seen by a Watcher, depending on the mode of the Publisher and the client of the Watcher (for a new thread).

**Table 3: in-tenant presence (new thread)**

|Watcher <br/>Client| |<br/>Islands |Publisher <br/>SfB\* |<br/>Teams Only|
|--- |--- |--- |--- |---|
|SfB <br/> Teams|&boxv;<br/>&boxv;<br/> |SfB <br/>Teams | SfB <br/>SfB | Teams  <br/> Teams |
| | | | |

## Federated presence

Federated presence is based upon the federated reachability shown in table 2.

The table below describes the Publisher’s presence that will be seen by a Watcher, depending on the mode of the Publisher and the client of the Watcher (for a new thread). In practice the client of the Watcher makes no difference in federation at this stage.

**Table 4: federated presence (new thread)**

|Watcher <br/> Client | |<br/> Islands  |Publisher <br/> SfB\* |<br/> Teams Only  |
|--- |--- |--- |--- |---|
|SfB <br/> Teams|&boxv;<br/>&boxv; |SfB <br/> SfB | SfB <br/> SfB | Teams <br/> Teams |
| | | | ||

## Presence in pre-existing threads

In order to align presence and reachability in pre-existing threads, the target’s presence exposed in that thread needs to be aligned with the routing of the thread, assuming routing is possible.

In particular, if a recipient you previously had a persistent interop conversation thread with is subsequently upgraded to Teams, that thread will no longer reflect accurate presence and will no longer be routable. You should start a new thread.
