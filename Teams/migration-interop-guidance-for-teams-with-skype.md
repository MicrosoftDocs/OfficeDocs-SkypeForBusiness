---
title: Migration and interoperability guidance for organizations using Teams together with Skype for Business
author: arachmanGitHub
ms.author: MyAdvisor
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: lehewe
description: Guidance for managing the transition to Teams from Skype for Business 
localization_priority: Normal
search.appverid: MET150
MS.collection: Teams_ITAdmin_PracticalGuidance
appliesto:
- Microsoft Teams
---
# Migration and interoperability guidance for organizations using Teams together with Skype for Business

Interop and migration are managed using “coexistence mode” as determined by TeamsUpgradePolicy. Selection of the user’s mode governs both routing of incoming calls and chats and whether user schedules meetings in Teams or Skype for Business.  Soon, in conjunction with the upcoming TeamsAppPermissionsPolicy, mode will also govern in which client the user can initiate chats and calls. 

As previously announced in April 2018, TeamsInteropPolicy is being retired. Its functionality has been consolidated into TeamsUpgradePolicy, and configuring TeamsInteropPolicy is no longer required. It is not honored unless TeamsUpgradePolicy has mode=Legacy.  Now that TeamsUpgradePolicy support is complete, *customers should update their configurations to use a mode other than Legacy*. Granting instances of TeamsUpgradePolicy with mode=Legacy is now blocked by default.

## Fundamental concepts

1.  *Interop* : 1 to 1 communication between a Lync/Skype for Business user and a Teams user.

2.  *Federation* : Communication between users from different tenants.

3.  All Teams users have an underlying Skype for Business account that is “homed” either online or on-premises:
    - Users already using Skype for Business Online use their existing online account.
    - Users already using Skype for Business/Lync on-premises use their existing on-premises account.
    - Users for whom we cannot detect an existing Skype for Business account will have a Skype for Business Online account automatically provisioned when the Teams user is created. No Skype for Business license is required.

4.  If you have an on-premises deployment of either Skype for Business or Lync, and you want those users to be Teams users, you must at a minimum ensure that Azure AD Connect is syncing the msRTCSIP-DeploymentLocator attribute into AAD, so that Teams/Skype for Business Online properly detects your on-premises environment. Furthermore, to move any users to Teams-only mode (i.e., upgrade a user), *you must configure Skype for Business hybrid mode*.

5.  Interop between Teams and Skype for Business users is only possible *if the Teams user is homed online in Skype for Business*. The recipient Skype for Business user can be homed either on-premises (and requires configuring Skype for Business Hybrid) or online. Users who are homed in Skype for Business on-premises can use Teams in Islands mode (defined later in this doc), but they cannot use Teams to interop or federate with other users who are using Skype for Business.  

6.  To upgrade a user to Teams (i.e., grant them TeamsUpgradePolicy with Mode=TeamsOnly), the user must be homed online in Skype for Business. This is required to ensure interop, federation, and full administration of the Teams user. To upgrade users who are homed on-premises, use `Move-CsUser` from the on-premises admin tools to first move the user to Skype for Business Online:

    - If you have Skype for Business Server 2019 or CU8 for Skype for Business Server 2015, specify the `-MoveToTeams` switch in `Move-CsUser` to move the user directly to Teams.
    - Otherwise, after `Move-CsUser` completes, assign TeamsOnly mode to that user using either PowerShell or the Teams Admin Center. 

7.	The core policy for managing upgrade and interop is TeamsUpgradePolicy. TeamsInteropPolicy is no longer honored except when using TeamsUpgradePolicy mode=Legacy, and customers using mode=Legacy should update their configuration of TeamsUpgradePolicy to use a different mode.  Granting mode=Legacy is now blocked by default, although admins can override this using `-Force` for the time being. Eventually, the `-Force` switch will be removed and granting mode=Legacy will not be possible. 

