---
title: Migration and interoperability guidance for organizations using Teams together with Skype for Business
author: lanachin
ms.author: v-lanac
manager: serdars
ms.topic: conceptual
ms.service: msteams
ms.reviewer: bjwhalen
description: Guidance for managing the transition to Teams from Skype for Business 
localization_priority: Normal
search.appverid: MET150
f1keywords: ms.teamsadmincenter.teamsupgrade.overview
MS.collection: 
- Teams_ITAdmin_PracticalGuidance
- M365-collaboration
appliesto:
- Microsoft Teams
---
# Migration and interoperability guidance for organizations using Teams together with Skype for Business

> [!Tip] 
> Watch the following session to learn about [Coexistence and Interoperability](https://aka.ms/teams-upgrade-coexistence-interop)

As an organization with Skype for Business starts to adopt Teams, administrators can manage the user experience in their organization using the concept of coexistence "mode" which is a property of TeamsUpgradePolicy. Using mode, administrators manage interop and migration as they manage the transition from Skype for Business to Teams.  A user's mode determines in which client incoming chats and calls land as well as in what service (Teams or Skype for Business) new meetings are scheduled. It also governs what functionality is available in the Teams client. 


## Fundamental concepts

1.  *Interop* : 1 to 1 communication between a Lync/Skype for Business user and a Teams user.

2.  *Federation* : Communication between users from different tenants.

3.  All Teams users have an underlying Skype for Business account that is “homed” either online or on-premises:
    - Users already using Skype for Business Online use their existing online account.
    - Users already using Skype for Business/Lync on-premises use their existing on-premises account.
    - Users for whom we cannot detect an existing Skype for Business account will have a Skype for Business Online account automatically provisioned when the Teams user is created.

4.  If you have an on-premises deployment of either Skype for Business or Lync, and you want those users to be Teams users, you must at a minimum ensure that Azure AD Connect is syncing the msRTCSIP-DeploymentLocator attribute into AAD, so that Teams/Skype for Business Online properly detects your on-premises environment. Furthermore, to move any users to Teams-only mode (i.e., upgrade a user), *you must first configure Skype for Business hybrid mode*. For more details, see [Configure Azure AD Connect for Skype for Business and Teams](https://docs.microsoft.com/en-us/SkypeForBusiness/hybrid/configure-azure-ad-connect).

5.  Interop between Teams and Skype for Business users is only possible *if the Teams user is homed online in Skype for Business*. The recipient Skype for Business user can be homed either on-premises (and requires configuring Skype for Business Hybrid) or online. Users who are homed in Skype for Business on-premises can use Teams in Islands mode (defined later in this doc), but they cannot use Teams to interop or federate with other users who are using Skype for Business.  

6.	Upgrade and interop behavior are determined based on Coexistence mode of a user, described later below. Mode is managed by TeamsUpgradePolicy. 

7.  Upgrading a user to the TeamsOnly mode ensures that all incoming chats and calls will always land in the user's Teams client, regardless of what client it originated from. These users will also schedule all new meetings in Teams. To be in TeamsOnly mode, a user must be homed online in Skype for Business. This is required to ensure interop, federation, and full administration of the Teams user.To upgrade a user to TeamsOnly:
    - If the user is homed in Skype for Business online (or never had any Skype account), grant them TeamsUpgradePolicy with Mode=TeamsOnly using the "UpgradeToTeams" instance using PowerShell, or use the Teams Admin Center to select the TeamsOnly mode.
    - If the user is homed on-premises, use `Move-CsUser` from the on-premises admin tools to first move the user to Skype for Business Online.  If you have Skype for Business Server 2019 or CU8 for Skype for Business Server 2015, you can specify the `-MoveToTeams` switch in `Move-CsUser` to move the user directly to Teams as part of the move online. This option will also migrate the user's meetings to Teams. If `-MoveToTeams` is not specified or not available, then after `Move-CsUser` completes, assign TeamsOnly mode to that user using either PowerShell or the Teams Admin Center. For more details see [Move users between on-premises and cloud](https://docs.microsoft.com/skypeforbusiness/hybrid/move-users-between-on-premises-and-cloud).  For more details on meeting migration, see [Using the Meeting Migration Service (MMS)](https://docs.microsoft.com/skypeforbusiness/audio-conferencing-in-office-365/setting-up-the-meeting-migration-service-mms).

8.	To use Microsoft Phone System with Teams, users must be in TeamsOnly mode (i.e., homed in Skype for Business Online and upgraded to Teams), and they must either be configured for Microsoft Phone System [Direct Routing](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/Direct-Routing-is-now-Generally-Available/ba-p/210359#M1277) (which allows you to use Phone System with your own SIP trunks and SBC) or have an Office 365 Calling Plan. Microsoft Phone System Direct Routing is not supported in Islands mode.    

9.  Scheduling Teams meetings with Audio Conferencing (dial-in or dial-out via PSTN) is available regardless of whether the user is homed in Skype for Business Online or Skype for Business on-premises. 


## Coexistence modes

Interop and migration are managed based on “coexistence mode” using TeamsUpgradePolicy. Co-existence modes provide a simple, predictable experience for end users as organizations transition from Skype for Business to Teams. For an organization moving to Teams, the TeamsOnly mode is the final destination for each user, though not all users need to be assigned TeamsOnly (or any mode) at the same time. Prior to users reaching TeamsOnly mode, organizations can use any of the Skype for Business modes (SfBOnly, SfBWithTeamsCollab, SfBWithTeamsCollabAndMeetings) to ensure predictable communication between users who are TeamsOnly and those who aren’t yet.


From a technical perspective, a user’s mode governs several  aspects of the user's experience:

- *Incoming routing*: In which client (Teams or Skype for Business) do incoming chats and calls land? 
- *Presence publishing*: Is the user's presence that is shown to other users based on their activity in Teams or Skype for Business? 
- *Meeting scheduling*: Which service is used for scheduling new meetings and ensuring that the proper add-in is present in Outlook? Note that TeamsUpgradePolicy does not govern meeting join. Users can always *join* any meeting, whether it be a Skype for Business meeting or a Teams meeting.
- *Client experience*: What functionality is available in Teams and/or Skype for Business client? Can users initiate calls and chats in Teams, Skype for Business or both? Is Teams & Channels experience available?  

For more details on routing and presence behavior based on mode, see [Coexistence with Skype for Business](https://docs.microsoft.com/en-us/MicrosoftTeams/coexistence-chat-calls-presence).

However, from an experience perspective, mode can more simply be described as defining the experience for:
- *Chat and Calling*: Which client does a user use?
- *Meeting Scheduling*: Do users schedule new meetings as Teams or Skype for Business meetings?
- *Availability of collaboration functionality in Teams client*. Is Teams & Channels and Files functionality available while users still have Skype for Business?

The modes are listed below.
</br>
</br>

|Mode|Calling and Chat|Meeting Scheduling<sup>1</sup>|Teams & Channels|Use Case|
|---|---|---|---|---|
|**TeamsOnly<sup>2</sup>**</br>*Requires home in Skype for Business Online*|Teams|Teams|Yes|The final state of being upgraded. Also the default for new tenants with <500 seats.|
|Islands|Either|Either|Yes|Default configuration. Allows a single user to evaluate both clients side by side. Chats and calls can land in either client, so users must always run both clients. To avoid a confusing or regressed Skype for Business experience, external (federated) communications, PSTN voice services and voice applications, Office integration, and several other integrations continue to be handled by Skype for Business.|
|SfBWithTeamsCollabAndMeetings<sup>2</sup>|Skype for Business|Teams|Yes|"Meetings First". Primarily for on-premises organizations to benefit from Teams meeting functionality, if they are not yet ready to move calling to the cloud.|
|SfBWithTeamsCollab|Skype for Business|Skype for Business|Yes|Alternate starting point for complex organizations that need tighter administrative control.|
|SfBOnly|Skype for Business|Skype for Business|No<sup>3</sup>|Specialized scenario for organizations with strict requirements around data control. Teams is used only to join meetings scheduled by others.|
||||||

</br>
</br>

**Notes:**

<sup>1</sup> The ability to join an existing meeting (whether scheduled in Teams or in Skype for Business) is not governed by mode. By default, users can always join any meeting they have been invited to.

<sup>2</sup> By default, when assigning either TeamsOnly or SfbWithTeamsCollabAndMeetings to an individual user, any existing Skype for Business meetings scheduled by that user for the future are converted to Teams meetings. If desired, you can leave these meetings as Skype for Business meetings either by specifying  `-MigrateMeetingsToTeams $false` when granting TeamsUpgradePolicy, or by unselecting the checkbox in the Teams Admin portal.   Note that the ability to convert meetings from Skype for Business to Teams is not avaialble when granting TeamsUpgradePolicy on a tenant-wide basis. 

<sup>3</sup> Currently, Teams does not have the ability to disable the Teams and Channels functionality so this remains enabled for now.



## TeamsUpgradePolicy: managing migration and co-existence

TeamsUpgradePolicy exposes two key properties: Mode and NotifySfbUsers. 
</br>
</br>

|Parameter|Type|Allowed values</br>(default in italics)|Description|
|---|---|---|---|
|Mode|Enum|*Islands*</br>TeamsOnly</br>SfBOnly</br>SfBWithTeamsCollab</br>SfBWithTeamsCollabAndMeetings|Indicates the mode the client should run in.|
|NotifySfbUsers|Bool|*False* or true|Indicates whether to show a banner in the Skype for Business client informing the user that Teams will soon replace Skype for Business. This cannot be true if Mode=TeamsOnly.|
|||||

Teams provides all relevant instances of TeamsUpgradePolicy via built-in, read-only policies. Therefore, only Get and Grant cmdlets are available. The built-in instances are listed below.
</br>
</br>

|Identity|Mode|NotifySfbUsers|
|---|---|---|
|Islands|Islands|False|
|IslandsWithNotify|Islands|True|
|SfBOnly|SfBOnly|False|
|SfBOnlyWithNotify|SfBOnly|True|
|SfBWithTeamsCollab|SfBWithTeamsCollab|False|
|SfBWithTeamsCollabWithNotify|SfBWithTeamsCollab|True|
|SfBWithTeamsCollabAndMeetings|SfBWithTeamsCollabAndMeetings|False|
|SfBWithTeamsCollabAndMeetingsWithNotify|SfBWithTeamsCollabAndMeetings|True|
|UpgradeToTeams|TeamsOnly|False|
|Global</br>*Default*|Islands|False|
||||

These policy instances can be granted either to individual users or on a tenant-wide basis. For example:
- To upgrade a user ($SipAddress) to Teams, grant the “UpgradeToTeams” instance:</br>
`Grant-CsTeamsUpgradePolicy -PolicyName UpgradeToTeams -Identity $SipAddress`
- To upgrade the entire tenant, omit the identity parameter from the grant command:</br>
`Grant-CsTeamsUpgradePolicy -PolicyName UpgradeToTeams`


## Federation Considerations

Federation from Teams to another user using Skype for Business requires the Teams user be homed online in Skype for Business. Eventually, Teams users homed in Skype for Business on-premises will be able to federate with Teams only users.

TeamsUpgradePolicy governs routing for incoming federated chats and calls. Federated routing behavior is the same as for same-tenant scenarios, *except in Islands mode*.  When recipients are in Islands mode: 
- Chats and calls initiated from Teams land in SfB if the recipient is in a *federated tenant*.
- Chats and calls initiated from Teams land in Teams if the recipient is in the *same tenant*.
- Chats and calls initiated from SfB always land in Skype for Business.

For more details, see [Coexistence with Skype for Business](https://docs.microsoft.com/en-us/MicrosoftTeams/coexistence-chat-calls-presence).

## The Teams client user experience when using SfB modes
When a user is in any of the Skype for Business modes (SfBOnly, SfBWithTeamsCollab, SfBWithTeamsCollabAndMeetings), all incoming chats and calls are routed to the user’s Skype for Business client. To avoid end user confusion and ensure proper routing, calling and chat functionality in the Teams client is automatically disabled when a user is in any of the Skype for Business modes. Similarly, meeting scheduling in Teams is automatically disabled when users are in the SfBOnly or SfBWithTeamsCollab modes, and automatically enabled when a user is in the SfBWithTeamsCollabAndMeetings mode. For details, see [Teams client experience and conformance to coexistence modes](https://docs.microsoft.com/en-us/MicrosoftTeams/teams-client-experience-and-conformance-to-coexistence-modes).

> [!Note] 
> - Prior to delivery of the automatic enforcement of Teams and Channels, the SfbOnly and SfBWithTeamsCollab modes behave the same.


## Detailed mode descriptions
</br>
</br>

|Mode|Explanation|
|---|---|
|**Islands**</br>(default)|A user runs both Skype for Business and Teams side-by-side. This user:</br><ul><li>Can initiate chats and VoIP calls in either Skype for Business or Teams client. Note: Users with Skype for Business homed on-premises cannot initiate from Teams to reach another Skype for Business user, regardless of the recipient's mode.<li>Receives chats & VoIP calls initiated in Skype for Business by another user in their Skype for Business client.<li>Receives chats & VoIP calls initiated in Teams by another user in their Teams client if they are in the *same tenant*.<li>Receives chats & VoIP calls initiated in Teams by another user in their Skype for Business client if they are in a  *federated tenant*. <li>Has PSTN functionality as noted below:<ul><li>When the user is homed in Skype for Business on-premises and has Enterprise Voice, PSTN calls are always initiated and received in Skype for Business.<li>When the user is homed on Skype for Business Online and has Microsoft Phone System, the user always initiates and receives PSTN calls in Skype for Business:<ul><li>IThis happens regardless of whether the user has a Microsoft Calling Plan, or connects to the PSTN network via either Skype for Business Cloud Connector Edition or an on-premises deployment of Skype for Business Server (hybrid voice)<li>Note: Microsoft Teams Phone System Direct Routing is not supported in Islands mode.</ul></ul><li>•	Receives Microsoft Call Queues and Auto-Attendant calls in Skype for Business<li>Can schedule meetings in Teams or Skype for Business (and will see both plug-ins by default).<li>Can join any Skype for Business or Teams meeting; the meeting will open in the respective client.</ul>|
|**SfBOnly**|A user runs only Skype for Business. This user:</br><ul><li>Can initiate chats and calls from Skype for Business only.<li>Receives any chat/call in their Skype for Business client, regardless of where initiated, unless the initiator is a Teams user with Skype for Business homed on-premises.*<li>Can schedule only Skype for Business meetings, but can join Skype for Business or Teams meetings.</br>\**Using Islands mode with on-premises users is not recommended in combination with other users in SfBOnly mode. If a Teams user with Skype for Business homed on-premises initiates a call or chat to an SfBOnly user, the SfBOnly user is not reachable and receives a missed chat/call email.*|
|**SfBWithTeamsCollab**|A user runs both Skype for Business and Teams side-by-side. This user:</br><ul><li>Has the functionality of a user in SfBOnly mode.<li>Has Teams enabled only for group collaboration (Channels); chat/calling/meeting scheduling are disabled.</ul>|
|**SfBWithTeamsCollab</br>AndMeetings**|A user runs both Skype for Business and Teams side-by-side. This user:<ul><li>Has the chat and calling functionality of user in SfBOnly mode.<li>Has Teams enabled for group collaboration (channels - includes channel conversations); chat and calling are disabled.<li>Can schedule only Teams meetings, but can join Skype for Business or Teams meetings.</ul>|
|**TeamsOnly**</br>(requires SfB Online home)|A user runs only Teams. This user:<ul><li>Receives any chats and calls in their Teams client, regardless of where initiated.<li>Can initiate chats and calls from Teams only.<li>Can schedule meetings in Teams only, but can join Skype for Business or Teams meetings.<li>Can continue to use Skype for Business IP phones.<br><br>*Using TeamsOnly mode in combination with other users in Islands mode is not recommended until Teams adoption is saturated, i.e. all Islands mode users actively use and monitor both the Teams and Skype for Business clients. If a TeamsOnly user initiates a call or chat to an Islands user, that call or chat will land in the Islands user’s Teams client; if the Islands user does not use or monitor Teams, that user will appear offline and will not be reachable by the TeamsOnly user.*</ul> |
|||




## Related topics

[Coexistence with Skype for Business](https://docs.microsoft.com/en-us/microsoftteams/coexistence-chat-calls-presence)

[Teams client experience and conformance to coexistence modes](https://docs.microsoft.com/en-us/MicrosoftTeams/teams-client-experience-and-conformance-to-coexistence-modes)

[Get-CsTeamsUpgradePolicy](https://docs.microsoft.com/powershell/module/skype/get-csteamsupgradepolicy?view=skype-ps)

[Grant-CsTeamsUpgradePolicy](https://docs.microsoft.com/powershell/module/skype/grant-csteamsupgradepolicy?view=skype-ps)

[Get-CsTeamsUpgradeConfiguration](https://docs.microsoft.com/powershell/module/skype/get-csteamsupgradeconfiguration?view=skype-ps)

[Set-CsTeamsUpgradeConfiguration](https://docs.microsoft.com/powershell/module/skype/set-csteamsupgradeconfiguration?view=skype-ps)

[Using the Meeting Migration Service (MMS)](https://docs.microsoft.com/skypeforbusiness/audio-conferencing-in-office-365/setting-up-the-meeting-migration-service-mms)
