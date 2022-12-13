---
title: Coexistence with Skype for Business
ms.author: mikeplum
author: MikePlumleyMSFT
manager: Serdars
ms.topic: conceptual
ms.service: msteams
ms.reviewer: francoid
audience: admin
ms.localizationpriority: medium
search.appverid: MET150
f1.keywords:
- NOCSH
ms.collection:
  - Teams_ITAdmin_JourneyFromSfB
  - M365-collaboration
appliesto:
  - Microsoft Teams
ms.custom: seo-marvel-mar2020
description: Coexistence behavior between Teams & Skype for Business, including routing parameters, chat & call routing, chats & calls from pre-existing threads, & presence.
---

# Coexistence with Skype for Business

Coexistence and interoperability between Skype for Business and Teams clients is controlled by coexistence modes. For more information, see [Migration and interoperability guidance for organizations using Teams together with Skype for Business](migration-interop-guidance-for-teams-with-skype.md). After the retirement of Skype for Business Online on July 31, 2021, users homed in the cloud are always TeamsOnly users. It is no longer possible to assign a coexistence mode other than TeamsOnly to an online user. Coexistence modes other than TeamsOnly are only relevant for organizations with on-premises deployments of Skype for Business Server or Lync Server 2013. In this article, any reference to "Skype for Business Server" also applies to Lync Server 2013.


## Determining a user's coexistence mode
All users in organizations without any on-premises deployment of Skype for Business Server are TeamsOnly mode, and the tenant's effective mode is also TeamsOnly. This can be confirmed by looking at TeamsUpgradeEffectiveMode property on the tenant or the user using Teams PowerShell.   Prior to the retirement of Skype for Business Online on July 31, 2021, organizations had the ability to change the coexistence mode for either the user or the tenant. This is no longer possible except for organizations with an on-premises deployment of Skype for Business Server, which must not have tenant-wide mode of TeamsOnly. You can confirm that coexistence mode can no longer be changed if TeamsUpgradePolicyIsReadOnly = "ModeAndNotifications" on either the user or tenant.  (TeamsUpgradePolicyIsReadOnly on any user will have the same value as the tenant's value.)  


 ```powershell
 //Check if Tenant is TeamsOnly and if mode is read only.
$t=Get-CsTenant
$t|fl TeamsUpgradeEffectiveMode, TeamsUpgradePolicyIsReadOnly

TeamsUpgradeEffectiveMode  : TeamsOnly
TeamsUpgradePolicyIsReadOnly: ModeAndNotifications

 //Check if user is TeamsOnly and if mode is read only.
$u=Get-CsOnlineUser
$u|fl TeamsUpgradeEffectiveMode, TeamsUpgradePolicyIsReadOnly

TeamsUpgradeEffectiveMode  : TeamsOnly
TeamsUpgradePolicyIsReadOnly: ModeAndNotifications
 ```

In an organization with an on-premises deployment of Skype for Business Server, the tenant global policy for TeamsUpgradePolicy can have any mode *other than TeamsOnly*. The allowed modes are: *SfBOnly*, *SfBWithTeamsCollab*, and *SfBWithTeamsCollabAndMeetings*. Users can also be directly assigned an instance of TeamsUpgradePolicy, which would supersede the tenant global policy.  Users homed in the cloud must be TeamsOnly, and users homed on-premises must be any mode other than TeamsOnly.  If a user is not assigned an instance of TeamsUpgradePolicy, the user receives the value from the tenant global policy. 

## Routing parameters

The coexistence mode of the recipient determines the behavior of chats, calls, and presence, both within a tenant and across federated tenants. If the sender is using Teams, the routing decision is made when creating a new conversation thread. Once a conversation thread is created, its routing does not change, and it retains the routing method determined when the thread was created.

Thread routing methods are:

- *native* for a Teams to Teams conversation in-tenant
- *interop* for a Teams to Skype for Business conversation in-tenant
- *native federated* for a federated conversation across tenants when both users have TeamsOnly mode. 
- *interop federated* for a federated conversation across tenants that relies on interop between Skype for Business and Teams.