8.	To use Teams Phone System features with Teams, users must be in TeamsOnly mode (i.e., homed in Skype for Business Online and upgraded to Teams), and they must either be configured for Microsoft Phone System [Direct Routing](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/Direct-Routing-is-now-Generally-Available/ba-p/210359#M1277) (which allows you to use Phone System with your own SIP trunks and SBC) or have an Office 365 Calling Plan.   

9.  Scheduling Teams meetings with Audio Conferencing (dial-in or dial-out via PSTN) is currently available only for users who are homed in Skype for Business Online. Support for Teams users with an on-premises Skype for Business account is in TAP.


## Coexistence modes

Interop and migration are managed based on “coexistence mode” using TeamsUpgradePolicy. A user’s mode determines:

- *Incoming routing*: In which client (Teams or Skype for Business) do incoming chats and calls land? 
- *Meeting scheduling*: Which service is used for scheduling new meetings and ensuring that the proper add-in is present in Outlook. Note that TeamsUpgradePolicy does not govern meeting join. Users can always *join* any meeting, whether it be a Skype for Business meeting or a Teams meeting.
- *Client experience*: What functionality is available in Teams and/or Skype for Business client? This is implemented for TeamsOnly mode. Support for other modes is dependent on the upcoming TeamsAppPermissionsPolicy. When this new policy is in place, TeamsUpgradePolicy will have a dependency on it to ensure that Teams is configured properly for the desired mode.

The planned modes are listed below. SfBWithTeamsCollab and SfBWithTeamsCollabAndMeetings will allow mixed usage of both clients, but with no overlapping functionality. Islands mode allows usage of both clients, but with overlapping functionality. For example, in Islands mode, a user could initiate a chat in either Skype for Business or Teams, but in SfBWithTeamsCollab, they can only chat in Skype for Business. Note that not all modes are yet fully available.  
</br>
</br>

|Mode|Routing Behavior|Meeting Scheduling|Client Experience|
|---|---|---|---|
|Islands|Incoming VOIP calls and chats land in same client as originator, except if recipient is federated and in islands mode, in which case they land in SfB.<sup>1</sup>|Both|End users can initiate calls and chats from either client, and can schedule meetings from either client.|
|SfBOnly|Incoming calls and chats are routed to Skype for Business|Skype for Business only|End users can initiate calls and chats from Skype for Business only, and only schedule Skype for Business meetings. (NOT YET ENFORCED)|
|SfBWithTeamsCollab<sup>2</sup>|Incoming calls and chats are routed to Skype for Business|Skype for Business only|End users can initiate calls and chats from Skype for Business only, and only schedule Skype for Business meetings. They can also use Channels in Teams. (NOT YET ENFORCED)|
|SfBWithTeamsCollabAndMeetings<sup>2</sup>|Incoming calls and chats are routed to Skype for Business|Teams only|End users can initiate calls and chats from Skype for Business only and only schedule Teams meetings. They can also use Channels in Teams. (NOT YET ENFORCED)|
|TeamsOnly|Incoming calls and chats are routed to Teams|Teams only|End users can initiate calls and chats from Teams only. Skype for Business is only available to join meetings.|
|Legacy</br>*Deprecated*|Routing is based on TeamsInteropPolicy|No impact|No impact. This was a temporary mode that facilitated transition from TeamsInteropPolicy to TeamsUpgradePolicy. TeamsUpgradePolicy is fully supported so *customers should update their configurations to modes other than Legacy.*  Granting of Legacy mode is now blocked by default. |
|||||

**Notes:**

<sup>1</sup> For details on PSTN calling, see table at the end of this document.

<sup>2</sup> SfBWithTeamsCollab and SfBWithTeamsCollabAndMeetings are not yet exposed in the admin user experience because they currently behave no differently than SfBOnly mode. Once the client experience is delivered, these modes will be available. 

## TeamsUpgradePolicy: managing migration and co-existence

TeamsUpgradePolicy exposes three properties. The primary properties are Mode and NotifySfbUsers. Action is a legacy parameter and is fully redundant with the combination of Mode and NotifySfbUsers.
</br>
</br>

|Parameter|Type|Allowed values</br>(default in italics)|Description|
|---|---|---|---|
|Mode|Enum|*Islands*</br>TeamsOnly</br>SfBOnly</br>SfBWithTeamsCollab</br>Legacy|Indicates the mode the client should run in. If mode=Legacy, components consuming this policy will revert to honoring TeamsInteropPolicy. TeamsUpgradePolicy is now fully supported and customers should update their configurations use modes other than Legacy.|
|NotifySfbUsers|Bool|*False* or true|Indicates whether to show a banner in the Skype for Business client informing the user that Teams will soon replace Skype for Business. This cannot be true if Mode=TeamsOnly.|
|Action</br>*Deprecated*|Enum|*None*, Notify, Upgrade|This is a legacy parameter that will eventually be removed, because it is redundant with the combination of Mode and NotifySfbUsers. |
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
|SfBWithTeamsCollabAndMeetings|SfBWithTeamsCollabAndMeetings|False|None|This mode exists at the PowerShell layer but is not yet exposed in the admin user experience. From a routing perspective, this is the same as SfBOnly mode. When TeamsAppPolicy is available, this will  allow Channels and meeting scheduling in Teams.|
|SfBWithTeamsCollabAndMeetingsWithNotify|SfBWithTeamsCollabAndMeetings|True|Notify|This mode exists at the PowerShell layer but is not yet exposed in the admin user experience. From a routing perspective, this is the same as SfBOnly mode. When TeamsAppPolicy is available, this will allow Channels and meeting scheduling in Teams.|
|UpgradeToTeams|TeamsOnly|False|Upgrade|Use this mode to upgrade users to Teams and to prevent chat, calling, and meeting scheduling in Skype for Business.|
|Global|Legacy|False|None|The mode will be updated to Islands in the near future.|
|NoUpgrade|Legacy|False|None|This instance will soon be retired.|
|NotifyForTeams|Legacy|True|Notify|This instance will soon be retired.|
||||||

These policy instances can be granted either to individual users or on a tenant-wide basis. For example:
- To upgrade a user ($SipAddress) to Teams, grant the “UpgradeToTeams” instance:</br>
`Grant-CsTeamsUpgradePolicy -PolicyName UpgradeToTeams -Identity $SipAddress`
- To upgrade the entire tenant, omit the identity parameter from the grant command:</br>
`Grant-CsTeamsUpgradePolicy -PolicyName UpgradeToTeams`



## TeamsInteropPolicy and Legacy Mode being retired 

As described previously, TeamsInteropPolicy has been replaced by TeamsUpgradePolicy. All components that previously honored TeamsInteropPolicy have been updated to honor TeamsUpgradePolicy instead. 

Microsoft previously introduced the “Legacy” mode in TeamsUpgradePolicy to facilitate the transition from TeamsInteropPolicy to TeamsUpgradePolicy. In Legacy mode, routing components that understood TeamsUpgradePolicy would revert back to TeamsInteropPolicy. Routing now fully supports TeamsUpgradePolicy and there is no further need to use Legacy mode. *Customers using Legacy mode should update their configuration of TeamsUpgradePolicy to use one of the other modes.* 

Customers still using Legacy mode are reminded that only the three specific instances of TeamsInteropPolicy listed below are supported. In each case, the value of CallingDefaultClient matches the value of ChatDefaultClient, and AllowEndUserClientOverride is always false. 
</br>
</br>
**Supported instances of TeamsInteropPolicy when using TeamsUpgradePolicy mode=Legacy**
</br>
</br>

|Identity|AllowEndUserClientOverride|CallingDefaultClient|ChatDefaultClient|
|---|---|---|---|
|`DisallowOverrideCallingDefaultChatDefault`|False|Default|Default|
|`DisallowOverrideCallingSfbChatSfb`|False|Sfb|Sfb|
|`DisallowOverrideCallingTeamsChatTeams`|False|Teams|Teams|
|||||

Use the following cmdlet syntax, where $policy is one of the above values of identity:
    `Grant-CsTeamsInteropPolicy -PolicyName $policy -Identity $SipAddress`

## Federation Considerations

Federation from Teams to another user using Skype for Business requires the Teams user be homed online in Skype for Business. Eventually, Teams users homed in Skype for Business on-premises will be able to federate with other Teams users.

TeamsUpgradePolicy governs routing for incoming federated chats and calls. Federated routing behavior is the same as for same-tenant scenarios, *except in Islands mode*.  When recipients are in Islands mode: 
- Chats and calls initiated from Teams land in SfB if the recipient is in a *federated tenant*.
- Chats and calls initiated from Teams land in Teams if the recipient is in the *same tenant*.
- Chats and calls initiated from SfB always land in SfB.


## Completing the transition to mode management

Later this year, Microsoft plans to introduce a new policy type, TeamsAppPermissionsPolicy, to control what portions of Teams client are enabled (such as IM, Meetings, Chat, Channels). When the new policy to enable/disable workloads in Teams becomes available, TeamsUpgradePolicy will be updated so that when an admin attempts to grant an instance of TeamsUpgradePolicy to a user, it will first check to ensure that TeamsAppPolicy is properly configured for the desired mode. If not, the grant will fail with an error explaining how the other policy must first be set. 

Until TeamsAppPolicy becomes available, TeamsUpgradePolicy essentially governs routing of calls and chats, as well as meeting scheduling (as exposed through Outlook add-ins). Because client behavior of Teams is not yet in place, not all modes are enabled in Modern Portal. From a routing perspective, the SfBOnly, SfBWithTeamsCollab, and SfBWithTeamsCollabAndMeetings modes are identical. 

## Action required for organizations that were using TeamsInteropPolicy

Any customers still using TeamsInteropPolicy: 
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




## Action required for organizations that are using Mode=Legacy

Customers using mode=Legacy in TeamsUpgradePolicy (policy instance = NoUpgrade or policy instance = NotifyForTeams) must update their configuration to use a policy with a mode other than legacy. 

 **Microsoft requests that customers remove all use of Legacy mode by November 15, 2018.** Sometime after that, Microsoft will be removing  instances of TeamsUpgradePolicy with mode=Legacy.</br> 


## Detailed mode descriptions
</br>
</br>

|Mode|Explanation|
|---|---|
|**Islands**</br>(default)|A single user runs both Skype for Business and Teams side-by-side. This user:</br><ul><li>Can initiate chats and VOIP calls in either Skype for Business or Teams client. Note: Users with Skype for Business homed on-premises cannot initiate from Teams to reach another Skype for Business user.<li>Receives chats & VOIP calls initiated in Skype for Business by another user in their Skype for Business client.<li>Receives chats & VOIP calls initiated in Teams by another user in their Teams client if they are in the *same tenant*.<li>Receives chats & VOIP calls initiated in Teams by another user in their Skype for Business client if they are in a  *federated tenant*. <li>Has PSTN functionality as noted below:<ul><li>If the user is homed in Skype for Business on-premises, PSTN calls are initiated and received in Skype for Business.<li>If the user is homed online, the user has Phone System, in which case the user:<ul><li>Initiates and receives PSTN calls in Teams if the user is configured for Direct Routing<li>Initiates and receives PSTN calls in Skype for Business if the user has an MS Calling Plan or connects to the PSTN network via either Skype for Business Cloud Connector Edition or an on-premises deployment of Skype for Business Server (hybrid voice)</ul></ul><li>Can schedule meetings in Teams or Skype for Business (and will see both plug-ins by default).<li>Can join any Skype for Business or Teams meeting; the meeting will open in the respective client.</ul>|
|**SfBOnly**|A single user runs only Skype for Business. This user:</br><ul><li>Can initiate chats and calls from Skype for Business only.<li>Receives any chat/call in their Skype for Business client, regardless of where initiated, unless the initiator is a Teams user with Skype for Business homed on-premises.*<li>Can schedule only Skype for Business meetings, but can join Skype for Business or Teams meetings.</br>\**Using Islands mode with on-premises users is not recommended in combination with other users in SfBOnly mode. If a Teams user with Skype for Business homed on-premises initiates a call or chat to an SfBOnly user, the SfBOnly user is not reachable and receives a missed chat/call email.*|
|**SfBWithTeamsCollab**|A single user runs both Skype for Business and Teams side-by-side. This user:</br><ul><li>Has the functionality of a user in SfBOnly mode.<li>Has Teams enabled only for group collaboration (Channels); chat/calling/meeting scheduling are disabled.</ul>|
|**SfBWithTeamsCollab</br>AndMeetings**|A single user runs both Skype for Business and Teams side-by-side. This user:<ul><li>Has the chat and calling functionality of user in SfBOnly mode.<li>Has Teams enabled for group collaboration (Channels); chat and calling are disabled.<li>Can schedule only Teams meetings, but can join Skype for Business or Teams meetings.</ul>|
|**TeamsOnly**</br>(requires SfB Online home)|A single user runs only Teams. This user:<ul><li>Receives any chats and calls in their Teams client, regardless of where initiated.<li>Can initiate chats and calls from Teams only.<li>Can schedule meetings in Teams only, but can join Skype for Business or Teams meetings.<li>Can continue to use Skype for Business IP phones.</ul> |
|**Legacy**</br>(deprecated)|This mode was used during the transition TeamsInteropPolicy to TeamsUpgradePolicy to ensure a consistent experience as software changes rolled out. This mode is no longer needed now that TeamsUpgradePolicy is fully supported. Customers using mode=Legacy should update their configuration to use on of the other modes.|
|||




## Related topics

[Get-CsTeamsUpgradePolicy](https://docs.microsoft.com/powershell/module/skype/get-csteamsupgradepolicy?view=skype-ps)

[Grant-CsTeamsUpgradePolicy](https://docs.microsoft.com/powershell/module/skype/grant-csteamsupgradepolicy?view=skype-ps)

[Get-CsTeamsInteropPolicy](https://docs.microsoft.com/powershell/module/skype/get-csteamsinteroppolicy?view=skype-ps)

[Grant-CsTeamsInteropPolicy](https://docs.microsoft.com/powershell/module/skype/grant-csteamsinteroppolicy?view=skype-ps)

[Remove-CsTeamsInteropPolicy](https://docs.microsoft.com/powershell/module/skype/remove-csteamsinteroppolicy?view=skype-ps)

[Get-CsTeamsUpgradeConfiguration](https://docs.microsoft.com/powershell/module/skype/get-csteamsupgradeconfiguration?view=skype-ps)

[New-CsTeamsUpgradePolicy](https://docs.microsoft.com/powershell/module/skype/new-csteamsupgradepolicy?view=skype-ps)

[Remove-CsTeamsUpgradePolicy](https://docs.microsoft.com/powershell/module/skype/remove-csteamsupgradepolicy?view=skype-ps)

[Set-CsTeamsUpgradeConfiguration](https://docs.microsoft.com/powershell/module/skype/set-csteamsupgradeconfiguration?view=skype-ps)

[Set-CsTeamsUpgradePolicy](https://docs.microsoft.com/powershell/module/skype/set-csteamsupgradepolicy?view=skype-ps)
