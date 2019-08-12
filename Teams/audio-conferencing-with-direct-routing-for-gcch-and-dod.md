---
title: "Audio Conferencing with Direct Routing for GCCH and DoD"
author:  LanaChin
ms.author: v-lanac
manager: serdars
ms.reviewer: oscarr
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.collection: 
- M365-collaboration
- Teams_ITAdmin_Help
search.appverid: MET150
audience: Admin
appliesto:
- Skype for Business 
- Microsoft Teams
localization_priority: Normal
description: "Learn how you can use Audio Conferencing with Direct Routing in GCCH and DoD environments."
---

# Audio Conferencing with Direct Routing for GCC High and DoD

Audio Conferencing with Direct Routing for GCC High and DoD enables participants to join Teams meetings in your GCC High or DoD organization by using a phone device. Meeting participants might prefer to use a phone device to join Teams meetings in scenarios such as when internet connectivity is limited or when users are on the road and don’t have access to Teams. Participants can choose to join meetings by either dialing in to a dial-in phone number for your organization or by having the meeting dial out to their phone device.

With Audio Conferencing with Direct Routing for GCC High and DoD, your organization uses its own numbers as dial-in phone numbers and all meeting dial-outs to phone devices are routed via Direct Routing. To enable the service, organizations need to set up Direct Routing and configure phone numbers that can be used as dial-in phone numbers. The requirement to use Direct Routing is different from the Audio Conferencing service that's offered to non-GCC High and non-DoD organizations where the dial-in phone numbers are provided by Microsoft.

## Deploy Audio Conferencing with Direct Routing for GCC High and DoD

### Step 1: Get Audio Conferencing with Direct Routing for GCC High or DoD licenses 

To use Audio Conferencing in GCC High or DoD, your organization and the users in your organization need to have an Audio Conferencing with Direct Routing license assigned. Here are the licenses you need to enable Audio Conferencing with Direct Routing for GCC High or DoD.

- GCC High: An Audio Conferencing - GCC High Tenant license for your organization and Audio Conferencing - GCC High licenses for your users.

- DoD: An Audio Conferencing - DoD Tenant license for your organization and Audio Conferencing - DoD licenses for your users.

A tenant license and at least one user license are required to enable the service. You can't enable the service with only the tenant license or with only user licenses. To get service licenses for your tenant and the users in your organization, contact your account team.

> [!IMPORTANT]
> Users can’t be enabled for Audio Conferencing with Direct Routing until dial-in phone numbers are set up. We recommend that you not assign Audio Conferencing with Direct Routing for GCC High or DoD licenses to users until you set up dial-in phone numbers as outlined in this article.

### Step 2: Set up Direct Routing

To set up Direct Routing, see the following articles:

- [Plan Direct Routing](direct-routing-plan.md)

- [Configure Direct Routing](direct-routing-configure.md)

> [!NOTE]
> When you set up Direct Routing, remember to use the GCC High or DoD-specific FQDNs and ports that are described in these two articles.

### Step 3: Set up dial-in phone numbers

Dial-in phone numbers are the phone numbers that are associated to your Audio Conferencing bridge. These numbers are used by participants to join meetings scheduled by users in your organization. These numbers are also included in the meeting invites of the users who schedule meetings in your organization and on the “Find a local number” page.

#### Define service phone numbers in your tenant

You can use the New-csHybridTelephoneNumber PowerShell cmdlet to define service phone numbers in your tenant that can be used to route calls to the Audio Conferencing service via Direct Routing. 

  ```
  New-csHybridTelephoneNumber -TelephoneNumber <Phone number in E.164 format>
  ```

For example:
  ```
  New-csHybridTelephoneNumber -TelephoneNumber “+14250000000”
  ```

#### Assign the service phone numbers to the Audio Conferencing bridge of your organization

You can assign service phone numbers to the Audio Conferencing bridge of your organization by using the Register-csOnlineDialInConferencingServiceNumber PowerShell cmdlet.

  ```
  Register-csOnlineDialInConferencingServiceNumber -identity <Telephone number in E.164 format> -BridgeId <Identity of the audio conferencing bridge>
  ```

You can see the ID of your Audio Conferencing Bridge using Get-CsOnlineDialInConferencingBridge. For example:

  ```
  $b= Get-CsOnlineDialInConferencingBridge
  Register-csOnlineDialInConferencingServiceNumber -identity 14257048060 -BridgeId $b.identity
  ```

### Step 4: Assign Audio Conferencing with Direct Routing for GCC High or DoD licenses to your users

To assign Audio Conferencing with Direct Routing for GCC High or DoD licenses to your user, see [Assign licenses to users in Office 365 for business](https://docs.microsoft.com/en-us/office365/admin/subscriptions-and-billing/assign-licenses-to-users).

### Step 5: (Optional) See a list of Audio Conferencing numbers in Teams

To see the list of Audio Conferencing numbers of your organization, go to [See a list of Audio Conferencing numbers in Microsoft Teams](see-a-list-of-audio-conferencing-numbers-in-teams.md)

### Step 6: (Optional) Set auto attendant languages for the Audio Conferencing dial-in numbers of you organization

To change the languages of the Audio Conferencing dial-in numbers of your organization, see [Set auto attendant languages for Audio Conferencing in Microsoft Teams](set-auto-attendant-languages-for-audio-conferencing-in-teams.md)

### Step 7: (Optional) Change the settings of the Audio Conferencing bridge of your organization

To change the settings of the Audio Conferencing bridge of your organization, see [Change the settings for an Audio Conferencing bridge](change-the-settings-for-an-audio-conferencing-bridge.md)

### Step 8: (Optional) Set the phone numbers included in the meeting invites of the users in your organization

To change the set of phone numbers that are included in the meeting invites of the users is your organization, see [Set the phone numbers included on invites in Microsoft Teams](set-the-phone-numbers-included-on-invites-in-teams.md)

## Audio Conferencing capabilities not supported in Audio Conferencing with Direct Routing for GCC High and DoD

The following are Audio Conferencing capabilities that are not supported in Audio Conferencing with Direct Routing for GCC High and DoD:

- Entry and exit notifications using name recording. For Audio Conferencing with Direct Routing, entry and exit notifications are played in the meeting as tones.

- Outbound calling restriction policies for Audio Conferencing. User-level controls to restrict outbound calls aren’t applicable to meeting dial-out calls routed via Direct Routing.

- Disable the usage of toll-free numbers for the meetings specific organizer. User-level controls to restrict the usage of toll-free numbers to join the meetings of your organization aren’t applicable to calls routed via Direct Routing.

- Sending notification emails to users when their settings change. Audio Conferencing notification emails aren’t supported for Audio Conferencing with Direct Routing for GCC High and DoD.
