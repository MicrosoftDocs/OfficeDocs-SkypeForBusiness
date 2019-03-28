---
title: Coexistence with Skype for Business  
author: jambirk
ms.author: francoid
manager: Serdars
ms.topic: conceptual
ms.service: msteams
ms.reviewer: francoid
localization_priority: Normal
search.appverid: MET150
MS.collection: 
- Teams_ITAdmin_PracticalGuidance
- M365-voice
appliesto:
- Microsoft Teams
description: "This document describes the behavior of chat, call routing and presence between users of Teams and Skype for Business, both in-tenant and federated, based on assigned TeamsUpgrade modes. It includes routing optimizations,  presence behavior, as well as the change of default TeamsUpgrade mode from *Legacy* to *Islands* and the impending retirement of *Legacy*."
---

# Coexistence with Skype for Business

Coexistence and interoperability between Skype for Business and Teams clients and users is defined by TeamsUpgrade modes, described in [Migration and interoperability guidance for organizations using Teams together with Skype for Business](migration-interop-guidance-for-teams-with-skype.md).

Any given user will always be assigned a TeamsUpgrade mode, either by default or explicitly by the administrator. The default value is *Islands*. Users upgraded to Teams have the mode of *TeamsOnly*. *SfBOnly*, *SfBWithTeamsCollab*, and *SfBWithTeamsCollabAndMeetings* are also possible modes.


## Routing parameters

The TeamsUpgrade mode of the recipient is key in determining the behavior of chats, calls, and presence, both within a tenant and across federated tenants.

If the sender is using Teams, the routing decision is made when creating a new conversation thread. Existing conversation threads in Teams always retain the routing method determined when the thread was created: Teams supports persistent threads.

 Thread routing methods are:  

- *native* for a Teams to Teams conversation in-tenant
- *interop* for a Teams to Skype for business conversation in-tenant
- *federated* for a federated conversation across tenants

The parameters that determine the thread routing method are:

- The TeamsUpgrade mode of the recipient
- The client used by the sender
- Whether the conversation is new, or part of an existing thread
- Whether the conversation is in-tenant or federated
- Whether the conversation is possible
    - *In-tenant* interoperability requires that the tenant is either pure online or Skype for Business hybrid. Purely on-premise tenants can't have in-tenant interoperability.
    - *Cross-tenant federation* always requires proper Skype for Business federation configuration as well as proper Teams federation  configuration from both tenants. Skype for Business hybrid is not required of either tenant.
    - If the Skype for Business account of the originator is homed on-premise, that user can't use the Teams client for in-tenant interoperability or for federation. That user can only use the Skype for Business client for interoperability and federation.
    - Teams to Teams communication is always possible in-tenant.

> [!NOTE]
> Currently, all federation involving Teams leverages the Skype for Business federation pipeline as well as Teams – Skype for Business interoperability. We are planning native Teams – Teams federation. The present document will be updated upon release of native federation.

# Chat and call routing

## In-tenant routing for new chats or calls 

The tables below capture routing of in-tenant chat and calls, and are valid for new calls or chats that are not started from a preexisting thread. It describes which client will receive a new call or chat, if originated by a user on the left, to an in-tenant recipient user on the right.

Messages sent to TeamsOnly users will always route to Teams. Messages sent to SfB\* users will always route to Skype for Business, if the conversation is possible as described above. Messages sent to Islands users will always route to the same client from which they were sent.

The tables below show which client in a given mode will receive a call from the originator (three leftmost columns), depending on the originator’s mode, client chosen, and where their Skype for Business client is homed (on-prem or online).

In the tables that follow: 
- **SfB\*** represents any of the following modes: *SfBOnly*, *SfBWithTeamsCollab*, *SfBWithTeamsCollabAndMeetings*.

- *Italic text* highlights an interop conversation.

- **Not Possible** represents a situation in which the chat or call is not possible. The originator must use Skype for Business instead in these cases. This is one of the reasons why Microsoft’s prescriptive guidance to on-prem/hybrid customers is to use a mode other than Islands (typically SfBWithTeamsCollab) as the starting point of their upgrade journey to Teams.

**Table 1a: in-tenant new chat or call routing to an islands mode recipient**

| <br/><br/> Mode | Originator <br/><br/> Client | <br/><br/> SfB&nbsp;homed | | Recipient <br/><br/> Islands  |
|--- |--- |--- |--- |--- |
| Islands | Teams <br/> Skype for Business<br/> Teams<br/> Skype for Business| Online<br/> Online<br/> On-prem<br/>On-prem| &boxv;<br/>&boxv;<br/>&boxv;<br/>&boxv;|Teams <br/> Skype for Business<br/> Teams<br/> Skype for Business|
|SfB\* <br/> | Skype for Business<br/>Skype for Business<br/> | Online<br/> On-prem<br/> |&boxv;<br/>&boxv;|Skype for Business<br/>Skype for Business<br/>|
|TeamsOnly |Teams| Online<br/>|&boxv;<br/>|Teams|
| | | | | |

