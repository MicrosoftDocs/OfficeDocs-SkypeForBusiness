---
title: "Audio Conferencing with Direct Routing, GCCH and DoD"
author: MicrosoftHeidi
ms.author: heidip
manager: serdars
ms.reviewer: oscarr
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.collection: 
  - M365-voice
  - M365-collaboration
search.appverid: MET150
audience: Admin
appliesto: 
  - Microsoft Teams
f1.keywords:
- NOCSH
ms.localizationpriority: medium
description: Admin can learn about how to use Audio Conferencing with Direct Routing in GCCH and DoD environments.
ms.custom: seo-marvel-apr2020
---

# Audio Conferencing with Direct Routing for GCC High and DoD

Audio Conferencing with Direct Routing for GCC High and DoD enables participants to join Teams meetings in your GCC High or DoD organization by using a phone device. Meeting participants might prefer to use a phone device to join Teams meetings in scenarios such as when internet connectivity is limited or when users are on the road and don't have access to Teams. Participants can choose to join meetings by either dialing in to a dial-in phone number for your organization or by having the meeting dial out to their phone device.

With Audio Conferencing with Direct Routing for GCC High and DoD, your organization uses its own numbers as dial-in phone numbers and all meeting dial-outs to phone devices are routed via Direct Routing. To enable the service, organizations need to set up Direct Routing and configure phone numbers that can be used as dial-in phone numbers. The requirement to use Direct Routing is different from the Audio Conferencing service that's offered to non-GCC High and non-DoD organizations where the dial-in phone numbers are provided by Microsoft.

## Deploy Audio Conferencing with Direct Routing for GCC High and DoD

### Step 1: Get Audio Conferencing with Direct Routing for GCC High or DoD licenses

To use Audio Conferencing in GCC High or DoD, your organization and the users in your organization need to have an Audio Conferencing with Direct Routing license assigned. Here are the licenses you need to enable Audio Conferencing with Direct Routing for GCC High or DoD.

- GCC High: An Audio Conferencing - GCC High Tenant license for your organization and Audio Conferencing - GCC High licenses for your users.

- DoD: An Audio Conferencing - DoD Tenant license for your organization and Audio Conferencing - DoD licenses for your users.

A tenant license and at least one user license are required to enable the service. You can't enable the service with only the tenant license or with only user licenses. To get service licenses for your tenant and the users in your organization, contact your account team.

> [!IMPORTANT]
> Users can't be enabled for Audio Conferencing with Direct Routing until dial-in phone numbers are set up. We recommend that you do not assign Audio Conferencing with Direct Routing for GCC High or DoD licenses to users until you set up dial-in phone numbers as outlined in this article.  Failure to follow this guidance may cause the dial pad to be completely missing in the Teams client.

### Step 2: Set up Direct Routing

To set up Direct Routing, see the following articles:

- [Plan Direct Routing](direct-routing-plan.md)

- [Configure Direct Routing](direct-routing-configure.md)

> [!NOTE]
> When you set up Direct Routing, remember to use the GCC High or DoD-specific FQDNs and ports that are described in these two articles.

### Step 3: Set up dial-in phone numbers

Dial-in phone numbers are the phone numbers that are associated to your Audio Conferencing bridge. These numbers are used by participants to join meetings scheduled by users in your organization. These numbers are also included in the meeting invites of the users who schedule meetings in your organization and on the "Find a local number" page.

#### Define service phone numbers in your tenant

You can use the New-csHybridTelephoneNumber PowerShell cmdlet to define service phone numbers in your tenant that can be used to route calls to the Audio Conferencing service via Direct Routing.

  ```PowerShell
  New-csHybridTelephoneNumber -TelephoneNumber <Phone number in E.164 format>
  ```

For example:

  ```PowerShell
  New-csHybridTelephoneNumber -TelephoneNumber "+14250000000"
  ```

#### Assign the service phone numbers to the Audio Conferencing bridge of your organization

You can assign service phone numbers to the Audio Conferencing bridge of your organization by using the Register-csOnlineDialInConferencingServiceNumber PowerShell cmdlet.

  ```PowerShell
  Register-csOnlineDialInConferencingServiceNumber -identity <Telephone number in E.164 format> -BridgeId <Identity of the audio conferencing bridge>
  ```

You can see the ID of your Audio Conferencing Bridge using Get-CsOnlineDialInConferencingBridge. For example:

  ```PowerShell
  $b= Get-CsOnlineDialInConferencingBridge
  Register-csOnlineDialInConferencingServiceNumber -identity 14257048060 -BridgeId $b.identity
  ```

### Step 4: Define a global voice routing policy to enable the routing of outbound calls from meetings

The routing of outbound calls that are made to the PSTN from meetings organized by users in your organization is defined by the global voice routing policy of your organization. If your organization has a global voice routing policy defined, verify that the global voice routing policy allows the outbound calls to the PSTN that are expected to be initiated from meetings organized by users in your organization. If your organization doesn’t have a global voice routing policy defined, you will need to define one to enable the routing of outbound calls to the PSTN from meetings organized by users in your organization. Note that the global voice routing policy of your organization also applies to one-to-one calls made to the PSTN by users in your organization. If one-to-one calls to the PSTN are enabled for users in your organization, make sure that the global voice routing policy meets the needs of your organization for both types of calls.

