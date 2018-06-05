---
title: Migration and interoperability guidance for organizations using Teams together with Skype for Business
author: arachmanGitHub
ms.author: MyAdvisor
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: lehewe
description: Guidance for managing the transition to Teams from Skype for Business 
localization_priority: Priority
MS.collection: Strat_MT_TeamsAdmin
appliesto:
- Microsoft Teams
---
# Migration and interoperability guidance for organizations using Teams together with Skype for Business

In April of 2018, Microsoft clarified its guidance for migrating to Teams from Skype for Business and how these two clients can co-exist for a given user. At that time, we announced planned changes to simplify manageability and increase end user satisfaction. Since then, Microsoft has delivered an update to the admin user experience, consistent with that plan. The guidance in this document reflects those changes.

As previously announced, TeamsInteropPolicy will be retired (targeted for the end of Q3), and its functionality is being consolidated into TeamsUpgradePolicy. Interop and migration will be managed using “coexistence mode” as determined by TeamsUpgradePolicy, which is now available. Selection of the user’s mode will govern both routing of incoming calls and chats and in which client the user can initiate chats and calls or schedule meetings. While TeamsInteropPolicy will be retired, it still needs to be set in parallel with TeamsUpgradePolicy during the phaseout.  

As part of this effort, Microsoft recently updated the “Microsoft Teams & Skype for Business Admin Center” (also known as Modern Portal) to reflect the new management model based on coexistence modes. In Modern Portal, configuring TeamsUpgradePolicy will now automatically also set TeamsInteropPolicy to consistent value, so TeamsInteropPolicy is no longer exposed in the user interface. *However, admins using PowerShell must still set both TeamsUpgradePolicy and TeamsInteropPolicy together to ensure proper routing.* After the transition to TeamsUpgradePolicy is complete, it will no longer be necessary to also set TeamsInteropPolicy.
</br>
</br>
|**Managing Interop and Migration**|**Modern Portal**|**PowerShell**|
|----|----|----|----|
|Until September 2018 (dates subject to change)|Use TeamsUpgradePolicy|Use both TeamsUpgradePolicy and TeamsInteropPolicy |
|Post September 2018 (dates subject to change)|Use TeamsUpgradePolicy|Use TeamsUpgradePolicy only; TeamsInteropPolicy deprecated|
|||||

To account for the introduction of coexistence modes and the pending retirement of TeamsInteropPolicy, Microsoft is providing this guidance now so customers using Teams today can manage the transition.

## In this article

