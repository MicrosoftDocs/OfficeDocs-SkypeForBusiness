---
title: 'Configure calling policies in Microsoft Teams'
author: mkbond007
ms.author: mabond
manager: pamgreen
ms.topic: conceptual
ms.service: msteams
ms.reviewer: jastark
ms.date: 01/10/2024
audience: admin
search.appverid: MET150
description: Learn how to create, modify, and add users to custom calling policies in Microsoft Teams, and various calling policy settings.
ms.localizationpriority: medium
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - Tier1
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

## Calling policy settings

Here are the settings that you can configure for calling policies.

- [Make private calls]()
- [Cloud recording for calling]()
- [Transcription](accessibility-guide-admin.md)
- [Routing for PSTN calls](inbound-call-routing.md)
- [Routing for federated calls](inbound-call-routing.md)
- [Call forwarding and simultaneous ringing to people in your organization](user-call-settings.md)
- [Call forwarding and simultaneous ringing to external phone numbers](user-call-settings.md)
- [Voicemail for inbound calls](set-up-phone-system-voicemail.md)
- [Inbound calls can be routed to call groups](call-sharing-and-group-call-pickup.md)
- [Delegation for inbound and outbound calls](shared-line-appearance.md)
- [Prevent toll bypass and send calls through the PSTN](location-based-routing-enable.md)
- [Music on hold for PSTN calls](music-on-hold.md)
- [Busy on busy during calls](inbound-call-routing.md)
- [Web PSTN calling]()
- [Real-time captions in Teams calls](accessibility-guide-admin.md)
- [Spam filtering]()
- [SIP devices can be used for calls](sip-gateway-configure.md)
- [Open apps in browser for incoming PSTN calls](inbound-call-routing.md)

### Cloud recording for calling

This setting controls whether users can record calls. This setting is off by default.

For more information, see [Routing inbound calls](inbound-call-routing.md).

### Prevent toll bypass and send calls through the PSTN

Turning on this setting sends calls through the Public Switched Telephone Network (PSTN) and incur charges rather than sending them through the network and bypassing the tolls. This setting is off by default.

### Web PSTN calling

This setting enables users to call PSTN numbers using the Teams web client. This setting is on by default.

### Spam filtering

This setting allows you to control the type of Spam filtering available on incoming calls. This setting is on by default. This setting has three options:

- **On** Spam filtering is fully enabled. Both Basic and Captcha Interactive Voice Response (IVR) checks are performed. In case the call is considered as spam, the user gets a "Spam Likely" notification in Teams.
- **On without IVR** Spam Filtering is partially enabled. Captcha IVR checks are disabled. A "Spam Likely" notification appears. A call might get dropped if it gets a high score from Basic checks.
- **Off** Spam filtering is completely disabled. No checks are performed. A "Spam Likely" notification doesn't appear.

### SIP devices can be used for calls

This setting enables users to use a SIP device to make and receive calls. This setting is turned off by default.

## Related articles

[Set-CsTeamsCallingPolicy](/powershell/module/skype/set-csteamscallingpolicy)

[Voice policies reference for Microsoft Teams](settings-policies-reference.md#voice)

[Assign policies to your users in Teams](policy-assignment-overview.md)

[Configure call forwarding and delegation settings](user-call-settings.md)

[PSTN connectivity options](pstn-connectivity.md)