> [!NOTE]
> Location-Based Routing isn't available in Microsoft 365 Government Community Cloud (GCC) High or DoD deployments. When enabling Audio Conferencing, verify that no Audio Conferencing users in the GCC High or the DoD environments are enabled for Location-Based Routing.

#### Defining a global voice routing policy

A global voice routing policy can be defined by defining a PSTN usage, a voice route, a voice routing policy, and assigning the new voice routing policy as the global voice routing policy of your organization.

The following steps describe how to define a new global voice routing policy for an organization without one. If your organization already has voice routing policies defined, verify that the following configuration doesn’t conflict with the existing voice routing policies of your organization.

To create a new PSTN usage in a remote PowerShell session in Teams, use the following command:

  ```PowerShell
  Set-CsOnlinePstnUsage -Identity Global -Usage @{Add="International"}
  ```

For additional information, see [Set-CsOnlinePstnUsage](/powershell/module/skype/set-csonlinepstnusage).

To create a new voice route, use the following command:

  ```PowerShell
  New-CsOnlineVoiceRoute -Identity "International" -NumberPattern ".*" -OnlinePstnGatewayList sbc1.contoso.biz -OnlinePstnUsages "International"
  ```

When defining a new voice route for your organization, specify one or multiple of the PSTN online PSTN gateways that have been defined for your organization during the configuration of Direct Routing.

The number pattern specifies which calls will be routed through the specified list of gateways based on the destination phone number of the call. In the example above, calls to any destinations in the world will match the voice route. If you would like to restrict the phone numbers that can be dialed from the meetings of users in your organization, you can change the number pattern to have the voice route match only the number patterns of the destinations allowed. Note that if there are no voice routes that match the number pattern of the destination phone number of a given call, the call will not be routed.

For additional information, see [New-CsOnlineVoiceRoute](/powershell/module/skype/new-csonlinevoiceroute).

To create a new voice routing policy, use the following command:

  ```PowerShell
  New-CsOnlineVoiceRoutingPolicy "InternationalVoiceRoutingPolicy" -OnlinePstnUsages "International"
  ```

If multiple PSTN usages are being defined in the voice routing policy, they will be evaluated in the order in which they are defined. It is recommended that the PSTN usages are defined in the order of the most specific to the more generic in terms of the number patterns of the voice routes associated with the PSTN usages. For example, if a PSTN usage was defined to route calls to the United States, and another PSTN usage was defined to route calls to any other location in the world, the PSTN usage for calls to the United States should be listed in the voice routing policy ahead of the PSTN usage to route calls to any other location in the world.

For additional information, see [New-CsOnlineVoiceRoutingPolicy](/powershell/module/skype/new-csonlinevoiceroutingpolicy).

To assign the new voice route to the global voice routing policy of your organization, use the following command:

  ```PowerShell
  Grant-CsOnlineVoiceRoutingPolicy -PolicyName "InternationalVoiceRoutingPolicy" -Global
  ```

For additional information, see [Grant-CsOnlineVoiceRoutingPolicy](/powershell/module/skype/grant-csonlinevoiceroutingpolicy).

Once the global voice routing policy has been defined, any outbound calls made from meetings organized by users in your organization will be evaluated against the voice routes associated to the PSTN usages of the global voice routing policy. The outbound calls will be routed according to the first voice route that matches the number pattern of the dialed phone number.

### Step 5: Assign Audio Conferencing with Direct Routing for GCC High or DoD licenses to your users

To assign Audio Conferencing with Direct Routing for GCC High or DoD licenses to your user, see [Assign licenses to users](/microsoft-365/admin/manage/assign-licenses-to-users).

### Step 6: (Optional) See a list of Audio Conferencing numbers in Teams

To see the list of Audio Conferencing numbers of your organization, go to [See a list of Audio Conferencing numbers in Microsoft Teams](see-a-list-of-audio-conferencing-numbers-in-teams.md).

### Step 7: (Optional) Set auto attendant languages for the Audio Conferencing dial-in numbers of you organization

To change the languages of the Audio Conferencing dial-in numbers of your organization, see [Set auto attendant languages for Audio Conferencing in Microsoft Teams](set-auto-attendant-languages-for-audio-conferencing-in-teams.md).

### Step 8: (Optional) Change the settings of the Audio Conferencing bridge of your organization

To change the settings of the Audio Conferencing bridge of your organization, see [Change the settings for an Audio Conferencing bridge](change-the-settings-for-an-audio-conferencing-bridge.md).

### Step 9: (Optional) Set the phone numbers included in the meeting invites of the users in your organization

To change the set of phone numbers that are included in the meeting invites of the users is your organization, see [Set the phone numbers included on invites in Microsoft Teams](set-the-phone-numbers-included-on-invites-in-teams.md).

## Audio Conferencing capabilities not supported in Audio Conferencing with Direct Routing for GCC High and DoD

The following are Audio Conferencing capabilities that are not supported in Audio Conferencing with Direct Routing for GCC High and DoD:

- Entry and exit notifications using name recording. For Audio Conferencing with Direct Routing, entry and exit notifications are played in the meeting as tones.

- Disable the usage of toll-free numbers for the meetings specific organizer. User-level controls to restrict the usage of toll-free numbers to join the meetings of your organization aren't applicable to calls routed via Direct Routing.

- Sending notification emails to users when their settings change. Audio Conferencing notification emails aren't supported for Audio Conferencing with Direct Routing for GCC High and DoD.
