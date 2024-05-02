---
title: 'Configure calling policies in Microsoft Teams'
author: mkbond007
ms.author: mabond
manager: pamgreen
ms.topic: conceptual
ms.service: msteams
ms.reviewer: jastark
ms.date: 02/26/2024
audience: admin
search.appverid: MET150
description: Learn how to create, modify, and add users to custom calling policies in Microsoft Teams, and discover various calling policy settings.
ms.localizationpriority: medium
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - Tier1
  - ContentFreshnessFY24
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.callingpolicies.overview
  - seo-marvel-apr2020
  - NewAdminCenter_Update
appliesto: 
  - Microsoft Teams
---

# Calling policies in Teams

In Microsoft Teams, calling policies control which calling and call forwarding features are available to users. Calling policies determine whether a user can make private calls, use call forwarding or simultaneous ringing to other users or external phone numbers, route calls to voicemail, send calls to call groups, use delegation for inbound and outbound calls, and so on.

You can use the global (Org-wide default) policy that's created automatically or create and assign custom policies.

## Create a custom calling policy

Follow these steps to create a custom calling policy.

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Calling policies**.
2. Select **Add**.
3. Turn on or turn off the features that you want to use in your calling policy.
    - For example, to control voicemail for inbound calls, select **On** or **Let users decide** to enable routing of calls to voicemail. To prevent routing to voicemail, select **Off**.
4. Select **Save**.

## Edit a calling policy

Follow these steps to edit an existing calling policy.

1. In the left navigation of the Microsoft Teams admin center, select **Voice** > **Calling policies**.
2. Select the policy or policies that you want to modify, and then select **Edit**.
3. Make the changes that you want, and then select **Save**.

## Assign a custom calling policy to users

[!INCLUDE [assign-policy](includes/assign-policy.md)]

## Calling policy PowerShell cmdlets

To create, modify, retrieve, assign, and remove calling policies, use the following cmdlets:

- [New-CsTeamsCallingPolicy](/powershell/module/teams/new-csteamscallingpolicy)
- [Set-CsTeamsCallingPolicy](/powershell/module/teams/set-csteamscallingpolicy)
- [Get-CsTeamsCallingPolicy](/powershell/module/teams/get-csteamscallingpolicy)
- [Grant-CsTeamsCallingPolicy](/powershell/module/teams/grant-csteamscallingpolicy)
- [Remove-CsTeamsCallingPolicy](/powershell/module/teams/remove-csteamscallingpolicy)

## Calling policy settings

Here are the settings that you can configure for calling policies:

- **Make private calls** - This setting controls all calling capabilities in Teams. Turn this setting off to turn off all calling functionality in Teams.
- **[Cloud recording for calling](call-recording-transcription-captions.md)**
- **[Transcription](call-recording-transcription-captions.md)**
- **[Routing for PSTN calls](inbound-call-routing.md)**
- **[Routing for federated calls](inbound-call-routing.md)**
- **[Call forwarding and simultaneous ringing to people in your organization](user-call-settings.md)**
- **[Call forwarding and simultaneous ringing to external phone numbers](user-call-settings.md)**
- **[Voicemail for inbound calls](set-up-phone-system-voicemail.md)**
- **[Inbound calls can be routed to call groups](call-sharing-and-group-call-pickup.md)**
- **[Delegation for inbound and outbound calls](shared-line-appearance.md)**
- **[Prevent toll bypass and send calls through the PSTN](location-based-routing-enable.md)**
- **[Music on hold for calls](music-on-hold.md)**
- **[Busy on busy during calls](inbound-call-routing.md)**
- **Web PSTN calling** - This setting enables users to call PSTN numbers using the Teams web client. This setting is on by default.
- **[Real-time captions in Teams calls](call-recording-transcription-captions.md)**
- **[Spam filtering](configure-call-spam-filtering.md)**
- **[SIP devices can be used for calls](sip-gateway-configure.md)**
- **[Open apps in browser for incoming PSTN calls](inbound-call-routing.md)**

## Related articles

[Voice policies reference for Microsoft Teams](settings-policies-reference.md#voice)

[Assign policies to your users in Teams](policy-assignment-overview.md)

[Configure call forwarding and delegation settings](user-call-settings.md)

[PSTN connectivity options](pstn-connectivity.md)
