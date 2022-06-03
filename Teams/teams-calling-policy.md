---
title: 'Calling policies in Microsoft Teams: Calling and call-forwarding features'
author: SerdarSoysal
ms.author: tonysmit
manager: serdars
ms.topic: conceptual
ms.service: msteams
ms.reviewer: jastark
audience: admin
search.appverid: MET150
description: Learn how to create, modify, and add users to custom calling policies in Microsoft Teams, as well as various calling policy settings.
ms.localizationpriority: medium
ms.collection: 
  - M365-voice
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.callingpolicies.overview
  - seo-marvel-apr2020
  - NewAdminCenter_Update
appliesto: 
  - Microsoft Teams
---

# Calling and call-forwarding in Teams

In Microsoft Teams, calling policies control which calling and call forwarding features are available to users. Calling policies determine whether a user can make private calls, use call forwarding or simultaneous ringing to other users or external phone numbers, route calls to voicemail, send calls to call groups, use delegation for inbound and outbound calls, and so on.

You can use the global (Org-wide default) policy that's created automatically or create and assign custom policies.

## Create a custom calling policy

Follow these steps to create a custom calling policy.

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Calling policies**.
2. Select **Add**.
3. Turn on or turn off the features that you want to use in your calling policy.
4. To control whether users can route inbound calls to voicemail, select **Enabled** or **User controlled**. To prevent routing to voicemail, select **Disabled**.
5. Select **Save**.

## Edit a calling policy

Follow these steps to edit an existing calling policy.

1. In the left navigation of the Microsoft Teams admin center, select **Voice** > **Calling policies**.
2. Click next to the policy that you want to modify, and then select **Edit**.
3. Make the changes that you want, and then click **Save**.

## Assign a custom calling policy to users

[!INCLUDE [assign-policy](includes/assign-policy.md)]

## Calling policy settings

Here are the settings that you can configure for calling policies.

### Make private calls

This setting controls all calling capabilities in Teams. Turn this off to turn off all calling functionality in Teams.

### Call forwarding and simultaneous ringing to people in your organization

This setting controls whether incoming calls can be forwarded to other users or can ring another person at the same time.

### Call forwarding and simultaneous ringing to external phone numbers

This setting controls whether incoming calls can be forwarded to an external number or can ring an external number at the same time.

### Voicemail is available for routing inbound calls

This setting enables inbound calls to be sent to voicemail. Valid options are:

- **Enabled** Voicemail is always available for inbound calls.
- **Disabled**  Voicemail is not available for inbound calls.
- **User controlled** Users can determine whether they want voicemail to be available.

### Inbound calls can be routed to call groups

This setting controls whether incoming calls can be forwarded to a call group.

### Delegation for inbound and outbound calls

This setting enables inbound calls to be routed to delegates, allowing delegates to make outbound calls on behalf of the users for whom they have delegated permissions. For more information, see [Share a phone line with a delegate](https://support.office.com/article/share-a-phone-line-with-a-delegate-16307929-a51f-43fc-8323-3b1bf115e5a8).

### Prevent toll bypass and send calls through the PSTN

Setting this to **On** will send calls through the PSTN and incur charges rather than sending them through the network and bypassing the tolls.

### Busy on busy is available when in a call

Busy on Busy (Busy Options) lets you configure how incoming calls are handled when a user is already in a call or conference or has a call placed on hold. New or incoming calls can be rejected with a busy signal or can be routed accordingly to the user's unanswered settings. You can enable busy options at the tenant level or at the user level. Regardless of how their busy options are configured, users in a call or conference or those with a call on hold are not prevented from initiating new calls or conferences. This setting is disabled by default.

### Web PSTN calling

This setting enables users to call PSTN numbers using the Teams web client.

### Automatically answer incoming meeting invites

This setting controls whether incoming meeting invites are automatically answered. It's turned off by default. Keep in mind that this setting applies only to incoming meeting invites. It doesn't apply to other types of calls.

### Allow music on hold

This setting allows you to turn on or turn off music on hold when a PSTN caller is placed on hold. It's turned on by default. This setting doesn't apply to call park and boss delegate features.

### Allow SIP devices calling

This setting enables users to use a SIP device to make and receive calls.

### Spam filtering

This setting allows you to control the type of Spam filtering available on incoming calls.

### Call recording, live captions and transcription

These settings allow you to control whether call recording, live captions and transcription are available for the users.

## Related articles

[New-CsTeamsCallingPolicy](/powershell/module/skype/new-csteamscallingpolicy)

[Set-CsTeamsCallingPolicy](/powershell/module/skype/set-csteamscallingpolicy)

[Get-CsTeamsCallingPolicy](/powershell/module/skype/get-csteamscallingpolicy)

[Grant-CsTeamsCallingPolicy](/powershell/module/skype/grant-csteamscallingpolicy)

[Remove-CsTeamsCallingPolicy](/powershell/module/skype/remove-csteamscallingpolicy)

[Assign policies to your users in Teams](policy-assignment-overview.md)