**Table 1b: in-tenant new chat or call routing to a recipient in an SfB\* mode**

| <br/><br/> Mode   | Originator <br/><br/> Client | <br/><br/> SfB&nbsp;homed | |   Recipient <br/><br/> SfB\*   |
|--- |--- |--- |---   |--- |
| Islands |Teams<br/>Skype for Business<br/>Teams <br/>Skype for Business  |Online<br/> Online<br/> On-prem<br/> On-prem<br/>  | &boxv;<br/>&boxv;<br/>&boxv;<br/>&boxv;<br/>| *Skype for Business* <br/> Skype for Business<br/> **Not Possible** <br/>Skype for Business<br/> |
|SfB\* <br/> | Skype for Business<br/>Skype for Business<br/> | Online<br/> On-prem<br/> |&boxv;<br/>&boxv; |  Skype for Business<br/>Skype for Business<br/> |
|TeamsOnly |Teams| Online<br/>|&boxv;<br/> |  *Skype for Business* <br/>| 
| | | | | |

**Table 1c: in-tenant new chat or call routing to a TeamsOnly mode recipient**

| <br/><br/> Mode   | Originator <br/><br/> Client | <br/><br/> SfB&nbsp;homed | |   Recipient <br/><br/> TeamsOnly  |
|--- |--- |--- |--- | --- |
| Islands   |Teams<br/>Skype for Business<br/>Teams <br/>Skype for Business<br/>|Online<br/> Online<br/> On-prem<br/> On-prem<br/>  | &boxv;<br/>&boxv;<br/>&boxv;<br/>&boxv;|  Teams <br/>*Teams* <br/>Teams <br/>*Teams*  |
|SfB\*  | Skype for Business<br/>Skype for Business<br/> | Online<br/> On-prem<br/> | &boxv;<br/>&boxv; | *Teams*  <br/>*Teams*   |
|TeamsOnly  | Teams | Online |  &boxv; |Teams   |
|  |  |  | | |

## Federated routing for new chats or calls
  
The tables below capture routing of federated calls and chats, and are  valid for new calls or chats. They describe which client will receive a new call or chat, if originated by a user on the left, to a federated target user on the right.

In summary, if the conversation is possible as described above, messages sent to TeamsOnly users will always land in Teams; messages sent to SfB\* users will always land in Skype for Business; messages sent to Islands users will always land in Skype for Business regardless of the client from which they were sent. Routing for federated chats and calls differs from in-tenant routing in that Islands users will always receive a federated communication in Skype for Business.

This is because we cannot assume that a federated Skype for Business partner already uses Teams if they are in Islands mode. Islands is the default mode, however we can't assume all Islands users run Teams. By routing to Skype for Business we ensure that no communication to an Islands user fails. If we routed to Teams, that communication could be missed if the target did not use Teams. Routing to Skype for Business ensures the message will always be received.  

> [!NOTE]
> Current implementation of Teams federation is based upon Skype for Business federation, therefore it leverages the interoperability infrastructure (which requires the tenant of the originator to be either pure online or Skype for Business hybrid) and provides a reduced set of capabilities compared to a native thread. We expect to provide native Teams to Teams federation in the future, at which point the thread will be native and provide full capabilities.

The tables below describe which client will receive a call from the originator (three leftmost columns), depending on the originator’s mode, client chosen, and where their Skype for Business client is homed (on-prem or online).

**Table 2a: federated new chat or call routing to an Islands recipient**

| <br/><br/>Mode   | Originator<br/><br/> Client| <br/><br/>SfB homed| | Recipient<br/><br/> Islands |
|--- |--- |--- |--- |--- |
| Islands |Teams<br/>Skype for Business <br/>Teams <br/>Skype for Business  |Online<br/> Online<br/> On-prem<br/> On-prem<br/>  | &boxv;<br/>&boxv;<br/>&boxv;<br/>&boxv;<br/>| *Skype for Business* <br/> Skype for Business <br/> **Not Possible**   <br/> Skype for Business |
| SfB\* |Skype for Business <br/>Skype for Business |Online<br/> On-prem<br/> | &boxv;<br/>&boxv;|Skype for Business <br/>Skype for Business |
| TeamsOnly |Teams |Online| &boxv;|*Skype for Business* |
|  | | | | 

**Table 2b: federated new chat or call routing to to a recipient in an SfB\* mode**

| <br/><br/>Mode   | Originator<br/><br/> Client| <br/><br/>SfB homed| |  Recipient<br/><br/> SfB\* |  
|--- |--- |--- |--- |--- |
| Islands |Teams<br/>Skype for Business <br/>Teams <br/>Skype for Business <br/>|Online<br/> Online<br/> On-prem<br/> On-prem<br/> | &boxv;<br/>&boxv;<br/>&boxv;<br/>&boxv;<br/>| *Skype for Business* <br/> Skype for Business <br/> **Not Possible** <br/>Skype for Business <br/> |  
| SfB\* |Skype for Business <br/>Skype for Business  |Online<br/> On-prem<br/>  |&boxv;<br/>&boxv; | Skype for Business <br/>Skype for Business  |
| TeamsOnly | Teams|Online |&boxv; |*Skype for Business*  |
|  | | | | |

