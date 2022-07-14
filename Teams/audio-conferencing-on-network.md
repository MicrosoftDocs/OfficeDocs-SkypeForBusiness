---
title: "On-network Conferencing for Audio Conferencing"
ms.author: heidip
author: MicrosoftHeidi
manager: serdars
ms.reviewer: oscarr
ms.topic: conceptual
ms.tgt.pltfrm: cloud
audience: admin
ms.service: msteams
search.appverid: MET150
ms.collection:
  - M365-voice
  - M365-collaboration
  - m365initiative-meetings
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.custom:
  - Audio Conferencing
description: "The following describes On-network for Audio Conferencing."
---

# On-network Conferencing for Audio Conferencing

On-network Conferencing allows organizations to send inbound and outbound Audio Conferencing calls to Microsoft dial-in numbers through Direct Routing. This capability is not intended to extend the support of Audio Conferencing to third party dial-in numbers. On-network Conferencing is not supported if it is used to route inbound calls to the Audio Conferencing service through third party dial-in phone numbers or outbound calls to the PSTN from Microsoft Audio Conferencing Bridge.

This article describes the prerequisites and configuration steps required to enable On-network Conferencing for your organization.

> [!IMPORTANT]
> On-network Conferencing must NOT be deployed with any telephony equipment in India.

## Prerequisites

Before configuring On-network Conferencing, make sure your organization meets the following prerequisites:

- Ensure that all users in your organization who are enabled, or will be enabled, for Audio Conferencing are using Teams for all Meetings. The routing of inbound and outbound Audio Conferencing calls through On-network Conferencing is only supported for Teams meetings.

- Assign Audio Conferencing licenses to all users who will be using On-network Conferencing.

- Set up the Audio Conferencing service. For additional information, see [Set up Audio Conferencing for Microsoft Teams](set-up-audio-conferencing-in-teams.md).

- Set up your Session Border Controller (SBC) for Direct Routing. For additional information, see [Plan Direct Routing](direct-routing-plan.md) and [Configure Direct Routing](direct-routing-configure.md).

  If you are setting up Direct Routing only for the purposes of Audio Conferencing, then you need only complete "Step 1: Connect your SBC" for On-network Conferencing.

## Enable the routing of dial-in calls to Microsoft Audio Conferencing through Direct Routing

To route dial-in calls made by your on-premises users to the Audio Conferencing service through Direct Routing, you need to configure appropriate routing rules for your SBCs and Private Branch Exchange(s) (PBXs).

You need to configure the telephony equipment of your sites to route calls to any service number of the conference bridge of your organization through a Direct Routing trunk.

You can find the service numbers in Teams admin center under **Meetings -> Conferencing Bridges** or by using the Skype for Business Online PowerShell cmdlet Get-CsOnlineDialInConferencingBridge. For additional information, see a list of [Audio Conferencing numbers in Microsoft Teams](see-a-list-of-audio-conferencing-numbers-in-teams.md).

> [!NOTE]
> This feature is not available to users with the pay-per-minute Audio Conferencing license.

## Enable the routing of Teams meeting dial-out calls through Direct Routing

Teams meeting dial-out calls are initiated from within a meeting in your organization to PSTN numbers, including call-me-at calls and calls to bring new participants to a meeting.

To enable Teams meeting dial-out routing through Direct Routing to on-network users, you need to create and assign an Audio Conferencing routing policy called "OnlineAudioConferencingRoutingPolicy".

The OnlineAudioConferencingRoutingPolicy policy is equivalent to the CsOnlineVoiceRoutingPolicy for 1:1 PSTN calls via Direct Routing. The OnlineAudioConferencingRoutingPolicy policy can be managed by using the following cmdlets:

- New-CsOnlineAudioConferencingRoutingPolicy
- Set-CsOnlineAudioConferencingRoutingPolicy
- Get-CsOnlineAudioConferencingRoutingPolicy
- Grant-CsOnlineAudioConferencingRoutingPolicy
- Remove-CsOnlineAudioConferencingRoutingPolicy

For more information about routing for Direct Routing, see [Configure voice routing for Direct Routing](direct-routing-voice-routing.md).

To enable the routing of meeting dial-out calls through Direct Routing, you need to:

- Configure Audio Conferencing routing policies
- Configure the routing on the telephony equipment of your organization
- (Optional) Configure a dial plan