> [!NOTE]
> - Native conversations, whether in the same tenant or federated scenarios, occur when both the receiver and sender have TeamsOnly mode. The conversation will be a native chat experience, which includes all the rich messaging and calling capabilities. To learn more, read [Native chat experience for external (federated) users in Teams](native-chat-for-external-users.md). 
> - If either of the conversation participants do NOT have TeamsOnly mode, the conversation is an interop experience with text-only messages.
> - Federated communications between TeamsOnly users in multi-tenant clouds and special cloud environments (for example, government clouds) will appear as interop federated chats.


When creating a new conversation, the factors that determine how the thread is routed are:

- The coexistence mode of the recipient
- The client used by the sender
- Whether the conversation is in-tenant or federated
- Whether the conversation is possible. If a user has a Skype for Business account homed on-premises, that user can't use the Teams client for in-tenant interoperability or for federation. That user can only use the Skype for Business client for interoperability and federation. Note that Teams to Teams communication is always possible in-tenant.

## Chat and call routing
The tables below show which client in a given mode will receive a call from the originator (three leftmost columns). Which cient receives the call depends on the originator's mode, the client chosen, and where the Skype for Business account is homed (on-premises or online).

In the tables that follow:

- **Skype for Business*** represents any of the following modes: *SfBOnly*, *SfBWithTeamsCollab*, *SfBWithTeamsCollabAndMeetings*.
- *Italic text* highlights an interop conversation.
- **Not Possible** represents a situation in which the chat or call is not possible. The originator must use Skype for Business instead in these cases. This is one of the reasons why Microsoft's prescriptive guidance to on-premises and hybrid customers is to use a mode other than Islands (typically SfBWithTeamsCollab) as the starting point for their upgrade journey to Teams.


### In-tenant routing for new chats or calls

The tables below capture routing of in-tenant chat and calls, and are valid for new calls or chats that are not started from a pre-existing thread. It describes which client will receive a new call or chat, if originated by a user on the left, to an in-tenant recipient user on the right.  Messages sent to TeamsOnly users will always route to Teams. Messages sent to Skype for Business users will always route to Skype for Business. Messages sent to Islands users will always route to the same client from which they were sent.


#### Table 1a: in-tenant new chat or call routing to a TeamsOnly mode recipient

<br>

|<br><br>Mode|Originator<br><br>Client|<br><br>Skype for Business&nbsp;homed|<br><br>Route-->|TeamsOnly Recipient|
|---|---|---|:---:|---|
|TeamsOnly|Teams|Online|&boxv;|Teams|
|Islands|Teams <br> Skype for Business| On-premises <br> On-premises|&boxv;<br>&boxv;|Teams <br> *Teams*|
|Skype for Business | Skype for Business | On-premises|&boxv;|*Teams*|
||||||

#### Table 1b: in-tenant new chat or call routing to an islands mode recipient

<br>

|<br><br>Mode|Originator<br><br>Client|<br><br>Skype for Business&nbsp;homed|<br><br>Route-->|Islands Recipient|
|---|---|---|:---:|---|
|TeamsOnly|Teams|Online|&boxv;|Teams|
|Islands| Teams <br> Skype for Business|On-premises<br>On-premises|&boxv;<br>&boxv;| Teams <br> Skype for Business|
|Skype for Business |Skype for Business | On-premises|&boxv;| Skype for Business|
||||||

#### Table 1c: in-tenant new chat or call routing to a recipient in a Skype for Business mode

<br>

|<br><br>Mode|Originator<br><br>Client|<br><br>Skype for Business&nbsp;homed|<br><br>Route-->|Skype for Business Recipient|
|---|---|---|:---:|---|
|TeamsOnly|Teams|Online|&boxv;|*Skype for Business*|
|Islands|Teams <br> Skype for Business| On-premises <br> On-premises|&boxv;<br>&boxv;| **Not Possible** <br> Skype for Business|
|Skype for Business | Skype for Business| On-premises|&boxv;| Skype for Business|
||||||


### Federated routing for new chats or calls