**Table 2c: federated new chat or call routing to a TeamsOnly mode recipient**

| <br/><br/>Mode | Originator<br/><br/> Client| <br/><br/>SfB homed| |  Recipient<br/>  <br/> TeamsOnly  |
|--- |--- |--- |--- |--- |
| Islands  |Teams<br/>Skype for Business <br/>Teams <br/>Skype for Business <br/>|Online<br/> Online<br/> On-prem<br/> On-prem<br/>  | &boxv;<br/>&boxv;<br/>&boxv;<br/>&boxv;| Teams <br/>*Teams* <br/>**Not Possible** <br/>*Teams* |
| SfB\* |Skype for Business <br/>Skype for Business  | Online<br/> On-prem| &boxv;<br/>&boxv;|*Teams* <br/>*Teams*   |
| TeamsOnly |Teams |Online |&boxv; |Teams |
|  | | | | |

## Chats and calls from pre-existing threads

### From Teams

Calls or chats started from a pre-existing persistent thread in Teams will be routed in the same manner as that thread, if that routing option is still available.

If the pre-existing persistent thread in Teams was a native thread (i.e. routed to Teams), additional chat messages and calls from that thread will go to Teams. If it was an interop thread (i.e. routed to Skype for Business), additional chat messages and calls will go to Skype for Business (again assuming routing options are available).

> [!NOTE]
> It's possible for pre-existing threads in Teams to no longer be routable, such as when the thread was an interop thread to a user that is now upgraded to Teams. Since it was created as an interop thread, the thread would route to Skype for Business, but that user no longer can use Skype for Business for chat and calling. In that case, the thread will be disabled and not permit further communication.

### From Skype for Business

Skype for Business threads do not persist beyond the 10 min. SIP session timeout. Chats and calls from an existing thread in Skype for Business prior to expiration of the SIP session will be routed in the same manner as the thread. Calls and chats from an existing thread in Skype for Business beyond the SIP session timeout will be routed to the remote party’s Skype for Business, regardless of which client the original thread came from on the other party’s side.

## Availability

Both the in-tenant and federated behaviors described above are available, with the following limitations:

- External attendees whose tenants reside in a different GoLocal deployment or geography won’t see IM chat while in a "federated" meeting
- Federation and interop between Multitenant O365 and Sovereign Clouds is not supported

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


## In-tenant presence

Messages sent to TeamsOnly users will always land in Teams. Messages sent to SfB\* users will always land in Skype for Business, if the conversation is possible as described above. Messages sent to Islands users will always land in the client from which they were originated.

The table describes the Publisher’s presence that will be seen by a Watcher, depending on the mode of the Publisher and the client of the Watcher (for a new thread).

**Table 3: in-tenant presence (new thread)**

|Watcher <br/><br/>Client| |<br/><br/>Islands |Publisher <br/><br/>SfB\* |<br/>Teams Only|
|--- |--- |--- |--- |---|
|Skype for Business |&boxv;|Skype for Business | Skype for Business | Teams|
|Teams |&boxv; |Teams |Skype for Business |Teams |
| | | | |

## Federated presence

Federated presence is based upon the federated reachability shown in table 2.

The table below describes the Publisher’s presence that will be seen by a Watcher, depending on the mode of the Publisher and the client of the Watcher (for a new thread). In practice the client of the Watcher makes no difference in federation at this stage.

**Table 4: federated presence (new thread)**

|Watcher <br/><br/> Client | |<br/><br/> Islands  |Publisher <br/><br/> SfB\* |<br/><br/> Teams Only |
|--- |--- |--- |--- |---|
|Skype for Business |&boxv; |Skype for Business  | Skype for Business  | Teams  |
|Teams | &boxv;|Skype for Business |Skype for Business |Teams|
| | | | ||

## Presence in pre-existing threads

In order to align presence and reachability in pre-existing threads, the target’s presence exposed in that thread needs to be aligned with the routing of the thread, assuming routing is possible.

In particular, if a recipient you previously had a persistent interop conversation thread with was upgraded to Teams, that thread will no longer reflect accurate presence and will no longer be routable. You should start a new thread.

## Related Links
[Migration and interoperability guidance for organizations using Teams together with Skype for Business](https://docs.microsoft.com/en-us/microsoftteams/migration-interop-guidance-for-teams-with-skype)

[Video: Manage Coexistence and Interoperability between SfB and Teams](https://www.youtube.com/watch?v=wEc9u4S3GIA&list=PLaSOUojkSiGnKuE30ckcjnDVkMNqDv0Vl&index=11)