- [Fundamental concepts](#fundamental-concepts)
- [Coexistence modes](#coexistence-modes)
- [TeamsUpgradePolicy: managing migration and co-existence](#teamsupgradepolicy-managing-migration-and-co-existence)
- [TeamsInteropPolicy to be retired](#teamsinteroppolicy-to-be-retired)
- [Completing the transition to mode management](#completing-the-transition-to-mode-management)
- [Action required for organizations that have already used TeamsInteropPolicy](#action-required-for-organizations-that-have-already-used-teamsinteroppolicy)	
- [Detailed mode descriptions](#detailed-mode-descriptions)	
- [Summary of planned functionality changes to simplify coexistence and migration](#summary-of-planned-functionality-changes-to-simplify-coexistence-and-migration)	
- [Known issues](#known-issues)

## Fundamental concepts

1.	*Interop* : 1 to 1 communication between a Lync/Skype for Business user and a Teams user.

2.	*Federation* : Communication between users from different tenants.

3.	All Teams users have an underlying Skype for Business account that is “homed” either online or on-premises:
    - Users already using Skype for Business Online use their existing online account.
    - Users already using Skype for Business/Lync on-premises use their existing on-premises account.
    - Users for whom we cannot detect an existing Skype for Business account will have a Skype for Business Online account automatically provisioned when the Teams user is created. No Skype for Business license is required.

4.	If you have an on-premises deployment of either Skype for Business or Lync, and you want those users to be Teams users, you must at a minimum ensure that Azure AD Connect is syncing the msRTCSIP-DeploymentLocator attribute into AAD, so that Teams/Skype for Business Online properly detects your on-premises environment. Furthermore, to move any users to Teams-only mode (i.e., upgrade a user), *you must configure Skype for Business hybrid mode*.

5.	Interop between Teams and Skype for Business users is only possible *if the Teams user is homed online in Skype for Business*. The Skype for Business user can be homed either on-premises (and requires configuring Skype for Business Hybrid) or online. Users who are homed in Skype for Business on-premises can use Teams in Islands mode (defined later in this doc), but they cannot use Teams to interop or federate with other users who are using Skype for Business.  

6.	Federation from Teams to another user using Skype for Business requires the Teams user be homed online in Skype for Business. Federation is in pilot and progressively becoming available. If your organization requires federation, you should not upgrade until federation support is in place. Eventually, Teams users homed in Skype for Business on-premises will be able to federate with other Teams users.

7.	To upgrade a user to Teams (i.e., grant them TeamsUpgradePolicy with Mode=TeamsOnly), the user must be homed online in Skype for Business. This is required to ensure interop, federation, and full administration of the Teams user. To upgrade users who are homed on-premises, use `Move-CsUser` from the on-premises admin tools to first move the user to Skype for Business Online. Then grant TeamsUpgradePolicy and TeamsInteropPolicy to the online user or use Modern Portal to assign TeamsOnly mode.

8.	The core policies for managing upgrade and interop are TeamsUpgradePolicy and TeamsInteropPolicy.  However, TeamsInteropPolicy is in the process of being retired and all functionality will be superseded by TeamsUpgradePolicy. Until the transition is complete, customers must set both TeamsUpgradePolicy and TeamsInteropPolicy consistently (as described [later](#important) in this document) to ensure proper functioning, or use the new Modern Portal, which does this automatically.

9.	To use Teams Phone System features, users must be in TeamsOnly mode (i.e., homed in Skype for Business Online and upgraded to Teams), and they must either be configured for Microsoft Phone System Direct Routing (which allows you to use Phone System with your own SIP trunks and SBC) or have an Office 365 Calling Plan. Direct Routing is in [public preview](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/Direct-Routing-NOW-in-Public-Preview/ba-p/193915) as of May 15, 2018.  

10.	Scheduling Teams meetings with Audio Conferencing (dial-in or dial-out via PSTN) is currently available only for users who are homed in Skype for Business Online. Support for Teams users with an on-premises Skype for Business account is planned.

11.	Message routing for organizations that have not yet been enabled for Unified Presence Service (UPS) does not honor either TeamsInteropPolicy (ChatDefaultClient) or TeamsUpgradePolicy (Mode). As UPS rollout completes over the next few weeks, TeamsInteropPolicy or TeamsUpgradePolicy will be honored. Eventually only TeamsUpgradePolicy will be honored.

## Coexistence modes

To simplify manageability and increase end user satisfaction, interop and migration are now managed based on “coexistence mode” using TeamsUpgradePolicy. A user’s mode determines:

- *Incoming routing* : In which client (Teams or Skype for Business) do incoming chats and calls land? This functionality replaces what was previously handled by TeamsInteropPolicy. TeamsInteropPolicy will be retired after the transition is complete. ***During the transition, both TeamsUpgradePolicy and TeamsInteropPolicy must be set in a coordinated manner, as described in the next section***.
- *Meeting scheduling* : Which service is used for scheduling new meetings and ensuring that the proper add-in is present in Outlook? Outlook add-in support is expected to be deployed in the coming weeks. Note that TeamsUpgradePolicy does not govern meeting join. Users can always *join* any meeting, whether it be a Skype for Business meeting or a Teams meeting.
- *Client experience* : What functionality is available in Teams and/or Skype for Business client? This is implemented for TeamsOnly mode. Support for other modes is dependent on the upcoming TeamsAppPolicy. When this new policy is in place, TeamsUpgradePolicy will have a dependency on it to ensure that Teams is configured properly for the desired mode.

The planned modes are listed below. SfBWithTeamsCollab and SfBWithTeamsCollabAndMeetings will allow mixed usage of both clients, but with no overlapping functionality. Islands mode allows usage of both clients, but with overlapping functionality. For example, in Islands mode, a user could initiate a chat in either Skype for Business or Teams, but in SfBWithTeamsCollab, they can only chat in Skype for Business. Note that not all modes are yet available.  
</br>
</br>
|Mode|Routing Behavior|Meeting Scheduling|Client Experience|
|---|---|---|---|
|Islands|Incoming VOIP calls and chats land in same client as originator<sup>1</sup>|Both|End users can initiate calls and chats from either client, and can schedule meetings from either client.|
|SfBOnly|Incoming calls and chats are routed to Skype for Business|Skype for Business only|End users can initiate calls and chats from Skype for Business only, and only schedule Skype for Business meetings. (NOT YET ENFORCED)|
|SfBWithTeamsCollab<sup>2</sup>|Incoming calls and chats are routed to Skype for Business|Skype for Business only|End users can initiate calls and chats from Skype for Business only, and only schedule Skype for Business meetings. They can also use Channels in Teams. (NOT YET ENFORCED)|
|SfBWithTeamsCollabAndMeetings<sup>3</sup>|Incoming calls and chats are routed to Skype for Business|Teams only|End users can initiate calls and chats from Skype for Business only and only schedule Teams meetings. They can also use Channels in Teams. (NOT YET ENFORCED)|
|TeamsOnly|Incoming calls and chats are routed to Teams|Teams only|End users can initiate calls and chats from Teams only. Skype for Business is only available to join meetings.|
|Legacy|Routing is based on TeamsInteropPolicy|No impact|No impact. This a temporary mode to facilitate transition from TeamsInteropPolicy to TeamsUpgradePolicy. After the transition is complete, this mode will be removed. |
|||||

**Notes:**

<sup>1</sup> For details on PSTN calling, see table at the end of this document.

<sup>2</sup> SfBWithTeamsCollab is not yet exposed in the admin user experience because it currently behaves no differently than SfBOnly mode. When the client experience is delivered, this mode will be available.

<sup>3</sup> SfBWithTeamsCollabAndMeetings is not yet available. 

## TeamsUpgradePolicy: managing migration and co-existence

TeamsUpgradePolicy now exposes three properties. The primary properties are Mode and NotifySfbUsers. Action is a legacy parameter and is fully redundant with the combination of Mode and NotifySfbUsers.
</br>
</br>
|Parameter|Type|Allowed values</br>(default in italics)|Description|
|---|---|---|---|
|Mode|Enum|*Islands*</br>TeamsOnly</br>SfBOnly</br>SfBWithTeamsCollab</br>Legacy|Indicates the mode the client should run in. If mode=Legacy, components consuming this policy will revert to honoring TeamsInteropPolicy. This is to aid in the transition to the new schema as components that previously honored TeamsInteropPolicy are updated to honor TeamsUpgradePolicy.</br>Mode=TeamsOnly is the equivalent of Action=Upgrade.|
|NotifySfbUsers|Bool|*False* or true|Indicates whether to show a banner in the Skype for Business client informing the user that Teams will soon replace Skype for Business. This cannot be true if Mode=TeamsOnly. This is the equivalent to Action=Notify.|
|Action|Enum|*None*, Notify, Upgrade|This is a legacy parameter that will eventually be removed, because it is redundant with the combination of Mode and NotifySfbUsers. |
|||||

Teams provides all relevant instances of TeamsUpgradePolicy via built-in, read-only policies. Therefore, only Get and Grant cmdlets are available. The built-in instances are listed below.
</br>
</br>
|Identity|Mode|NotifySfbUsers|Action|Comments|
|---|---|---|---|---|
|Islands|Islands|False|None||
|IslandsWithNotify|Islands|True|Notify||
|SfBOnly|SfBOnly|False|None|For now, this mode is effectively the same as setting preferred client=SfB. We expect in the future this will restrict Teams functionality.|
|SfBOnlyWithNotify|SfBOnly|True|Notify|For now, this mode is effectively the same as setting preferred client=SfB. We expect in the future this will restrict Teams functionality.|
|SfBWithTeamsCollab|SfBWithTeamsCollab|False|None|This mode exists at the PowerShell layer but is not yet exposed in the admin user experience. From a routing perspective, this is the same as SfBOnly mode. When TeamsAppPolicy is available, this will only allow Channels in Teams app.|
|SfBWithTeamsCollabWithNotify|SfBWithTeamsCollab|True|Notify|This mode exists at the PowerShell layer but is not yet exposed in the admin user experience. From a routing perspective, this is the same as SfBOnly mode. When TeamsAppPolicy is available, this will only allow Channels in Teams app.|
|UpgradeToTeams|TeamsOnly|False|Upgrade|Use this mode to upgrade users to Teams and to prevent chat, calling, and meeting scheduling in Skype for Business.|
|Global|Legacy|False|None|The mode will eventually be updated to Islands.|
|NoUpgrade|Legacy|False|None|This instance will eventually be retired.|
|NotifyForTeams|Legacy|True|Notify|This instance will eventually be retired.|
||||||

These policy instances can be granted either to individual users or on a tenant-wide basis. For example:
- To upgrade a user ($SipAddress) to Teams, grant the “UpgradeToTeams” instance:</br>
`Grant-CsTeamsUpgradePolicy -PolicyName UpgradeToTeams -Identity $SipAddress`
- To upgrade the entire tenant, omit the identity parameter from the grant command:</br>
`Grant-CsTeamsUpgradePolicy -PolicyName UpgradeToTeams`

### IMPORTANT!
Components that previously honored TeamsInteropPolicy are in the process of being updated to honor TeamsUpgradePolicy. During the transition, management of these two policies must be coordinated as specified below. Note that the recent update to Modern Portal automatically grants both of these policies properly when you select a coexistence mode.
</br>
</br>
|If you grant an instance of TeamsUpgradePolicy</br>with this value of Mode…|…Then grant this instance of TeamsInteropPolicy|
|---|---|
|Islands|`DisallowOverrideCallingDefaultChatDefault`|
|SfBOnly, SfBWithTeamsCollab|`DisallowOverrideCallingSfbChatSfb`|
|TeamsOnly |`DisallowOverrideCallingTeamsChatTeams`|
|||

## TeamsInteropPolicy to be retired 

As described previously, TeamsInteropPolicy will be replaced by TeamsUpgradePolicy. Until this transition is complete, only the three specific instances of TeamsInteropPolicy listed below are supported. In each case, the value of CallingDefaultClient matches the value of ChatDefaultClient, and AllowEndUserClientOverride is always false. 
</br>
</br>
**Supported instances of TeamsInteropPolicy prior to retirement**
|Identity|AllowEndUserClientOverride|CallingDefaultClient|ChatDefaultClient|
|---|---|---|---|
|`DisallowOverrideCallingDefaultChatDefault`|False|Default|Default|
|`DisallowOverrideCallingSfbChatSfb`|False|Sfb|Sfb|
|`DisallowOverrideCallingTeamsChatTeams`|False|Teams|Teams|
|||||

Use the following cmdlet syntax, where $policy is one of the above values of identity:
    `Grant-CsTeamsInteropPolicy -PolicyName $policy -Identity $SipAddress`

## Completing the transition to mode management

Later this year, Microsoft plans to introduce a new policy type, TeamsAppPolicy, to control what portions of Teams client are enabled (such as IM, Meetings, Chat, Channels). When the new policy to enable/disable workloads in Teams becomes available, TeamsUpgradePolicy will be updated so that when an admin attempts to grant an instance of TeamsUpgradePolicy to a user, it will first check to ensure that TeamsAppPolicy is properly configured for the desired mode. If not, the grant will fail with an error explaining how the other policy must first be set. 

Until TeamsAppPolicy becomes available, TeamsUpgradePolicy essentially governs routing of calls and chats, as well as meeting scheduling (as exposed through Outlook add-ins). Because client behavior of Teams is not yet in place, not all modes are enabled in Modern Portal. From a routing perspective, the SfBOnly, SfBWithTeamsCollab, and SfBWithTeamsCollabAndMeetings modes are identical. 

## Action required for organizations that have already used TeamsInteropPolicy

To prepare for these upcoming changes, customers must do the following:

1. Ensure that users with TeamsInteropPolicy are assigned only one of these three built-in instances, for which CallingDefaultClient = ChatDefaultClient, and for which AllowEndUserClientOverride=false. These instances are:
</br>
</br>
   |Identity|AllowEndUserClientOverride |CallingDefaultClient|ChatDefaultClient|
   |---|---|---|---|
   |`DisallowOverrideCallingDefaultChatDefault`|False|Default|Default|
   |`DisallowOverrideCallingSfbChatSfb`|False|Sfb|Sfb|
   |`DisallowOverrideCallingTeamsChatTeams`|False|Teams|Teams|
   |||||

    Use the following cmdlet syntax, where $policy is one of the above values of identity:

    `Grant-CsTeamsInteropPolicy -PolicyName $policy -Identity $SipAddress`

    **Microsoft requests that customers update their policies by June 30, 2018.** Sometime after that, Microsoft will be removing the other instances of TeamsInteropPolicy.</br> 
    ***Organizations that do not update to one of these instances will eventually have their users automatically updated to one of these instances. We obviously prefer that customers do this, so you can choose what is best for your users.***

2. If you customized the built-in global policy, undo this. Your global policy should have the following values:
</br>
</br>
    |Parameter|Value|
    |---|---|
    |`AllowEndUserClientOverride`|False|
    |`CallingDefaultClient`|Default|
    |`ChatDefaultClient`|Default|
    |||

    If any of the values are different than above, run the following to remove any tenant-specific customizations:

    `Grant-CsTeamsInteropPolicy -PolicyName $null`

## Detailed mode descriptions
</br>
</br>

|Mode|Explanation|
|---|---|
|**Islands**</br>(default)|A single user runs both Skype for Business and Teams side-by-side. This user:</br><ul><li>Can initiate chats and VOIP calls in either Skype for Business or Teams client. Note: Users with Skype for Business homed on-premises cannot initiate from Teams to reach another Skype for Business user.<li>Receives chats & VOIP calls initiated in Skype for Business by another user in their Skype for Business client.<li>Receives VOIP calls initiated in Teams by another user in their Teams client.<li>Receives chats initiated in Teams by another user in:<ul><li>Skype for Business provided the recipient is homed online and never logged in to Teams<li>Teams in all other cases.</ul><li>Has PSTN functionality as noted below:<ul><li>If the user is homed in Skype for Business on-premises, PSTN calls are initiated and received in Skype for Business.<li>If the user is homed online, the user has Phone System, in which case the user:<ul><li>Initiates and receives PSTN calls in Teams if the user is configured for Direct Routing<li>Initiates and receives PSTN calls in Skype for Business if the user has an MS Calling Plan or connects to the PSTN network via either Skype for Business Cloud Connector Edition or an on-premises deployment of Skype for Business Server (hybrid voice)</ul></ul><li>Can schedule meetings in Teams or Skype for Business (and will see both plug-ins by default).<li>Can join any Skype for Business or Teams meeting; the meeting will open in the respective client.</ul>|
|**SfBOnly**|A single user runs only Skype for Business. This user:</br><ul><li>Can initiate chats and calls from Skype for Business only.<li>Receives any chat/call in their Skype for Business client, regardless of where initiated, unless the initiator is a Teams user with Skype for Business homed on-premises.*<li>Can schedule only Skype for Business meetings, but can join Skype for Business or Teams meetings.</br>\**Using Islands mode with on-premises users is not recommended in combination with other users in SfBOnly mode. If a Teams user with Skype for Business homed on-premises initiates a call or chat to an SfBOnly user, the SfBOnly user is not reachable and receives a missed chat/call email.*|
|**SfBWithTeamsCollab**|A single user runs both Skype for Business and Teams side-by-side. This user:</br><ul><li>Has the functionality of a user in SfBOnly mode.<li>Has Teams enabled only for group collaboration (Channels); chat/calling/meeting scheduling are disabled.</ul>|
|**SfBWithTeamsCollab</br>AndMeetings**</br>(planned)|A single user runs both Skype for Business and Teams side-by-side. This user:<ul><li>Has the chat and calling functionality of user in SfBOnly mode.<li>Has Teams enabled for group collaboration (Channels); chat and calling are disabled.<li>Can schedule only Teams meetings, but can join Skype for Business or Teams meetings.</ul>|
|**TeamsOnly**</br>(requires SfB Online home)|A single user runs only Teams. This user:<ul><li>Receives any chats and calls in their Teams client, regardless of where initiated.<li>Can initiate chats and calls from Teams only.<li>Can schedule meetings in Teams only, but can join Skype for Business or Teams meetings.<li>Can continue to use Skype for Business IP phones.</ul> |
|**Legacy**|This mode is used during the transition while we phase out TeamsInteropPolicy. Different components of the system will be updated to use TeamsUpgradePolicy at different times. During this transition, users with this mode will continue to honor the existing TeamsInteropPolicy value. This allows a consistent user experience even though different components in the service are updated at different times.|
|||

## Summary of Planned Functionality Changes to Simplify Coexistence and Migration

Based on strong feedback from TAP customers and other early adopters, Microsoft announced planned changes in April to simplify manageability and increase end user satisfaction as organizations migrate from Skype for Business to Teams. These changes will deliver a simplified and more predictable end user experience, using a simplified policy model for managing upgrade and interoperability. The changes described below will be rolled out incrementally over the next several months. At a high level, there are four planned functional changes, outlined below.
</br>
</br>
**CHANGE #1:  No more overlapping modalities when preferred client is set**
|||
|---|---|
|**DECISION**|*When a user’s preferred client is set to either “Teams” or “Sfb”*, a given modality (IM, Meeting scheduling, Calling) will only be available and supported in one client (Teams or Skype for Business) for that user. (*Preferred client* refers to the DefaultChatClient and DefaultCallingClient parameters in TeamsInteropPolicy.) Only when the preferred client is set to “Default” (in the future referred to as “Islands mode”) will a given modality be available and supported in both clients. |
|**RATIONALE**|The consistent feedback we’ve received is that users are confused for one reason or another when trying to use both clients with overlapping modalities. It is difficult to predict and understand why messages and calls land in one client vs. another, and presence can be inaccurate or misleading.|
|**STATUS**|This is supported for Mode=TeamsOnly. Support for other modes will be available in the next few months. |
|||

**CHANGE #2: Unify preferred client for Messaging and Calling**
|||
|---|---|
|**DECISION**|Microsoft will unify management of preferred client for IM and Calling. Specifically, DefaultChatClient and DefaultCallingClient must both have the same value - either both Default (Islands), both Teams, or both Skype for Business.  |
|**RATIONALE**|If these are not aligned, presence will in some cases be misleading and confusing. Furthermore, initiating a call from an existing chat could be confusing because the call may land in a different client than the existing chat. |
|**STATUS**|This change has been implemented at the policy layer using TeamsUpgradePolicy, as well as in the admin UX (modern portal). However, the transition is not yet complete, so customers must also set TeamsInteropPolicy. Customers must only set one of the three supported instances of TeamsInteropPolicy, which are: DisallowOverrideCallingTeamsChatTeams, DisallowOverrideCallingDefaultChatDefault, DisallowOverrideCallingSfbChatSfb|
|||

**CHANGE #3: No more end user choice of preferred client**
|||
|---|---|
|**DECISION**|End users will no longer have a choice of preferred client. (AllowEndUserClientOverride in TeamsInteropPolicy must be set to false.) The preferred client will be based on Mode, which is set by the admin.|
|**RATIONALE**|Analysis of usage data shows that almost no users set this. Eliminating this choice simplifies admin/helpdesk scenarios and reduces engineering complexity. Finally, if the end user were to choose a different preferred client from what the admin has configured for voice routing in an org with Enterprise Voice, this would cause a confusing end user experience because it would result in VOIP and PSTN calls landing in different clients.|
|**STATUS**|This change has been implemented at the policy layer using TeamsUpgradePolicy, as well as in the admin UX (Modern Portal). However, the transition is not yet complete, so customers using cmdlets must also set TeamsInteropPolicy to one of the three supported instances of TeamsInteropPolicy, all of which disallow override.|
|||

**CHANGE #4: Management based on client “mode”**
|||
|---|---|
|**DECISION**|Microsoft is introducing the concept of “mode” to manage client behavior as orgs using Skype for Business start to adopt Teams. Admins can set the mode on a per-user basis, and a user’s mode will drive what functionality is available in which client, as well as where calls and chats land. Admins will manage this via the revised TeamsUpgradePolicy, which has been updated to support Mode. TeamsInteropPolicy will eventually be deprecated and removed, after all components have been updated to read from TeamsUpgradePolicy.|
|**RATIONALE**|To simplify manageability and increase end user satisfaction, interop and migration will be managed using “coexistence mode” using TeamsUpgradePolicy. Selection of the user’s mode will govern routing of incoming calls and chats, and in which client the user can initiate chats and calls or schedule meetings. Consolidation of TeamsUpgradePolicy and TeamsInteropPolicy also prevents misconfigurations that could result if these two policies were not set consistently. |
|**STATUS**|TAP customers now see three modes in the Admin UX. As support for Change #1 lands, additional modes will be made available. SfBOnly mode does not currently prevent users from using Teams, but it will in the future. |
|||

## Known issues

- When creating new conversations in Teams, chats do not yet honor TeamsUpgradePolicy or TeamsInteropPolicy of the target user. A fix is planned.
- When creating new conversations in Skype for Business, chats do not yet honor TeamsUpgradePolicy or TeamsInteropPolicy if the organization isn’t yet enabled for UPS/messaging interop.

## Related topics

[Get-CsTeamsInteropPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/get-csteamsinteroppolicy?view=skype-ps)

[Grant-CsTeamsInteropPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/grant-csteamsinteroppolicy?view=skype-ps)

[Remove-CsTeamsInteropPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/remove-csteamsinteroppolicy?view=skype-ps)

[Get-CsTeamsUpgradeConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/get-csteamsupgradeconfiguration?view=skype-ps)

[Get-CsTeamsUpgradePolicy](https://docs.microsoft.com/en-us/powershell/module/skype/get-csteamsupgradepolicy?view=skype-ps)

[Grant-CsTeamsUpgradePolicy](https://docs.microsoft.com/en-us/powershell/module/skype/grant-csteamsupgradepolicy?view=skype-ps)

[New-CsTeamsUpgradePolicy](https://docs.microsoft.com/en-us/powershell/module/skype/new-csteamsupgradepolicy?view=skype-ps)

[Remove-CsTeamsUpgradePolicy](https://docs.microsoft.com/en-us/powershell/module/skype/remove-csteamsupgradepolicy?view=skype-ps)

[Set-CsTeamsUpgradeConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/set-csteamsupgradeconfiguration?view=skype-ps)

[Set-CsTeamsUpgradePolicy](https://docs.microsoft.com/en-us/powershell/module/skype/set-csteamsupgradepolicy?view=skype-ps)