The tables below capture routing of federated calls and chats, and are valid for new calls or chats. They describe which client will receive a new call or chat, if originated by a user on the left, to a federated target user on the right. In summary, if the conversation is possible as described above, messages sent to TeamsOnly users will always land in Teams; messages sent to Skype for Business mode users will always land in Skype for Business; messages sent to Islands users will always land in Skype for Business regardless of the client from which they were sent. 

Routing for federated chats and calls differs from in-tenant routing in that Islands users will always receive a federated communication in Skype for Business. This is because the federated partner may not yet be using Teams. Routing to Skype for Business for any islands mode recipeint ensures messages will always be received.  Routing to Teams could potentially result in missed communication if the intended recipient does not use Teams. 

#### Table 2a: federated new chat or call routing to a TeamsOnly mode recipient

<br>

|<br><br>Mode|Originator<br><br>Client|<br><br>Skype for Business homed|<br><br>Route-->|TeamsOnly Recipient|
|---|---|---|:---:|---|
|TeamsOnly|Teams|Online|&boxv;|Teams|
|Islands|Teams <br> Skype for Business|On-premises <br> On-premises|&boxv;<br>&boxv;|**Not Possible** <br> *Teams*|
|Skype for Business |Skype for Business|On-premises|&boxv;| *Teams*|
||||||


#### Table 2b: federated new chat or call routing to an Islands recipient

<br>

|<br><br>Mode|Originator<br><br>Client|<br><br>Skype for Business homed|<br><br>Route-->|Islands Recipient|
|---|---|---|:---:|---|
|TeamsOnly|Teams|Online|&boxv;|*Skype for Business*|
|Islands|Teams <br> Skype for Business| On-premises <br> On-premises|&boxv;<br>&boxv;| **Not Possible** <br> Skype for Business|
|Skype for Business |Skype for Business| On-premises|&boxv;| Skype for Business|
|||||

#### Table 2c: federated new chat or call routing to a recipient in an Skype for Business mode

<br>

|<br><br>Mode|Originator<br><br>Client|<br><br>Skype for Business homed|<br><br>Route-->|Skype for Business Recipient|
|---|---|---|:---:|---|
|TeamsOnly|Teams|Online|&boxv;|*Skype for Business*|
|Islands|Teams <br> Skype for Business| On-premises <br> On-premises|&boxv;<br>&boxv;|**Not Possible** <br> Skype for Business|
|Skype for Business |Skype for Business|On-premises|&boxv;<br>&boxv;|Skype for Business|
||||||



## Chats and calls from pre-existing threads

### From Teams

Calls or chats started from a pre-existing conversation thread in Teams are routed in the same manner as that thread. If the pre-existing thread in Teams was a native thread (i.e. routed to Teams), additional chat messages and calls from that thread will go to Teams. If it was an interop thread (i.e. routed to Skype for Business), additional chat messages and calls will go to Skype for Business (assuming routing options are available).

> [!NOTE]
> It's possible for pre-existing threads in Teams to no longer be routable, such as when the thread was an interop thread to a user that has since been upgraded to Teams. Since it was created as an interop thread, the thread would route to Skype for Business, but that user no longer can use Skype for Business for chat and calling. In that case, the thread will be disabled and not permit further communication.

### From Skype for Business

Skype for Business threads do not persist beyond the 10 minute SIP session timeout. Chats and calls from an existing thread in Skype for Business prior to expiration of the SIP session will be routed in the same manner as the thread. Calls and chats from an existing thread in Skype for Business beyond the SIP session timeout will be routed to the remote party's Skype for Business, regardless of which client the original thread came from on the other party's side.

## Presence

In situations where some users are using the Teams client and others are using the Skype for Business client, it's possible some of these users are using both clients. It's important to understand that Presence is published based on a user's coexistence mode. For example, if an originator's chat or call should land on the target's Skype for Business client, then it's the Skype for Business client's presence that should be shown to the originator. If it should land on the target's Teams client, then it's the Teams client's presence that should be shown.

Presence is shared based on a user's coexistence mode as described below:

- If a user is in TeamsOnly mode, then any other user (whether in Teams or Skype for Business) will see that TeamsOnly user's Teams presence
- If a user is in any of the Skype for Business modes (SfbOnly, SfbWithTeamsCollab, SfbWithTeamsCollabAndMeetings), then any other user (whether in Teams or Skype for Business) will see that Skype for Business user's Skype for Business presence
- If a user is in Islands mode, presence in Teams and presence in Skype for Business are independent (the values need not match) and other users will see one or the other presence of the Islands user, depending on whether they are in the same tenant or in a federated tenant and which client they use
  - From Teams, any other user within the same tenant will see the Islands user's Teams presence; this is aligned with the in-tenant routing table above
  - From Teams, any other user in a federated tenant will see the Islands user's Skype for Business presence; this is aligned with the federated routing table above
  - From Skype for Business, any other user will see the Islands user's Skype for Business presence (both in-tenant and federated); this is aligned with the routing tables above

### In-tenant presence

Messages sent to TeamsOnly users will always land in Teams. Messages sent to Skype for Business mode users will always land in Skype for Business, if the conversation is possible as described above. Messages sent to Islands users will always land in the client from which they were originated.

The table describes the Publisher's presence that will be seen by a Watcher, depending on the mode of the Publisher and the client of the Watcher (for a new thread).

#### Table 3: in-tenant presence (new thread)

<br>

|Watcher<br><br>Client|<br><br>Route-->|<br><br>Islands|Publisher<br><br>Skype for Business|<br>Teams Only|
|---|:---:|---|---|---|
|Skype for Business|&boxv;|Skype for Business|Skype for Business|Teams|
|Teams|&boxv;|Teams|Skype for Business|Teams|
|||||

### Federated presence

Federated presence is based upon the federated reachability shown in table 2.  The table below describes the Publisher's presence that will be seen by a Watcher, depending on the mode of the Publisher and the client of the Watcher (for a new thread). In practice the client of the Watcher makes no difference in federation at this stage.

#### Table 4: federated presence (new thread)

<br>

|Watcher<br><br>Client|<br><br>Route-->|<br><br>Islands|Publisher<br><br>Skype for Business|<br><br>Teams Only|
|---|:---:|---|---|---|
|Skype for Business|&boxv;|Skype for Business|Skype for Business|Teams|
|Teams|&boxv;|Skype for Business|Skype for Business|Teams|
||||||

### Presence in pre-existing threads

In order to align presence and reachability in pre-existing threads, the target's presence exposed in that thread needs to be aligned with the routing of the thread, assuming routing is possible.  In particular, if a recipient you previously had a persistent interop conversation thread with was upgraded to Teams, that thread will no longer reflect accurate presence and will no longer be routable. You should start a new thread.

### Federation and interop with Office 365 operated by 21Vianet

Federation and interop between multi-tenant Office 365 and Office 365 operated by 21Vianet are supported when the multi-tenant Office 365 users are in Teams Only mode. In such a scenario, Skype for Business Online users in Office 365 operated by 21Vianet will be able to communicate with Teams Only users in multi-tenant Office 365 through chats and calls. The following table shows the supported scenarios in this configuration:
 
|Scenario|Origin|Recipient|Supported?|
|---|---|---|---|
|Presence|Teams <br> Skype for Business <br> | Skype for Business <br> Teams|Yes<br>Yes|
|Chat|Teams <br> Skype for Business <br> | Skype for Business <br> Teams|Yes (1:1 only)<br>Yes(1:1 only)|
|Audio Calls|Teams <br> Skype for Business <br> | Skype for Business <br> Teams|Yes (1:1 only)<br>Yes (1:1 only)|
|Video Calls|Teams <br> Skype for Business <br> | Skype for Business <br> Teams|Yes (1:1 only)<br>Yes (1:1 only)|
|Screen Sharing|Teams <br> Skype for Business <br> | Skype for Business <br> Teams |Yes (through a promoted Teams meeting)<br>Yes (through a promoted Skype for Business meeting)|
|||||


## Related Links
[Migration and interoperability guidance for organizations using Teams together with Skype for Business](./migration-interop-guidance-for-teams-with-skype.md)

[Video: Manage Coexistence and Interoperability between Skype for Business and Teams](https://www.youtube.com/watch?v=wEc9u4S3GIA&list=PLaSOUojkSiGnKuE30ckcjnDVkMNqDv0Vl&index=11)