Dial-out calls from Teams meetings are coming from the default service number on the conference bridge. For additional information on the default service number of your Audio Conferencing bridge, see [Change the phone numbers on your Audio Conferencing bridge](change-the-phone-numbers-on-your-audio-conferencing-bridge.md).

### Configure Audio Conferencing routing policies

The Audio Conferencing routing policy OnlineAudioConferencingRoutingPolicy determines which meeting dial-out calls are routed to Direct Routing trunks. If you are familiar with the CsOnlineVoiceRoutingPolicy policy, this policy works in a very similar way.

The following steps are needed to set up Audio Conferencing routing policies:

1. Create PSTN usages
1. Configure voice routes
1. Create Audio Conferencing voice routing policies
1. Assign a policy to your users

#### Create PSTN usages

PSTN usages are collections of voice routes. When a dial-out call is initiated from the meeting of a given organizer, voice routes will be used to determine the routing path of the call based on the PSTN usages that are associated to the user via the user's voice routing policy.

You can create a PSTN usage by using the "Set-CsOnlinePstnUsage" cmdlet. For Example:

```powershell
Set-CsOnlinePstnUsage -Identity Global -Usage @{Add="US and Canada"}
```

#### Configure voice routes

Voice routes determine the PSTN gateway that should be used to route a call based on the phone number that is dialed from a Teams meeting. Voice routes determine the PSTN gateway that should be used to route a given call by matching the phone number dialed from a Teams meeting with a regex pattern. When creating a voice route, the route must be associated to one or more PSTN usages.

You can create a voice route and define the regex and gateways to be associated with the voice route by using the "New-CsOnlineVoiceRoute" cmdlet. For Example:

```powershell
New-CsOnlineVoiceRoute -Identity "Redmond 1" -NumberPattern "^\+1(425|206)(\d{7})$" -OnlinePstnGatewayList sbc1.contoso.biz, sbc2.contoso.biz -Priority 1 -OnlinePstnUsages "US and Canada"
```

#### Create Audio Conferencing voice routing policies

Audio Conferencing voice routing policies determine the possible routes that can be used to route a call originating from the meetings of an organizer based on the target phone number of the meeting dial-out call. Audio Conferencing voice routing policies are associated to one or more PSTN usages, which in turn, determine the possible routes that will be attempted to be used for the meeting dial-out calls of the organizers associated to the policy.

You can create an Audio Conferencing voice routing policy by using the "New- CsOnlineAudioConferencingRoutingPolicy" cmdlet. For Example:

```powershell
New-CsOnlineAudioConferencingRoutingPolicy "Policy 1" -OnlinePstnUsages "US and Canada"
```

After the policy is assigned to a user, and when a meeting dial-out call is initiated from one of the user's meetings, the voice routes in the PSTN usages that are associated to the organizer through the user's voice routing policy will be evaluated. If the meeting dial-out call destination matches a regex in one of the voice routes that are associated to the organizer, the meeting dial-out call will be routed to the PSTN gateway defined in the voice route. If the meeting dial-out call destination does not match any of the voice routes associated to the organizer, the meeting dial-out call will be routed by Microsoft.

#### Assign a policy to your users

After the Audio Conferencing routing policies are defined, you can now assign them to users. After policies are assigned to them, the meeting dial-out calls will be evaluated against it to determine their routing path. Audio Conferencing routing policies are always evaluated based on the organizer of the meeting, independently from the user in the meeting that initiates a meeting dial-out call.

You can assign an Audio Conferencing voice routing policy to a user by using the "Grant-CsOnlineAudioConferencingRoutingPolicy" cmdlet. For example:

```powershell
Grant-CsOnlineAudioConferencingRoutingPolicy -Identity "<User Identity>" -PolicyName "Policy 1"
```

### Configure routing on the telephony equipment of your organization

On the telephony equipment of your organization, you need to ensure that the meeting dial-out calls routed through Direct Routing are routed to the intended on-network destination.

### (Optional) Configure a dial plan

A dial plan is a set of normalization rules that translate dialed phone numbers by an individual user into an alternate format (typically E.164) for purposes of call authorization and call routing.

By default, Teams users can dial-out to PSTN numbers in E.164 format, that is, +\<country code\>\<number\>. However, dial plans can be used to allow users to dial phone numbers in other formats, for instance 4-digit extensions.

If you would like to enable extension-based dialing through On-network conferencing, you can set up dial plans to match the extension dialing pattern to the phone number ranges of the phone number of your organization. To set up dial plans, see [Create and manage dial plans](create-and-manage-dial-plans.md).

## Related topics
